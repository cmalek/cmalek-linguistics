---
title: >-
    aenglisc_toolkit: producing academic-quality annotated output
category: concepts
tags: [aenglisc-toolkit, translation, philology, export, tei, provenance]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]"
    type: extends
  - target: "[[references/translation-tools-and-scholarly-editing-standards]]"
    type: derived_from
  - target: "[[entities/bosworth-toller]]"
    type: related_to
  - target: "[[concepts/typography-as-linguistic-signal]]"
    type: related_to
sources:
  - "[[references/translation-tools-and-scholarly-editing-standards]]"
  - "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-current-capabilities]]"
  - "repo:/Users/cmalek/src/personal/aenglisc_toolkit @ 981e093 (models/annotation.py, services/export_pdf.py, utils.py)"
summary: >-
    A plan for output a scholar can cite and reuse: a source record on every gloss, text identifiers, Leipzig-style labels, two note layers, a cited glossary, and TEI and CoNLL-U exports. Evidence for edition conventions is thin.
provenance:
  extracted: 0.25
  inferred: 0.65
  ambiguous: 0.10
base_confidence: 0.45
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:30:00Z
updated: 2026-10-18T22:30:00Z
---

# aenglisc_toolkit: producing academic-quality annotated output

Goal from the request: output with the original text, the Modern English text, and a glossary with context, at an academic standard. The code facts below were read on 2026-10-18; the standards come from [[references/translation-tools-and-scholarly-editing-standards]]. **Decision 2026-10-18: the document is the exported PDF**, so the PDF is the primary artifact and TEI and CoNLL-U (items 6 and 7) are secondary. After the first draft of this page, one real edition was read for its conventions ([[references/mertens-2020-old-english-lives-of-st-martin]]); it is a single research edition, not the field. ^[inferred]

## Evidence from a real edition

Mertens (2020) shows these conventions, each of which maps to a field or a PDF feature:

- **Declared, visible deviations.** Expansions in italics, insertions in square brackets, emendations italicised and commented below the text; "full information" so that readers can disagree. For this app: any normalisation the translator applies (a spelling folded, a word joined, a reading supplied) should be recorded and shown, and the PDF should say which it used. The app already keeps surface spelling apart from the normalised form for search ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]); the question is whether any *edited* reading is marked in print.
- **Identifiers for the text.** Shelfmark and date, Ker and Gneuss numbers, DOE Short Title and Cameron number, in a table of sigla. Optional text metadata, printed on the title page or in the front matter.
- **Facing-page translation that stays close to the Old English**, with source or comparative material in the apparatus beneath the translation. That is where explanatory notes go, not inside the translation.
- **Layout carries an argument**: the editor lays Ælfric's alliterative prose out as half-lines to show the metre. The app marks verse lines with numbers every five lines; a verse versus prose layout toggle per text is the matching option.
- **No glossary at all** in that research edition. A glossary is an audience decision ("different audiences demand different editions", citing Liuzza). Keep it optional per export. ^[inferred]

## What exists

- `Annotation` stores grammar fields, `root`, `modern_english_meaning`, `sense`, `confidence`, but **no field for where a gloss came from** (which dictionary, entry, edition). The sidebar's dictionary button opens `https://bosworthtoller.com/search?q=...`, which records nothing.
- The PDF glossary aggregates by `(root, pos)` with attested forms and genders and cases, but cites no dictionary.
- Exports: PDF (LaTeX via Tectonic), DOCX, project JSON, plain text. Import accepts `.tei`/`.xml`, but there is no TEI export.

## Plan, in order of payoff

1. **A source record per gloss.** Dictionary (Bosworth-Toller, DOE, Clark Hall, other), edition or year, entry or URL, access date. Bosworth-Toller's own citation shows the minimum: headword, editors, Prague 2014 online edition, numeric entry URL. The translator enters or pastes it; the app never fills it. Print it in the glossary. ^[inferred]
2. **Text identifiers.** Per text, optional DOE Short Title and Cameron number plus the edition used. Cheap metadata that makes a citation checkable.
3. **Stable IDs and a manifest.** Stable IDs for tokens and lines, plus app version, schema version, timestamp and a content hash in every export. This supports reproducible citation and reuse.
4. **Leipzig-style labels in the PDF morphology line**, aligned word by word, using the standard abbreviation list; keep the app's own tags in the data. The rules target examples in papers, so apply them to the PDF, not to storage. ^[inferred]
5. **Two note layers** (textual versus explanatory) with line numbers, using the `reledmac` note series A and B and `reledpar` for facing pages. The current exporter is a 1,522-line module that mixes glossary logic with LaTeX emission (Trello F9), so this belongs after that split. Check ƿ, dotted ċ ġ and macrons in the chosen font; Junicode follows the MUFI set ([[entities/junicode]]).
6. **TEI export**: `<lg>/<l n>` for verse, `<ab>` or `<s>` per sentence with `xml:id`, `<w lemma lemmaRef pos msd>` per token, idioms as spans, translation as a second `<div xml:lang="en">` aligned with `<linkGrp>`, and sense, confidence and source records in standOff markup because TEI itself says word attributes are too limited. This is the best format for scholarly reuse and the largest job. ^[inferred]
7. **CoNLL-U** as a cheap secondary export. It is lossy for spans and notes; sense, confidence and TODO would go in `MISC`.
8. **Bibliography export** (BibTeX or CSL JSON) for the sources named in notes. Only the CSL landing page was read.

## Not worth building

TBX, XLIFF and TMX as storage or output. They are terminology and localisation formats, and a single translator working on one text gains nothing from them. DOCX parallel layout has no source and stays second-class. ^[inferred]

## Tensions

- The TEI mapping, source records and manifest add fields the translator must fill. Make every one optional and leave the existing workflow untouched.
- Remembered annotations carry no source record, so a propagated gloss would have no citation. Another reason to mark propagated annotations unreviewed ([[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ux-recommendations]]).

## Open Questions

- Which dictionary does the user actually cite, and is DOE access good enough to record entry IDs?
- Should the glossary group by root and sense, not just `(root, pos)`? That is a content decision for the translator.
- Which published editions does the owner want to resemble? One research edition has been read; Dumbarton Oaks volumes and student editions are known only from review summaries. Check the physical books before fixing a layout.
- Should the PDF print a conventions page (how expansions, emendations and normalisations are marked) so a reader can disagree "on the basis of full information"?

## Related

- [[projects/aenglisc-toolkit/aenglisc-toolkit]]
- [[skills/translating-ancient-texts]]
- [[entities/tei-p5-guidelines]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- [[references/translation-tools-and-scholarly-editing-standards]]
- Repo files named in the front matter.
