---
title: "3 Morphology Sphere"
source: "https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter3.xhtml"
author:
  - "Mohamed Zakaria Kurdi"
published: 2026-08-01
created: 2026-08-23
description: "3Morphology Sphere3.1. Elements of morphology Morphology is a branch of linguistics that focuses on the way in which words are formed from morphemes. Morphemes are the smallest linguistic..."
tags:
  - "linguistics"
citation: "Kurdi (2016), \"Natural Language Processing and Computational Linguistics\", Wiley-ISTE"
---
## 3.1. Elements of morphology

Morphology is a branch of linguistics that focuses on the way in which words are formed from morphemes. Morphemes are the smallest linguistic unit which hold any meaning; thus, a word can be composed of one or more morphemes. For example, *book, cat* and *house* are simple words, while *books, finis hed* and *dis miss* are complex words because they are made up of multiple morphemes. There are two types of morphemes: lexical morphemes and grammatical morphemes. Also called *monemes*, lexical morphemes designate common objects such as *book, computer, city* or *flight*. These morphemes are distinguished by their number in a given language; it is always possible to add to the list of lexical morphemes with new morphemes, which are generally referred to as neologisms. Grammatical morphemes, on the other hand, concern words that play a grammatical role in a sentence, such as prepositions, articles and pronouns. Because these groups of words cannot in practice be modified by speakers of a language, they constitute closed groups. Thus, it is possible to add a new noun to designate a new object, but not to add a new preposition or pronoun.

The consideration of morphology as an independent branch of linguistics like phonology, syntax and semantics is not unanimous within the linguistic community. Certain syntactic theories, such as distributed morphology, posit that the role of syntax is to make all of the combinations required to construct a sentence, in terms of both word construction and the formation of syntactic units \[HAL 93\]. In addition, there are many interconnections between phonology and morphology. As we saw in the previous chapter, several phonological phenomena manifest during the realization of a phonological marker such as the plural. The relationship between semantics and morphology does not need to be proven since the meaning of an utterance is a function of the meanings of the morphemes that compose it.

In this chapter, we will try to cover key morphological properties of several langauges, such as English, French, Arabic and Turkish. For a general overview of morphology and its theoretical tendencies, we refer readers to \[VIL 93, LIB 09\] and \[KIR 04\].

### 3.1.1. Morphological typology

In terms of morphological typology, there are two major language groups: isolating languages and inflected languages.

*Isolating languages*, also called analytic languages, are languages (such as Vietnamese and Chinese) in which the morpheme-to-word ratio is very close to 1:1. In other words, in the majority of cases, the words in these languages are formed of a single morpheme, which means that their form hardly changes at all. These languages are rare and replace morphological information with the syntactic context represented by the order of words/morphemes. For example, a word such as *prehistoric* is equivalent, in these languages, to the following word/morpheme sequence: pre historic.

*Inflected* (or synthetic) *languages* constitute a linguistic family in which there is a principal morpheme, the stem, surrounded by affixes. This group can be further divided into two subgroups: fusional languages and agglutinative languages.

