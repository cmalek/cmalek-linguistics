---
title: >-
    Translation tools and scholarly editing standards: OmegaT, Weblate, TEI, Leipzig, LaTeX
category: references
tags: [translation, annotation, tei, philology, standards, tooling]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]]"
    type: informs
  - target: "[[concepts/manual-translation-workbench-features]]"
    type: informs
  - target: "[[skills/translating-ancient-texts]]"
    type: related_to
sources:
  - "https://omegat.sourceforge.io/manual-latest/en/chapter.project.folder.html"
  - "https://omegat.sourceforge.io/manual-latest/en/chapter.panes.html"
  - "https://docs.weblate.org/en/latest/workflows.html"
  - "https://docs.weblate.org/en/latest/user/glossary.html"
  - "https://www.tbxinfo.net/"
  - "https://tei-c.org/release/doc/tei-p5-doc/en/html/AI.html"
  - "https://tei-c.org/release/doc/tei-p5-doc/en/html/SA.html"
  - "https://tei-c.org/release/doc/tei-p5-doc/en/html/VE.html"
  - "https://www.eva.mpg.de/lingua/resources/glossing-rules.php"
  - "https://universaldependencies.org/format.html"
  - "https://ctan.org/pkg/reledpar"
  - "https://ctan.org/pkg/leipzig"
  - "https://bosworthtoller.com/70"
  - "https://www.uky.edu/~kiernan/ENG519/oec-guide.htm"
summary: >-
    What CAT tools, TEI, the Leipzig Glossing Rules, CoNLL-U and LaTeX parallel-text packages offer a manual scholarly translator, which parts are machine-dependent and unusable, and how thin the evidence for edition conventions is.
provenance:
  extracted: 0.70
  inferred: 0.22
  ambiguous: 0.08
base_confidence: 0.55
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:00:00Z
updated: 2026-10-18T22:00:00Z
---

# Translation tools and scholarly editing standards

Read 2026-10-18 by a research subagent; some pages by section or `grep`, not in full. The evidence on how published Old English editions lay out notes and glossaries is **weak**: DOE, publisher and edition pages were blocked or not found.

## CAT tools: what maps to manual work

- OmegaT: a project is a plain folder (`omegat.project`, `source`, `target`, `tm`, `glossary`) with a backup of the project file; panes dock, tab, undock and reset with "Restore OmegaT Window". Glossary terms matching the current segment light up in a Glossaries pane, and a shortcut adds an entry from the editor. ([OmegaT manual](https://omegat.sourceforge.io/manual-latest/en/chapter.project.folder.html))
- Weblate: per-string states (Untranslated, Needs editing, Needs rewriting, Needs checking, Translated, Approved, Read-only); an "Inconsistent" check flags a string with more than one translation; glossary entries can be preferred, forbidden or untranslatable. ([workflows](https://docs.weblate.org/en/latest/workflows.html), [glossary](https://docs.weblate.org/en/latest/user/glossary.html))
- Machine-dependent parts: OmegaT's `tm/auto` and `tm/enforce` folders insert TMX translations automatically, and it has fuzzy-match and MT panes. These are what a never-auto-translate tool must not copy.
- TBX (ISO 30042), XLIFF and TMX are exchange formats for terminology and localization. The page read for TBX confirms it exists; XLIFF 2.1 was fetched but not read. Whether they fit a root-and-sense glossary with citations is the agent's judgement. ^[inferred]

## Scholarly annotation standards

- TEI `<w>` takes `lemma`, `lemmaRef` ("a pointer to a definition of the lemma ... in an online lexicon"), `pos` and `msd`; TEI itself says word attributes are limiting and points to standOff markup for richer or competing analyses. Parallel translation uses `<ab>` blocks with `xml:id` and symmetric `corresp` or `<linkGrp>`; verse uses `<lg>` and `<l n="...">`. ([TEI AI](https://tei-c.org/release/doc/tei-p5-doc/en/html/AI.html), [SA](https://tei-c.org/release/doc/tei-p5-doc/en/html/SA.html), [VE](https://tei-c.org/release/doc/tei-p5-doc/en/html/VE.html))
- Leipzig Glossing Rules: "Glosses are part of the analysis, not part of the data"; word-by-word alignment; a standard abbreviation list. They are meant for examples in a paper or book, and "When an entire corpus is tagged, somewhat different considerations may apply". ([Leipzig](https://www.eva.mpg.de/lingua/resources/glossing-rules.php))
- CoNLL-U has 10 tab-separated fields, with `MISC` for anything else; spans and notes do not fit it. ([UD format](https://universaldependencies.org/format.html))
- INCEpTION says "Nothing enters your data until you accept it" but also runs recommenders that learn as you go. CATMA, Recogito and Alpheios were read at landing-page depth only.

## Citation and conventions

- Bosworth-Toller's recommended citation gives headword, editors, the Prague 2014 online edition and a numeric entry URL (`bosworthtoller.com/70`). ([entry page](https://bosworthtoller.com/70)) The app's sidebar opens a search URL, not an entry URL. ^[inferred]
- A University of Kentucky guide (read in part) shows DOE Short Title and Cameron number as the standard text identifiers. The DOE's own page could not be read. ([guide](https://www.uky.edu/~kiernan/ENG519/oec-guide.htm))
- Elements that read as academic (stable line numbers, a text identifier, sparse notes, a glossary that cites its dictionary) are the agent's inference from the above and one review; no published edition's layout was checked. ^[ambiguous]

## Typesetting

- `reledpar` (columns or facing pages) belongs to `reledmac`, which has five note levels A to E for critical and familiar footnotes; `paracol` is simpler with no line-number machinery; `leipzig` and `glossaries` supply gloss abbreviations and glossaries. CTAN marks `reledpar`, `paracol` and `expex` "Tagged PDF – incompatible". Junicode 2 follows the MUFI recommendation. Nothing was found on DOCX parallel layout.

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-academic-output-plan]]
- [[concepts/manual-translation-workbench-features]]
- [[entities/omegat]]
- [[entities/tei-p5-guidelines]]
- [[entities/bosworth-toller]]
- [[entities/junicode]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- The pages in the front matter, plus the Weblate checks page, `ctan.org/pkg/paracol`, `ctan.org/pkg/glossaries`, the Junicode repository and the INCEpTION, CATMA, Recogito and Alpheios landing pages.
