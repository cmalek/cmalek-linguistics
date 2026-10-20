---
title: "Syntacticus treebank data: authoritative XML and CoNLL-X"
category: "references"
tags: ["corpus", "treebank", "nlp"]
sources: ["repo:github.com/syntacticus/syntacticus-treebank-data"]
summary: "The clipped README distinguishes complete PROIEL XML annotation from the alternate CoNLL-X distribution."
provenance: {"extracted": 0.7, "inferred": 0.3, "ambiguous": 0}
base_confidence: 0.5917
lifecycle: "draft"
lifecycle_changed: "2026-10-18"
tier: "supporting"
created: "2026-10-18T19:48:28.152600+00:00"
updated: "2026-10-18T19:48:28.152600+00:00"
snapshots:
  - "[[_raw/_archived/GITHUB syntacticus-treebank-data 2026-10-18|GITHUB syntacticus-treebank-data 2026-10-18]]"
---

# Syntacticus treebank data: authoritative XML and CoNLL-X

The captured README describes raw annotated data for the Syntacticus collection and identifies two distribution formats.

| Format | What the README establishes |
| --- | --- |
| PROIEL XML | Authoritative source files containing all available annotation: morphological, syntactic, and information structure, plus complete text, punctuation, and section headers |
| CoNLL-X | An alternate available format; the clip does not say that it retains every XML field |

Use the XML when preserving all annotations is a requirement. Treat the alternate format as a separate representation whose field coverage needs checking. ^[inferred]

[[references/old-english-texts-iswoc]] is the related treebank reference already in this vault. [[concepts/nlp-corpus]] supplies the general corpus context. The clip does not establish which languages or texts are present, release completeness, licensing, or conversion fidelity; those questions require the data and schema, which were not fetched here.

## Sources

- [[_raw/_archived/GITHUB syntacticus-treebank-data 2026-10-18.md]]