In *fusional languages* such as Arabic, words are not modified by adding morphemes before or after the stem, but rather by inserting new phonemes within the stem itself. Take the example of the Arabic stem k-t-b (“to write”) which gives a multitude of derived words (see [Table 3.1](#tab3-1)).

[**Table 3.1.**](#Rtab3-1) *Examples of Arabic words derived from the stem k-t-b*

| Arabic word | Translation | Arabic word | Translation |
| --- | --- | --- | --- |
| Kataba | wrote | Kateb | writer |
| Kaataba | correspond | Maktaba | library |
| Kitab | book | Maktab | office |
| Kutub | books | Maktoub | written |

*Agglutinative languages* are another type of inflected languages. Unlike fusional languages, these languages form words from a number of morphemes that are completely separate from one another. For example, in the Turkish language, which is the most representative of this group, words begin with a stem followed by one or more suffixes \[OFL 94\]. The difference between this and other inflected languages is that it is possible to construct entire sentences with this procedure because the suffixes can be prepositions, possessives, etc. (see [Table 3.2](#tab3-2) for examples).

[**Table 3.2.**](#Rtab3-2) *Examples of words in Turkish*

| Word | Morphemes | Translation |
| --- | --- | --- |
| sütsüz | süt-süz / milk-without | without milk |
| bankadan | bank-adan / bank-from | from the bank |
| gitti | gitt-i / went-he | he went |
| akarsuyunuz | akar-su-yunuz / river-2PP-POSS | our river is |

Finally, we should mention that the classification presented above does not apply to all languages as there are languages, such as Japanese, which show mixed characteristics.

### 3.1.2. Morphology of English

Throughout the different phases of its development, English has been influenced by linguistic sources that have left their mark on its morphological system. Besides Latin and Greek, which form the classical substratum, English words have been borrowed from languages as varied as French, Spanish, German and Arabic. This has contributed to the creation of a rich lexical and morphological system.

#### 3.1.2.1. Types of morphemes in English

English words are generally composed of a stem and an optional set of affixes. The stem, as a morpheme that cannot be removed, is the true morphological base of an English word. For example, in a plural word such as *books* we can remove the morpheme – *s* but not the morpheme *book*.

Stems may be surrounded by multiple secondary morphemes called affixes. These are classified into one of three types according to their placement in relation to the stem: prefixes, suffixes and circumfixes.

Prefixes are morphemes that precede the stem. In the vast majority of cases, they do not exist independently of the stem. Their role is essentially semantic, in that they do not affect the grammatical role of the word. Over time, some prefixes may become part of the lexicon, and consequently, be used independently as stems, like the prefix *ex*, which means ex-husband or ex-wife when used alone rather than as part of a word. In some cases, multiple prefixes may be placed before the stem, as in *anticonstitutional* in which the prefixes *anti* and *con* are used. Other examples are provided in [Table 3.3](#tab3-3).

[**Table 3.3.**](#Rtab3-3) *Examples of prefixes commonly used in English*

| Prefix | Meaning | Examples |
| --- | --- | --- |
| im– | opposite | impossible, imprudent, imparity |
| pre– | before | prehistoric, premeditate, premature |
| anti– | Against | anti-abortion, anti-war, antibiotic |
| extra– | beyond | extrasensorial, extracellular, extrarural |
| over– | too much | overcook, overdose, overkill |
| para– | self | automobile, autobiography, autocracy |

Suffixes are morphemes that come after the stem. Unlike prefixes, their role is not limited to modifying the meaning of the word but extends to the modification of its grammatical function. For example, if we add the suffix *–ly* to the adjective *slow*, we get the adverb *slowly*. For this reason, we classify suffixes according to the grammatical category they give; thus, there are nominal suffixes such as – *tion* and – *ment* and adjectival suffixes like *–ful* and *–al*. In [Table 3.4](#tab3-4) are provided some examples of common suffixes.

[**Table 3.4.**](#Rtab3-4) *Examples of suffixes commonly used in English*

| suffix | Meaning | Examples |
| --- | --- | --- |
| – ist | Person who practices an activity | specialist, guitarist, linguist |
| – er, –or | Agent of an action | employer, actor, lawyer |
| – ism | Doctrine, belief, practice | sophism, abolitionism, animism |
| – able | Able to be | reasonable, portable, affordable |
| – ac | Pertaining to | cardiac, paranoiac, insomniac |
| – al | The action or process of | remedial, denial, trial |

Finally, in bound or amalgamated morphemes, the affix is inseparable from the stem. For example, we cannot separate the stem from the suffix in verbs such as *began* or *bought*. Because these are conjugated verbs, we know that this is a case of a stem followed by an ending that is inseparable from it.

#### 3.1.2.2. Allomorphs

Similar to the concept of an allophone, an allomorph involves phonetic or graphic variants of the same morpheme. In other words, this is a case in which two chains of phonemes or characters (depending on whether we are speaking of the oral or written case, respectively) correspond to the same morpheme. These variations may be contextual or combinatorial. In this case, the context in question may be phonological in nature, the plural morpheme *–s* is probably the most obvious case. In fact, in a word like *hats* it is realized without modification \[s\], while it is realized as \[z\] in words like *dogs* and finally as \[əz\] in words such as *boxes*.

#### 3.1.2.3. Morpheme combination operations

There are several morphological combination operations we can use to form words from phonemes in English; these include inflection, derivation, composition and blending.

Inflection (or inflexion) is an operation that consists of combining the stem with a grammatical morpheme to give number for a noun, or time and person for a verb. They belong to the same category as the original, and the semantic difference between the base word and the new word, obtained via inflection, is easily noticeable. The purpose of inflection is, thus, essentially syntactic, such as gender or number agreement. For example, the following pairs of words are created via inflection: *livre/livres* (plural), *veuf/veuve*, (feminine), *mangent/mangeons* (conjugation).

Like inflection, derivation consists of combining the stem with a grammatical morpheme. It is distinguished by the fact that it produces a more significant semantic change. In addition, words composed by derivation generally belong to a different syntactic category than the starting word. For example, via the derivation process, we obtain the adverb *constitutionally* from the adjective *constitutional*, which is itself constructed from the noun *constitution*, which is itself obtained from the verb *constitute*. In other words, in this case, we have the following chain of words: verb → noun → adjective → adverb.

Composition, or compounding, is another type of word creation, in which at least two stems are juxtaposed within the same word. From an orthographical point of view, these words are written using three conventional methods which have no linguistic motivation. The first method consists of stringing together morphemes without spaces or hyphens, as in *darkroom, railroad* and *smalltalk*. In the second method, words are composed of stems separated by a space, as in *ice cream* and *real estate*. Finally, in the third method, words are composed of stems separated by a hyphen, as in *merry-go-round* and *actor-director*. There are several criteria which allow us to identify compound words. For example, nothing can be inserted between the parts of a compound word. Likewise, the semantics of compound words is a special case, since the overall meaning of a compound word is not equal to the assembled meanings of its components.

Blending, is a procedure that consists of joining the start of one word to the end of another. For example, the word *mockumentary* is obtained in the following way: mock + documentary. These words are usually used in the fields of science, technology, advertising and even poetry, in order to create nouns specific to new objects or concepts. Common examples include internet (international network), malware (malicious software) and bionic (biology + electronic).

#### 3.1.2.4. Abbreviation

Abbreviation consists of creating a word by simplifying one or more other words. Truncation is a simplification procedure that consists of removing one or more syllables, as in *lab oratory, math ematics, Pat rick*, *Ed ward*, etc. Another form of simplification consists of using the initials of the words in an expression or a complex noun. Words obtained in this way are called acronyms. Some of these acronyms are widely known, such as EU (European Union) and NASA (National Aeronautics and Space Administration), while others, like EMNLP (Empirical Methods on Natural Language Processing) and LDC (Linguistic Data Consortium) are known only in specialized fields.

### 3.1.3. Parts of speech

In the context of syntactic parsing, it is also useful to identify the part of speech of each word in the text or sentence under consideration. Given the many ambiguities that can exist, this procedure is anything but trivial. In reality, it is often necessary to use a combination of morphological structure and syntactic context in order to attain this objective, sometimes extending to include the semantic and practical levels. This explains why some specialists consider part-of-speech annotation to be part of syntax rather than morphology.

The classic categorization of many European languages is an inheritance from Latin and goes back to the beginning of the last century. It posits the existence of 9 categories, a view that is currently being questioned in general linguistics (see \[CRE 95\]). We will avoid these controversies and give a general description of the various categories and their basic syntactic properties.

The parts of speech adhere to the general classification of the language’s words into two categories: open categories and closed categories. Open categories, the members of which cannot be limited, include the categories: noun, verb, adjective, and adverb. The closed categories, on the other hand, include so-called functional categories such as determiners, prepositions, conjunctions, interjections, and numerals.

Along with verbs, nouns are universally acknowledged as categories that must be present in all known languages. Nouns in English vary in number but unlike languages such as French and Arabic they don’t have gender (feminine or masculine). Besides, there are nouns in English that do not vary in number, such as *sheep* and *salmon*. Some invariant nouns can sometimes have a plural form as well. For example, *antelop* and *antelopes* can be used as plural of *antelop* the same goes for fish that can have *fish* or *fishes* as plurals. Some nouns are always singular, like *physics, news* and *furniture*, while others, like *trousers* and *scissors*, are always plural. Based on syntactic and semantic criteria, we can distinguish two types of nouns: common nouns, also called substantive nouns; and proper nouns. Substantive nouns are almost always preceded by a determiner, and sometimes by an adjective, which can also be placed after the noun. In terms of syntax, the noun, or more precisely the noun phrase of which it is the core, plays a variety of roles, including subject, object, attribute or complement of another noun (see example [\[3.1\]](#Requ3-1)).

[\[3.1\]](#equ3-1) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image110_c1052.jpg)

In French, proper nouns have also a gender, and in certain exceptional cases may vary in number. However, this causes a semantic change, as in the group of proper nouns in example [\[3.2\]](#Requ3-2).

[\[3.2\]](#equ3-2) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image110_c1053.jpg)

In terms of syntax, the particular characteristic specific to proper nouns is that they can form a noun phrase alone or plays its role at least. Although usually used alone, a proper noun can also be preceded by a determiner, as in [\[3.3\]](#Requ3-3).

[\[3.3\]](#equ3-3) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image110_c1054.jpg)

In English, adjectives are invariable while they vary in both gender and number in French depending on the nature of the noun to which they are connected. In English, there are three major types of adjectives: attribute, predcative and nominal. Attributive adjectives are used before (prepositive) or after (postpositive) a noun, typically playing the role of head of the nominal phrase. Predicative adjectives come after the noun to which they are linked with a copula or another linking mechanism. Finally, when the noun is elided, the adjective can play the role of head of a Noun Phrase (NP). In this case, it is called a nominal adjective (see example [\[3.4\]](#Requ3-4)).

[\[3.4\]](#equ3-4) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image111_c1055.jpg)

Verbs are morphologically variable in number, person, modality, time and voice. Preceded by their subjects and followed by their objects in the preferential order of English, they are the core of both verbal groups and sentences. Verb complements take on highly variable functions and forms, such as direct object complement, indirect object complement, infinitive and gerund. Several typologies exist for classifying verbs on the basis of their relationships with their complements: intransitive verbs, direct transitive verbs, indirect transitive verbs, verbs that take two complements, etc. Likewise, we will consider the relationship between the verb and its subject; defined subject: *he walks, John works*, indefinite subject: *somebody walks* or in which the subject is the agent of the action, as with the verbs *beat, attack* and *give* or in which it is the patient, as in *die*.

As emphasized by \[CRE 95\], the category of adverbs includes the most syntactically heterogeneous words; in other words, this category contains groups of words that cannot be categorized otherwise. These include words such as circumstantial adverbs including *somewhere now* and *tomorrow*; and adverbs of place such as *here, there* and *far*; of manner such as *slowly, softly* and *loudly*; and of degree, such as *very* and *too*. Generally invariant in English, we have some cases where two adverbs differ in number such as somtime and sometimes. However, in French, in unusual cases, the adverbs agree in number with the names or adjectives they modify as in example [\[3.5\]](#Requ3-5).

[\[3.5\]](#equ3-5) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image112_c1056.jpg)

The role of adverbs is to modify, particularly adjectives and verbs. One of the specific characteristics of many adverbs is that they play roles considered to be secondary; for this reason, they can be removed without causing a significant semantic change.

Determiners, which occur together with nouns, may vary in number, gender (like in French) and even person in the case of possessives. These elements are adjacent to nouns and can only be separated from them by attributive adjectives, sometimes preceded by one or more adverbs. Only one determiner can be used per noun, except in the case of quantifiers such as *all* and *other*. In French, there are cases where the gender or number of a noun cannot be determined, so determiners help solve the ambiguity, as in *un vieux* (an old) versus *des vieux* (det\_plural old)*, un élève* (det\_masc student) versus *une élève* (det\_fem student), etc. This ambiguity is even more significant in spoken language since the same spoken form of some nouns can correspond to the written forms of the feminine singular, masculine singular or feminine plural. Note that the category of determiners includes several subcategories, including articles, possessive adjectives, demonstrative adjectives, indefinite adjectives, numeral adjectives and interrogative adjectives.

Pronouns act as substitutes for noun phrases. For this reason, they are highly variable in terms of gender, number and person. In terms of morphology, they can correspond to words such as *he, me* or *nothing*. This category includes a multitude of subcategories including demonstrative pronouns, possessive pronouns, relative pronouns, interrogative pronouns, indefinite pronouns and numeral pronouns (e.g. *two have left their homes*).

Prepositions are invariable and play an important role in the structuring of linguistic elements. As we have already seen, they serve to create certain compound words such as *on top of* and also introduce noun or indirect object complements as in example [\[3.6\]](#Requ3-6).

[\[3.6\]](#equ3-6) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image113_c1057.jpg)

### 3.1.4. Terms, collocations and colligations

In this section, we will look at the different types of word clusters that are constructed on the basis of syntactic and/or semantic criteria. The recognition and correct processing of these clusters is an important factor in the understanding of any text. These clusters take various forms such as *technical* terms, collocations and colligations.

What we mean by “terms” includes a heterogeneous number of linguistic phenomena including common nouns, named entities and noun phrases that may be composed of other noun phrases. The difference between an ordinary word and a term is that the latter identifies a specific concept in a specialized field, such as *bovine spongiform encephalopathy* in the field of medicine. From a linguistic point of view, terms constitute a cohesive unit both syntactically and semantically, even if the term cannot stand as a sentence on its own.

Expressions such as *an awful lot, a good deal, kick the bucket* and *curriculum vitae* are particular linguistic units requiring specific treatment at the lexical, syntactic and semantic levels, and which are commonly known as collocations. Coined by Firth \[FIR 57\], the term *collocation* designates a group of words with strong statistical relationships. The weight attributed to the role of grammar in this relationship has been the subject of intense debate within the linguistic community. Traditionally, the terms phraseological units, idiomatic expressions, fixed expressions \[MIS 87, GRO 96\] and semi-fixed expressions \[LAM 05\] have been preferred. A more recent view considers words to have a linguistic charge, and to exercise an attraction or repulsion for other words \[REN 07\]. We refer readers to the summaries by \[PAR 98\] and \[PEC 04\] for a more complete overview. Note that the concept of collocation is closely linked to the analysis of corpora, which supports the calculation of co-occurrence statistics (see [Table 3.5](#tab3-5) for some examples in French literature).

[**Table 3.5.**](#Rtab3-5) *Examples of collocations in three French literary corpora \[LEG 12\]*

| Collocation |  | Balzac | Hugo | Zola |
| --- | --- | --- | --- | --- |
| Faire fortune | Get rich | 131.31 | – | 21.38 |
| Faire faillite | Going bankrupt | 74.96 | 14.58 | 23.27 |
| Faire banqueroute | Going bankrupt | 7.99 | 5.98 | 5.91 |

Another type of lexical cluster that should be mentioned is *colligation*. This is a multidimensional unit in which relationships of lexical co-occurrence have the same importance as the pattern of grammatical relationships of words \[HUN 01, HOE 04\] (see [Table 3.6](#tab3-6)).

[**Table 3.6.**](#Rtab3-6) *Examples of colligation*

| Pattern | Examples |
| --- | --- |
| The most + adjective | The most advanced   The most rich |
| N/NP + replaced + by | The old car is replaced by a new one. |

Even if the use of such patterns is not tightly integrated within syntactic theories, these constructions have been the subject of various applications in the field of task-oriented dialog systems. Moreover, collocations and colligations are used in applications aimed at the classification of texts according to author or era.

## 3.2. Automatic morphological analysis

Modern computers have enough memory to store all the inflected forms of a language. However, devices with limited memory such as mobile phones and handheld computers, require more compact methods for storing these various forms. Likewise, certain languages, as we have seen, have a very rich morphology that makes their raw data very heavy to store. For a general introduction to the questions of computational morphology, we refer readers to \[ROA 07\] and \[BEE 03\].

### 3.2.1. Stemming

Steming is the simplest form of morphological processing. It consists of returning inflected, derived or compound words to a canonical form, called the lemma, which is not necessarily a word or morpheme in the language. Generally speaking, the goal behind lemmatization is to identify the concept or approximate meaning of the word. Used particularly in the field of information retrieval, lemmatization gives more flexibility to textual information retrieval by making it possible to find words that are morphologically different but conceptually similar. For example, the words *consolatory* and *constancy* are stemmed into the lemmas *consolatori* and *constanc* respectively that are not part of the English vocabulary. Likewise, in French, the lemma *mainten*, which is neither a word nor a morpheme, corresponds to the words *maintenir* (keep), *maintenant* (now), *maintenait* (have kept), *maintenaient* (have kept in plural), *maintint* (kept), etc.

Several approaches have been proposed for automatic lemmatization. Some are more statistical, while others are more heuristic or based more or less on linguistic criteria.

#### 3.2.1.1. Successor variety

The successor variety approach was proposed by Margaret Hafer \[HAF 74\]. Influenced by structural linguistics, this approach attempts to identify the boundaries between morphemes based on the distribution of phonemes as observed in a large corpus. The basic criterion is the number of letters likely to follow the current chain in the corpus. To illustrate the function of this approach, imagine that we have a micro-corpus containing the following words: able, ape, beatable, fixable, read, readable, reading, reads, red, rope and ripe. To find the value of the successor for a word such as *read*, we create a table of successors (see [Table 3.7](#tab3-7)).

[**Table 3.7.**](#Rtab3-7) *Successors of the word read \[FRA 92\]*

| Prefix | Successors | Letters |
| --- | --- | --- |
| R | 3 | E, I, O |
| RE | 2 | A, D |
| REA | 1 | D |
| READ | 3 | A, I, S |

With a larger corpus, the number of successors shrinks until we reach the boundary of a segment, and then increases. The question at this stage is one of establishing the boundary of the lemma. The simplest (and most controversial) solution consists of establishing a theoretical value for the number of successors. Since there are no concrete criteria for choosing this threshold, error is fairly likely. One heuristic approach consists of considering a boundary to have been reached when the number of occurrences of a letter is greater than that of the two letters that precede and follow it, respectively. Statistical criteria such as entropy have also been used (see \[MAN 99\]).

#### 3.2.1.2. Porter stemming algorithm

Developed in the 1970s as part of an information retrieval project at Cambridge University in the United Kingdom, the Porter stemming algorithm is distinguished by its simplicity and effectiveness \[POR 80\], making it one of the most popular algorithms for lemmatization \[WIL 06a\]. Versions for several European languages has been proposed by \[POR 06\]. However, a detailed presentation and analysis of the algorithm is beyond the scope of our objectives in this book. Consequently, we will limit ourselves to a general description of its features.

In the first stage, we tag letters that correspond to vowels as v. A sequence of consonants or vowels with length greater than zero will be denoted by C and V, respectively. This yields the following general pattern: \[C\](VC)m\[V\], where the square brackets denote the arbitrary presence of their content and m is a constant that can be zero or more. Then a series of rules of the form (condition) S1 – > S2 are applied to remove the suffixes. The general meaning of these rules is as follows: S1 is replaced by S2 if the word is ending with the suffix S1, and the stem before S1 satisfies the given condition. Note that the condition may be expressed in terms of the value of m, such as m > 1. The rules are organized into groups that are applied in cascade. Some examples of transformations after this stage are given as follows:

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image116_c1061.jpg)

#### 3.2.1.3. N-gram-based clustering

This approach aims at the clustering of morphologically similar words without identifying the lemma. From a functional point of view, in many applications, this goes back to the same thing since the objective of the lemmatization process is to reduce the variety of morphological forms without the modular use of higher processing related to the syntax or semantics of the text.

The principle consists of identifying the n-grams of each word in the corpus and then calculating their similarity to other words using the Sørensen–Dice coefficient ([equation \[3.7\]](#Requ3-7)) \[DIC 45\]:

[\[3.7\]](#equ3-7) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image117_c1062.jpg)

where:

1. – Z is the number of unique bigrams shared by both words;
2. – X is the number of unique bigrams in the first word;
3. – Y is the number of unique bigrams in the second word.

Take the French words *bonbon* and *bonbonne* (carboy). First, we will identify the bigrams that make up each of these two words. We must also identify the bigrams whose occurrence in the word is greater than one (see [Table 3.8](#tab3-8)). Note that a trigram- (or higher) based approach is also possible, but the principle is the same.

[**Table 3.8.**](#Rtab3-8) *Bigrams of the words bonbon and bonbonne*

| Word | Bigrams | Repeated bigrams |
| --- | --- | --- |
| bonbon | bo on nb bo on | bo on |
| bonbonne | bo on nb bo on ne | bo on |

As we can see in [Table 3.8](#tab3-8), the word *bonbon* has five bigrams, two of which are repeated and the word *bonbonne* has six bigrams, two of which are also repeated. For our example, this gives: sim = 2\*1/1+2 = 0.66. In a real application with a corpus of *n* words, we would then move on to calculating the distances between all of the words and storing the result of this calculation in a matrix of *n* rows and *n–1* columns. The matrix thus constructed serves to support a clustering algorithm used to find morphologically similar words.

### 3.2.2. Regular expressions for morphological analysis

First developed by Stephen Kleene \[KLE 56\], regular expressions are aimed at specifying classes of character chains through the specification of patterns. A chain is a sequence of symbols: numbers, letters, spaces, tabulations and punctuation marks. In this context, spaces are symbols like any other and can be represented by a specific chosen character. The simplest form of regular expressions is a simple character chain. Regular expressions are conventionally placed between two slashes / /. For example, the expression /Ouagadougou/ is used to recognize all chains containing the subchain *Ouagadougou*, such as “Ouagadougou *is an African capital* ” or “ *Ouagadougou is a city* ”. Some other examples are given in [Table 3.9](#tab3-9).

[**Table 3.9.**](#Rtab3-9) *Some regular expressions with simple sequences*

| Expression | Recognized chains |
| --- | --- |
| /Ouagadougou/ | Ouagadougou is the capital city of Burkina Faso. |
| /city/ | The city of Damascus was among the most splendid cities in the world. |
| /play/ | He played football during his entire life. |

Square brackets can be used to recognize a class of characters that is a set of equivalent characters. Look at the examples in [Table 3.10](#tab3-10).

[**Table 3.10.**](#Rtab3-10) *Regular expressions with character categories*

| Expression | Recognized  category | Examples |
| --- | --- | --- |
| /\[Oo\]uagadougou/ | Ouagadougou   ouagadougou | Ouagadougou is a modern city.   Ouagadougou is far from here. |
| /\[xyz\]/ | x, y or z | Lexique, zanini |
| /\[0123456789\]/ | 0, 1 or 2 etc. | un ensemble de 1 jusqu’à 9 |

We can use shortcuts to designate continuous sequences of characters as follows:

1. – \[a–z\] one character among all lower-case letters;
2. – \[e–h\] one character among e, f, g, h;
3. – \[A–Z\] one character among all upper-case letters;
4. – \[0–9\] a single digit.

We use special operators like Kleene operators, anchors, joker operators and disjunction to increase the power of regular expressions.

The Kleene star operator **\***, represented by the symbol \*, means zero or more occurrences of the character or pattern that precedes it. For example, /b\*/ recognizes a chain of zero or more *b* and /vv\*/ recognizes a chain of one or more *v*. Likewise, the expression /\[0–9\]\*/ recognizes any number, such as 124, 6547 or 098, as well as empty chains. The operator? is a particular case of the operator \* because it designates the preceding character or expression, or nothing. Thus, the expression /cars?/ is used to recognize the chain *cars* or *car.*

The Kleene operator + is used to render the occurrence of the previous character or regular expression mandatory at least once. In other words, in order to be satisfied, this operator requires one or more occurrences of what precedes it. Thus, the expression /goo+d/ is used to recognize *good* or *goood* or *gooood*, etc.

To express more specific limitations regarding the number of occurrences of any item, we use two curly brackets { *n* }, with *n* corresponding to the number of repetitions of the element. For example, /hello{5} the world/ recognizes *Hellooooo the world* but not *Hellooo the world.* A variant of this operator follows the syntax {n, m}, with *n* and *m* expressing the minimum and maximum limits, respectively, of a range of occurrences. For example, the expression /cour{2,4}/ will recognize *courr, courrr*, and *courrrr*, but not *cour* or *courrrrrrrr.* If the upper limit in the expression {n} is not specified, so it will recognize at least *n* occurrences of the preceding chain. Thus, the expression /Voila{3}/ recognizes *voilaaa* and *voilaaaaaa* but not *voila* or *voilaa*.

As its name suggests, the Joker operator, designated by a period, is a character that recognizes all other characters except the back slash \\, which is a character that plays an important role in the syntax of regular expressions. For example, the expression /fin.r/ recognizes the chains *finar, finir, finur, finmr, finxr*, etc. Likewise, the expression /see.\*future/ recognizes chains that begin and end, respectively, with *see* and *future*, such as *see the future* and *see the beginning of new future*.

Anchors constitute a set of operators, with various uses, having to do with the position of the regular expression in the chain. Here are some examples:

1. – ^ tags the starting character of the row;
2. – $ marks the end of the row;
3. – \\b end of a word;
4. – \\B not the end of a word.

For example, the expression /^The animals hunt.$/ specifies a row that contains only the chain *The animals hunt*. / \\b44/ this regular expression recognizes the chain 44 in *Mary is 44 year old today* because it follows the end of the word.

The copy operator is used to memorize part of the chain in order to reproduce it identically later on. Suppose that we are trying to create an expression in which we have two identical subchains such as: the world is beautiful the world is crazy. To do this, we can tag the first chain using the operator () and the second using \\1. The (.\*) is beautiful. The \\1 is crazy. Of course, we can repeat the copying to get new subchains, such as: the world is crazy. The (.\*) is beautiful. The \\1 is superb. The \\2 is vaste.

The disjunction operator, which takes the form of a transverse bar, |, is used to express an alternative between two possibilities. Thus, the expression /flower | rose/ recognizes either the chain *flower* or the chain *rose.*

To combine multiple operators within one expression, we must be aware of their precedence. It is important to know that simple character chains have higher precedence than the disjunction character, which has lower precedence than all other operators. A list of operators ranked by priority is given in [Table 3.11](#tab3-11).

[**Table 3.11.**](#Rtab3-11) *Priority of operators in regular expressions*

| Operators | Precedence | Examples |
| --- | --- | --- |
| Parentheses | Highest | () |
| Counters/repetition |  | \* +? {} |
| Sequences and anchors |  | ^ $ \\b \\B |
| Disjunction | Lowest | \| |

To understand the concept of precedence properly, let us take two examples. The verb *connaître* (to know) can be written in two ways in French: *connaître* and *connaitre*. To express this fact with a regular expression, all we need to do is use the disjunction operator to choose between everything to its left and everything to its right. This gives the following expression: connaitre | connaître. A more elegant way of expressing this divergence of writing consists of using two parentheses as follows: conna(i|î)tre. Since parentheses have higher priority than disjunction, disjunction is limited to sequences of characters between parentheses. Moreover, because repetition operators or counters, have higher priority than sequence operators, the expression hello\* can interpret *hello* or *helloo*, while the expression (hello)\* can interpret *hello hello* or *hello hello hello* due to the higher priority of parentheses.

Regular expressions have been used as a means of optimizing the process of creating morphological analyzers, as well as executing multiple wordretrieval tasks in a given corpus. For example, a regular expression can be used to find all the words in a corpus that share the same affix or to specify rules of morphological analysis. They have also been used for the syntactic analysis of temporal expressions such as dates of events and tokenization \[KAR 97\].

### 3.2.3. Informal introduction to finite-state machines

First introduced in 1945 by Warren McCulloch, a neurophysiologist, and Walter Pitts, a logician, finite-state machines (FSM) were developed to model the activity of a neuron that gives an output of 1 when active and an output of 0 when inactive \[MCC 43\]. According to this approach, each neuron receives input from the other neurons to which it is connected and possesses an activation function. Between 1951 and 1956, Kleene continued this work by defining finite-state machines and regular expressions and by proving the equivalence between them. Today, FSM are used in a large number of fields including NLP, particularly for morphological and syntactic analysis and the modeling of sequential logic circuits and communication protocols. For an introduction to FSM in the context of NLP in general, and morphology in particular, see \[ROC 96, KAR 05, KAP 97\] and \[SIL 15\].

Informally speaking, an FSM consists of a finite number of states and transitions. It is known that Markov chains, which we saw in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter2.xhtml), are formally equivalent to FSM, with the probability of transition on the arcs of a Markov chain being the only difference. Likewise, FSM are formally equivalent to regular expressions, which means that any regular expression can be expressed in the form of an FSM, and *vice versa*.

Let us begin by examining an FSM to express or recognize an expression of encouragement or surprise that can have the following forms: *well!, bravo!, very good*!, *very very good!, very very very good!*, etc. To do this, we need an FSM that includes four states and appropriate transitions between these states. Using a graph is an effective way to represent an FSM (see [Figure 3.1](#fig3-1)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image122_c1070.jpg)

Figure 3.1. FSM for expressions of encouragement

As we can see in [Figure 3.1](#fig3-1), we have two arcs to go from the initial state e0 to the state e2 with two different words: *bravo* and *well*. Another important point is the cyclical transition to state e <sub>1</sub>, which makes it possible to repeat the word *very* an unlimited number of times. Finally, the final state e <sub>3</sub> is marked with a double circle to indicate that it is a valid stopping point. This prevents the recognition of an incomplete chain such as *very* or *very good* (without an exclamation point) as a valid chain. Another way of representing the information contained in an FSM consists of constructing a so-called transition table. For our example, it takes the form of [Table 3.12](#tab3-12).

[**Table 3.12.**](#Rtab3-12) *FSM transition table for expressions of encouragement*

| **Input state** | **very** | **bravo** | **well** | **good** | **!** |
| --- | --- | --- | --- | --- | --- |
| e0 | e1 | e2 | e2 | ϕ | ϕ |
| e1 | e1 | ϕ | ϕ | e2 | ϕ |
| e2 | ϕ | ϕ | ϕ | ϕ | e3 |
| e3 | ϕ | ϕ | ϕ | ϕ | ϕ |

FSM are equivalent to a type of grammar called regular grammar or typethree grammar (in Chomsky’s hierarchy of formal grammars), which we will examine in [Chapter 4](https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter4.xhtml). Likewise, we have seen that Kleene’s work proved the equivalence of regular expressions to FSA. A conversion algorithm has even been suggested to automate the conversion of a regular expression into a machine \[THO 68\]. To illustrate the relationship between FSM and regular expressions, let us look at the examples of basic cases shown in [Figure 3.2](#fig3-2).

As we can see in [Figure 3.2](#fig3-2), the repetition of an element by the \* operator is obtained via a cyclical link. Likewise, the step backward with an empty element represented by the symbol ɛ enables the infinite repetition of the sequence *ab* in the expression: (ab)+. Finally, the disjunction operator in the third expression is translated via an alternative route, starting from the same state.

In the context of NLP, it is important to distinguish between two types of FSM: deterministic machines and non-deterministic machines, which can be considered as different formal variants for expressing the same thing. It has been shown that for each non-deterministic FSM there is a deterministic equivalent that recognizes exactly the same language (see \[HOP 01\] for a discussion of the proof).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image124_1.jpg)

Figure 3.2. Examples of regular expressions with their FSM equivalence

A deterministic FSM is a machine which, with a given input chain, always carries out the same processing. This means that each transition in a deterministic FSM always leads to one single state for a given symbol being processed. For example, the FSM that corresponds to the expression a\*b in [Figure 3.2](#fig3-2) is a deterministic FSM. As we can see, there is always a single destination state no matter what symbol is analyzed.

On the other hand, a non-deterministic FSM is not required to obey the constraint of the uniqueness of analysis for a given chain and may, therefore, allow a multitude of destination states from the same initial state and with analysis of the same symbol. There are generally two reasons for the nondeterminism of a machine: empty transition and cyclical transition. The FSM of the expression a+b in [Figure 3.2](#fig3-2) is an example of a non-deterministic machine with a cyclical transition. We can see that from the initial state e <sub>0</sub> and with the symbol *a* being analyzed, we can reach either state e <sub>0</sub> with the cyclical transition, or state e <sub>1</sub> with the other transition.

From a formal point of view, an FSA can be defined as a quintuplet: <E, Σ, Δ, e <sub>0</sub>, F>, where:

1. – E is a finite number of states;
2. – Σ is a finite number of input symbols;
3. – Δ is a function used to find the next state. This function gives a single state for a given symbol in the case of a deterministic machine and can give multiple states in the case of a non-deterministic machine;
4. – e <sub>0</sub> ∈ E is the initial state;
5. – F ⊆ E is the group of final states. In exceptional cases, all the states of a machine can be final states.

The intuitive application of FSM to morphological analysis consists of dedicating one transition between two states for each morpheme; for example, in processing the French verbs *poser* (put) and *porter* (carry), which can take one of sixteen possible prefixes as well as a fairly large number of suffixes depending on time and modality. To avoid repetitions, we can design an FSM like the one shown in [Figure 3.3](#fig3-3), in which these prefixes are divided into three subgroups; two groups for the prefixes proper to each verb and one group for the prefixes shared between them. An empty transition is used to pass shared prefixes to the stems of the two verbs concerned. For the sake of simplicity, we have shown present indicative tense suffixes only.

A more refined way of representing information consists of considering phonemic level rather than morphemic level. This makes it possible also to take into account the phonological phenomena discussed in the previous chapter. For example, this increased fineness allows us to insert the vowel *e* at the end of the stem of the French verb *manger* (eat) with the plural firstperson present indicative suffix – *ons*. This, of course, entails an additional cost in terms of the time needed to prepare such a machine and makes the use of an automatic compilation module to generate it indispensable.

Despite its interest, a machine like the one shown in [Figure 3.3](#fig3-3) allows us to see whether a word conforms to the morphological rules of a given language without giving any more information about its internal structure. To do this, we need more advanced tools, such as finite-state transducers (FST), which we will examine in the next section.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image126_c1074.jpg)

Figure 3.3. Conjugation of the verbs poser and porter in the present indicative tense

### 3.2.4. Two-level morphology and FST

The origins of two-level morphology lie in the work of Noam Chomsky and Morris Hall, conducted in the 1960s on the SPE model we saw in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter2.xhtml). It is an ordered sequence of rules of rewriting that convert abstract phonological representations into surface representations via a series of intermediary representations (see \[ANT 91a, ANT 91b, KOS 83\], and \[KAR 01\] for an introduction). The pioneers of FST-based morphological analysis, namely Lauri Kartunen, Martin Kay, Ronald Kaplan and Kimmo Koskenniemi (the four Ks), met at a conference at the University of Texas at Austin. Koskenniemi discovered the idea of FST reinvented by Kay and Kaplan and subsequently developed it for morphological and morphophonological analysis.

In 1972, C. Douglas Johnson published his thesis entitled *Formal Aspects of Phonological Description*, in which he showed that phonological rules are less powerful than they appear to be \[DOU 72\]. Johnson observed that the same rules of rewriting, which are dependent on context, can be applied recursively to their own output. Phonologists have observed that the point of application can be applied to the left or right of the chain after each application. For example, if the rule x → y / z \_ w is used to rewrite the chain “uzxwv” as “uzywv”, all applications following the same rule must leave the y unchanged and affect only the parts “uz” or “wv”. Johnson showed that this property could be modeled by an FST, a result that was rediscovered by Ronald Kaplan and Martin Kay in 1981 \[KAP 94\].

In two-level morphology, words are represented by a correspondence between two levels, the lexical level and the surface level. The lexical level is a simple concatenation of morphological information describing the nature and properties of the word in question. These items of information are attached to one another via a group of features such as: +N (noun), +V (verb), +Pl (plural), +Sg (singular), +PART-PRES (present participle), +PAST-PART (past participle), 3SING (3  person singular), +Masc (masculine), +Fem (feminine), etc. The surface level affects the graphic form of the word; that is, the sequence of its characters (e.g. *house*). In other words, two-level morphology represents a word as a series of complex sequences called *correspondence pairs*. Analysis is, thus, defined as the establishing of a relationship between the surface level and the lexical level. As an example, here are the correspondence pairs for some words:

1. – houses: H:H O:O U:U S:S E:E +N:ε +Pl:S;
2. – looks: L:L O:O O:O K:K +V:ε +3P:S +Sg:ε;
3. – choice: C:C H:H O:O I:I CC E:E +N:ε +Sg: ε.

As we can see in the above examples, each phoneme corresponds to a phoneme when it is part of a stem. For lexical morphemes reflecting one aspect of the totality of the stem such as +N and +V in order to indicate whether it is a noun and a verb, respectively. We have an empty equivalent at the surface level, represented by the symbol ɛ. Morphemes are marked on the surface by a single character such as *s*, which marks the plural of a noun, or *e*, which marks the ending of the verb at the end of the noun. This pair can be represented hierarchically as shown in [Figure 3.4](#fig3-4).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image127_c1076.jpg)

Figure 3.4. Correspondence pair for the word houses

Note that this method of representation is very well-suited for incorporating modifications at the surface level using the phonological constraints that we saw in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter2.xhtml), such as deletion and assimilation. Thus, in certain contexts, the stop consonant \[d\] is replaced by the silent occlusive \[t\]. This can be easily represented by the correspondence pair D:T E:E. A case of marked assimilation in French consists of pronouncing the word *cheveu* (hair) \[ʃəvø\] as \[ʃfø\], with the removal of the ə and the replacement of the consonant \[v\] with \[f\] under the effect of the silent consonant \[ʃ\]. With two-level morphology, this gives us the correspondence pair C:C H:H E:ɛ V:F E:E U:U.

According to the representation in [Figure 3.4](#fig3-4), analysis is viewed as a passage from the surface level to the lexical level, while the process of generation consists of moving in the opposite direction, from the lexical level to the surface level. It is clear that the FSM we saw in the previous section are not capable of executing both of these procedures. For this, researchers have suggested using Finite State Transducers (FST) which are finite-state machines annotated with two tags on each transition, where each tag corresponds to a pair of symbols (see [Figure 3.5](#fig3-5)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image128_c1077.jpg)

Figure 3.5. FST for some words in French with the prefix “anti–”

As we can see in [Figure 3.5](#fig3-5), words are represented in terms of characters rather than morphemes. This makes it possible to gain detailed knowledge of the phenomena described by transition pairs. Besides, this allows us to avoid repeating certain characters, particularly at the start and end of words, thus giving a more compact representation.

As we saw in [section 3.1.2.3](#sec3.1.2.3), derivation is another interesting phenomenon. To exemplify the way in which derivations are represented in FST, we have chosen an example of some stems of which the derivations are shown in [Figure 3.6](#fig3-6). This FST shows how to move from a noun such as the French word *concept* to an adjective such as *conceptuel*, and then to a verb such as *conceptualiser* and finally on to a new noun with *conceptualisation*. For the sake of clarity, we have used the infinitive form of the verb only, but it is easy to imagine the complexity of the FST with all the possible forms for variations according to time and modality. The feminine and plural forms of adjectives, as well as the plurals of nouns, are also considered. This shows the flexibility given by an FST, which covers morphological aspects as well as phonological ones such as the doubling of the *l* in the feminine version of an adjective like *conceptuelle*.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image129_c1078.jpg)

Figure 3.6. Partial FST for the derivation of some French words

In its role as recognizer, an FST takes a correspondence pair as input and yields as output a confirmation or negation of the matching of the surface level with the lexical level, knowing the language of the correspondence pairs defined by the FST. In its role as analyzer, the FST takes a surface chain as input and must produce the corresponding lexical chain. Conversely, when acting as a generator, the FST produces the surface chain from the lexical chain provided as input. Finally, the FST can act as a translator by taking a chain as input and producing a transformed version of this chain as output.

It is important to mention that rules of rewriting can be converted into transducers. In fact, each cascade of transducers can be converted into a single transducer which establishes a relationship between the lexical forms on one hand and the surface forms on the other. The diagram proposed by Kay and Kaplan is shown in [Figure 3.7](#fig3-7).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image130_c1079.jpg)

Figure 3.7. Kay and Kaplan diagram

In real applications, the rules and lexicon are first defined as regular expressions. These rules are then converted by a compiler into an FST. The compiler is a computer program designed to translate expressions expressed using any formal language, in this case regular expressions into expressions in another formal language (FST) (see [Figure 3.8](#fig3-8)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image131_c1080.jpg)

Figure 3.8. Xerox approach to the use of FST in morphological analysis

Lexical transducers can contain hundreds of thousands or even millions of states and arcs. The size of the FST is particularly large when morphologically rich languages such as German are involved.

### 3.2.5. Part-of-speech tagging

Part-of-speech (POS) tagging consists of automatically attaching a part-of-speech tag to all of the words in a given corpus. This process is very important in many NLP applications. In the context of syntactic analysis, POS tagging facilitates the task of the analysis module by providing it with a starting point. As part of information retrieval, the annotation of words in a given corpus may improve search functions by giving more weight to categories known to better characterize texts, such as nouns and adjectives, rather than categories judged to be less representative semantically, such as determiners, pronouns, verbs and adverbs. In the field of speech synthesis, we saw examples in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter2.xhtml) in which the grammatical category is used to select the appropriate phonetic transcription for two homographs in different grammatical categories. We have also covered examples like the word *live*, the pronunciation of which changes depending on whether it is noun or a verb. This interest explains the multitude of approaches proposed by many research centers all over the world. For an introduction to this issue, we refer readers to \[VOU 09\] and \[ASM 14\].

The main obstacle that must be overcome by a POS tagging system is ambiguity. There are many words, or more precisely graphic forms, in languages such as French and English, which can be associated with multiple parts of speech. Some examples are *dogs* (verb, noun), *heat* (verb, noun), slow (adjective, verb, adverb), *in* (preposition, adverb, adjective, noun), *large* (adjective, noun, adverb), etc. In a study on English conducted by Steven DeRose, it was demonstrated that, though ambiguity is found in only 11.5% of categories, in reality, it concerns around 40% of the words in the Brown Corpus, the subject of the study \[DER 88\]. This shows the importance of this phenomenon and the necessity of an effective solution.

In addition to ambiguity, modules must overcome various problems of form. These problems include the processing of new words that have not yet been observed in the training corpus. This problem, which is common to several NLP applications, makes it necessary to use contextual and morphological heuristics among others. Another problem observed in corpora of real data has to do with spelling errors and various types of grammatical errors. In transcribed spoken language corpora, this can be manifested in the form of hesitations, repetitions, false starts, etc. This phenomenon is difficult to model and causes changes of context, making it difficult to assess the part of speech of the current word. The writing systems of certain languages, such as Arabic, can also be an additional source of ambiguity that can be qualified as artificial. In this language, the diacritical marks corresponding to short vowels are usually optional. For example, without diacritical marks, the grapheme ﻜﺘﺐ can correspond to different words such as \[kataba\] *wrote* and \[kutub\] *books*.

There are lists of tags called *tagsets* for several languages. Though true standards do not exist on this subject, some lists have been commonly adopted, such as the *Penn Treebank tagset*, which includes between 36 and 41 tags depending on the version. This tagset is based on the one developed for the annotation of the Brown corpus \[NEL 64, GRE 81, MAR 93\]. The Xerox tagger  has 77 categories for English, 45 for French and 67 for German. As an example, we have provided a list of eleven basic tags drawn from the *Universal Part-of-Speech Tagset* in \[BIR 09\] (see [Table 3.13](#tab3-13)). The definition of lists like these is only part of a wider convention that must specify, among other things, the way in which compound and conflated words must be tagged. For example, the *Penn Treebank* uses the same tag for each part of the word. Another possibility consists of joining the components of a compound word with an underscore to indicate a single word. Likewise, conflated words require a special convention. It is common to split them when possible into multiple parts according to rules such as *I’ll = I will*. In cases where morphemes cannot be separated, a possible way to process them consists of a replacement like in *gonna = going to*.

[**Table 3.13.**](#Rtab3-13) *A minimal list of tags*

| Tag | Category | Examples |
| --- | --- | --- |
| ADJ | Adjective | beautiful, legal, cold, round |
| ADP | Preposition | from, at, to, with |
| ADV | Adverb | slowly, far, here, now |
| CONJ | Conjunction | and, or, if, but, whereas |
| DET | Determiner | the, a, some |
| NOM | Noun | house, book, table, France, Delaware |
| NUM | Numeral | one, thirty-five, 2016, 22.5 |
| PRON | Pronoun | he, she, we, they, them |
| VERB | Verb | eat, see, live |
| AUX | Auxiliary | is, was, has |
| . | Punctuation | .;,:? |
| X | other | dunno, ersatz |

Using the tag list shown in [Table 3.13](#tab3-13), we can tag the micro-corpus shown in [Figure 3.9](#fig3-9).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image133_c1083.jpg)

Figure 3.9. A micro-text tagged with POS

In terms of linguistics, part-of-speech tagging is done on the basis of multiple sources of information. First, at the lexical level, we need a database in which all of the graphemes with their possible tags are stored. Next, we need contextual information that is both syntactic and semantic. Morphology plays a significant role as well. As we have seen, the suffixes of words formed with derivation make it possible, in certain cases, to figure out the part of speech to which the word belongs. For example, it is possible to assume with a reasonable degree of certainty that a word ending with *–tion* is a noun. However, because many suffixes are shared by multiple parts of speech, this is not always a decisive source of information. In a tagging module, it is common to use low-level sources of information, avoiding higher-level information like semantics. This is due partly to the fact that it is possible to get good results with low-level information, and partly to the dependency of the task and the heaviness of development that such higher-level information causes.

The tagging process is, generally, carried out in two main stages: identification of potential tags for input words and disambiguation. The first stage consists of using a dictionary in which the words with their possible tags are stored. The second, disambiguation stage consists of choosing the most appropriate tag among the candidates identified in the first stage.

In terms of technologies, a fairly large number of approaches have been used to construct taggers. Statistical approaches and learning-based approaches have frequently been used to solve problems of ambiguity in the domain of NLP. These approaches are good for modeling problems that are still poorly understood in theoretical terms. This has motivated a considerable amount of research since the 1980s \[DER 88, GAR 87, CHU 88, SCH 94b\]. Several variants of learning-based approaches such as memory-based learning \[DAE 96, DAE 10\], neural networks \[SCH 94a, MAR 96\] and genetic algorithms \[ARA 02, BEN 13\] have also been tested with varying degrees of success.

#### 3.2.5.1. Statistical approaches

The simplest statistical approach consists of using n-grams, the simplest form of which, as we saw in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter2.xhtml), are unigrams. We intuitively count frequencies of categories per word in an annotated corpus. During automatic tagging, we choose the most probable category for this word, independent of its context. Suppose that we have a tagger trained on the corpus shown in [Figure 3.9](#fig3-9) and that this module must tag the sentence *The written history of the Gauls is known*. To do this, we must resolve the ambiguity of the word *written*, which, as we have seen, can be tagged with both the verb and adjective categories. Based on the statistics of our micro-corpus, the probability that *written* can be tagged with the category ADJ is 2/3 = 0.66, while the probability of its tagging with VERB is 1/3 = 0.33. Therefore, the category ADJ is chosen for this sentence. The same choice is made for the sentence *The history was written*, which is not the correct choice. Note that, depending on the language considered, the expansion of the contextual window by taking into account a larger value for *n* in an n-gram-based model does not always guarantee improved results. This is mainly due to the fact that the larger the history, the more data it requires. For example, a study conducted on three southeast Asian languages has shown that the results of tagging with unigrams are better than those with bigrams. However, the same study showed that tagging with hidden Markov models (HMMs) yields results that are clearly superior to n-grams \[HAS 07\]. To benefit the most from n-grams even with a limited amount of data, we can use a so-called *backoff heuristic*, which consists of tagging all the words we can tag with trigrams and leaving the rest for lower levels. The process is then repeated with bigrams and then unigrams, and finally unknown words are tagged with the most frequent category.

A more refined way of modeling the problem consists of considering HMMs as a framework \[CHA 93a\]. This uses two different complementary sources of information: the probabilities of transition from one tag to another p(e <sub>i</sub> |e <sub>i-1</sub>), which model the context of occurrence, and the probabilities of generation of a given word knowing a specific tag p(W <sub>i</sub> |E <sub>i</sub>), which takes the lexical level into account. These two probabilities are calculated using [equations \[3.8\]](#Requ3-8). We refer readers to the section on HMMs in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848218482/chapter2.xhtml) for further details.

[\[3.8\]](#equ3-8) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image135_c1084.jpg)

As we saw in the speech sphere, we can make three types of inference with HMMs by using different algorithms. Firstly, in a context of language modeling, we can calculate the probability of a sequence of words with a hidden sequence of tags. The other possibility is to find the most probable tag sequences, knowing the sequence of words observed. Finally, we can estimate the parameters of the model based on the observed sequence and the corresponding tag sequence.

Let us return to our example: *The written history of the Gauls is known*. To analyze this sentence with an HMM, we can have the two representations below in the form of a Bayesian network, the first of which is correct. The probabilities on the arcs of the networks in [Figure 3.10](#fig3-10) are obviously calculated from the corpus being used.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image136_c1085.jpg)

Figure 3.10. Tag sequences for “The written history of the Gauls is known”

The main problem with the statistical approaches we have just presented is the need for significant linguistic resources, which are not always available, particularly for minority languages or those from the countries of the south. Approaches based on Bayesian networks, the generic form of HMMs, have been proposed, among other solutions, as an unsupervised learning framework for tagging modules \[LEE 10, GOL 07\]. Though the results of these approaches are encouraging, this work is still in the research stage and its results are clearly inferior to those of supervised approaches.

#### 3.2.5.2. Transformation-based approach

Proposed by Eric Brill at the University of Pennsylvania, the transformation-based approach is a hybrid process combining statistical information with symbolic rules \[BRI 93\]. According to this approach, the tagging process is carried out according to the architecture in [Figure 3.11](#fig3-11).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image137_c1086.jpg)

Figure 3.11. Architecture of the Brill tagger \[BRI 95\]

The first stage of processing consists of rough tagging using an n-gram based module (in the initial version, a unigram was used). Words tagged in this way and liable for improvement are marked for possible correction in a subsequent stage. The rules to be applied to the corpus being tagged are learned automatically from the corpus so as to guarantee maximum improvement. The process of applying a rule is called a transformation. There are two types of transformations; rules and triggers. Rules specify the way in which the input must be modified, while triggers serve to describe the conditions of application of a given rule.

<table><tbody><tr><td><p>Trigger</p></td><td><p>the previous word is in the Tag <sub>z</sub> category</p></td></tr><tr><td><p>Rule</p></td><td><p>if <i>trigger</i> then Tag <sub>x</sub> → Tag <sub>y</sub></p></td></tr><tr><td colspan="2">For example, we can have the following trigger and rule:</td></tr><tr><td><p>Trig <sub>01</sub></p></td><td><p>The previous word is in Category DET.</p></td></tr><tr><td><p>Rule</p></td><td><p>If Trig <sub>01</sub> then VRB → NOM</p></td></tr></tbody></table>

Transformations are learned as follows. First, the training corpus is annotated with the initial tagger. The results of the annotation are compared with the annotation of this corpus and the number of errors is obtained. Then, we apply a number *n* of possible transformations, and for each transformation we calculate the number of errors. The transformation that reduces most of the errors is chosen. We repeat this process with the rest of the transformations until we arrive at a state in which there are no more transformations that might improve tagging. An example of learning adapted from Brill \[BRI 95\] with four possible transformations is given in [Figure 3.12](#fig3-12).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848218482/files/image/image138_c1089.jpg)

Figure 3.12. Example of transformation-based learning

As we can see in [Figure 3.12](#fig3-12), the transformation T2 is the one that gives the minimum number of errors; therefore, it is chosen as the first transformation to be carried out. Next, we choose T3 for the same reason. Finally, since none of the transformations improve the results, we stop our search.

This approach is distinguished not only by its effectiveness and good results, but also in terms of data savings. Unlike statistical approaches requiring the storage of n-gram models, the size of which increases along with the size of *n,* the Brill approach requires much less memory. This is particularly appreciated in mobile telephone systems or similar applications.

The final advantage of this approach concerns the readability of internal representations in the form of rules that can be understood by humans. Finally, it is probably worth to mention that a generic toolbox for the transformation-based learning algorithm is available \[FLO 02\] and transformation-based tagging has been applied to several languages.