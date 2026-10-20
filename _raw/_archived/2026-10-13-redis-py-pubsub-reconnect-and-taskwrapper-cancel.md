---
title: "redis-py PubSub reconnects silently; TaskWrapper await re-raises CancelledError"
category: skills
tags:
  - topic/redis-py
  - python/asyncio
  - resilience
summary: "redis-py 8.1.0 PubSub retries and resubscribes internally with no signal to the caller; awaiting a cancelled TaskWrapper raises CancelledError into shutdown code."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "access.caltech-proxy"
base_confidence: 0.6
lifecycle: draft
lifecycle_changed: 2026-10-13
provenance:
  extracted: 0.8
  inferred: 0.2
sources:
  - "access.caltech-proxy session (2026-10-13)"
---

## redis-py PubSub recovers from short drops without telling the caller

**Behavior:** In redis-py 8.1.0 (`redis/asyncio/client.py`), `PubSub._execute` wraps reads in `conn.retry.call_with_retry`. On a connection error it calls `_reconnect`, and `PubSub.on_connect` resubscribes to every channel. A drop shorter than the retry budget therefore produces no exception from `listen()`, but any messages published during the gap are lost (pub/sub has no replay).

**Explanation:** The retry budget is bounded. Once exhausted, `listen()` raises `ConnectionError`. `listen()` is `while self.subscribed: ...`, so it can also end cleanly when the connection closes.

**Workaround / Pattern:** A watchdog that wants a catch-up after every gap cannot rely on seeing an exception. Either disable the internal retry for the pub/sub connection so every drop surfaces, or hook `PubSub.on_connect`. Also set `health_check_interval`, which defaults to 0, so a half-open TCP connection raises instead of hanging.

**Confirmed by:** reading the installed source. Not yet tested against a live Redis. The card reproduced the terminal case against Redis 7. Prod runs Redis 7.

## Awaiting a cancelled TaskWrapper raises into cleanup

**Behavior:** In `acproxy/utils.py`, `TaskWrapper.__await__` returns the inner task's awaitable. If the wrapped coroutine re-raises `CancelledError` (the correct pattern), `cleanup_background_tasks` (`cancel()` then `await app[...]`) raises `CancelledError` during shutdown. The current tasks avoid this by returning from `except asyncio.CancelledError`.

**Workaround / Pattern:** When changing a background task to propagate cancellation, make the shutdown awaits tolerate `CancelledError`, for example with `contextlib.suppress`.

**Confirmed by:** code reading only.

**Notes:** `docker-compose.yml` uses `redis/redis-stack:latest`, which is unpinned. Pin a Redis 7 tag for failover testing.
