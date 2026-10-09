---
title: >-
    CliRunner and a Rich stderr Console
category: skills
tags: [python, testing, click]
relationships:
  - target: "[[projects/wyrdcraeft/wyrdcraeft]]"
    type: related_to
sources:
  - "agent:wyrdcraeft-session-2026-10-08"
summary: >-
    CliRunner does not capture a Rich Console bound to stderr at import time; monkeypatch the print helper in the module under test.
provenance:
  extracted: 0.90
  inferred: 0.10
  ambiguous: 0.00
base_confidence: 0.42
lifecycle: draft
lifecycle_changed: "2026-10-09"
tier: supporting
created: 2026-10-09T15:54:00Z
updated: 2026-10-09T15:54:00Z
snapshots:
  - "[[_raw/_archived/2026-10-08-click-clirunner-rich-stderr-console-not-captured|2026-10-08-click-clirunner-rich-stderr-console-not-captured]]"
---

# CliRunner and a Rich stderr Console

Click tests on [[projects/wyrdcraeft/wyrdcraeft]] that asserted on `print_info` text failed even when the command succeeded: `CliRunner` never saw the message.

## Key Ideas

- A helper that writes to `Console(stderr=True)` created at **import** time binds the real `sys.stderr`. `CliRunner.invoke` swaps `sys.stderr` later, so that console bypasses capture. `result.output` stays empty of those lines.
- Output from `click.echo`, `Prompt.ask`, and a console bound to **stdout** is captured as usual.
- Monkeypatch the helper **in the module that looks it up**, not in the utility module, and record messages:

```python
messages: list[str] = []
monkeypatch.setattr(command_module, "print_info", messages.append)
result = runner.invoke(cli, [...])
assert any(m.startswith("Added 2") for m in messages)
```

- Confirmed on the wyrdcraeft queue, mark-diacritics, and import-variants CLI tests.

## Open Questions

- Recreating the Console inside the helper (after invoke) might capture stderr without monkeypatching; not tried here. ^[inferred]

## Sources

- [[_raw/_archived/2026-10-08-click-clirunner-rich-stderr-console-not-captured.md]]
