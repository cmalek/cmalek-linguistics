---
title: "OldEnglishMorphology"
owner: "anasfkhan81"
source: "https://github.com/anasfkhan81/OldEnglishMorphology"
website:
description: "Modelling Old Enlgish Strong Verbs in OntoLex-Lemon"
stars: "0"
language: "\"Python100%\""
tags:
  - "old_english"
  - "morphology"
created: 2026-10-15
---
## README

Modelling Old English Strong Verbs in OntoLex-Lemon

# Introduction

Our plan is to use OntoLex/Morph/Lexinfo to encode the morphological information in the Clark-Hall dictionary as RDF with **bonus**, the use of SHACL to encode various constraints/morphological patterns; another **bonus**: look into whether it’s better to work directly in paralex and map the results into OntoLex later, since we are looking to integrate information from unimorph too; further **bonus,** start looking into the use of RDF 1.2 along with SHACL

Main aim is: use Semantic Web standards to make the morphology more machine actionable!

## Ontology of Old English Strong Verbs

### The Basic Classes

Here is the core class which we define (might be better to change the name to OE\_StrongVerb)

```
chm:StrongVerb a owl:Class ;
  rdfs:label "Strong verb (Clark–Hall morphology)"@en ;
  rdfs:subClassOf ontolex:LexicalEntry , lexinfo:Verb .
```

Copy code to clipboard

We define seven classes of StrongVerb

```
chm:StrongVerbI a owl:Class ;
  rdfs:label "Strong verb class I"@en ;
  rdfs:subClassOf chm:StrongVerb .

chm:StrongVerbII a owl:Class ;
  rdfs:label "Strong verb class II"@en ;
  rdfs:subClassOf chm:StrongVerb .

chm:StrongVerbIII a owl:Class ;
  rdfs:label "Strong verb class III"@en ;
  rdfs:subClassOf chm:StrongVerb .

chm:StrongVerbIV a owl:Class ;
  rdfs:label "Strong verb class IV"@en ;
  rdfs:subClassOf chm:StrongVerb .

chm:StrongVerbV a owl:Class ;
  rdfs:label "Strong verb class V"@en ;
  rdfs:subClassOf chm:StrongVerb .

chm:StrongVerbVI a owl:Class ;
  rdfs:label "Strong verb class VI"@en ;
  rdfs:subClassOf chm:StrongVerb .

chm:StrongVerbVII a owl:Class ;
  rdfs:label "Strong verb class VII"@en ;
  rdfs:subClassOf chm:StrongVerb .
```

Copy code to clipboard

We go into further subclasses (our intention is that each leaf level sub-class is granular enough that it shares the same morphological pattern):

```
chm:StrongVerbIIa a owl:Class ; rdfs:label "Strong verb class IIa"@en ; rdfs:subClassOf chm:StrongVerbII .
chm:StrongVerbIIb a owl:Class ; rdfs:label "Strong verb class IIb"@en ; rdfs:subClassOf chm:StrongVerbII .

chm:StrongVerbIIIa a owl:Class ; rdfs:label "Strong verb class IIIa"@en ; rdfs:subClassOf chm:StrongVerbIII .
chm:StrongVerbIIIb a owl:Class ; rdfs:label "Strong verb class IIIb"@en ; rdfs:subClassOf chm:StrongVerbIII .
chm:StrongVerbIIIc a owl:Class ; rdfs:label "Strong verb class IIIc"@en ; rdfs:subClassOf chm:StrongVerbIII .
chm:StrongVerbIIId a owl:Class ; rdfs:label "Strong verb class IIId"@en ; rdfs:subClassOf chm:StrongVerbIII .
chm:StrongVerbIIIe a owl:Class ; rdfs:label "Strong verb class IIIe"@en ; rdfs:subClassOf chm:StrongVerbIII .

chm:StrongVerbVIIa a owl:Class ; rdfs:label "Strong verb class VIIa"@en ; rdfs:subClassOf chm:StrongVerbVII .
chm:StrongVerbVIIb a owl:Class ; rdfs:label "Strong verb class VIIb"@en ; rdfs:subClassOf chm:StrongVerbVII .
```

Copy code to clipboard

## Example Entries

We will look at one of the entries, from the first strong verb class, the entry *bīdan*.

