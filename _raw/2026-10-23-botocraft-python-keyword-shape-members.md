---
title: "botocraft sync: Python-keyword botocore members break ruff formatting"
category: skills
tags:
  - topic/botocraft
  - topic/code-generation
  - topic/pydantic
summary: "A botocore member named `lambda` made the generated service file unparseable; fix with a `rename` in the service's models.yml, not in botocraft.sync."
tier: supporting
related: []
extends: null
contradicts: null
superseded_by: null
capture_source: claude-session
project: "botocraft"
base_confidence: 0.85
lifecycle: draft
lifecycle_changed: 2026-10-23
provenance:
  extracted: 0.9
  inferred: 0.1
sources:
  - "botocraft session (2026-10-23)"
---

## Python-keyword shape members fail `ruff format` during `botocraft sync`

**Problem:** `botocraft sync` died with `ruff: Failed to parse .../tmpXXXX/<service>.py:5602:5: Invalid assignment target`. The temp file is deleted on failure, so the error points at nothing on disk.

**Root cause:** A botocore shape member whose name is a Python keyword (here `lambda` on `HarnessHookTarget` in bedrock-agentcore-control) is emitted verbatim as `lambda: "X | None" = None`. `ServiceGenerator.write()` in `botocraft/sync/service.py` runs `ruff format` on that code, which fails to parse it.

**Debugging tip:** On ruff failure `write()` prints the whole generated source with 0-indexed line numbers, then the ruff error. The ruff line number is 1-indexed, so find the line prefixed `N-1` in the log. Run `botocraft sync --service <name>` with `PATH=.venv/bin:$PATH` (the subprocess calls bare `ruff`).

**Fix:** add a secondary-model field rename in `botocraft/data/<service>/models.yml`. The generated field gets `Field(alias="lambda")`, so the wire name is unchanged.

```yaml
secondary:
  HarnessHookTarget:
    fields:
      lambda:
        rename: lambdaConfiguration
```

**Confirmed by:** `botocraft sync --service bedrock-agentcore-control` exits 0 and emits `lambdaConfiguration: HarnessHookLambdaTarget = Field(default=None, alias="lambda")`.

**Notes:**
- The same rename already existed for `InterceptorConfiguration` and `McpTargetConfiguration`; grep models.yml for `lambdaConfiguration` first.
- A `rename` drops the `| None` from the type. Adding `python_type: "X | None"` on the field made the later `ruff check --fix` step fail (cause not investigated).
- Do not edit `botocraft.services.*` (generated) and ask before changing `botocraft.sync`; auto-renaming keyword members in the generator is a possible follow-up.
