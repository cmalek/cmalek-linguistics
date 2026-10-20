---
title: >-
    Mertens 2020: The Old English Lives of St Martin of Tours, edition and study
category: references
tags: [old-english, editing, translation, philology, edition-conventions]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]]"
    type: informs
  - target: "[[references/translation-tools-and-scholarly-editing-standards]]"
    type: extends
  - target: "[[entities/dictionary-of-old-english]]"
    type: related_to
sources:
  - "https://doi.org/10.17875/gup2017-1033"
  - "https://univerlag.uni-goettingen.de/handle/3/isbn-978-3-86395-313-3"
  - "paper-search CLI (crossref, openalex, semantic, google_scholar), 2026-10-18"
summary: >-
    A recent open-access Old English edition read first-hand for its conventions: a transparency rule, marked expansions and emendations, facing-page translation with source apparatus, DOE and Cameron identifiers, and no glossary.
provenance:
  extracted: 0.80
  inferred: 0.15
  ambiguous: 0.05
base_confidence: 0.60
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T23:30:00Z
updated: 2026-10-18T23:30:00Z
---

# Mertens 2020: The Old English Lives of St Martin of Tours

Andre Mertens, *The Old English Lives of St Martin of Tours: Edition and Study* (Göttingen University Press; dissertation PDF `mertens_diss.pdf`, open access). It was found with `paper-search` and read from the PDF on 2026-10-18: the contents, the manuscript sigla table and the Editorial Policy chapter (pp. 155–164). The rest was not read. It is one edition by one editor, a research edition and not a student one, so it shows one set of conventions and not the field's. ^[inferred]

## Structure

Manuscript sigla and list of abbreviations; a long study; then Editions. Each text has Manuscripts, Editorial Note, Language, and "TEXT with Translation, Sources and Comments"; then a General Commentary, appendices (a parallel-text edition of three manuscripts; one late manuscript edited on its own) and a bibliography. **There is no glossary** in the contents, and a text search finds no glossary section.

## Conventions it states

- **Transparency as the governing rule.** Quoting Irvine, "[s]cholars must have the opportunity to disagree with editorial changes on the basis of full information". The editor also cites Liuzza that "different audiences demand different editions".
- **Conservative emendation.** "I emended in the edited text only in very rare cases", always marked in italics and commented on in the apparatus below the text. Gneuss's rule is cited: whenever the editor deviates from the manuscript, the reader's attention must be drawn to it.
- **Expansions are never silent.** Abbreviations are expanded and set in italics (tironian *nota* as *and* or *ond*, crossed thorn as *þæt*, the nasal tilde). Insertions go in square brackets. Page breaks are marked with a vertical bar and the folio or page number sits in the margin.
- **Letters.** Wynn becomes *w* and yogh becomes *g*; þ, ð and æ stay. Accents are kept "even if their exact purpose is unclear", and manuscript punctuation is kept (punctus, punctus versus and elevatus rendered by dot and semicolon).
- **Silent changes are few and declared**: joining words split by stray spaces (*ge haten* to *gehaten*), no inserted hyphens in compounds.
- **Facing page.** A modern English translation sits opposite the Old English; the Latin source text sits in the apparatus below the translation. "The translation adheres closely to the Old English text." For the verse-like Ælfric texts, half-line translation was dropped because word order had to change to show subject and object.
- **Layout is an argument.** The editor sets Ælfric's alliterative prose as half-lines with a caesura space, against Skeat's long lines and Mitchell and Robinson's prose layout, because only a verse layout shows the metre.
- **Identifiers.** A sigla table gives each manuscript's shelfmark and date, Ker catalogue number and Gneuss Handlist number, and for each item the DOE Short Title and Cameron number (for example `LS 17.2 (MartinVerc 18) / B3.3.17.3`, the Cameron number following Frank and Cameron 1973).

## What this changes on the vault pages

It turns the earlier "what reads as academic" inference into evidence for one edition: identifiers, declared and marked deviations, a source apparatus and a closely literal facing translation. It also shows that a glossary is audience-dependent. See [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]].

## Other leads from the literature search

Titles and metadata only; the papers were not opened.

- Di Biase-Dyson, Kammerzell, Werning, "Glossing Ancient Egyptian: Suggestions for adapting the Leipzig Glossing Rules" (2009): a model for adapting the rules to a historical language.
- Lahaussois, "The translation tier in interlinear glossed text" (2016, HAL open): how the free-translation line is treated.
- Pagan and Seiler, "Multilingual Annotations in Ælfric's Glossary in London, British Library, MS Cotton Faustina A X: A Commented Edition" (2019).
- Zavrl, "Chaucer's Pardoner in Slovenian and the significance of paratext in making meaning in translation" (2023); Ruokkeinen and Liira, "Material approaches to exploring the borders of paratext" (2019).
- Search summaries, not opened pages: Dumbarton Oaks Medieval Library reviews describe a volume as an introduction, Old English on the verso and translation on the recto, "pared-down textual notes" and fuller "Notes on the Translation"; one review calls the Clayton volume uncluttered, with no macrons or footnotes. A review of a student edition describes "unobtrusive footnotes" for emendations plus commentary notes keyed to line numbers. These come from `WebSearch` summaries. ^[ambiguous]

## Tool note

`paper-search-mcp` is installed but fails to start (it needs `mcp<2`) and was not connected as an MCP server this session; the `paper-search` CLI from the same package worked with `-s crossref,openalex,semantic,google_scholar`. Google Scholar results carry mangled titles.

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]]
- [[references/translation-tools-and-scholarly-editing-standards]]
- [[skills/translating-ancient-texts]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- The Göttingen University Press PDF (contents, sigla, Editorial Policy) and the `paper-search` results of 2026-10-18.
