---
title: >-
  redis-py PubSub reconnects silently; awaiting a cancelled TaskWrapper raises
category: skills
tags: [redis-py, asyncio, resilience]
relationships:
  - target: "[[skills/split-python-module-into-package]]"
    type: related_to
sources:
  - "agent:access.caltech-proxy-session-2026-10-13"
summary: >-
  redis-py 8.1.0 PubSub retries and resubscribes with no signal to the caller, losing messages from the gap; awaiting a cancelled TaskWrapper raises CancelledError into shutdown.
provenance:
  extracted: 0.8
  inferred: 0.2
  ambiguous: 0.0
base_confidence: 0.4
lifecycle: draft
lifecycle_changed: "2026-10-15"
tier: supporting
created: 2026-10-15T00:00:00Z
updated: 2026-10-15T00:00:00Z
snapshots:
  - "[[_raw/_archived/2026-10-13-redis-py-pubsub-reconnect-and-taskwrapper-cancel|2026-10-13-redis-py-pubsub-reconnect-and-taskwrapper-cancel]]"
---

# redis-py PubSub reconnects silently; awaiting a cancelled TaskWrapper raises

Both findings come from reading source, not from a live failure test. The first is checked against the installed redis-py 8.1.0 source only; the terminal case (retry budget exhausted) was reproduced against Redis 7, and prod runs Redis 7.

## PubSub recovers from short drops without telling the caller

In `redis/asyncio/client.py`, `PubSub._execute` wraps reads in `conn.retry.call_with_retry`. On a connection error it calls `_reconnect`, and `PubSub.on_connect` resubscribes to every channel.

```mermaid
sequenceDiagram
    participant L as listen()
    participant P as PubSub._execute
    participant R as Redis
    L->>P: read
    P->>R: read
    R--xP: connection drops
    P->>P: _reconnect, on_connect resubscribes
    P->>R: read (retry)
    Note over L,R: no exception reaches listen(); messages published in the gap are lost
```

- A drop shorter than the retry budget raises nothing from `listen()`. Pub/sub has no replay, so messages published during the gap are gone.
- Once the budget is exhausted, `listen()` raises `ConnectionError`. `listen()` is `while self.subscribed: ...`, so it can also end cleanly when the connection closes.
- A watchdog that wants a catch-up pass after every gap cannot count on seeing an exception. Either disable the internal retry on the pub/sub connection so every drop surfaces, or hook `PubSub.on_connect`.
- Set `health_check_interval` (default 0), so a half-open TCP connection raises instead of hanging.

## Awaiting a cancelled TaskWrapper raises into cleanup

In `acproxy/utils.py`, `TaskWrapper.__await__` returns the inner task's awaitable. If the wrapped coroutine re-raises `CancelledError` (the correct pattern), `cleanup_background_tasks` (`cancel()` then `await app[...]`) raises `CancelledError` during shutdown. The current tasks avoid it by returning from `except asyncio.CancelledError`. When a background task is changed to propagate cancellation, make the shutdown awaits tolerate it, for example with `contextlib.suppress`.

## Test setup

`docker-compose.yml` uses `redis/redis-stack:latest`, which is unpinned. Pin a Redis 7 tag before failover testing.

## Sources

- [[_raw/_archived/2026-10-13-redis-py-pubsub-reconnect-and-taskwrapper-cancel]]
