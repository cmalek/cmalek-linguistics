---
title: "Testing click commands that print through a Rich stderr console"
category: skills
tags:
  - topic/python
  - testing
  - click
summary: "CliRunner does not capture a Rich Console bound to stderr at import time; monkeypatch the print helper to record messages."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "wyrdcraeft"
base_confidence: 0.9
lifecycle: draft
lifecycle_changed: 2026-10-08
provenance:
  extracted: 0.9
  inferred: 0.1
sources:
  - "wyrdcraeft session (2026-10-08)"
---

## CliRunner misses output from a module-level Rich stderr console

**Behavior:** A click command that reports through a helper like `print_info`, which writes to a `Console(stderr=True)` created at import time, leaves `result.output` without that text, so assertions on the message fail even though the command ran.

**Explanation:** The console binds to the real `sys.stderr` when the module is imported. `CliRunner.invoke` swaps `sys.stderr` later, so the already-bound console bypasses the capture. Output from `click.echo`, `Prompt.ask` and a console bound to stdout is captured normally.

**Workaround / Pattern:** Monkeypatch the helper in the module that calls it and record the messages:

```python
messages: list[str] = []
monkeypatch.setattr(command_module, "print_info", messages.append)
result = runner.invoke(cli, [...])
assert any(m.startswith("Added 2") for m in messages)
```

Patch the name in the module under test (where it is looked up), not in the utility module.

**Confirmed by:** the wyrdcraeft queue, mark-diacritics and import-variants CLI tests passed with this pattern.