```
chm:biidan rdf:type owl:NamedIndividual ,
                    ontolex:LexicalEntry ,
                    chm:StrongVerb ,
                    chm:StrongVerbI ;
           rdfs:label "bīdan"@ang ;
           ontolex:canonicalForm chm:biidan_inf ;
           ontolex:otherForm chm:biidan_pres-2sg_1 ,
                             chm:biidan_pres-2sg_2 ,
                             chm:biidan_pres-2sg_3 ,
                             chm:biidan_pres-3sg ,
                             chm:biidan_pret-3sg ,
                             chm:biidan_pret-pl_1 ,
                             chm:biidan_pret-pl_2 .

###  https://example.org/chm#biidan_inf
chm:biidan_inf rdf:type owl:NamedIndividual ,
                        ontolex:Form ;
               chm:rootVowel "ī" ;
               lexinfo:verbFormMood lexinfo:infinitive ;
               ontolex:writtenRep "bīdan"@ang .

###  https://example.org/chm#biidan_pres-2sg_1
chm:biidan_pres-2sg_1 rdf:type owl:NamedIndividual ,
                               ontolex:Form ;
                      chm:rootVowel "ī"^^xsd:string ;
                      lexinfo:number lexinfo:singular ;
                      lexinfo:person lexinfo:secondPerson ;
                      lexinfo:tense lexinfo:present ;
                      lexinfo:verbFormMood lexinfo:indicative ;
                      ontolex:writtenRep "bīst"@ang .

###  https://example.org/chm#biidan_pres-2sg_2
chm:biidan_pres-2sg_2 rdf:type owl:NamedIndividual ,
                               ontolex:Form ;
                      chm:rootVowel "ī"^^xsd:string ;
                      lexinfo:number lexinfo:singular ;
                      lexinfo:person lexinfo:secondPerson ;
                      lexinfo:tense lexinfo:present ;
                      lexinfo:verbFormMood lexinfo:indicative ;
                      ontolex:writtenRep "bīdst"@ang .

###  https://example.org/chm#biidan_pres-2sg_3
chm:biidan_pres-2sg_3 rdf:type owl:NamedIndividual ,
                               ontolex:Form ;
                      chm:rootVowel "ī"^^xsd:string ;
                      lexinfo:number lexinfo:singular ;
                      lexinfo:person lexinfo:secondPerson ;
                      lexinfo:tense lexinfo:present ;
                      lexinfo:verbFormMood lexinfo:indicative ;
                      ontolex:writtenRep "bītst"@ang .

###  https://example.org/chm#biidan_pres-3sg
chm:biidan_pres-3sg rdf:type owl:NamedIndividual ,
                             ontolex:Form ;
                    chm:rootVowel "ī"^^xsd:string ;
                    lexinfo:number lexinfo:singular ;
                    lexinfo:person lexinfo:thirdPerson ;
                    lexinfo:tense lexinfo:present ;
                    lexinfo:verbFormMood lexinfo:indicative ;
                    ontolex:writtenRep "bīt"@ang .

###  https://example.org/chm#biidan_pret-3sg
chm:biidan_pret-3sg rdf:type owl:NamedIndividual ,
                             ontolex:Form ;
                    chm:rootVowel "ā"^^xsd:string ;
                    lexinfo:number lexinfo:singular ;
                    lexinfo:person lexinfo:thirdPerson ;
                    lexinfo:tense lexinfo:past ;
                    lexinfo:verbFormMood lexinfo:indicative ;
                    ontolex:writtenRep "bād"@ang .

###  https://example.org/chm#biidan_pret-pl_1
chm:biidan_pret-pl_1 rdf:type owl:NamedIndividual ,
                              ontolex:Form ;
                     chm:rootVowel "eo"^^xsd:string ;
                     lexinfo:number lexinfo:plural ;
                     lexinfo:tense lexinfo:past ;
                     lexinfo:verbFormMood lexinfo:indicative ;
                     ontolex:writtenRep "beodan"@ang .

###  https://example.org/chm#biidan_pret-pl_2
chm:biidan_pret-pl_2 rdf:type owl:NamedIndividual ,
                              ontolex:Form ;
                     chm:rootVowel "i"^^xsd:string ;
                     lexinfo:number lexinfo:plural ;
                     lexinfo:tense lexinfo:past ;
                     lexinfo:verbFormMood lexinfo:indicative ;
                     ontolex:writtenRep "bidon"@ang .
```

Copy code to clipboard

### SHACL Shapes

Here is the SPARQL-SHACL shape for Strong Verb Class I. It makes use of the root vowels associated with four different forms (if these exist)

```
chm:StrongVerbIShape a sh:NodeShape ;
  sh:targetClass chm:StrongVerbI ;

  sh:sparql [
    a sh:SPARQLConstraint ;
    sh:message "For Strong Verb Class I, the infinitive must have root vowel ī."@en ;
    sh:select """
      PREFIX chm:     <https://example.org/chm#>
      PREFIX ontolex: <http://www.w3.org/ns/lemon/ontolex#>

      SELECT $this
      WHERE {
        $this ontolex:canonicalForm ?f .
        ?f chm:rootVowel ?v .
        FILTER(?v != "ī")
      }
    """
  ] ;

  
  sh:sparql [
    a sh:SPARQLConstraint ;
    sh:message "For Strong Verb Class I, any 1sg past indicative form must have root vowel ā."@en ;
    sh:select """
      PREFIX chm:     <https://example.org/chm#>
      PREFIX ontolex: <http://www.w3.org/ns/lemon/ontolex#>
      PREFIX lexinfo: <http://www.lexinfo.net/ontology/3.0/lexinfo#>

      SELECT $this
      WHERE {
        $this ontolex:otherForm ?f .
        ?f lexinfo:tense lexinfo:past ;
           lexinfo:person lexinfo:firstPerson ;
           lexinfo:number lexinfo:singular ;
           lexinfo:verbFormMood lexinfo:indicative ;
           chm:rootVowel ?v .
        FILTER(?v != "ā")
      }
    """
  ] ;

  sh:sparql [
    a sh:SPARQLConstraint ;
    sh:message "For Strong Verb Class I, any past participle form must have root vowel i."@en ;
    sh:select """
      PREFIX chm:     <https://example.org/chm#>
      PREFIX ontolex: <http://www.w3.org/ns/lemon/ontolex#>
      PREFIX lexinfo: <http://www.lexinfo.net/ontology/3.0/lexinfo#>

      SELECT $this
      WHERE {
        $this ontolex:otherForm ?f .
        ?f lexinfo:tense lexinfo:past ;
           lexinfo:verbFormMood lexinfo:participle ;
           chm:rootVowel ?v .
        FILTER(?v != "i")
      }
    """
  ] .
```

Copy code to clipboard

