---
title: >-
  Old English automatic lemmatisation (Martín Arista 2026)
category: references
tags: [old-english, lemmatisation, nlp]
sources:
  - "url:https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser"
  - "url:https://acl-bg.org/proceedings/2026/LaTeLL%202026/pdf/2026.latell-1.2.pdf"
source_url: "https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser"
relationships:
  - target: "[[concepts/old-english-lemmatisation]]"
    type: implements
  - target: "[[entities/nerthus-project]]"
    type: related_to
  - target: "[[entities/ycoe]]"
    type: uses
summary: >-
  Character-level Transformer lemmatiser: 67.58 percent lemma accuracy and 82.75 percent UPOS on a YCOE held-out split.
provenance:
  extracted: 0.88
  inferred: 0.08
  ambiguous: 0.04
base_confidence: 0.67
lifecycle: draft
lifecycle_changed: 2026-10-09
tier: supporting
created: 2026-10-09T19:50:00Z
updated: 2026-10-09T19:50:00Z
---

# Old English automatic lemmatisation (Martín Arista 2026)

Javier Martín Arista, “Data Curation, Annotation Quality, and Error Patterns in Old English Automatic Lemmatisation,” *Proceedings of LaTeLL 2026*, pp. 8–17 ([PDF](https://acl-bg.org/proceedings/2026/LaTeLL%202026/pdf/2026.latell-1.2.pdf)). The model card says this conference paper is authoritative where it differs from the companion article in *Procesamiento del Lenguaje Natural* (2026). Weights: [Nerthus-Project/Old_English_Lemmatiser](https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser).

The model is a character-level Transformer encoder–decoder with a joint UPOS head. It maps one word form to `(lemma, UPOS)` with no sentence context. Released checkpoint: `d_model` 512, 8 heads, 4 encoder and 4 decoder layers, about 26.5 million parameters, 140-symbol vocabulary. The papers describe a 98-symbol, 21.5-million-parameter baseline. The card says the evaluation numbers are the released model’s.

## Training and scores

Corpus-only condition: word–lemma–POS triples from [[entities/ycoe|YCOE]] prose (Taylor et al. 2003) and the York–Helsinki poetry corpus (Pintzuk and Plug 2001). After harmonisation: 105,063 instances, split 84,050 / 10,506 / 10,507, 37,627 lemmas, 11.7 percent *ge-* forms, **11.3 percent inconsistently lemmatised types**. Dictionary augmentation (DOE A–I, Bosworth–Toller, DOEC embeddings) was an ablation and is not the released model. VARIOE is listed as a related lemma inventory.

Held-out test: **lemma accuracy 67.58 percent**, **UPOS accuracy 82.75 percent**. A BiLSTM seq2seq baseline reached 53.15 percent lemma accuracy on dev. Word2Vec fusion and a 500-merge BPE both lowered test lemma accuracy (63.53 and 54.66 percent).

Approximate accuracy by UPOS, from the card: ADP ~85, CCONJ ~83, DET ~80, ADV ~75, NOUN ~68, ADJ ~65, VERB ~55, PROPN ~45.

Error mass, as the card states it: strong-verb ablaut about 25 percent, spelling variation about 20 percent, *ge-* about 15 percent. Proper nouns and hapax legomena are the hardest. The card treats human agreement of about 90–95 percent, given the inconsistent gold, as a ceiling.

Augmentation during training substitutes *þ*/*ð*, *æ*/*a*/*e*, and *i*/*y*. That is an orthographic noise model, not a dialect label. See [[concepts/old-english-orthographic-variation]].

## What it does not return

No inflectional class, no case, no gender, no dialect. Context-free, so *þā* as determiner versus adverb is out of scope. It is an analyzer of attested YCOE spellings, not a paradigm generator. See [[concepts/old-english-lemmatisation]].

## Related

- [[references/nerthus-v5-database]]
- [[references/miani-2025-oe-poetry-pos]]
- [[entities/javier-martin-arista]]

## Sources

- [Hugging Face model card](https://huggingface.co/Nerthus-Project/Old_English_Lemmatiser)
- [LaTeLL 2026 paper PDF](https://acl-bg.org/proceedings/2026/LaTeLL%202026/pdf/2026.latell-1.2.pdf)
