---
title: "Incrementally update the Old English literature review"
category: skills
tags: ["old-english", "research", "literature"]
relationships:
  - target: "[[concepts/old-english]]"
    type: related_to
sources: ["references/old-english-2016-2026-corpus.json"]
created: 2026-10-28T18:35:13.294185+00:00
updated: 2026-10-28T19:40:00-07:00
summary: "Add deduplicated batches to the same Old English review, revise the cumulative synthesis, and preserve evidence scope and coverage history."
provenance:
  extracted: 0.9
  inferred: 0.1
  ambiguous: 0.0
base_confidence: 0.9
lifecycle: draft
lifecycle_changed: 2026-10-28
---


# Incrementally update the [[concepts/old-english|Old English]] literature review

## Established scope

The user is an Old English student with experience conducting literature searches manually. They want the whole field, publications from January 1, 2016 through October 28, 2026, and classification by **topics and methodology**. Main corpus: journal articles and scholarly book chapters. Books and editions are separate. The user selected **scoping review**, approved abstracts when they state both topic and methodology, and requested incremental synthesis into the same page at a scale of hundreds of sources.

Do not restart the scope interview or repeat the ARS review-form note. Preserve the October 28, 2026 cutoff unless the user asks to extend it. Do not create a schedule unless requested.

## Canonical artifacts

- Master: [[synthesis/Research: Old English Scholarship 2016–2026]]. Update this page in place.
- Full chart: [[references/old-english-2016-2026-literature-map]].
- Structured source of counts and record metadata: `references/old-english-2016-2026-corpus.json`.
- Protocol and exact user decisions: [[references/old-english-scoping-review-protocol]].
- Batch history and coverage: [[references/old-english-review-batch-log]].
- Dimensions: [[concepts/old-english-research-topics]] and [[concepts/old-english-research-methodologies]].

## Each update

1. Read these artifacts and the last completed batch. Reuse source IDs and classifications. Select an undercovered source family, period, or subject using the saved next-batch plan; do not merely find more examples of already prominent topics.
2. Aim for 50–100 additional main records per batch, adjusted to actual eligible sources and access. Search bibliographic reviews, venue tables of contents, and edited-collection contents as well as targeted keywords. Record the actual queries, date, sources searched, access failures, and candidate decisions from the start. A target is not a claim of available evidence or a stopping rule.
3. Verify titles, authors, publication type, dates, and URLs against publisher/journal/institutional records. Preserve original publication and online years separately. Reprints and new digitization dates are not new studies.
4. Deduplicate first by case-insensitive DOI, then normalized title with author and year checks. Reconcile preprints/published versions and corrections explicitly. Preserve stable IDs; assign new IDs without renumbering older records. Put unresolved leads in a candidate queue outside the included counts.
5. Chart topics and methods separately. An informative abstract is sufficient; record its URL and the supporting method description or concise paraphrase. Distinguish frameworks, analytical procedures, and evidence sources. Do not infer a method from a title alone. Record missing methods as unspecified; mark classifications provisional when the basis is an interview or summary rather than the abstract. Never mark a source as personally read by the user.
6. Integrate the batch into the existing corpus and literature chart. Append a batch receipt with new IDs, duplicates/exclusions, cumulative group counts, metadata corrections, and unresolved questions. Keep main papers, books/editions, adjacent experiments, and supplementary material distinct.
7. **Rewrite the relevant synthesis passages.** State what the new batch adds, supports, qualifies, contradicts, or overturns. Revise topic/method families when justified and record the change. Preserve disagreement and evidence-access limits. Do not leave the old synthesis unchanged with a new batch essay appended underneath.
8. Recompute coverage tables from the cumulative records. Counts describe the retrieved corpus, not publication prevalence across the whole field. Label retrieval gaps as search gaps until broader evidence establishes a research gap.
9. Check DOI/title duplicates, dates/cutoff, required metadata, methods/evidence basis, group counts, table formatting, and resolving internal links. Check a sample of classifications against the cited abstracts, focusing on new or ambiguous labels.
10. Update the research manifest through its lock and the memory index/log/hot cache through `obsidian-wiki memory sync`. Refresh the configured QMD collection after writes. Report the batch’s actual additions, cumulative counts, changed conclusions, remaining gaps, and next retrieval target.

## Evidence limits to carry forward

B001 contains 49 main records and 64 records of all types. It is pilot coverage. B002, completed 28 October 2026, raised the cumulative main count to 108 and the all-groups count to 126. B003, the same day, raised those counts to 140 and 161 after deduplicating late retrieval returns. The review still does not represent the whole field. B001 has no complete discovery/exclusion register; later batches can improve auditability but cannot repair that missing history by inventing counts. No authenticated citation-index searches, independent dual screening, whole-corpus critical appraisal, or comprehensive retraction/COI audit has yet occurred. The review remains a draft, not a claim of full PRISMA-ScR compliance.

A useful stopping discussion considers coverage of relevant venues, languages, years, and subfields and whether later batches still change the map. Reaching any particular source count alone does not establish completeness.
