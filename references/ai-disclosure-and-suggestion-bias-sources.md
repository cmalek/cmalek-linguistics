---
title: >-
    AI disclosure rules and suggestion-bias evidence for a manual translation tool
category: references
tags: [ai, ethics, translation, ux, provenance]
relationships:
  - target: "[[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]]"
    type: informs
  - target: "[[concepts/manual-translation-workbench-features]]"
    type: informs
sources:
  - "https://publicationethics.org/guidance/cope-position/authorship-and-ai-tools"
  - "https://style.mla.org/citing-generative-ai-updated-revised/"
  - "https://www.chicagomanualofstyle.org/qanda/data/faq/topics/Documentation/faq0422.html"
  - "https://aclweb.org/anthology/2017.mtsummit-commercial.10.pdf"
  - "https://dl.acm.org/doi/10.1145/2470654.2470718"
  - "https://pmc.ncbi.nlm.nih.gov/articles/PMC3240751"
summary: >-
    COPE, MLA and Chicago rules for crediting AI text, plus one MT study showing suggestion bias and one showing post-editing gains; the evidence that suggestions anchor translators is thin and mixed.
provenance:
  extracted: 0.70
  inferred: 0.20
  ambiguous: 0.10
base_confidence: 0.50
lifecycle: draft
lifecycle_changed: "2026-10-18"
tier: supporting
created: 2026-10-18T22:00:00Z
updated: 2026-10-18T22:00:00Z
---

# AI disclosure rules and suggestion-bias evidence

Read 2026-10-18 by a research subagent. Only abstracts or introductions were read for the three studies.

## Disclosure rules

- COPE: "AI tools cannot meet the requirements for authorship as they cannot take responsibility for the submitted work"; authors "must be transparent in disclosing ... how the AI tool was used and which tool was used". ([COPE](https://publicationethics.org/guidance/cope-position/authorship-and-ai-tools))
- MLA: do not treat the tool as an author; cite it "whenever you paraphrase, quote, or incorporate into your own work any content" it created, and acknowledge functional uses "like editing your prose or translating words". The 2025 revision asks for the model version and a stable conversation URL. ([MLA 2025](https://style.mla.org/citing-generative-ai-updated-revised/))
- Chicago: credit generated text; if edited, "you should say so". ([Chicago](https://www.chicagomanualofstyle.org/qanda/data/faq/topics/Documentation/faq0422.html))
- APA's page returned no content; no journal-level policy beyond these three was found.

## Suggestion bias

- Picinini and Ueffing (MT Summit XVI, 2017): about 18 "bias errors" per 1,000 words from MT influence on post-editors, most often "ambiguous modifiers, terminology errors, polysemy, and omissions". English to Portuguese, about 15k words, e-commerce, statistical MT; abstract and introduction read. ([paper](https://aclweb.org/anthology/2017.mtsummit-commercial.10.pdf))
- Green et al. (CHI 2013), abstract only: post-editing "leads to reduced time and, surprisingly, improved quality for three diverse language pairs". This points the other way for professional MT post-editing. ([ACM](https://dl.acm.org/doi/10.1145/2470654.2470718))
- Goddard, Roudsari and Wyatt (2011), clinical decision support: automation bias is "the tendency to over-rely on automation"; it "can be reduced by decreasing on-screen detail ... and providing supportive information rather than commands". Not a translation study. ([PMC3240751](https://pmc.ncbi.nlm.nih.gov/articles/PMC3240751))
- No study of reading-with-lookup tools (Alpheios, Perseus) and translator behaviour was found.

## Reading

The case that suggestions anchor a translator rests on one industrial MT study plus a clinical review, against one study where suggestions helped. It is a design instinct with some support, not a settled result, and should be stated that way. ^[inferred]

## Related

- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-ai-context-policy]]
- [[concepts/manual-translation-workbench-features]]
- [[projects/aenglisc-toolkit/concepts/aenglisc-toolkit-intent]]
- [[synthesis/Research: Qt and Translation Workbench Best Practice]]

## Sources

- The pages in the front matter.
