---
title: "4 The Sphere of Applications"
source: "https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch04.xhtml"
author:
  - "Mohamed Zakaria Kurdi"
published: 2026-08-01
created: 2026-08-23
description: "4The Sphere of Applications4.1. Software engineering for NLP software In the previous chapters, the basic components of NLP systems were presented. They focused on separate linguistic levels..."
tags:
  - "linguistics"
citation: "Kurdi (2017), \"Natural Language Processing and Computational Linguistics 2\", Wiley-ISTE"
---
## 4.1. Software engineering for NLP software

In the previous chapters, the basic components of NLP systems were presented. They focused on separate linguistic levels such as speech, morphology, syntax, semantics and discourse. This chapter will focus on combining different levels of linguistic knowledge with other sources of knowledge to build applicative NLP software that is directly usable by humans. Particular attention will be paid to presenting the specificities of NLP software regarding their development cycle, architecture and evaluation.

### 4.1.1. Lifecycle of an NLP software

Developing an NLP software is a complex process that involves many actors and occurs through successive or parallel steps, some of which are optional. It all starts with the identification of a need, whether it comes from the world of research, the daily practices of the general public or a business opportunity. Then comes the analysis and definition of the system prerequisites recorded in the project specifications. The next step is the design, which consists of describing all aspects of the system, including the interface, creating diagrams, writing documentation and pseudocode. During the development phase, the system’s code is written, generally in a modular way. A test of the system’s code is then carried out. The modules are tested individually (modular tests) and when they have been integrated into the system (integration tests). The development phases and the tests therefore partially overlap. The final phase of the development process is maintenance. This is a phase that consists of verifying that the system always responds to prerequisites and identifying points that can be improved. In the case of NLP systems, there is often an additional phase of data collection. The steps and the approaches of such a procedure are described in the spheres of linguistic resources in the first volume of this book, and this step occurs between the steps of designing and writing code.

Several models for managing software development phases have been created, including the spiral model, the incremental model and the Extreme Programming (XP) model (see \[BEL 05\] for more details about these different models). The rapid prototyping approach is probably the most commonly used option for developing NLP systems. With this approach, the development of the system occurs according to several large steps, each of which involves most of the phases presented here. It starts with a basic prototype that covers a part of the domain to evaluate its compatibility with the project specifications. An update to the design and then the code produces a new version of the prototype until the final version of the system is produced. A review of some software engineering questions regarding the development of linguistic software can be found in the first part of the dissertation of \[LAF 94\] as well as in \[LEI 03\].

The boundaries between linguistic levels are not absolute. In many cases, to solve a problem at a given level, knowledge of the higher level is needed. This is especially the case with the problem of ambiguity, which is very often lexical. There are two strategies to deal with this. The first consists of making a decision based on the available knowledge and sending the most correct possible result to the higher-level modules. The advantage of this strategy is that it is the simplest to implement, but the results rendered may not be optimal. The second strategy consists of involving the higher levels in the decision-making. This occurs either by invoking the higher levels to solve the problem or simply by propagating the ambiguity as is in the higher levels.

### 4.1.2. Software architecture for NLP

In the early 1950s, programs were written in machine language. At the time, the instructions and the data were individually and explicitly placed in the computer’s memory. To carry out even the slightest modification of the code, a manual verification of the entire code was often necessary. Later, the first high-level programming languages started to be created. Toward the end of the 1960s, experienced programmers intuitively realized that organizing the information in the data structures would make programming easier. In the 1970s, these insights were realized as a formal theory of software architecture.

Software architecture is the structure of the system that includes the software components (modules), the properties visible on the exterior of these components and the relations between them \[BAS 98\]. The interest in a description of the software architecture is manifold. It makes it possible to determine the relevance of the software design in relation to the prerequisites and to discuss alternatives, thereby reducing risks of error in the development process. A description of the software architecture also sometimes makes it possible to anchor the software in the context of works originating from other related disciplines, including the cognitive sciences in particular. Finally, a well-designed architecture makes it possible to divide the system into units or modules that are likely to be reused in other projects. Similarly, this makes it possible to distribute tasks within the project team, which can sometimes be widely distributed geographically. Data flow diagrams (DFDs) (see \[KEN 13\] for an introduction) are commonly used to describe the software architecture of systems the same way that some UML diagrams are, especially in the context of object-oriented applications (see \[RUM 04\] for an introduction to UML).

Several forms of software architecture have been developed, many of which are intended for the development of commercial applications for information systems such as the famous layered architecture. The following sections are limited to architectures that are most relevant for NLP. For more details about software architecture in general, see \[GAR 93, GOR 06\].

### 4.1.3. Serial architectures

Serial architectures are the simplest. They have two types of constituents: modules and connections. In the case of NLP systems, the modules can do the processing of linguistic components (morphological analysis, syntactic parsing) or accessory modules such as databases, ontologies, etc. The connectors make it possible to transmit data from one module to another. They can be unidirectional or bidirectional. According to the principles of this architecture, the modules must be independent entities without any sharing of state or data.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_1.jpg)

Figure 4.1. Examples of simple serial architectures. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

[Figure 4.1](#fig4_1) presents four examples of simple architectures. Type (a) is a bottom-up unidirectional architecture, where the information moves from the lower-level modules to the higher levels. Decision-making occurs only at the local level, because higher-level knowledge is not invoked for the decision-making. Type (b) is a bidirectional architecture, where each module exchanges information with the neighboring modules, notably to resolve ambiguities. Type (c) is a bottom-up architecture that uses external data, in this case a dictionary, for the morphological analysis module and an ontology for the semantic and discursive analysis modules. Type (d) has a conditional activation phase. Based on a topic detection module, this architecture only activates syntactic parsing units that are relevant for a given context. This has the advantage of only mobilizing the grammatical and lexical resources that are strictly necessary for the processing in progress, which contributes to considerably improving the efficiency of the system without affecting the quality of the processing (for more details about this kind of architecture, see (\[GAV 00b, KUR 03\]). In all of these cases, it is assumed that the input into the system is a sentence or a text and the output is high-level linguistic analysis. To facilitate the integration of modules, the adoption or specification of standards, as much for the format as for the content, seems to be a good choice. XML and JSON are particularly useful data formats for this kind of task.

Aside from their simplicity, serial architectures have the advantage of facilitating reusability and a better understanding of the global behavior of a system. The implementation of modules can occur in parallel, and each team can focus on developing a module independently of the other teams’ work. This kind of architecture facilitates the comparison of several modules. For example, we can use two or more morphological analysis modules and compare the effects of the change on the global performance of the system.

Serial architectures are not very well suited to process applicative domains where the interaction between the modules is very complex. However, many NLP applications require such an interaction. Because of the reduction of interactions between modules, this architecture encourages local decisions that only consider a limited part of the information sources available. This pushed researchers to explore architectures that offer more possibilities, such as blackboard or hub architectures.

### 4.1.4. Data-centered architectures

The idea behind these architectures is to create a central space shared by all the modules. Two main types of spaces have been used: blackboards and hubs.

In blackboard-based architectures, there is a central module that plays the role of active data repository, surrounded by a number of peripheral modules. In addition to storing data to be shared, it contacts all of the modules to inform them of the existence of these data or their state change. In other words, the blackboard plays the role of a memory space shared by the system modules.

The first implementation of a blackboard was realized at the end of the 1970s in the context of a speech recognition system called Hearsay II \[ERM 80, ERM 81\]. The content of a blackboard can be seen as hypotheses, which are often hierarchically structured. The modules, seen as knowledge sources, only communicate through the blackboard (see [Figure 4.2](#fig4_2)).

The solicitation of knowledge sources occurs through a control module. This module can be implemented as an integral part of the blackboard, in other modules, or as a completely separate module.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_2.jpg)

Figure 4.2. Architecture of the Hearsay II system

In Hearsay II, the blackboard is divided into a set of information levels that correspond to the intermediary levels of representation of the acoustic decoding process (phrase, word, syllable, etc.). Each hypothesis is located at the level of corresponding knowledge and is labeled with additional information about managing the analysis process such as the time frame within an utterance and the confidence value. The possible hypotheses at a given level constitute a search space for each knowledge source of the level under consideration. This space can be considered in a top-down or bottom-up fashion.

[Figure 4.3](#fig4_3) shows that the blackboard of the Hearsay II system is composed of six levels: acoustic parameters, from which segments are produced, the syllables that are used to make word hypotheses, which are the basis for predicting word sequences, which are phrase hypotheses. The VERIF operation attributes a weight to the coherence of the word hypotheses and contiguous word segments. The CONCAT operation creates a phrase hypothesis from a pair of contiguous word-groups. The top level is that of semantics, which generates an unambiguous interpretation of the user’s query. All the hypotheses in the blackboard have a confidence value *CONF*. The *PREDICT* process predicts all of the words that can follow or precede a given group. The *STOP* process decides to stop the processing when it detects a sentence with an acceptable confidence value or when the input data has been entirely processed. A blackboard-based recognition system has been realized at the ICP in Grenoble \[NAS 90\]. Similarly, this kind of architecture has been adopted in domains beyond the classical applications of artificial intelligence, for example, web applications \[MET 05\].

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_3.jpg)

Figure 4.3. Levels of knowledge in the Hearsay II blackboard

One of the advantages of the blackboard model is that it facilitates the software integration of models written in different languages as well as the addition of a new module or the modification of an existing module. Despite these different advantages that make the model appealing for interactive systems, its conceptual complexity and the difficulty of implementing it remain major disadvantages. This complexity also affects the global performance of the system. From a cognitive point of view, a strong centralization of processes is likely to bias the emergence of collective behaviors. This pushed researchers to adopt architectures that have a similar general concept, but a simpler structure. These are hub-based architectures, which are central but passive data repositories. Several dialogue systems have adopted this architecture, including the CU Communicator of the University of Colorado \[PEL 01, PEL 00\] and the Vico multilingual dialogue system. Highly interactive, Vico is a human–machine dialogue system that serves as a vocal interface for a GPS equipped in a car, whose role is to guide the driver not only to find his route toward a given destination but also to provide tourist information and indicate service stations.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_4.jpg)

Figure 4.4. Architecture of the Vico system \[BER 02\]. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

The dialogue manager plays a particularly important role within this system. As shown in the data flow diagram in [Figure 4.4](#fig4_4), this model interacts with the majority of the system components by providing delay queries and instructions for the four modules of linguistic processing: recognition, understanding, generation and synthesis, all while making requests on the Car Wide Web (CWW), the main source of information about the world in this system. The interaction of modules occurs through the CORBA [](#ch4en1) interfaces, a standard that was chosen in particular for the heterogeneity of the modules and the necessity of accessing CWW information through the network. The dialogue manager or hub is an obligatory passage for all inter-modular communication. Each module deposits its output there and searches for information that it could take as input there.

### 4.1.5. Object-oriented architectures

Object-oriented architectures are both a conceptual view of the breakdown of a program into units and a practical realization that guarantees the encapsulation of data and primitive operations within objects organized in a hierarchy of classes that facilitate the reuse of the code. This architecture has several advantages. From a common design, often made in the form of UML diagrams (class diagrams, collaboration diagrams, deployment diagrams, etc.), several programmers or even several teams can work in parallel on developing different classes of the same software, without risk of collision. The integration of new classes with an existing software or the modification of one or more existing classes is also facilitated. Contrary to models in serial architectures, the objects are not completely independent to the extent that each one must know the identity of the objects in its environment within the system and some of their properties, notably their input and output methods. This means that when an object is changed, all of the objects that invoke it must also be modified. In the NLP domain, object-oriented architectures are very commonly adopted, not only because of the advantages of this paradigm but also because of the popularity of many object-oriented languages.

One example of an NLP software developed with an object-oriented architecture is the GATE [](#ch4en2) (General Architecture for Text Engineering) system. Intended to process texts of all forms and sizes, GATE is an open-source software developed by a fairly large community. It was launched in 1994 by the Natural Language Processing Group at the University of Sheffield under the initiative of Yorick Wilks, Rob Gaizauskas and Hamish Cunningham. This system contains a large number of tools including an integrated development tool (GATE Developer) for NLP applications, which is widely used in the domain of information extraction; a collaborative annotation tool (GATE Teamwear) for the semantic annotation of data on an industrial scale and a process for the creation of robust services.

The GATE architecture is designed to take over the most important part of the engineering work to allow users to focus on developing their linguistic software. It also includes tools for syntactic analysis, labeling parts of discourse, information retrieval, information extraction, generating finite-state transducers for morphological and superficial syntactic analysis, evaluation and, most recently, interfacing with temporal expression extraction platforms \[DER 16\]. It is also possible to integrate tools used in the domain of automatic learning such as Weka [](#ch4en3) \[EIB 16\] and SVM Lite [](#ch4en4).

### 4.1.6. Multi-agent architectures

The idea of multi-agent systems comes from a collective conception of intelligence that emerges from the behavior of a group \[MIN 88\]. Multi-agent architectures are an extension of multi-expert systems, blackboard-based architectures and object-oriented architectures. The advantage of these architectures is that they make it possible to simulate the behavior of several types of systems, including cognitive systems, social systems and systems that mimic animal behavior (ants, bees, fish, etc.). To learn more about multi-agent systems, see \[WOO 95, BOI 01, CIA 01\].

Let us begin with the definition of the concept of agent. In the literature, two definitions of agents are opposed: weak and strong. According to the weak definition, an agent is an electronic system or software that is characterized by the following properties: autonomy, social capacities, reactivity and proactivity. In other words, it consists of completely autonomous entities that have internal objectives and that submit to community or social rules of interactions with their peers. The strong conception of an agent stipulates that it has, in addition to the previously mentioned properties, anthropomorphic characteristics such as mental states, beliefs, intentions and emotions. In this case, the agent is often represented by an animated character or even a robot.

Agents are located in an environment made up of external elements that affect their behavior. There are two types of environment: physical environment and communicative environment. The physical environment provides the principles and the processes that govern and support the population of entities, and the communicative environment defines the principles and the infrastructure necessary for the transmission of information by the agents.

In the domain of NLP, the first forms of multi-agent systems were developed as multi-expert systems, following the example of the Caramel system, designed to promote collaboration between several expert systems specialized in processing a knowledge source \[SAB 90\]. Later, several multi-agent architectures were adopted for various goals. For example, the design of the architecture of the TALISMAN system intends to resolve linguistic ambiguities by making accessible all of the necessary information for each linguistic level represented by the corresponding agent \[STE 95\]. The objective of the MICRO system was to propose a cognitively valid architecture \[CAE 94\]. Realized using the generic MAPS platform that is intended for the design of multi-agent systems, MICRO simulates the organization of the brain into two hemispheres: the analytic left hemisphere and the holistic right hemisphere (see [Figure 4.5](#fig4_5)). The holistic processes are responsible for a global and synthetic Gestalt-type analysis, and the left hemisphere is considered to be the language center. Thus, two groups of agents distributed on two paths are distinguished: linguistic agents on the analytical and phonetic path and prosodic agents on the holistic path. The prosodic analysis conducts a rapid pre-labeling of events to guide the left path. The acoustic analysis at the input of the system is carried out using a mathematical model of an ear that has several processing stages \[CAE 79\].

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_5.jpg)

Figure 4.5. Architecture of the MICRO system \[CAE 94\]

Systems designed based on the strong conception of agents equipped with dialogic and emotional capacities have been developed \[CHI 02, RIV 11\]. Multiagent systems have also served as a basis to experiment with fundamental hypotheses about the emergence of a form of linguistic code within an artificial community of agents. On this subject, the work of \[KAP 00\] focuses on the emergence of a lexicon within a population of artificial agents based on minimal hypotheses inspired by Wittgenstein’s designation games.

### 4.1.7. Syntactic–semantic cooperation: from cognitive models to software architecture

The correlations between the architecture of an NLP system and cognitive models are very strong. To demonstrate this, consider the case of the interaction between syntax and semantics. This choice is motivated by both the interest in this question from theoretical linguistic and psycholinguistic perspectives as well as the central role played by syntactic parsing and semantic analysis modules in NLP applications.

It is a well-received idea in linguistics that semantic analysis occurs after the construction of a syntactic representation of an utterance. However, there is no consensus within the experimental psycholinguistics community regarding the mode of integrating syntactic and semantic knowledge. Some researchers argue that humans first proceed with the selection of an initial syntactic interpretation, which shows the priority of the syntactic analysis over semantic analysis \[FOR 79\]. Similarly, some studies on eye movement, including that of \[RAY 92\], have shown that the first decisions regarding sentence analysis, such as minimal attachment, are based on syntactic knowledge. The researchers showed subjects utterances with prepositional groups including ambiguous attachment. These utterances were anchored in discursive contexts that either did or did not support minimal syntactic attachment. The results showed that the subjects followed a garden path in the analysis and that the discursive context did not help to find a syntactic analysis. On the other hand, there are many studies in the domain of semantics that have shown the existence of a strategy for precociously integrating syntactic information with high-level information during the comprehension process. One example of these studies is \[TYL 77\], in which an experiment was conducted to verify whether semantics intervenes at the end of an utterance or whether it intervenes during processing alongside syntactic analysis. To do this, they used ambiguous adjective–verb pairs such as *landing planes* in utterances such as [\[4.1\]](#eq4.1). The results of this experiment show that semantics intervenes before the end of the utterance. When the word *planes* was followed by a context-appropriate word (such as *are* for [\[4.1a\]](#eq4.1)), the response time was quicker than in cases where an inappropriate word was in the same place (such as *is* for [\[4.1a\]](#eq4.1)). This shows that the subjects have a semantic preference, induced from general knowledge about the world as well as semantic analysis of the start of the utterance, which they apply in order to choose the most plausible syntactic analysis:

1. a) If you walk too near the runway, *landing planes* … [\[4.1\]](#ieq4.1)
2. b) You’ve been trained as a pilot, *landing planes…*.

In addition, \[TYL 77\] used passive utterances with relative propositions to show that semantics as well as referential context can guide the choice of syntactic structure as in [\[4.2\]](#eq4.2):

1. a) The teachers taught by the Berliz method passed the test. [\[4.2\]](#ieq4.2)
2. b) The children taught by the Berliz method passed the test.

Utterances similar to [\[4.2b\]](#eq4.2) were judged to be grammatical more frequently than utterances similar to [\[4.2a\]](#eq4.2). The semantic difference between the two utterances seems to be the reason for this difference in judgment, given that it is more probable that a child will be taught than a teacher. The researchers also showed that semantic cues intervene before the end of the utterance or even before a group boundary. Therefore, \[CRA 85\] concluded by considering the garden path as a contextual phenomenon, which can be avoided by knowledge of the context in which the utterance is produced. For example, according to the researchers, utterances such as [\[4.3a\]](#eq4.3) were judged to be ungrammatical because their semantic bias distanced them from the hypothesis of a relative structure and led them to a *garden path*,[](#ch4en5) when they encountered the verb *passed*. This garden path was avoided in utterances similar to [\[4.3b\]](#eq4.3), where the semantic context made it possible to guide the subjects toward a relative structure that was syntactically correct. A similar study to that of Crain and Steedman was conducted by \[TRU 92\] from a discourse analysis perspective. The researchers used utterances with ambiguous verbs (whose form is identical to equivalent past participles) as in [\[4.3\]](#eq4.3):

1. a) The fossil examined…. [\[4.3\]](#ieq4.3)
2. b) The archeologist examined….

In these utterances, the verb *examined* has the same form as the past participle of the same verb. As in \[CRA 85\], the researchers found that semantic knowledge directly influenced the choice of syntactic structure and sometimes led to garden paths.

\[CAR 88\] conducted a study of eye movement during reading. This work showed that the duration of fixation on words that were semantically abnormal to the context was longer than that of equivalent words (in terms of length, frequency and syntactic adaptation compared to the rest of the utterance) that were semantically normal. This shows that the semantic analysis occurs in parallel with the reading process (and therefore with the syntactic analysis). Several experiments aiming to clarify the role of the discursive context in comprehension have been conducted \[SPI 93, BOL 95\]. In his study, \[ALT 99\] described two experiments concerning this problem. In these two experiments, the subjects had to read utterances similar to [\[4.4\]](#eq4.4). These utterances were used in contexts that introduced possible objects. The idea was that after the verb *drank*, the subjects were supposed to think that the utterance did not make sense if the object of the verb was not a drinkable element. After asking the subjects to examine different groups of utterances, he observed that the negative answers (i.e. that the utterance did not make sense) required more time when the anterior context was ambiguous. The author concluded that the semantic roles (agent, patient, recipient, etc.) associated with arguments that are discursively anterior to a verb (arguments located in a prior conversational turn) are selected at the moment of perceiving the verbal head by considering the available roles (i.e. roles that have not yet been associated with a lexical unit), even when the entity that refers explicitly to these antecedents (anaphoric pronouns) is in a post-verbal position and this entity has not yet been processed by the subjects. This shows that the discursive context intervenes in the syntactic analysis of an utterance and that this intervention occurs in parallel with the syntactic analysis, given that its effect is detected before the end of processing the utterance:

He drank some…. [\[4.4\]](#ieq4.4)

The disagreement between the results of these experimental studies can be interpreted in two different ways. On the one hand, it could be the result of methodological or technological issues in the investigation of the considered problems. On the other hand, it could be the reflection of the existence of a variety of strategies whose triggering is produced by specific conditions. This divergence in the cognitive domain has affected the divergence of the architectures of NLP systems that are divided into three main forms: sequential, integrated and parallel \[MAH 95\] (see examples in [Figure 4.6](#fig4_6)). The architectures (a) and (b) in [Figure 4.6](#fig4_6) are relatively simple to explain because they are the direct translation of syntax first or semantics first strategies, respectively. They presuppose the existence of independent knowledge sources and independent processing methods for both syntax and semantics. The interaction between the modules occurs unidirectionally from the source toward the destination. The integrated architectures (c and d in [Figure 4.6](#fig4_6)) in turn start from the premise that there is a unified framework for the representation of syntactic and semantic knowledge as well as for their processing. In practice, the use of modules based on rich formalisms such as HPSG, which integrates morphological, syntactical and semantic knowledge, is an example of an integrated architecture.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_6.jpg)

Figure 4.6. Some software configurations for integrating syntax and semantics

More complex, parallel approaches use independent knowledge sources and processing that occurs on two axes simultaneously. These can be realized in more varied forms than sequential or integrated approaches, as in the four forms, (e), (f), (g) and (h), shown in [Figure 4.6](#fig4_6). The main reason for this divergence is the mode of coordination between the two parallel axes. Some architectures implement a blackboard-based coordination whose role is to coordinate efforts, while others implement an arbitration that attributes a fixed or context-dependent weight to resolve potential conflict between the two knowledge sources. Non-controlled parallel architectures presuppose the adoption of a single generic framework for syntax and semantics that makes direct communication impossible. When the two modules have different theoretical backgrounds, a module to translate formats or convert content is required for all interactions between these two modules.

### 4.1.8. Programming languages for NLP

Although NLP applications can be coded with a very large number of high-level programming languages, notably including Java, C++, C# and Python, some seem more appropriate for language processing due to either their inherent properties or the massive adoption of these languages by the community and, consequently, the availability of rapid development tools for NLP written in these languages.

Historically, LISP, designed by John McCarthy in 1958, is the programming language that first attracted the interest of NLP experts, notably because of the ability to process lists and lambda calculus (see \[GAZ 89a\] for an introduction to NLP with LISP).

For a long time, Prolog was very directly linked to NLP. In fact, this language was designed with the intention of automatically processing language (Colmerauer’s metamorphosis grammars) and Definite Clause Grammar (DCG). This language is an implementation of predicate logic that offers a privileged framework for semantic representation. The native integration of backtracking considerably facilitates the implementation of a large number of NLP algorithms, mainly including parsing algorithms. Another important advantage of Prolog is the availability of books that cover the main topics of NLP such as \[PER 87, GAZ 89b, MIC 91, COV 94\]. Two major families of Prolog can be distinguished, Marseille Prolog or Prolog II and Edinburgh Prolog, which is more common. Following the interest in this language, several implementations of the Edinburgh version were created, each with specific properties. Swi-Prolog is an academic version that is largely used for teaching around the world. Developed in the Netherlands at the University of Amsterdam, this version of Prolog is distinguished by respecting the Edinburgh syntax as well as is efficiency. It is also distributed with an open-source license. SICStus Prolog was developed at the Swedish Institute for Computer Science and is also popular in academic environments. Gnu Prolog is a free version developed at the INRIA. Amzi-Prolog is distinguished by its easy integration with Java, notably in the context of the Integrated Development Environment (IDE) ECLIPSE. A comparative study of the performances of several versions of Prolog showed that there are substantial differences in performance between these different versions (see [Table 4.1](#tab4_1)).

**[Table 4.1](#itab4_1).** *Comparison of several programming environments in Prolog \[FER 00\]*

| **System** | **Version** | **Time** |
| --- | --- | --- |
| SWI | 1.8 | 1.2 |
| SICStus | 3.11.2 | 11.8 |
| Yap | 4.4.4 | 19.5 |
| Ciao | 1.10 | 6.6 |
| GNU | 1.2.16 | 10.9 |

Despite its many advantages, Prolog also has several disadvantages. Based on logic, Prolog syntax is difficult to learn compared to other languages with more conventional forms for computer scientists. The many variants also make it difficult to interface with programs written in other languages. Although it is very well suited for processing logical formulas, Prolog is not a natural tool for implementing statistical algorithms or matrix calculations, which are very important for many NLP applications. The most significant disadvantage of Prolog is probably its low speed compared to other lower-level languages such as C, Java or Python.

Python is increasingly popular within the NLP community. Developed in 1991 in the Netherlands by Guido Van Rossoum, this language is included in the list of languages officially adopted by Google. The advantage of Python is that it can be used as an object-oriented language or as a script language whose syntax is intended to have a simplicity similar to natural language. This gives it the advantage of greater generality compared to a strictly object-oriented language such as Java with slightly more complex and strict syntax. In other words, Python can be used to write small projects quickly, large commercial applications and a glue code to integrate programs written with languages such as C, C++ and Java. Python is a particularly attractive language for developing Web applications, notably thanks to the availability of libraries or frameworks like Zope, CherryPy or Django. Python also has rich documentation as well as abundant literature that covers practically all aspects of programming related to this language \[LUT 06, DAW 03, ASC 03, MER 03\].

For an NLP specialist, what make Python an attractive language are the data structures such as lists and dictionaries that facilitate the processing of character sequences. External tools developed with Python make it even more attractive, including the NLTK toolbox, which includes morphological, syntactic and semantic analysis tools. Particularly easy to use and well documented, it is used in research as a support for practical works in NLP courses \[BIR 09\] and in the industry. In Python, the availability of other tools and generic libraries related to the domains of artificial intelligence and machine learning that also apply to NLP, for example Orange [](#ch4en6), Scikit Learn [](#ch4en7), PyBrain [](#ch4en8), PyML [](#ch4en9), LibSvm [](#ch4en10) and Neurolab [](#ch4en11), make this language even more attractive. The major disadvantage of Python is its relative slowness compared to languages like C. As an indication, an informal comparison of the speed of loop processing was conducted between three languages: C (reputedly the most efficient of the high-level languages) with the MinGW compiler (a minimalist version of the GNU compiler for Windows), Python (2.7) and Prolog (Swi-Prolog). Realized on a machine with a Pentium III processor and Windows 2000, the experiment had the following results: the code written in C was 28 times faster than the code written in Python, and Python was, in turn, 10 times faster than the code in Prolog.

### 4.1.9. Evaluation of NLP systems

The question that is always posed when developing an NLP software is: does this software respond to the prerequisites initially expressed in the project specifications? The evaluation is an objective way to answer this question. There are two types of evaluation, depending on when the operation is conducted: formative evaluation and summative evaluation. Formative evaluations occur during the development of the program on prototypes or intermediary versions. The objective of these evaluations is to inform people involved in the development, of possible problems regarding the system design or its code. Summative evaluations are done on an intermediary or final version of the system and are intended to evaluate the system’s performance and the degree to which it satisfies the project specifications. A comparison of these performances with the performances of one or more similar systems can be one of the objectives of a summative evaluation. The evaluation can be done manually or automatically using a battery of tests.

Regarding the object of the evaluation, two different dimensions of the software are verified: structural dimension and functional dimension. The structural dimension concerns the code and its internal logic in a way that is almost independent from the system requirements. The idea is that software with errors or bugs in the code cannot satisfy the specifications, whatever they may be. The functional evaluation, in turn, is intimately linked with the system requirements. The results of this evaluation are a good indication with which to judge the quality of the cognitive or linguistic model adopted and sometimes the quality of the data used in the development process. There are two types of functional evaluation: quantitative and qualitative. For a general introduction to the evaluation of NLP systems, see \[RES 10, PAR 07, KIN 98\]. For more information on the structural test as well as other forms of similar evaluation, see \[LEW 05\].

#### 4.1.9.1. Structural test

Sometimes called the *whitebox test*, the structural test is intended to evaluate a program’s logical paths. This kind of test pertains more to the internal logic of the program than to the specific requirements in the project specifications. It requires very deep knowledge of the internal structure of the program and its logic. It is intended for the identification of malfunctions or bugs in the code or malfunctions related to module compatibility. In heterogeneous software systems, partial incompatibility of module input and output formats is a major source of errors. A complementary test, not for errors but for the runtime speed, can reveal problems in the implementation. The idea is to prepare a battery of input sentences of varying lengths and measure the runtime for each one. This makes it possible to draw up a line of the runtimes. Comparing the practical curve with the theoretical complexity of the algorithm implemented makes it possible to identify the problems. For example, to evaluate the runtime of the Oasis system, a corpus of 588 utterances was chosen \[KUR 03\]. The utterances chosen were extracted from the hotel reservation corpus and the corpus collected in the challenge evaluation campaign which will be presented in [section 4.1.9.3](#se4.1.9.3). To get a clearer idea of the runtime curve, consider the graph that only contains the worst runtimes observed ([Figure 4.7](#fig4_7)). The observation of all of the utterances was confirmed with the analysis of these cases that generally show a linear behavior. Note that the exceptions to the gradual increase in runtime with the increase in utterance length are due to the difference in frequency terms between the different lengths.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_7.jpg)

Figure 4.7. Runtime of the worst cases observed by length

#### 4.1.9.2. Quantitative evaluation

This type of evaluation is intended to establish a general idea of a system’s performance. It is done using a set of representative cases that is sometimes called a battery of tests. Typically, the corpus is divided into two unequal parts. The first part, generally two-thirds of the cases, is used for training the system or writing the rules. The second part, composed of the rest of the cases, is used for the evaluation. The motivation behind this separation is the evaluation of the generalization of the system, which is related to its capacity to process new cases. In practice, this division does not guarantee a complete diagnostic of the limits of a system because it depends on the variation of the data in the corpus (linguistic structures, vocabulary, etc.) but nevertheless remains a minimum. Note that the evaluation can also concern an independent module (known as a modular evaluation) rather than the entire software.

When evaluating any system, there are four types of cases:

- – True Positives TP: acceptable cases that are considered as such by the system. For example, in the case of the evaluation of a syntactic parsing module, an example of this type would be a well-formed sentence that is correctly parsed by the system.
- – True Negatives TN: unacceptable cases that are rejected by the system. In the case of a syntactic parsing, an example of this type would be a malformed sentence correctly rejected by the system.
- – False Positives FP: unacceptable cases that are incorrectly analyzed as being acceptable. This is sometimes referred to as overgeneration. This is an ungrammatical sentence that is incorrectly syntactically parsed as a correct sentence.
- – False Negatives FN: correct cases that are incorrectly rejected by the system. For example, a grammatical sentence incorrectly rejected by the parser.

Having established a typology of the analysis cases, the next step is to define the three main quantitative measures of evaluation: recall, precision and F-measure or F-score (see formulae [\[4.5\]](#eq4.5)). The *recall* is a way of measuring the completeness of a system or its horizontal coverage. It consists of the number of correctly analyzed cases divided by the total number of analyses. The *precision* is a measure of the processing quality or the system’s rate of overgeneration. It is found by dividing the number of correctly analyzed cases by the total number of analyses. The idea is that a system that relaxes its constraints results in good recall but that this causes a decrease in the precision. Inversely, if the system is too restrictive, the precision will be good but the recall will be low. A good NLP system must find the right balance between the recall and precision. To unify these two measures, Nancy Chinchor \[CHI 92\] proposed the F-score:

[\[4.5\]](#ieq4.5) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_1.jpg)

Evaluating one’s own system is often a biased process despite the good intentions of the system’s designer. Besides using test data from the same corpus as the training, an evaluation by the designer risks repeating use scenarios that are typical for the system and avoiding scenarios that could mislead the system. It is also practically impossible to compare the performances of two different systems whose evaluation has been made using two different corpora. One solution to this problem is to proceed with collective evaluation campaigns of similar systems (with the same requirements). Especially in the competitive American tradition, this results in a sequencing of the systems involved in the campaign according to the results. Several evaluation campaigns have been organized first in the United States and then in Europe. For example, there have been campaigns to evaluate TREC information retrieval systems \[VOO 05\], tagging parts of speech \[ADD 98\], understanding spoken or written language with the ATIS and MUC campaigns \[CHI 92\] and analyzing speech \[ANT 02b\].

#### 4.1.9.3. Qualitative evaluation

A qualitative evaluation method should satisfy a set of requirements. For example, it should be generic and independent of all applicative domains. It should also be applicable to systems whose output is encoded in different formats. It should also provide a detailed diagnostic of the system’s behavior that exposes its weaknesses and strong points. This diagnosis should ideally include all relevant phenomena while having the possibility of establishing a partial diagnosis per phenomenon. For example, if we wish to evaluate a syntactic parsing module, it must be possible to evaluate it on all syntactic phenomena such as subordination, coordination and displacement, but a partial evaluation on a system on a limited number of phenomena such as negation or coordination should also be possible.

To gain a deeper understanding of a system’s behavior, not only can the system’s recall and precision be given for the entire test corpus, but these measures can also be used per phenomenon of interest. For a syntactic analysis module, the recall and the precision can be found for sentences with ellipses, coordination, subordination, etc. This makes it possible to establish a deeper diagnosis of the system’s performances. It is also sometimes useful to draw up a record of the kinds of errors in terms of confusion. In particular, this makes it possible to determine the percentage of confusion between the different phenomena. To do this, a confusion matrix can be established in the form of a table where each cell \[i, j\] indicates the prediction frequency of a label *j* in the place of the label *i*.

The DCR method (Declaration Control Reference) is an attempt to satisfy the requirements of an objective evaluation. The basic idea behind this method is to produce a derived corpus that can be used to evaluate the system from an initial corpus, based upon which the system was constructed. The derived corpus is composed of several parts, each of which is dedicated to evaluating a specific linguistic phenomenon. On the one hand, this is a way of bypassing a lack of relevant data and, on the other hand, this makes it possible to guarantee the objectivity of the evaluation. A DCR evaluation has three steps \[ANT 00\]:

1. 1) *The declaration D*: consists of an ordinary utterance that features in the system’s training corpus.
2. 2) *The control C*: consists of modifying the version *D* of the utterance in order to account for a specific phenomenon.
3. 3) *The reference R*: is a Boolean value that accounts for the coherence of the utterance.

To clarify these three steps, consider this example:

- \<D> I would like a double room with a view of the sea.
- \<C> I would like a single room.
- \<R> False.

In order to make the process of deriving C utterances from D utterances more systematic, a modified version of DCR, called extended DCR, was proposed by \[KUR 02\]. The primary innovation consists of using a description, the most exhaustive possible, of the intended phenomena called the derivation grammar as the basis for the derivation process.

A combination of objective evaluation methods and collective evaluation campaigns was also proposed in \[ANT 02b\]. This campaign, called the challenge evaluation, involved five automatic spoken language understanding systems from four French laboratories specializing in NLP and human–machine dialogue systems. These include the CLIPS-IMAG laboratory in Grenoble, the IRIT laboratory in Toulouse, the Valoria laboratory in Vannes and the LIMSI laboratory in Paris. Each system designer proposed his own initial corpus composed of 20 initial utterances that his system was capable of processing correctly. Proposed to the project partners, the initial corpus served as a basis on which to obtain the derived corpus. Having the only constraint of not leaving the semantic domain of the initial utterance, the partners were strongly encouraged to use their imaginations to propose original structural modifications. The modifications could have the form of grammatical phenomena (extractions, parentheses, ellipses, etc.), extra-grammatical phenomena (repetitions, hesitations, etc.) or simulations of artificial phenomena such as recognition errors (the subjects remove, replace or add words in a similar way to what recognition systems can do in cases of error). For each initial utterance, each participant created 15 derived utterances. In other words, for each initial utterance, there were 60 derived utterances and 1,200 utterances in the derived corpus. As an example, a translation of an initial utterance and a set of derived utterances are given in [Figure 4.8](#fig4_8). Before being used, the derived corpus was validated by the designer of each system. The validation consisted of a judgment by the system’s creator of the adaptation of the derived utterances proposed by the campaign participants. Utterances deemed unsuitable were modified by the creator of the test. The main requests that were made by the participants concerned spelling errors as well as utterances judged not relevant or not realistic in relation to the system’s task.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_8.jpg)

Figure 4.8. An example of an initial utterance and some derived utterances

## 4.2. Machine translation (MT)

Today, globalization has made enormous quantities of information accessible, for example, in the form of web documents or texts scanned and transcribed with OCR [](#ch4en12) software, but use of this information sometimes faces a linguistic barrier. New multinational organizations are being added to many existing organizations such as the World Trade Organization (WTO) and the European Union. This need has grown even more with the arrival on the global stage of certain Asian countries whose languages are little-known outside their national borders. It should also be noted that, far from its ideals, MT is an excellent means of technical and industrial spying. Human translation, the natural response to all these needs, suffers from several disadvantages, notably its high cost and the need for a foreign human presence which is not necessarily possible or desirable depending on location (translation of military texts or conversations, for example), the time of day or year or the subject in question. Hence, there is a need for a software system that is capable of taking the input of a text in a source language and producing an equivalent text in a target language. The advantage of these systems compared to human translation is the spatial and temporal availability (a telephone or internet connection is sufficient to access the system when it is deployed in the form of Software As a Service (SaaS)). For a general introduction to machine translation, see \[HUT 92, ARN 94, ACL 16\].

### 4.2.1. Why is translation difficult?

Translation is a very difficult task and, whatever the skill level of the human translator, translation errors are always possible. The constantly changing dynamics of language is a common reason for these errors. In addition, some texts require extra-linguistic knowledge related to the content that the translator does not necessarily have. This contributes to an incomplete or even incorrect understanding of the original text and, consequently, a bad translation.

#### 4.2.1.1. Linguistic divergences

From a lexical point of view, cases of polysemy where a single word can have several different meanings are probably the most important. For example, the verb *know* can be translated as *savoir* or *connaîtr* *e* in French depending on the context (see examples [\[4.6\]](#eq4.6)).

| 1) I know the book you’re talking about. | 3) Je **connais** le livre dont tu parles. |
| --- | --- |
| 2) I know how to go to England. | 4) Je **sais** comment aller en Angleterre. [\[4.6\]](#ieq4.6) |

In addition, certain cases of homonymy can also be a source of problems. For example, the British words *pound* (unit of weight and currency) are impossible to distinguish. Sometimes the context makes it possible to disambiguate the meaning but not always. Similarly, the French word *langue* is one example that linguists know well. This word does not have a direct equivalent in English, which is why English linguists are obliged to borrow the French word for their texts, notably when they are discussing the famous Saussurian distinction of langue/parole. Many words or expressions do not have an equivalent in other languages. For example, the notion of the *weekend* does not exist in the Arab world in the same way as in the Western world. Consequently, there is no clear equivalent in Arabic of the French word *weekend*, which is itself borrowed from English [](#ch4en13). Moreover, the locutions *right away*, *see you soon* and *see you in half an hour* do not have an exact equivalent in Arabic. Obviously, a more or less equivalent expression can always be found; however, as the concept itself is not familiar, this expression will seem unexpected or even bizarre.

Given the syntactic differences, the correspondence between two sentences belonging to two different languages, regardless of their degree of similarity, seems impossible. Word order differs from one language to the next. For example, French and English are languages where the preferred sentence order is Subject Verb Object (SVO), German is a SOV language and Arabic is a VSO language. Similarly, agreement does not have the same form in all languages. In French, for example, the verb agrees with its subject in number but not in gender, unlike Arabic, where the verb agrees in number and gender. Note that there are also particular forms like the subject pronoun that are not given in sentences in Italian (see [\[4.7\]](#eq4.7)):

> Parlo bene l’italiano [\[4.7\]](#ieq4.7)
> 
> I speak Italian well.

The binary in Arabic, a particular form of the plural that, to my knowledge, does not have an equivalent in European languages, is another example of these particular cases.

#### 4.2.1.2. Ambiguities in the source text

Ambiguity is one of the key problems in NLP. Ambiguities concern all linguistic levels from the words to the text. Resolving these ambiguities is not a simple task. Even humans with a good understanding of the context sometimes have difficulties.

#### 4.2.1.3. Errors in the source text

In real applications, notably on the Internet, the level of formality and therefore of grammaticality of texts can vary substantially, which can lead to reduced performance of machine translation which makes manual correction necessary.

### 4.2.2. History of MT systems

#### 4.2.2.1. The early days: (late 1940s–1965)

The beginnings of machine translation go back to the late 1940s, with the work of W. Weaver among others, who proposed using cryptographic decoding techniques to translate texts automatically \[WEA 55\]. In 1952, the first conference on machine translation was held at the Massachusetts Institute of Technology (MIT). This conference occurred in the context of the American–Soviet rivalry during the Cold War. The first prototype called the Georgetown Automatic Translation (GAT) was created at Georgetown University by the team of D. Dorstert and R. McDonald. The hopes elicited by MT systems were quickly diminished. These systems, called the first generation or direct translation, were based on a word-for-word translation model that only made recourse to a dictionary, without using syntactic or semantic representations. Critics of the systems during this period continuously emphasized the errors that these systems produced during the translation of two English proverbs into Russian and back into English, to ridicule MT (see, for example, [\[4.8\]](#eq4.8) for a French adaptation):

| The spirit is willing but the flesh is weak | La vodka est bonne mais la viande est pourrie. [\[4.8\]](#ieq4.8) |
| --- | --- |
|  | *The vodka is good but the meat is rotten*. |
| Out of sight, out of mind | Invisible et fou. |
|  | *Invisible and insane* |

At the same time as the work conducted in the United States, Soviet researchers focused more on theoretical and linguistic subjects. Already at that time, their work considered the possibility of creating a universal formal language that could serve as a bridge between the source language and the target language.

Following the controversy over the performances and use of MT systems, the American government agencies who had funded the research work of about 20 teams in MT created a special commission called the Automatic Language Processing Advisory Committee (ALPAC) in order to evaluate the progress made by the teams in question. Under the direction of John R. Pierce, this committee wrote a report that can be summarized by the following points \[ALP 66\]. First, the mediocre quality of the translation obtained by these systems often required human intervention to obtain a good translation. Next, because microcomputing was non-existent at the time, the development of such systems was particularly expensive. Finally, it seemed necessary to consider the linguistic factors and consequently increase support for computational linguistics. However, it was the negative content that the readers of this report retained and it resulted in a decrease in funding for MT projects and MT research was set on the back burner for several years.

#### 4.2.2.2. The second generation (1965–1975)

During this period, despite the decline in funding, some teams nevertheless managed to continue their work on MT systems, including:

- – the METAL system (University of Texas);
- – the SYSTRAN system;
- – the TAUM system (University of Montreal);
- – the CETA/GETA system in Grenoble directed by Bernard Vauquois.

Most of the systems in this generation adopted an “indirect” approach where intermediary semantic representations independent of language served as a point of passage between the source language and the target language. From an architectural point of view, these systems opted for a strict separation between linguistic resources, notably syntax and semantics on the one hand, and software resources on the other hand. Aiming for better translation than the first-generation systems was also an objective of this generation of systems, which were characterized by these features:

- – The syntactic analysis was gradually enriched by a semantic and even contextual analysis.
- – The domain of application was restricted, for example, to the translation of weather reports, like the TAUM-METEO system from the University of Montreal.
- – The vocabulary and syntactic constructions were relatively small in number and therefore easily catalogued and the risks of ambiguities decreased.
- – The languages covered diversified and expanded beyond the Russian–English pair.

#### 4.2.2.3. Resurgence in interest (1975–1990)

After 1975, there was an increase in the need for translation systems by companies. This resurgence in interest was also supported by the development of new computer and electronic tools, such as programming languages and modeling, and the availability of more powerful computers. The systems developed at this time were mainly the most advanced and most sophisticated second-generation systems. The pace of work on MT accelerated in the early 1980s, as demonstrated by these projects:

- – the PN-TAO project between 1983 and 1987 (France);
- – the EUROTRA project launched by the European Commission in 1982 that covered its nine majority languages;
- – the national Canadian program launched in 1985;
- – the programs of fifth- and sixth-generation systems launched by the University of Kyoto in Japan;
- – the SYSTRAN software was adapted for MS-DOS and ran on the IBM PC in its version with two disk drives, meaning without a hard drive.

With developments in linguistics, notably in syntax, several researchers explored the adoption of new linguistic formalisms based on unification or constraints in machine translation. The advantage of these formalisms was their capacity to incorporate several levels of representation with a single formalism.

#### 4.2.2.4. The recent period

The power of computers made it possible to imagine a different solution: drawing from immense corpora of computerized databases to reuse fragments of already-translated sentences. Notably initiated by IBM, the approach grew in the 2000s with Google, which collects all the translations on the Internet, marking a turning point in the history of MT. This period has also seen the launch of initiatives to create large-scale linguistic resources. It is also distinguished by the creation of collection and distribution centers of resources such as the Linguistic Data Consortium (LDC) (University of Pennsylvania, USA) and the European Language Resource Agency (ELRA) (Paris, France). It has also seen the launch of the first conference dedicated to NLP resources, the Language Resources and Evaluation Conferences (LREC) (see [Chapter 1](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch01.xhtml) of the first volume of this book \[KUR 16\] for more details).

### 4.2.3. Typology of MT systems

The number of languages covered by an MT system is an important criterion when drawing up a typology of MT systems. From this perspective, two types of systems can be distinguished: bilingual systems and multilingual systems. Bilingual systems are divided into two groups: reversible or bidirectional systems, where translation can occur between the source language and the target language and vice versa, and unidirectional systems. The number of languages plays a very important role in the choice of technique to adopt for the translation.

Beyond the purely quantitative aspects, the number of languages concerned by a system affects the software aspects, the approach adopted for the translation. Another criterion for classifying an MT system is the input media. In fact, the input of an MT system can be a scanned text that is transcribed automatically by an OCR software. With the progress with OCR, this task is doable with the current technology except that some transcription errors can occur especially when dealing with a handwritten text. Other types of MT systems are designed to deal with spoken conversations. In this case, they should not only handle speech recognition errors but also the specific phenomena that can occur within spoken language such as extragrammaticality. It should be noted here that prosody is not usually accounted for by MT systems.

Regarding the sharing of tasks between the machine and the human translator, these types can be distinguished: human translation, machine translation assisted by humans and machine translation.

In the case of human translation, all of the translation steps are completed manually. The only possible assistance by machine in this case is the level of formatting of the translation (word-processing software) or the level of access to lexical information (electronic dictionary or translation memories). It is important to note that purely human translation does not preclude the intervention of other human experts during or after the translation. This intervention is sometimes formalized by the addition of the name of the translator and the reviser in the meta-data of the translation.

Moreover, metalinguistic information, sometimes necessary to translate a text well, is also accessible through electronic encyclopedias or on the Internet. In some cases, a translator can use computer resources, which is known as Computer-Assisted Translation (CAT).

Regarding automatic translation assisted by humans, the input text can be modified by a human at three different steps. The first type of intervention can occur before the intervention of the machine, when a translator quickly reads through the text to correct potential spelling or grammar errors. Depending on the system, lexical processing can sometimes be carried out, for instance the replacement of words outside of the system’s vocabulary. A first translation of the text toward a controlled natural language can also be done. In this type of language, the vocabulary and the syntactic constructions are limited in advance to control the ambiguities. The second type of intervention occurs during translation by the machine. Some MT software interacts with the user through dialogue to resolve certain ambiguities that the software could not resolve on its own. Requiring an alert user, this process becomes cumbersome when the text contains many ambiguities because the translation time increases considerably. Finally, the third type of intervention occurs after the machine intervention in post-processing to correct errors or improve style. Some MT software produce several alternative translations in cases of structural or semantic ambiguities, giving the translator the responsibility of choosing which one should be retained during this last step.

Machine Translation itself is an entirely automated process where the machine carries out all steps of the translation without any external intervention.

### 4.2.4. The use of MT

From a functional point of view, J. Carbonell established the distinction between two processes: assimilation and dissemination (see [Figure 4.9](#fig4_9)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_9.jpg)

Figure 4.9. Functional typology of MT systems according to Carbonell

Assimilation consists of formulating a synthesis of what is written about a subject like a political, economic or sporting event in different languages ([Figure 4.10](#fig4_10)) from a set of documents that often come from a collection on the Internet. Given the wide variety of topics that can be addressed, this cannot involve high-level knowledge, notably semantic and pragmatic knowledge, in the translation system. Consequently, it is expected that the quality of the translation will require human post-editing.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_10.jpg)

Figure 4.10. General diagram of the assimilation process

Dissemination, on the other hand, occurs from a given language toward several languages (see diagram in [Figure 4.11](#fig4_11)). A typical example of this process is the translation of product catalogues intended to be exported. In general, this consists of translations that concern a limited domain. This makes it possible to carry out deep linguistic analyses and therefore allows for a better-quality translation that requires little or no post-editing.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_11.jpg)

Figure 4.11. General diagram of the dissemination process

The translation of literary works, especially poetry, is distinguished from the two abovementioned types by the fact that the form and poetic function must be transposed. This type of translation requires very advanced skill in the target language. Generally, translators of this kind of literature are themselves bilingual authors or poets. In some cases, the translation is done by two people: a translator provides a translation of the meaning into the target language and an editor reformulates it in the target language in an appropriate literary style. For example, the most famous Arabic translation of *Paul et Virginie [](#ch4en14)* by Bernardin de Saint-Pierre was formulated by Egyptian author Mustapha-Lutfi al-Manfalouti, who did not speak French. An MT software can thus be used to obtain drafts whose final formulation will be done by a professional in the target language without necessarily needing to have perfect mastery of the source language.

### 4.2.5. MT techniques

It is possible to carry out a translation using several levels of linguistic knowledge. The more diverse the knowledge, the better the quality of the translation, but the more complex the development process. To represent this diversity of systems, Bernard Vauquois proposed the triangle given in [Figure 4.12](#fig4_12) \[VAU 68\].

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_12.jpg)

Figure 4.12. The Vauquois triangle with some modifications \[VAU 68\]

Four different approaches can be distinguished from the triangle: the direct approach, the transfer approach (syntactic and semantic) and the pivot approach.

#### 4.2.5.1. Direct approach

Adopted by the majority of the first-generation systems, the direct approach is the most intuitive and the simplest. The translation process consists of finding an equivalent in the target language for each word in the source sentence to form the target sentence (see [Figure 4.13](#fig4_13)). First of all, a superficial morphological analysis phase makes it possible to find the basic forms of words: lemmas. They are then used to find an equivalent in the target language with a bilingual dictionary, without any consideration for syntax or semantics. Finally, some local rules make it possible to order the words obtained, for example, by moving the adjectives or prepositions.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_13.jpg)

Figure 4.13. Architecture of a system using the direct approach

Because it does not consider the context, this approach comes up against all kinds of ambiguities. Moreover, the local rules for re-ordering are not sufficient and sentences obtained in the target language are often not correctly formulated.

#### 4.2.5.2. Transfer approach

These systems are less ambitious than the pivot systems, because they provide two distinct representations *R* and *R’* whose level of abstraction is lower than the pivot language (see [Figure 4.14](#fig4_14)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_14.jpg)

Figure 4.14. Architecture of the transfer approach. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

The targeted representations are often syntactic–semantic constructions of sentences instantiated by words in the language. They are therefore concrete linguistic representations rather than abstract conceptual representations. The transfer module has the goal of transforming the representation of the input text in the source language into an equivalent representation that serves as a point of departure for a translation into the target language. A special module is necessary for each language pair as shown in [Figure 4.15](#fig4_15).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_15.jpg)

Figure 4.15. Architecture of a transfer-based system with three languages

Many translation systems have adopted this easily implemented approach. The complexity of the system increases considerably with an increase in the number of languages. For example, for *n* languages, we need *n* analysis modules and *n* generation modules as well as n \* (*n−1*) transfer modules. This adds up to a total of n \* (*n+1*) modules in the system. For example, for a value of *n* equal to 3, there is a total of 12 modules. For *n* equals 6, the total number of modules is 42, 30 of which are transfer modules.

The syntactic transfer is a particular form of this approach. It consists of connecting two surface syntax structures, one in each language. Three main steps are necessary to realize a translation system in this case. First, the syntactic analysis tree of the input sentence is constructed. Then, the constituents are rearranged. Finally, the words are translated and the tree of the sentence is constructed in the target language. In the example in [Figure 4.16](#fig4_16), the syntactic parsing of the input group is shown. The syntactic transfer is a rearrangement of the elements in the sentence.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_16.jpg)

Figure 4.16. An example of a syntactic transfer

In reality, it is not always this simple. Often, the translation results in deeper changes. For example, the subject becomes the object, or vice versa. Consider the following pair: *You(subject) like \[the house\](object), \[La maison\](subject) te(object) plaît*. The subject of the sentence in French becomes the object of the sentence in English, as shown in [Figure 4.17](#fig4_17).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_17.jpg)

Figure 4.17. Syntactic transfer with order inversion

The introduction of syntactic knowledge resolves issues with the order, but the semantics of the translations obtained are often inappropriate, in particular because the formulation of fixed expressions from one language to another can pose problems for this kind of translation.

Semantic transfer approaches consider the translation as a relation between two semantic representations of the input sentence and the output sentence, respectively. Several semantic formalisms have been used such as the QLF (quasi-logical form), based on predicate logic. To make the syntax–semantics interaction more explicit within the LTAG formalism, \[SHI 90\] proposed parallelizing the syntactical structure, represented by elementary trees, and an argument predicate structure that serves as a semantic interpretation skeleton for the elementary tree with which it is associated. The semantic representation also has the form of a tree structure. Thus, at least one semantic tree is associated to each elementary tree and the links are defined between the nodes of the two trees that restrict the possible derivations. The main innovation of this formalism is that the syntactic and semantic derivations must be synchronized. Thus, the derivation of two trees < *α <sub>1</sub>*, *α <sub>2</sub>* > follows these steps:

1. 1) In a non-deterministic way, choose a link between two nodes (*n <sub>1</sub>* to *α <sub>1</sub>* and *n <sub>2</sub>* to *α <sub>2</sub>*).
2. 2) In a non-deterministic way, choose a pair of trees < *β <sub>1</sub>*, *β <sub>2</sub>* > of the grammar.
3. 3) Create the pair < *β <sub>1</sub>* < *α <sub>1</sub>*, *n <sub>1</sub>* >, *β <sub>2</sub>* < *α <sub>2</sub>*, *n <sub>2</sub>* >> where *β* < *α*, *n>* is the result of a primitive relation on *α* at node *n* using *β*.
![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_18.jpg)

Figure 4.18. Example of a synchronized syntactic tree and semantic tree

Machine translation is the most common application of this formalism. The basic principle of these applications is to use the transfer rules from one language to another. For each derivation tree in the source language, a corresponding derivation tree is constructed in the target language. This is done by establishing a link between each node on both sides and by preserving the relations of dominance between the nodes in the source derivation tree. The transfer diagram is presented in [Figure 4.19](#fig4_19). A modified version of this formalism has been proposed for the automatic translation of speech \[CAV 98\].

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_19.jpg)

Figure 4.19. Diagram of a simple transfer \[PRI 94\]

From an engineering perspective, transfer-based approaches are not an elegant way to carry out translation. As shown, there are many modules for each language pair. Despite this design problem, this approach remains a fast way to construct translation systems. The transfer-based approach closely resembles the pivot-based approach if attempting to obtain deep linguistic representations.

#### 4.2.5.3. The pivot or interlingua approach

In 1629, René Descartes proposed this approach using mathematics as a universal language. It was this very principle that was taken up in the second half of the last century as a solution to machine translation problems. In the interlingua approach, processing occurs in two steps, as shown in [Figure 4.20](#fig4_20):

- – *An analysis module* that produces a representation of the input text in the source language in a pivot language (designed to be independent of all language).
- – *A generation module* that generates a well-formed sequence of words from the semantic representations obtained in the pivot language. An automatic translation system involves practically all components of linguistic knowledge: morphological analysis, syntactic analysis and semantic analysis.
![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_20.jpg)

Figure 4.20. Architecture of pivot-based systems

Contrary to semantic transfer approaches, pivot-based analysis also involves pragmatic knowledge that allows for a better consideration of the context. However, this depth also has a cost, which is the requirement of analysis at several levels. On the one hand, this weighs down the development process considerably (requires more work). On the other, in terms of processing, this increases the translation time, which is crucial for some applications (especially in speech translation, where the translation must be instantaneous). An example of a pivot from the European project NESPOLE is given in [Figure 4.21](#fig4_21).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_21.jpg)

Figure 4.21. Example of a pivot in the domain of the translation of hotel reservations

Adopted in several machine translation systems (ARIANE by GETA, 1961–1971 and CSTAR, 2000s), this approach appeals to researchers for several reasons. On the one hand, it is ideal for typologically distant language pairs like (French–Arabic) and (English–Chinese). On the other hand, it stands out for its economy because the pivot can be developed once for all (regardless of the languages pairs intended). Finally, from a theoretical point of view, it relies on the idea, which is not unanimously agreed upon in linguistics, of the existence of language universals.

Imperfect, pivot translation suffers from limits that are known in the literature. It requires deep analyses that are difficult to implement such as the consideration of global textual phenomena, including inter-sentential phenomena. The multiplication of modules increases the sources of errors that can spread from one module to another. For example, a morphological analysis error causes a syntactic analysis error, which in turn leads to a semantic interpretation error. Due to the complexity of implementation, pivot translation is practically only used in closed domains like the translation of tourism texts like the CSTAR, VERBMOBIL and NESPOLE projects.

#### 4.2.5.4. Example-based translation (EBT)

The use of search engines by human translators to find the translation of an unknown expression is a common practice today. For example, to find the English equivalent of the expression *fait pour servir et valoir ce que de droit* [](#ch4en15), an Internet search of some French sites can lead to the correct response. Sometimes, however, the search results in a variety of possible translations with different meanings. To transform this empirical process into an efficient algorithm, a parallel corpus should be used in practice. In this kind of corpus, the sentences are associated with their translations considered in their original context. These sentences are preferred to minimal pairs, that is, sentences where one element is changed at a time (see sentences [\[4.9\]](#eq4.9)):

| How much is that **big watch**? | Combien coute **cette grosse montre**? [\[4.9\]](#ieq4.9) |
| --- | --- |
| How much is **that yellow bike**? | Combien coute **ce vélo jaune**? |

Example-based translation was first proposed by the Japanese \[NAG 84\]. Particularly appropriate for representing the context, this approach is well equipped to resolve ambiguities because verbal groups are particularly dependent on context by nature. It generally consists of a verb potentially followed by an adverb or a nominal or prepositional group, or sometimes both. The different forms that the arguments of the verb can take considerably affect its meaning and are sources of ambiguities, for example, the verb *ask* whose meaning changes significantly depending on the nature of its arguments. In general, most of the example-based translation approaches follow these steps:

- – Matching: searching for fragments of the input sentence in the corpus.
- – Alignment: identification of corresponding translations in the corpus. This step has the most variety between the EBT approaches. It can consist of the alignment of pairs of character strings or pairs of more complex forms: syntactic trees with context-independent grammar or formalisms like LFG and LTAG.
- – Recombination: this consists of the assembly of the fragments into a correct sentence in the target language.

From the point of view of performance, example-based systems give satisfactory results when the data used are well aligned and have good coverage of phenomena that are likely to be encountered in the target language, which is difficult to obtain except where it concerns limited applicative domains. That is why this approach is not used by commercial systems that prefer statistical approaches whose results are more easily controlled and are therefore better suited for their needs. However, EBT remains a promising domain and many teams of researchers are working on possible improvements.

#### 4.2.5.5. Statistical approach

Like the example-based approach, this approach is based on prior experiences through a parallel corpus. The basic principle of statistical translation is the following [](#ch4en16): suppose that there is a sentence in French *f* that we want to translate into Arabic to obtain sentence *a*. Depending on the translators, we can obtain different formulations that are more or less equivalent for *a*. The question is then to choose the best one of these forms. One possible response to this question is provided by probabilities. We can calculate the probabilities of possible translations pr(a|f) knowing the sentence *f* and selecting the more probable one. These probabilities are calculated starting from a parallel corpus. Of course, the quality of the translation model will directly depend on the quality of translations present in the base corpus. To infer probabilities from the base corpus, the Bayes formula is traditionally used ([equation \[4.10\]](#eq4.10)):

[\[4.10\]](#ieq4.10) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_2.jpg)

We can ignore the probability of the input sentence *p* (*f*) because it is shared by all of the translations. Thus, finding a better translation comes down to finding the value of *a* that will maximize *p* (*f* | *a*) *p* (*a*).

The idea of statistical MT is closely linked to the alignment of units of translation in the source language and the target language. These units can concern the sentence, the group or the word. To do this, several models have been proposed by IBM (see \[KNI 99, LOP 08\] for an overview). Finally, note that since 2006 statistical translation has had its own annual international workshop [](#ch4en17).

### 4.2.6. Example of a translation system: Verbmobil

The German project Verbmobil is, to my knowledge, the largest project ever realized in the world on the translation of speech in real time. As indicated by its name, this project is intended to process spoken conversations through mobile telephones \[WAH 00b\]. The main objective of the system constructed over the course of this project is the automatic translation of speech, but automatic dialogue summary functions have been added as well, for example, to generate a general reminder of what the two interlocutors have said during their negotiation and thereby validate the information exchanged in the dialogue.

Processing these dialogues occurs in an entirely centralized way in the main server of the system. As [Figure 4.22](#fig4_22) shows, the first locutor emits his utterance via his mobile phone. The signal emitted is then transmitted by satellite to the central server that carries out the automatic translation and produces a synthesized utterance in the target language that corresponds to the utterance received. Finally, the synthesized utterance is transmitted via the satellite to the addressee’s mobile phone. Users only need a mobile phone to use this translation service in this model that is known as Software As a Service (SAS).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_22.jpg)

Figure 4.22. Diagram of a mediated dialogue in Verbmobil \[WAH 00a\]

One of the specificities of Verbmobil is the parallelization of different modules that have the same function and merging the results to combine their advantages without their disadvantages.

The following paragraphs will present the main components of Verbmobil that are relevant to this book. [Figure 4.23](#fig4_23) presents the system interface as well as its main functionalities, but it does not provide its real architecture, which is much more complex. The final version of Verbmobil contains 69 modules, each of which interacts with at least one other module. Given the parallel processing approach and the constraints of real-time processing, the communication requirements between the different modules are enormous from the point of view of the quantity of information. Given the non-sequential aspect of Verbmobil, this implies that the modules exchange not only the input and the output of each module but also the attempts of the high-level modules to synchronize the flow of information, constraints, alternatives, confidence scores, probabilities, etc.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_23.jpg)

Figure 4.23. The interface of the Verbmobil system \[WAH 00a\]. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

To meet these requirements, a multi-blackboard architecture has been implemented. This architecture contains three different types of components \[KLÜ 00\]. There is a set of independent modules called knowledge sources. These modules are the main element of the Verbmobil system. Unlike most blackboard-based architectures, Verbmobil uses a series of boards which are each used to represent the intermediary results of each step of the processing. Finally, there is a control module whose function is to allocate resources to optimize the runtime and module sequencing. The adoption of a central blackboard-based architecture makes it possible to add or remove modules without significant repercussions in the other modules. For example, two recognition modules for German are used to process multi-lateral conversations involving two Germans. Despite its complexity, this architecture has proven to be more effective and more appropriate than a multi-agent architecture that was used in the first phase of the project. Concerning the syntactic analysis, the system adopts a multi-engine approach to guarantee robustness. Thus, three syntactic parsers have been used in the processing: a stochastic LR parser, a chunker and a HPSG-based deep parser.

The stochastic LR parser adopts an incremental approach \[RUL 00\]. It was inspired, among others, by the works of Ted Brisoe at the University of Cambridge on LR parsers and their extension for processing unification-based grammars. The choice of the LR algorithm was essentially motivated by its efficiency and its adaptation for processing the word trellis in the graph provided by the recognition system. To improve the analysis quality, this module uses a post-processing phase with tree transformation rules. These rules are learned automatically from a corpus with the transformation-based learning method \[BRI 93\].

Based on the CASS system developed by Steven Abney, the partial parser uses memory-based learning techniques (see \[DAE 05\] for an introduction). In order to satisfy the constraints imposed by Verbmobil, this parser adopted an incremental approach \[HIN 00\]. Particular attention was paid to the assembly of segments, a subject that is addressed relatively rarely in the context of partial parsing approaches. The objective was to facilitate the task of the semantic analysis module as much as possible and consequently obtain a better-quality analysis. Compared to other approaches, the evaluation showed that this approach produced better analysis results in terms of robustness but with the shallowest analysis.

A deep syntactic parser based on the HPSG formalism, this parser was realized in the context of a collaboration between the DFKI at Saarbrücken, the CSLI at Stanford and the Language Processing Lab at the University of Tokyo \[USZ 00\]. One of the main problems faced by this parser was the reduction in necessary runtime. The features used to represent the linguistic constraints in the framework of the HPSG formalism require many calculations that make the parser’s runtime too slow to be integrated in the framework of a real-time application. Two solutions have been combined to solve this problem: 1) elimination of features that are not central to the processing as well as disjunctive features that increase the complexity of the processing, and 2) the testing of several types of implementation like, among others, the grammar approximation of finite-state automata. Finally, this problem was overcome by researchers in the Computational Linguistics department at the University of Saarbrücken, who combined several solutions proposed by different participants and managed to satisfy the analysis time constraints, which are about 0.45 s for a 10-word utterance. As expected, the evaluation results showed that this system, compared to the two others, provides the deepest analysis but the least robust analysis of problems of recognition or extra-grammaticalities of speech (see \[MÜL 00, FLI 00, SIE 00\] for the final results of this parser on German, English and Japanese, respectively).

The three parsers process the same graph of words enriched with prosodic annotations produced by the recognition system. The three parsers are also guided by an A\* algorithm to choose the most likely paths from a speech recognition perspective \[ULR 00\]. The three parsers use a specific analysis module to construct a semantic representation corresponding to the output of each one. This applies to complete parses as well as partial ones. The data exchanged between the different modules are represented in the Verbmobil Interface Terms (VIT) format, which is, as the name indicates, a special format intended to standardize the output of the parsers. The conversion of the output of the parsers into a standardized semantic representation makes if possible to carry out the post-processing operations intended to select the best analysis from the candidates \[RUP 00\].

As with the ALPAC report, the difficulty of the semantic approach has been known since the 1960s. Thirty years later, the statistical method has tentatively given the impression of solving the problem; however, after the leap forward that it has allowed, specialists in machine translation are now faced with the same difficulty, because although enormous progress has been made in a relatively short amount of time, the expectations of users have also progressed with the technology.

## 4.3. Information retrieval (IR)

### 4.3.1. IR and related domains

We are constantly making more or less important decisions on a daily basis. Of course, our decisions are generally based on information that we collect in our near or distant environment. In the case of so-called intelligent artificial systems, this happens in the same way. Every serious decision requires access to information. This information can be prepared in advance at the level of the format or the level of the content, as it can be raw, without any formatting or any constraints on the content. Depending on the nature of the information provided to the system, there are two types of systems: Information Systems (IS) and Information Retrieval Systems (IR) or search engines. The data flow diagrams (DFDs) of these systems are provided in [Figure 4.24](#fig4_24).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_24.jpg)

Figure 4.24. DFDs of information systems and information retrieval systems

Information Systems, which are increasingly common in our daily lives, are equipped with structured information frames based on which they provide the required information. The most common examples of this type are administrative management systems such as Enterprise Resource Planning (ERP) systems and Geographic Information Systems (GIS) like Google and Bing Maps that make it possible to view enriched maps from satellite images. The main task of these systems is to find a precise and structured answer to a precise and structured query with potential modifications to it. For example, a simple query for an information system consists of finding the list of customers who bought a given product, indicating for each one the quantity purchased as well as the purchase total. A modification of the previous query would consist of making a list of sales of the same product, by geographical area or customer age group. Finding such information requires storing information in tables, each of which is specifically dedicated to storing a part of the information, such as the names and addresses of customers. Interconnections between these tables make it possible to assemble the parts of the information in order to find or calculate the information requested. In terms of content, constraints can be imposed on the fields of tables like the type of values stored (date, character strings, etc.) with the universal constraint that the values in these fields all be recognizable by deterministic finite-state automata.

With the increase in power of electronic data processing, the Internet and the move to e-only document management, Information Systems are led increasingly often to also store information in natural language, images or sound signals, which are called semi-structured information. For example, this includes the answer to an open question in an inquiry, a hospitalization report written by a doctor, a photo, a video or song recording, etc. However, the analysis of these fields can no longer occur with simple deterministic finite-state automata; it requires tools that are specific to the type of information stored, such as NLP software, image recognition software and sound pattern software. With these richer and more complex data, we lose the property of structured data that is the assurance in all cases of getting an answer if the information system contains at least one field with information responding to the query.

Search engines, in turn, have the mission of finding documents that are relevant to the query expressed by a user. They can therefore be considered to be a particular case of information systems. Their specificity in relation to information systems resides in the absence of constraints on the queries, data collections and the system’s output. In the case of a textual search, users can interrogate the system using a string of words, either a complete sentence or a combination of keywords that may contain meta-symbols based on a rudimentary syntax accepted by the search engine. The same applies for the documents that form the search space as well as for the output of the system, which consists of a subset of the documents in the collection. Another characteristic of search engines is the type of document collection that they include; they can be limited, as in the case of a documentary information retrieval system, or completely open, as in the case of the Internet.

There are two major functionalities in a search engine. Indexing is a step that occurs offline and consists of constructing a simplified representation of the collection in order to reduce the space necessary for its storage while making access to information faster. Indexing is done on both the basis of the content of each document and its interconnections through hyperlinks to other documents. The latter information is used to calculate the page rank, which is a global score of the importance of a document that makes it possible to distinguish two documents that are related in a similar way by the hyperlinks to other documents in the collection. More generally, the page rank is a measure of the centrality of a node in a graph.

The other major functionality of a search engine is the search in a collection for documents that are relevant to the query and the presentation of results. This is generally done in the form of a list arranged in order of decreasing relevance. The response documents are generally presented as hyperlinks associated with a small extract of the document or a summary. Other forms are also possible, such as a navigable graph, where each node represents a document, a topological map or lists of icons, generally used for image search engines.

For a general introduction to information retrieval, see \[AMI 13, KOW 11, FRA 92, MAN 08\].

### 4.3.2. Lexical information and IR

All texts, regardless of type, are formed by a sequence of words that are aligned according to constraints that are morphological, syntactic, discursive, etc. It is therefore natural to start by understanding the contribution of lexical knowledge to information conveyed by the text and, consequently, to possible simplifications that can occur at this level.

#### 4.3.2.1. Zipf’s law

In the domain of information retrieval, we typically search for texts that are most relevant to a query formulated as one or more keywords. This comes down to searching for texts where these words have a significant role. The occurrence of a word in a text is not enough to judge that this word has a privileged role in this text. To understand the measure of importance of a word in a text, Zipf’s law and its derivatives are essential.

In his quest to formalize the principle of minimal effort that is supposed to explain human behavior, Zipf proposed an empirical law called Zipf’s law \[ZIP 49\]. This law stipulates that, in a given corpus, the frequency of a word is inversely proportional to its rank in a frequency table. In other words, the most frequent word in the corpus appears two times more than the next word in the frequency table and three times more than the third word and so on. This observation can be noted by [equation \[4.11\]](#eq4.11):

[\[4.11\]](#ieq4.11)

From [equation \[4.11\]](#eq4.11), it is clear that for every corpus, there is a constant k such as The function of mass in Zipf’s law is given by [equation \[4.12\]](#eq4.12), where the symbol N corresponds to the number of words, the symbol k corresponds to the rank and s > 0 corresponds to the value of the exponent that characterizes the distribution:

[\[4.12\]](#ieq4.12) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_4.jpg)

To verify Zipf’s law empirically, consider a collected set of French novels from different genres and different periods that I call Corpus of Selected French Novels (CSFN). This collection contains about 1.5 million words from the following 10 literary works: *A la recherche du temps perdu* by Proust, *La comédie humaine* by Balzac (three volumes), *La princesse de Clèves* by Madame de la Fayette, *Germinal* by Émile Zola, *Voyage au centre de la terre* by Jules Verne, *Le rouge et le noir* by Stendhal, *Madame Bovary* by Gustave Flaubert and *Notre-Dame de Paris* by Victor Hugo. [Table 4.2](#tab4_2) contains the 50 most common words, their frequencies (f), their ranks (r) and the value f\*r that is supposed to be fixed throughout the corpus. As we can see, the values of (f\*r) are not fixed as predicted by Zipf’s law. However, a tendency toward the stabilization of these values starts to be seen as of rank 15 with *k* close to 250,000. Note that \[MAN 99\] observed similar phenomena for the novel Tom Sawyer in English, which means that these observations are not unique to CSFN corpus or the French language.

Thus, it can be said that Zipf’s law corresponds to a general tendency rather than a real law that can be verified in all cases. Drawing the curve of function of the equation is a good way to observe the Zipf *effect* on a larger scale. The curve of the function for the 300 most frequent words in the CSFN corpus is given in [Figure 4.25](#fig4_25). This curve shows that there is a small group of words whose frequency is very great, and at the same time, there is a large number of words whose frequency is not very high. This can be clearly seen by the rapid merging of the curve with the x-axis.

**[Table 4.2](#itab4_2).** *List of the most frequent words in the CSFN*

| **Word** | **Frequency** | **Rank** | **(f\*r)** | **Word** | **Frequency** | **Rank** | **(f\*r)** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| de (of) | 70,982 | 1 | 70,982 | ce (this) | 9,738 | 26 | 253,188 |
| la (the; fem. sing) | 42,268 | 2 | 84,536 | s’ (refl. pronoun) | 9,695 | 27 | 261,765 |
| et (and) | 32,821 | 3 | 98,463 | est (is) | 9,336 | 28 | 261,408 |
| le (the; masc. sing) | 32,296 | 4 | 129,184 | son (his or her) | 9,240 | 29 | 267,960 |
| à (to) | 30,435 | 5 | 152,175 | n’ (not) | 9,045 | 30 | 271,350 |
| il (he) | 26,459 | 6 | 158,754 | était (was) | 8,975 | 31 | 278,225 |
| l’ (the; sing) | 25,565 | 7 | 178,955 | au (at the) | 8,721 | 32 | 279,072 |
| les (the; plur) | 25,118 | 8 | 200,944 | vous (you; plur) | 8,586 | 33 | 283,338 |
| un (a; masc) | 22,043 | 9 | 198,387 | sa (his or her) | 8,479 | 34 | 288,286 |
| d’ (of) | 20,839 | 10 | 208,390 | avait (had) | 8,410 | 35 | 294,350 |
| en (in) | 18,760 | 11 | 206,360 | plus (more) | 8,305 | 36 | 298,980 |
| que (that) | 18,684 | 12 | 224,208 | par (by) | 8,079 | 37 | 298,923 |
| une (a; fem) | 17,637 | 13 | 229,281 | sur (on) | 7,190 | 38 | 273,220 |
| elle (she) | 16,194 | 14 | 226,716 | avec (with) | 6,369 | 39 | 248,391 |
| des (some) | 15,217 | 15 | 228,255 | comme (like) | 6,354 | 40 | 254,160 |
| qui (who) | 15,214 | 16 | 243,424 | a (has) | 6,230 | 41 | 255,430 |
| qu’ (that) | 13,471 | 17 | 229,007 | mais (but) | 6,174 | 42 | 259,308 |
| ne (not) | 12,919 | 18 | 232,542 | si (if) | 6,150 | 43 | 264,450 |
| dans (in) | 12,617 | 19 | 239,723 | ses (his, her or their) | 6,055 | 44 | 266,420 |
| je (I) | 12,096 | 20 | 241,920 | cette (this) | 5,945 | 45 | 267,525 |
| se (refl. pronoun) | 11,715 | 21 | 246,015 | on (we) | 5,738 | 46 | 263,948 |
| pas (not) | 11,360 | 22 | 249,920 | tout (all) | 5,215 | 47 | 245,105 |
| du (of the) | 10,647 | 23 | 244,881 | y (there) | 5,083 | 48 | 243,984 |
| pour (for) | 10,180 | 24 | 244,320 | dit (said) | 5,040 | 49 | 246,960 |
| lui (him or her) | 9,797 | 25 | 244,925 | nous (we) | 4,627 | 50 | 231,350 |

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_25.jpg)

Figure 4.25. Curve of the relation between frequency and rank for the first 300 words in the CSFN corpus. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

It is natural that such a strong declaration about linguistic systems attracted so much interest from among researchers, especially in the domains of applied mathematics. Zipf’s law has been refined many times, the most well-known of which is probably Mandelbrot’s law \[MAN 57\].

#### 4.3.2.2. Filtering empty words

As can be observed in [Table 4.2](#tab4_2), the most frequent words are grammatical: prepositions, determinants, pronouns, particles, etc. Despite their linguistic value, these words are so common in all documents that they have practically no distinctive role. To reduce the size of the documents and therefore the calculation cost and the space necessary to store the data, some researchers recommend simply removing these kinds of words, which are commonly called empty words, stop words or anti-lexical words. The lack of theoretical foundation makes the creation of such lists an essentially empirical and ad hoc process. This explains the presence of a multitude of lists of this kind with fundamental differences, as much from a quantitative point of view as from a function point of view (categories of words concerned). However, it must be admitted that grammatical words are an essential tool for search engines, for example, to detect keyword stuffing that occurs by repeating these words in a text to bias its indexing.

#### 4.3.2.3. Weighting words

The simplest method of indexing consists of associating each document in a collection with a list of keywords that are included in it. That way, the search engine simply says that a document does or does not contain the keyword in question. This is called Boolean indexing. This view is said to be naive because it does not consider the importance of the role of each keyword in the document. This role is particularly important when there are a large number of documents. Moreover, it presupposes the existence of a large list of keywords whose creation requires considerable efforts especially for large documents where the content is likely to change. To reflect the importance of a word in the text, the simplest way would be to consider the Term Frequency (tf). In other words, the more frequent a word is in a text, the more important is its weight. Again, this is not sufficient because some words, not necessarily grammatical words, are more frequently used in some registers than others, which means that the discriminating capacity of these words is not very great.

One way to consider the importance of a word at the document level while considering its frequency on a global level would be to examine what is called the Collection Frequency (cf), which is the frequency of a word throughout the entire corpus. Before going further, consider [Table 4.3](#tab4_3), which includes a comparison between the frequencies of certain terms in the novel *Germinal* by Emile Zola in opposition to their frequency in the CSFN corpus, which includes 10 novels.

**[Table 4.3](#itab4_3).** *Comparison tf, cf, tf/cf, idf and tf-idf scores*

| **Word** | **Germinal (tf)** | **CSFN (cf)** | **tf/cf\*100** | **idf** | **tf-idf** |
| --- | --- | --- | --- | --- | --- |
| Froid (cold) | 62 | 330 | 18.7% | 10 | 0 |
| Mine (mine) | 57 | 145 | 39.3% | 10 | 0 |
| Houille (coal) | 50 | 54 | 92.5% | 3 | 26.14 |
| Herscheuse (female worker who pushes a cart) | 24 | 24 | 100% | 1 | 24 |

The word *cold* is a relatively frequently used word in *Germinal* (rank = 321). It also frequently occurs in other documents in the collection and therefore has a limited discriminatory power of only tf/cf=0.187. As it has a generic meaning, this word does not belong to a specific semantic field and does not play a particular semantic role at the global level of the corpus. Because the events of *Germinal* take place in the world of mining, it would at first seem tempting to think that the word *mine* itself would be characteristic of this novel. The results show that this word is frequent at the local level and the collection level. This frequency at the collection level can be explained by the highly polysemic character of this word: in the Petit Robert (French–French dictionary), there are eight meanings arranged in two different entries. On the other hand, the word *houille* (coal), which is relatively frequent in *Germinal*, is not frequent at the collection level, which gives it an important distinctive role. Finally, although the word *herscheuse* (female worker who pushes a coal cart) is not very frequent in *Germinal* (rank = 751), it is very characteristic of this novel because it does not appear in any other novel in the collection.

To push this weighting method even further, another important factor should be considered, which is the size of the collection as well as the number of documents in which the term appears. The high frequency of a term in a collection of a few documents does not have the same significance as in a collection with several thousand documents. Similarly, the collection frequency does not give an idea of the distribution of the term throughout the collection: the word might appear in only a few documents or in all of them. To consider this information, some researchers consider the Inverse Document Frequency (idf) multiplied by the local frequency of the term *tf* \[ROB 76, ROB 04\]. The global score of a term *t* in a document *d* is therefore calculated using [equation \[4.13\]](#eq4.13), which corresponds to what is called the Term Frequency-Inverse Document Frequency (tf-idf), where *N* is the number of documents in the collection and *fdt* is the number of documents in the collection where the term *t* appears:

[\[4.13\]](#ieq4.13)

Returning to the CSFN corpus, the value of *N* is equal to 10. For example, the word *froid* (cold) appears in all documents in the collection, so fdt =10. The score of this word in *Germinal* is obtained using the equation: *S* (*froid, Germinal*) = 62 × = As noted, the tf-idf method considers that words that appear in all of the documents in the collection do not have a distinctive power and attribute them zero weight, independently of their frequency. Similarly, this method is very generous with words that only appear in a limited number of documents even if their frequency is not very great: *herscheuse* has a similar weight to *houille*, even though *houille* has a *tf* that is almost two times greater.

Many kinds of frameworks have been proposed to further optimize word weighting. For a review of some of these frameworks, see \[SAL 88, LAN 05, CUM 07, NAN 04\].

#### 4.3.2.4. Lemmatization

Lemmatization is another way to simplify a document. It consists of grouping all of the inflectional variants of a word into a single item that serves as its identifier in a dictionary. Thus, the singular and plural forms of a noun will be reduced to its singular form or all conjugated forms of verb in all tenses and all modes will be associated with the infinitive form. The advantage of lemmatization in the context of information retrieval is that it reduces the lexical forms considered for the search.

### 4.3.3. Information retrieval approaches

#### 4.3.3.1. Scanning the complete file

The simplest method to establish a link between a query and a document is to search for documents that contain this word in the entire database of available documents. This is made easy by using one of the efficient search algorithms proposed, for example, by \[BOY 77, SUN 92\]. The major disadvantage of this method is that it provides a very superficial analysis of the query–document relation. For example, there is no distinction between words that play an important role in distinguishing between two documents and words whose distinctive role is limited. Moreover, searching through all of the documents significantly limits the processing speed. This kind of solution was used at the end of the 1990s, particularly in the filters of classic messaging systems like Pegasus Mail and Outlook Express.

#### 4.3.3.2. Inverted lists

According to this method, each document can be represented by a series of keywords. In order to accelerate the search process, the inverted file is built. This provides a list of keywords from all of the documents, ordered alphabetically or according to their global frequencies, and each associated with the documents in which it appears. Typically, grammatical words are removed from this list to reduce its size and make the search more efficient. To increase the efficiency of this approach even more, double-pass solutions have been proposed. In the second level, all of the words starting with the first two letters are stored in the same place, while the first level contains hyperlinks to the second level. The advantages of this approach are its easy implementation, fast searching capacity and the possibility of easily processing synonyms. The disadvantages include the size of the inverted file, which can sometimes be quite large, and the difficulties related to updating modifications to documents, especially in the case of a dynamic environment.

#### 4.3.3.3. Signature files

This approach consists of reducing the document to a sub-document containing only information that is relevant to the search. The document that results from the filtering process is stored in a separate file called the signature file, which is much smaller than the original document and consequently can be searched more quickly. Like the other approaches in information retrieval, it starts by simplifying the document. Grammatical words are eliminated and all uncommon words are reduced to their lemmas. Next is the file segmentation phase. Several techniques are possible for this operation, including digital techniques and n-grams. The idea of this segmentation is to identify the relevant words by segments and not at the global level of the text in order not to fall into generalities. Other approaches have gone further by proposing signature file processing on two levels. In the first level, the files are represented in the form of trees. In the second level, the information within the files are divided according to their frequencies.

The main problem with this method is finding an ideal compromise between the detail and the speed of the search: the larger the size of the signature file, the more accurately it represents the original document, but the less it allows for fast searching. As noted in \[CHR 84\], signature files require between 10% and 15% of the size of the initial file, whereas inverted files require between 50% and 300%. It is also much easier to add new information to the document with signature files than with inverted lists, which potentially require a new rearrangement of information for each addition.

#### 4.3.3.4. Clustering-based approaches

Approaches based on clustering are the most common form of unsupervised learning algorithms. Unlike supervised methods, clustering does not require the intervention of a human expert to label the data first to guide the learning algorithm.

The basic idea of clustering in the context of information retrieval is that similar documents are assembled to form a group of the same type. The main motivation for this choice is that, generally, the documents forming a cluster tend to share the same queries or respond to the same needs in terms of information. The cluster can be used for documents as well as words. In the second case, the cluster can be used for the automatic construction of a thesaurus. For more information about clustering, see \[AND 07, ROS 06, STE 00\].

There are two types of clustering: flat clustering and hierarchical clustering. In flat clustering, the clusters obtained have equal importance, whereas in hierarchical clustering, the clusters hold dependency relations in the form of trees. [Figure 4.26](#fig4_26) depicts the operation of a flat clustering of a set of documents, which shows three classes of documents.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_26.jpg)

Figure 4.26. Flat clustering of a set of documents. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

Clustering approaches are based on the transformation of texts analyzed in the form of a point vector. First, a series of preparatory processing steps are carried out, like the removal of stop words, lemmatization and clustering words in conceptual classes using a thesaurus. This pre-processed document is represented by a t-dimension vector, where *t* is the size of the indexing vocabulary. The vectors used can be binary or not. The absence of an indexing term is marked by a 0 and its presence is marked bya 1 or by a positive number indicating the importance (weight) of the concept in the classification of the document. Different functions have been proposed to determine the weight of a term:

- – FREQ <sub>ik</sub>: this function considers the frequency of a word *k* in a document *i*. It is easy to obtain and allows for greater results than binary vectors.
- – The specificity of a term: logN – log(DOCFREQ <sub>k</sub>)+1, where DOCFREQ <sub>k</sub> is the number of documents that contain the term *k* and *N* is the total number of documents. This function is relatively easy to obtain and more powerful than binary vectors.
- – The inverted frequency of a document: FREQ <sub>ik</sub> /DOCFREQ <sub>k</sub>; experimental results have shown that this function is more effective than the previous one.
- – FREQ <sub>ik</sub> \* TERMREL <sub>k</sub>, where TERMREL <sub>k</sub> = r <sub>k</sub> /(R – r <sub>k</sub>) s <sub>k</sub> /(I – s <sub>k</sub>). The term TERMREL <sub>k</sub> represents the relevance factor, *r* is the total number of relevant documents that contain the term *K, I* is the total number of non-relevant documents and *s <sub>k</sub>* is the number of non-relevant documents that contain the term k. Experimental studies have shown that this method is the best \[SAL 83\].

After having represented the documents in a t-dimensional vector, the next step consists of dividing the points obtained into clusters. This operation must satisfy the following set of diverse criteria:

- – The method must be stable as the documents increase in number. In other words, the distribution of points should not radically change with the insertion of new documents.
- – Small modifications in the description of the documents should lead to small modifications in the distribution.
- – The method should be independent of the initial order of documents.
- – The algorithmic efficiency of the proposed methods, particularly the speed of the algorithm.

Several types of methods have been proposed in the literature to satisfy these constraints, including similarity-based methods, iterative methods and Bayesian methods, which will be discussed in the following sections.

Finally, searching in a set of documents analyzed in clusters is simpler than generating the clusters. The operation consists of representing the query as a t-dimensional vector and comparing it to the centroids of the cluster. The similarity between the cluster and the query is detected using a special function: the cosine is the most commonly used function (see [section 4.3.3.8](#se4.3.3.8) for an example).

#### 4.3.3.5. Similarity-based approaches

These approaches use techniques based on graphs and require a O *(n )* time or sometimes more (where *n* is the number of documents). The basic principle behind this technique is to calculate the similarity (distance) between two documents. The first step consists of choosing a similarity function between two documents that makes it possible to measure the distance between two documents represented in the form of a matrix. In the literature, a series of similarity functions have been proposed and give approximately equivalent results if the documents are properly standardized \[SAL 83\].

Suppose that we have a set of documents *D <sub>1</sub>, …. D <sub>m</sub>* and a set of terms that are employed in these *T <sub>1</sub>, …. T <sub>n</sub>*. For each term *T <sub>i</sub>* and document *D <sub>j</sub>*, we have a weight *W <sub>ij</sub>* that indicates the weight of this term in the document. An example of a similarity function between two documents would be the sum of the multiplication of the weight of the terms in these two documents (see [equation \[4.14\]](#eq4.14)):

[\[4.14\]](#ieq4.14)

Consider the corpus of six micro-texts presented in [Figure 4.27](#fig4_27).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_27.jpg)

Figure 4.27. Collection of documents

To determine whether two documents are similar or not in a corpus like the one in [Figure 4.27](#fig4_27), first we conduct two pre-processing operations: filtering stop words and lemmatization. For the sake of simplicity, we will skip the step of conceptual clustering with a thesaurus. The result is the documents in [Figure 4.28](#fig4_28).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_28.jpg)

Figure 4.28. List of keywords retained in the documents in this collection

Next, we create a term-document matrix where we consider the frequency of a word in a document as an indication of its weight. For the scope of this presentation, we will draw up a partial term-document matrix for 10 terms.

To calculate the symmetry between two documents, according to [equation \[4.14\]](#eq4.14), we multiply the weight of the terms in the documents. Because the weight of terms that are not shared is equal to zero, calculate the sum of the multiplications of the weights of the shared terms. Consider the following examples of similarities:

> sim(Doc01, Doc02) = (1\*0)+(1\*1)+(1\*1)+…. = 2.
> 
> sim(Doc01, Doc05) = (1\*2)+(1\*0) + (1\*1)+…= 2.
> 
> sim(Doc01, Doc06) = 0.

**Table 4.4.** *Term-document matrix*

|  | **Tourist** | **ador** | **visit** | **Bastille** | **Grenoble** | **John** | **Louvre** | **Paris** | **sport** | **good** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Doc <sub>01</sub>** | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| **Doc <sub>02</sub>** | 0 | 1 | 1 | 0 | 0 | 1 | 1 | 1 | 0 | 0 |
| **Doc <sub>03</sub>** | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| **Doc <sub>04</sub>** | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| **Doc <sub>05</sub>** | 2 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **Doc <sub>06</sub>** | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

By calculating all of the similarities, we obtain the document–document matrix in [Table 4.5](#tab4_5). It consists of a symmetrical matrix whose diagonal is empty because it corresponds to the relation of the document with itself.

**[Table 4.5](#itab4_5).** *Document–document matrix for the collection in [Figure 4.27](#fig4_27)*

|  | Doc <sub>01</sub> | Doc <sub>02</sub> | Doc <sub>03</sub> | Doc <sub>04</sub> | Doc <sub>05</sub> | Doc <sub>06</sub> |
| --- | --- | --- | --- | --- | --- | --- |
| **Doc <sub>01</sub>** |  | 2 | 0 | 0 | 2 | 0 |
| **Doc <sub>02</sub>** | 2 |  | 0 | 0 | 0 | 0 |
| **Doc <sub>03</sub>** | 0 | 0 |  | 1 | 0 | 0 |
| **Doc <sub>04</sub>** | 0 | 0 | 1 |  | 0 | 0 |
| **Doc <sub>05</sub>** | 2 | 0 | 0 | 0 |  | 0 |
| **Doc <sub>06</sub>** | 0 | 0 | 0 | 0 | 0 |  |

After calculating the similarity matrix, a similarity threshold is chosen starting from which two documents are considered to be linked. In this example, given the limited size of the documents, it has been decided to consider that two documents are similar if their weight of resemblance is at least equal to one (see [Table 4.6](#tab4_6)).

**[Table 4.6](#itab4_6).** *Standardized document–document matrix (binary)*

|  | Doc01 | Doc02 | Doc03 | Doc04 | Doc05 | Doc06 |
| --- | --- | --- | --- | --- | --- | --- |
| Doc01 |  | 1 | 0 | 0 | 1 | 0 |
| Doc02 | 1 |  | 0 | 0 | 0 | 0 |
| Doc03 | 0 | 0 |  | 1 | 0 | 0 |
| Doc04 | 0 | 0 | 1 |  | 0 | 0 |
| Doc05 | 1 | 0 | 0 | 0 |  | 0 |
| Doc06 | 0 | 0 | 0 | 0 | 0 |  |

The connected graph representing the relations between the texts is the final product of this step (see [Figure 4.29](#fig4_29)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_29.jpg)

Figure 4.29. Graph of connections between the documents

The next step consists of applying a clustering algorithm like the connected components algorithm. This algorithm requires a similarity between the terms of a cluster. In a graph, a connected component is a set of nodes that are accessible to each other. The steps of this algorithm are given in [Figure 4.30](#fig4_30).

Computationally advantageous, this algorithm produces classes whose members are weakly classified. These classes are not strongly equivalent to concepts. Regarding the performance, this algorithm tends to be good for precision but not as good for recall.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_30.jpg)

Figure 4.30. Connected components algorithm

Note that the Class <sub>01</sub> includes documents that do not share any terms between them, like doc <sub>01</sub> and doc <sub>03</sub>.

The result of the classification obviously depends strongly on the algorithm used. It depends on the similarity function between documents and the way in which it is calculated. For example, the Stars algorithm takes an initial document that is called the kernel, considered to be the node of nucleus of the class, and then searches for documents that are similar to the seed \[ASL 82\]. If no more documents similar to the current kernel are found, other kernels are searched and so on. Note that the classes obtained can vary according to the initialization of this algorithm. If the documents are arranged in ascending order, it provides the following classes:

- Class <sub>01</sub> (doc <sub>01</sub>, doc <sub>02</sub>, doc <sub>05</sub>)
- Class <sub>02</sub> (doc <sub>03</sub>, doc <sub>04</sub>)
- Class <sub>03</sub> (doc <sub>06</sub>)

Classes 01, 02 and 03 do not share any documents. This is a hard cluster. When two or more clusters share one or more documents, it is called a soft cluster. The main disadvantage of this method is that it requires at least one constant found empirically, which is the reconciliation threshold of texts and sometimes it is also necessary to specify the number of clusters *a priori*. These constants impose structural constraints on the data, and consequently they affect a search engine’s performance considerably.

#### 4.3.3.6. Iterative approaches

These methods are based directly on the description of the text, based on a hashing key, without calculating an inter-document similarity. The algorithmic complexity of this approach is very good, in general O(*nlogn*) or O(*n  /logn*). This efficiency is obtained to the detriment of certain constraints like sensitivity to the order in which the texts were analyzed or the impossibility of predicting the error rate in the description of the document. The general functioning of this approach follows these two steps:

- – determination of the initial distribution;
- – reiteration and association of the document to clusters, until there are no more good associations to make.

Finally, it should be noted that hybrid methods can be used. The iterative method can be used to partition documents into clusters and then the graph method can be used to divide each of the clusters obtained.

#### 4.3.3.7. Bayesian approaches

These approaches are based on applying a Bayesian network to a classification task. The network contains a node *C* for the class variable and a node *X <sub>i</sub>* for each feature describing an individual to order. Given a specific case *X*, the Bayesian network makes it possible to calculate the probability: P(C = c <sub>k</sub> | X = x) for each possible class *c <sub>k</sub>*. The optimization of the classification occurs by selecting the class *c <sub>k</sub>* for which the probability is maximized. Although all forms of Bayesian networks can be used for the classification, empirical results have shown that networks where all of the variables are directly connected give better results than those in “naive” Bayesian networks, where the variables are completely separate (see [Figures 4.31](#fig4_31)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_31.jpg)

Figure 4.31. Diagrams of naive and complex Bayesian networks

In order to extend the capacities of naive Bayesian networks, represented by the classic equation: P(X|C) = ∏ <sub>i</sub> P(X <sub>i</sub> | C), several solutions have been proposed, including the TAN algorithm by Friedman and Goldszmidt \[FRI 96\] and the KDB algorithm by Sahami \[SAH 96\]. The TAN algorithm requires that each node has a maximum of one additional parent, and in this case, the algorithm can find the optimal solution in quadratic time. Sahami’s KDB algorithm in turn is based on a heuristic search of the best structure, which can potentially be sub-optimal. It can be used to find classifiers, where each node has a maximum of *k* parents, for a random value of *k*. Essentially, this algorithm chooses the *k* other features as parents of a node *X <sub>i</sub>*, of which *X <sub>i</sub>* is the most dependent. This approach has been used by Sahami for the classification of unwanted mail, or spam, in the context of the SONIA project and seems to give satisfying results for this task \[SAH 98a, SAH 98b\].

Aside from the approaches just presented, there are also the self-organizing maps developed by Kohonen, which is a generic neural network technique that can be applied to a cluster of documents \[KOH 97\], as well as the clique algorithm \[AGR 98\] and k-means \[LLO 82, FOR 65\].

#### 4.3.3.8. Vector approaches: latent semantic analysis (LSA)

Vector approaches consist of constructing a representation of the texts in a collection as well as the query in the form of vectors to be able to calculate the distances between documents, on the one hand, and those between the queries and the documents, on the other hand. One of the most common vector approaches is latent semantic analysis (LSA).

LSA is both a theoretical approach and a method for extracting and representing information relative to word usage from a large corpus \[LAN 97, LAN 98, BER 95\]. It was initially developed to solve the problem of synonymy in the domain of information retrieval. According to this approach, the meaning of a text can be represented by a matrix that considers the occurrences of all the words in that text as well as the (co-)occurrences of these words in other possible contexts in other texts. As a cognitive model of human intelligence, several works have shown that LSA parsers make it possible to simulate the acquisition and recognition of vocabulary \[FOL 96, ALB 08\]. Finally, from an applicative point of view, as will be presented later in this text, latent semantic analysis and its variant latent semantic indexing (LSI) have been used notably in the domain of indexing and information retrieval, but there are also applications in other domains, such as intelligent tutoring systems \[GRA 05, MIL 03, KU 11\].

The processing principle is simple. It calculates and stores the reduced vectorial representation of all of the documents of the collection offline. When a user submits a query, it calculates the vectorial representation of this query in the same way and then it displays the documents whose vectorial representation is the closest to that one, in ascending order of distance (see [Figure 4.32](#fig4_32)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_32.jpg)

Figure 4.32. General diagram of information retrieval with LSA. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

One of the main objectives of LSA is to reduce redundancies in the documents as much as possible in order to facilitate the search process and reduce the space necessary for storing information. To do this, the processing starts by removing words that are determined to have little informative value or empty words. Then, the retained words are lemmatized and used to construct term–document matrices. In this matrix, each entry consists of an integer representing the number of occurrences of a specific term in a given document. The singular value decomposition (SVD) of the matrix obtained in the previous step is then calculated. Consider the term–document matrix *X* with *t* lines (one for each term that appears in the chosen document) and *d* columns (one for each document). The result of the SVD is calculated according to [equation \[4.15\]](#eq4.15):

[\[4.15\]](#ieq4.15)

The main innovation of LSA is the possibility of considering only the k greatest singular values in the matrix *S <sub>0</sub>* and reducing the other values to zero. The value of *k* is a pre-defined parameter: in general, values between 100 and 200 are used. The matrix of X is then approached by *X’=TSD *, where T is the matrix *t × k* with orthonormal columns, S is a positive diagonal matrix defined as *K × K* and D is the matrix *d × K* with orthonormal columns. [Figure 4.33](#fig4_33) presents the SVD of X, where the parts considered to obtain *X* ’ are shaded. To calculate the SVD of a matrix, most high-level programming languages have matrix calculation libraries that contain functions specifically dedicated to this purpose. The interest of the SVD here is not to reconstruct the original matrix that we already have, but rather to find an approximation of rank *k* in order to improve the search efficiency.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_33.jpg)

Figure 4.33. Application of the SVD to a matrix X

The last step consists of calculating the distance between the vector of the query (q) and the matrix of every document (d), the most common of which is the cosine distance that is calculated according to [equation \[4.16\]](#eq4.16). The cosine distance between two vectors is found by dividing the dot product by the multiplication of the absolute values of the two vectors:

[\[4.16\]](#ieq4.16)

To clarify the different steps of LSA processing, consider this example. Let’s start by supposing that there is a collection of documents typed by a user (with a few errors) and the queries presented in [Figure 4.34](#fig4_34). For other detailed examples, see \[LAN 98, GRO 04\].

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_34.jpg)

Figure 4.34. Collection of documents

In the three micro-documents in our collection, the words do not have the same distinctive role. For example, the word *the* figures in two documents out of three and consequently only has a limited distinctive interest. On the other hand, the word *fruit* is only employed in the second document, and it is even repeated twice, which makes it very characteristic of this document.

Thus, from our collection of documents, we obtain the term–document matrix in [Table 4.7](#tab4_7). It should be noted that, given the extremely reduced size of our collection of texts and given the pedagogical objective, we have decided not to carry out lemmatization or the removal of empty words and we have used the number of occurrences of forms instead of, for example, the specificity values of terms like tf-idf.

**[Table 4.7](#itab4_7).** *Term–document matrix for our collection and the two queries*

| **Term** | **Doc <sub>01</sub>** | **Doc <sub>02</sub>** | **Doc <sub>03</sub>** | **Q01** | **Q02** |
| --- | --- | --- | --- | --- | --- |
| The | 2 | 1 | 0 | 0 | 0 |
| Transportation | 1 | 0 | 0 | 0 | 1 |
| Of | 1 | 1 | 1 | 0 | 0 |
| Vegetables | 1 | 0 | 1 | 0 | 1 |
| Is | 1 | 0 | 0 | 0 | 0 |
| Most | 1 | 0 | 0 | 0 | 0 |
| Important | 1 | 0 | 0 | 0 | 0 |
| Some | 0 | 1 | 0 | 0 | 0 |
| Fruit | 0 | 2 | 0 | 1 | 0 |
| Arrives | 0 | 1 | 0 | 0 | 0 |
| Soon | 0 | 1 | 0 | 0 | 0 |
| In | 0 | 1 | 1 | 0 | 0 |
| Truck | 0 | 1 | 1 | 1 | 0 |
| Big | 0 | 1 | 0 | 0 | 0 |
| One | 0 | 0 | 1 | 0 | 0 |

The next step consists of calculating the SVD of the term–document matrix to find an approximation of it according to [equation \[4.15\]](#eq4.15). With an approximation factor of two (where k=2) for our example, we will only consider the first two columns of the matrix. Thus, we obtain the matrices in [Figure 4.35](#fig4_35) whose multiplication is approximately equal to the original matrix X2 ([equation \[4.15\]](#eq4.15)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_35.jpg)

Figure 4.35. Approximation factor of 2 of the SVD of X

To integrate the queries into the process, we consider that queries are also documents as can be observed in [Figure 4.33](#fig4_33). From [equation \[4.15\]](#eq4.15), we can infer [equations \[4.17\]](#eq4.17) to calculate the vector of a document D and a query Q:

[\[4.17\]](#ieq4.17) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_8a.jpg)

To calculate the vector of Q01, which corresponds to the query (fruit truck) still with k = 2, in reduced space, we proceed as in [Figure 4.36](#fig4_36). By carrying out a similar processing for all of the documents, we obtain their vectors in reduced space. The vectors of the other documents are also given in [Figure 4.36](#fig4_36).

These vectors then serve to calculate the distances between the query and each of the documents according to [equation \[4.16\]](#eq4.16). It should be noted that these are directed distances (their value can be negative) and therefore d(a,b)=−d(b,a)), contrary to the general notion of distance, which can only be positive and for which d(a,b)=d(b,a).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_36.jpg)

Figure 4.36. Vector calculation of the queries and the documents in this collection

Calculating the other distances in the same way and repeating the same process for the query R <sub>02</sub> (vegetable transportation) gives the results in [Table 4.8](#tab4_8).

**[Table 4.8](#itab4_8).** *The distances between the queries and the documents in this collection*

| **Document/Query** | **Q <sub>01</sub>** | **Q <sub>02</sub>** |
| --- | --- | --- |
| Doc <sub>01</sub> | −0.28925511 | 0.98556838 |
| Doc <sub>02</sub> | 0.96230936 | −0.18701158 |
| Doc <sub>03</sub> | 0.68292419 | 0.34805227 |

Presented in a bidimensional space, this gives the vectors in [Figure 4.37](#fig4_37).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_37.jpg)

Figure 4.37. The vectors corresponding to the texts in reduced space (k = 2). For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

The order of the distances between the first query and the three documents is doc02, doc03, doc01. This order can be explained by the presence of the words *fruit* and *truck* in doc02 and the absence of these two words in doc01. Similarly, the order of similarity of the three documents in relation to the second query is doc01, doc03, doc02. This can be explained by the fact that the words *vegetable* and *transportation* occur in doc01 while only the word vegetable is used in doc03. Doc02, which does not contain any words in the query, is in the last place. One of the advantages of this method is that it is robust in the face of the variabilities that can exist in texts (typographic errors) and does not depend on a specific vocabulary.

Finally, it should be noted that, given the importance of information retrieval in today’s world, many techniques from AI have been applied to this problem with varying degrees of success, including the popular Support Vector Machine (SVM) method \[COR 95\], neural networks and genetic algorithms \[HSI 95\].

## 4.4. Big Data (BD) and information extraction

With the democratization of the Internet, there was an explosion in the size of digital data. Gradually, there was a move from mostly formatted data (search results, information sites) toward more personal and sometimes intimate data. This large mass of data, impossible to exploit manually, required the emergence of a new discipline called *data science* that includes another even younger discipline called *Big Data* \[RUS 14b, MAN 14, HUR 13\].

### 4.4.1. Structured, semi-structured and unstructured data

BD applications are distinguished by the use of a variety of information resources that are available in various formats and types. Classically, computer systems use structured data. These data follow a strict framework typically defined in the form of a database table. These tables have relations between them that are defined through connections that are called foreign keys. The advantage of this framework is that there are theoretical foundations that make it possible to reduce data redundancy as much as possible through a standardization process as well as the existence of platforms, called Database Management Systems (DBMS), which guarantee rapid access to information even in cases of large databases. To manipulate this data, SQL (Structured Query Language) and its procedural derivatives such as TransactSQL and PL/SQL play an important role.

Semi-structured data have less rigid structures. They are notably represented in the form of XML documents. As shown in [section 1.2.2.2](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch01.xhtml#se1.2.2.2), with the DTD, it is possible to define a general structure that can be instantiated in several possible forms.

Unstructured data are organized without constraints on the content (see [section 4.3.1](#sec58)). Among others, it can consist of scientific, journalistic, personal or literary texts. Regarding formats, the data also vary considerably. Another important challenge worth noting regarding the data is that it consists of data distributed on several platforms on a network that can also be localized in distant geographical areas. This disposition, which is commonly called the cloud, has opened the door to new approaches.

### 4.4.2. Architectures of BD processing systems

BD are commonly considered to be an evolution of Business Intelligence. According to this approach, a company’s data can all be gathered into a single space that is called a data warehouse where they are processed offline unlike databases where the data is modified and accessed online. Data warehouses are typically constructed according to the Extract Load Transform (ELT) approach (see [Figure 4.38](#fig4_38)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_38.jpg)

Figure 4.38. ELT approach for data warehouses. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

The extraction, the most difficult phase, consists of collecting data from several systems. These data are typically relational databases with sometimes semi-structured data. The transformation itself applies a set of rules that aim to modify the data in order to guarantee its coherence in the warehouse. Every database designer can adopt a unique convention to represent information. For example, some use the letters *M* and *F* to indicate the genders masculine and feminine, respectively, while others prefer the digits 1 and 2 for the same task. Other differences that require a harmonization are the adoption of different units (weight, sizes, distances, etc.). The last phase consists of introducing the data in the data warehouse according to processes that vary considerably from one data warehouse to another. It is important to note that, as these three steps are purely technical and as they do not involve real scientific challenges, they are easily mastered and implemented in many companies.

Once the data is stored in a warehouse, *data mining* makes it possible to recognize patterns such as the products that customers buy together or in relation to a socio-economic profile in order to predict future behaviors. Classic algorithms like decision trees, neural networks and Bayesian networks are used to carry out this task (see \[WIT 05, BER 04\] for more details).

Because Big Data processing is a domain that is still in development, there is not yet one architecture that can be called a standard. [Figure 4.39](#fig4_39) presents a possible architecture for which there are many alternatives in the literature. The central element of this architecture is the parallel file system Hadoop, an essential support for parallel processing (implemented in clusters, groups of computers working in parallel on shared disk spaces), which has become essential to talk about BD. Initially constructed by Doug Cutting of Yahoo!, Hadoop is currently an open-source product distributed by the Apache foundation, notably known by its HTTP server. Two main components are at the core of Hadoop: the distributed file system and the MapReduce engine. Written in Java, Hadoop’s distributed file system is a system designed to process distributed files in a portable way. This file system uses a TCP/IP communication layer and Remote Procedure Call (RPC) clients. The MapReduce engine is a parallel and distributed implementation of the data-processing algorithm, making it possible to distribute one calculation over several machines (the map phase) and aggregate the different results into one coherent whole (the reduce phase).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_39.jpg)

Figure 4.39. BD processing architecture. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

The data are then analyzed statistically with pattern-matching and data-mining algorithms. Of course, given that a large quantity is available in text form, NLP is a fundamental part of the analysis process, especially to extract information.

### 4.4.3. Role of NLP in BD processing

Combining robustness and depth in the processing was the objective of many works in the NLP domain at the start of the 2000s, notably in the domains of human–machine dialogue and speech translation. The problem is that this occurred to the detriment of the independence of the applicative domain as these applications required recourse to deeper knowledge about the domain concerned. With the advent of the challenge of BD, gradually the priority given to the robustness and independence in the domain became essential again to the detriment of the depth of analysis. To a certain extent, BD allowed for the redeployment of existing tools and approaches but in a different way through new architectures. The new philosophy was to make the most of existing tools, techniques and models. The new approach to NLP could be seen as a rising exploration of the applicative possibilities of NLP: starting from the simplest applications and attempting to go as far as possible toward the ultimate objective, which is the construction of applications that satisfy the demands of the market.

However, as Big Data is a new form of input, it entailed changes to data-processing strategies. The abundance of data facilitated the use of statistical or, more generally, machine learning algorithms. In addition, this same abundance required the use of unsupervised or lightly supervised learning algorithms in order to reduce efforts related to annotating the data that are necessary for supervised learning approaches. This involves adapting these algorithms, which were initially designed to process thousands of cases, to process millions of cases. The parallelization required by environments constructed on Hadoop, even for high-level environments like the ESB (Enterprise Service Bus) TALEND [](#ch4en18) that offer an integrated graphic programming interface from the base code (java, Spark) to the project management, requires revising the design of NLP algorithms to adapt them to the MapReduce model.

Moreover, because the data is distributed in clouds, this requires adopting new strategies to process them. The distribution of data on different servers can also be accompanied by a topical distribution. For example, the data in one particular server can pertain only or mainly to the medical domain, while the data in other servers may concern biology or the environment. This requires algorithms that are capable of extracting general principles independent of the task while being able to merge the parameters related to the applicative domains distributed over different servers.

### 4.4.4. Information extraction

Information extraction is the extraction of structured information from unstructured information. It is a superficial approach that consists of finding partial information that is determined to be useful in a text or a data collection. The information extracted can concern security, transportation, urban planning, scientometrics, etc. Often, the outcome of the information extraction modules are analyzed statistically in order to recognize trends. A common example is the calculation of positive and negative opinions about a product, a politician, an institution, etc. \[GRI 10\]. Compared to information retrieval, information extraction involves extracting structured data from a structured query while the queries in an information retrieval system are more open. The common point remains that the search space is a collection of documents (see [Figure 4.40](#fig4_40)).

Question answering systems can be seen as a variant of information extraction systems. The main difference is that these systems have an interface capable of analyzing questions input and a module capable of transforming the answer into an utterance. For more details about question answering systems, see \[GUP 12, WEB 10\] (see [Figure 4.40](#fig4_40)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_40.jpg)

Figure 4.40. DFD of an information extraction system and a question answering system

As shown in [Figure 4.40](#fig4_40), the main difference between an information extraction system and a question answering system is the existence of two analysis and generation modules that are capable of processing open questions produced by users and generating responses in natural language, respectively. It should be noted that, in order to facilitate the comparison, in the case shown, the analysis and generation modules use schema-based semantic representation; however, in reality, other forms of semantic representations are also possible, such as representations based on different types of logic (modal logic [](#ch4en19), fuzzy logic [](#ch4en20), etc.) (see [section 2.2.2](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch02.xhtml#sec22)) or even word embeddings on a large scale (see \[MIK 13\]).

#### 4.4.4.1. Extraction of named entities (NEs)

The extraction of NEs consists of identifying and classifying proper nouns in pre-defined categories based on the needs of a given application. Typically, three basic categories are used: person, place and organization. In addition to these three large categories, sometimes emails, temporal expressions, measurement expressions like monetary amounts, distances or weight, bibliographic references, etc. are added. Without needing to create connections between the identified entities, entity extraction can be used as a module in a larger information extraction system. As demonstrated with the Prolex proper noun database presentation, proper nouns are an important part of a text, especially in journalistic and scientific domains, where they account for about 10% of words according to some studies. For an overview of works related to this question, see \[NAD 07\].

The extraction of NEs seems to be a simple task at first glance, but in practice there are many rhetorical phenomena, including notably metonymy, that make identifying them problematic. As an example, consider the set of sentences [\[4.18\]](#eq4.18) (for more details, see the section on metonymy in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch02.xhtml)).

| Team vs. country | France won the World Cup. |
| --- | --- |
|  | The World Cup was organized in France. |
| Location vs. authority | The President of France officially resides at the Elysée. |
|  | The Elysée declared that elections would not take place next month. |
| Company vs. product | He drinks Coca Cola every morning, he’s crazy! |
|  | Coca Cola just launched a new advertising campaign. [\[4.18\]](#ieq4.18) |

According to the approach of Message Understanding Conference (MUC) evaluation campaigns, it could be considered that *France* is always a place but this does not seem to be an ideal solution. At the same time, it is not always possible to count on general ontological knowledge in order to distinguish the different uses of a term. The simplest method of processing NEs consists of using an appropriate dictionary like Prolex. Despite its speed and simplicity, this approach suffers from a major inconvenience, which is the updating required for the dictionary to reflect the current changes that, naturally, have an impact on the proper noun dictionaries in a much more substantial way than on ordinary dictionaries. Moreover, such a dictionary is not sufficient to resolve ambiguity, because its resolution requires using contextual information. Another approach consists of using regular expressions to consider internal and external indicators. Internal indicators are morphemes, which are part of the proper noun, but through their semantic nature, they indicate a location. Common examples of internal indicators are lake, river, airport, city, street and boulevard. This makes it possible to predict the role of the rest of the sequence like in the segments in italics in sentences [\[4.19\]](#eq4.19):

1. a) John lives on *Lexington Avenue*.
2. b) The *Saint Louis Lambert Airport* is one of the prettiest airports in the US. [\[4.19\]](#ieq4.19)
3. c) The *Riverside Park* is located along *Hudson river*.
4. d) The *city of Knoxville* is located in the *south of the US*.

External indicators are not part of the noun properly speaking but rather part of the cotext. They indicate that an NE will follow. As an example, consider the following indicators: in the south of, in the north of, beside and very close to.

Pattern-based methods, despite their simplicity, are very limited and do not make it possible to resolve many cases of ambiguity (e.g. John F. Kennedy, the airport or the person). This pushed researchers to adopt learning-based approaches like HMMs \[BIK 97, BOU 02\], SVM \[TJO 03\], naive, semi-supervised \[PAS 08\] or unsupervised \[NAD 06\] Bayesian networks.

As an example, consider the KnowItAll system developed by Oren Etzioni and his collaborators at the University of Washington \[ETZ 05\]. This system uses an unsupervised approach that is based on a three-step processing (see [Figure 4.41](#fig4_41)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_41.jpg)

Figure 4.41. DFD of KnowItAll

First, the system proceeds to the start-up phase that consists of providing a set of predicates that represent classes of entities like movieActor, city and brand of car. Each of these predicates is associated with a set of labels that are the surface forms that can take an entity in an utterance. For example, consider the predicates for the domains of geography and films given in [Figure 4.42](#fig4_42).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_42.jpg)

Figure 4.42. Examples of predicates in the domains of geography and films

Inspired by a Hearst pattern-based approach, the second step consists of labeling using eight generic patterns to produce candidates. The labels identified in the start-up step can serve to instantiate patterns with the appropriate classes. As an example, consider sentence [\[4.20\]](#eq4.20). In this sentence, the word city serves to indicate the class of entities that follow. Using the pattern “NP such as ListNP”, we can analyze sentence [\[4.20\]](#eq4.20) and propose four candidates for the class of city: Richmond, Charlottesville, Lynchburg and Roanoke.

> Our buses stop at cities like Richmond, Charlottesville, Lynchburg and Roanoke. [\[4.20\]](#ieq4.20)

Based on the Pointwise Mutual Information (PMI) algorithm developed by David Turney \[TUR 01\], the system then tests the plausibility of each hypothesis using the Web as a corpus. Thus, the system uses a search engine to bring up pages that contain entities that it intends to verify. For example, to verify that Lynchburg is the name of a city, the system seeks to verify that there is a mutual information (PMI) between Lynchburg and discriminating sequences (or discriminators) that indicate that it really is a city, such as: -is a city, the city of-, etc. Formally, the PMI score is calculated using [equation \[4.21\]](#eq4.21):

[\[4.21\]](#ieq4.21)

The PMI score is the number of results for a query that combines the discriminator D and the instance I divided by the number of results for the instance itself. To transform PMI scores into a co-occurrence probability, the system takes a set of *k* positive cases and *k* negative cases for each class and defines the threshold that serves to divide all of the cases. Then, another set of *k* positive cases and *k* negative cases is used to estimate the following probabilities:

| P(PMI > threshold \| class), | P(PMI ≤ threshold \| class), |
| --- | --- |
| P(PMI > threshold \| ¬class), | P(PMI ≤ threshold \| ¬class), |

It should be noted that in the experiments described, the value of *k* is equal to 10. The probabilities obtained are then used as input features for a naive Bayesian classifier according to [equation \[4.22\]](#eq4.22), which shows the probability of a fact given the features t <sub>1</sub>, t <sub>2</sub>, ……t <sub>n</sub>:

[\[4.22\]](#ieq4.22) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_10.jpg)

As emphasized in \[ETZ 05\], the use of PMIs presents problems that merit further reflection, like rare data for some cases, even with the Web as a corpus, and the case of homonyms.

#### 4.4.4.2. Extraction of relations

The relations between the entities in a text can be useful for many applications. For example, in a bibliographic information extraction application, it is essential to associate the articles with their authors and institutions. In medical applications, it is possible to extract relations between the genes that cause certain illnesses \[CHU 06\]. The extraction of relations can have the goal of the automatic construction of ontologies \[WON 09\].

The task of extracting relations can be described as the construction, from raw texts, of predicates, whose diagram is: relation (e <sub>1</sub>, e <sub>2</sub>, …e <sub>n</sub>), where *e* represents an entity cited in the text. Here are a few examples:

| Emmanuel Macron is the president of France. | president (Emmanuel Macron, France) |
| --- | --- |
| Ouagadougou is the capital of the African Republic of Burkina Faso. | capital (Ouagadougou, Burkina) |
| The discus is a very pretty fish that lives in the Amazon. | lives (discus, Amazon) |
| Nadine is the mother of Celine and Amandine. | mother (Nadine, Celine, Amandine) |

The simplest approaches are based on pattern recognition. \[HEA 92\] proposed five patterns to extract hyponyms (see [Table 4.9](#tab4_9)).

**[Table 4.9](#itab4_9).** *Hearst’s extraction patterns for hyponyms*

| **Patterns** | **Examples** |
| --- | --- |
| Y such as X <sub>1</sub>, X <sub>2</sub>,..., X <sub>n</sub> | A sports car like a Ferrari, Bugatti or Porsche. |
| X <sub>1</sub>, X <sub>2</sub>,..., X <sub>n</sub> and/or/among others Y | Car, train, plane among other modes of transportation |
| Y, including X <sub>1</sub>, X <sub>2</sub>, …, X <sub>n</sub> | Combat sports, including karate, judo and boxing |
| Y, in particular X <sub>1</sub>, X <sub>2</sub>, …, X <sub>n</sub> | Planes, in particular the F22 and F35. |
| Some Y such as X <sub>1</sub>, X <sub>2</sub>, …, X <sub>n</sub> | Programmers like John, Patrick and Will |

The idea behind supervised approaches is to manually annotate a corpus and automatically extract patterns and rules. The general diagram of this process is shown in [Figure 4.43](#fig4_43).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_43.jpg)

Figure 4.43. Induction of rules from examples

To make the process of writing rules less demanding, it is possible to start by annotating a certain number of cases manually in order to start the system of automatic rule induction. The system obtained can then be used to annotate new cases. The idea is to define a confidence threshold in order to select only cases annotated by the system whose confidence score is greater than the threshold. Over the course of the system’s development, its performance improves and the percentage of cases annotated with an acceptable score increases until a maximum is reached (a plateau on the performance curve), where the system’s performance stagnates even after the addition of new learning cases.

In the literature, two learning-based approaches are opposed (see \[BAC 07\] for an overview): feature methods and kernel methods \[LOD 02\]. In feature-based approaches, an input sequence analysis is used to attempt to identify the disposition patterns of the entities that are found in this sequence (see, for example, \[KAM 04\]), for example, the number of words that separate two entities and the types of entities (person, place or institution). Some approaches go further by using dependency trees for a sentence. For example, to extract relations from the sentence *John invented a new steam engine in his garage*, we can use a decision tree like the one in [Figure 4.44](#fig4_44).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_44.jpg)

Figure 4.44. Dependency tree to extract relations

In general, a set of features is the result of a process of trial and error. More formally, a sentence *S* with *n* entities and *k* words is presented in this way: *P* = *w <sub>1</sub>, w <sub>2</sub>, e <sub>1</sub>, w <sub>i</sub>, e <sub>2</sub>,..., w <sub>l</sub>, …, e <sub>n</sub>, …, w <sub>k-1</sub>, w <sub>k</sub>*, where *k* > *n* ≥ *i*. The sentence thus represented is analyzed by a classification function *f <sub>R</sub>* that provides two defined outputs according to these criteria:

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_11.jpg)

The classification function can be realized by any classification algorithm, for example, a variation of an entropy-based statistical algorithm.

Kernel-based approaches use structural representations with similarity scores to guide the classifier and thereby considerably reduce problems related to the choice of similarity features. The principle of these approaches is to use a function K(X, Y) that defines the similarity relation between the objects *X* and *Y*. For example, when considering the level of character sequences, the similarity of two sequences increases with the number of sub-sequences shared between these two sequences. Thus, the similarity between the sequences is sim(livre, livrent) > sim(livre, livarot) [](#ch4en21).

The integration of supplementary knowledge resources such as parts of speech and syntactic analysis in segments or dependency trees has also been used to complete this task \[ZEL 03, CUL 04, ZHA 05\]. For example, to calculate the similarity between two analysis trees, a relatively simple algorithm can be used (see [Figure 4.45](#fig4_45)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_45.jpg)

Figure 4.45. Algorithm to calculate tree similarity

Given the cost of preparing data in supervised learning-based approaches, researchers gradually began to explore semi-supervised and unsupervised learning approaches \[BUN 07, BOL 11\]. Semi-supervised approaches are a compromise between the minimal effort of unsupervised approaches and the performance of supervised approaches. The principle of semi-supervised learning consists of annotating a limited number of cases to avoid the effort required to annotate an entire corpus and using them to construct groups of cases that are called *sentence bags*. A sentence bag is constructed like this: first, some entities that are related or not by a known semantic relation are identified. For example, \[BUN 07\] considers the case of companies acquired by multi-nationals (see examples in [Figure 4.46](#fig4_46)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_46.jpg)

Figure 4.46. Pairs of acquisition by multi-nationals

Then, a search is done on the Web using the two entities in each predicate as keywords. The results that the search engine provides are verified in a large number of pages but not necessarily all pages. Moreover, some pages may discuss the acquisition of YouTube by Google more or less explicitly while others may provide information related to these two entities without necessarily evoking their mutual relationships. It can also be assumed that the relation between these two entities will not be verified in practically all of the results where it is not a proven fact. More concretely, it can reasonably be assumed that the number of pages that a search engine will present that discuss the acquisition of Yahoo by Google is zero. Therefore, the number of pages serves as a factuality indicator for the supposed relation between the entities. The set of results for a pair of entities is called a *case bag*. Some examples of search results with the acquisition pairs are given in [Figure 4.47](#fig4_47).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_47.jpg)

Figure 4.47. Examples of search results

Finally, it is important to note that the way to proceed corresponds to the Multiple Instance Learning (MIL) paradigm that was initially proposed by \[DIE 97\] (see \[AMO 13\] for a general presentation of this paradigm).

#### 4.4.4.3. Event extraction

Event extraction was one of the first applications in the domain of information extraction. The events concerned were as varied as terrorist attempts, road accidents and announcements. The events could be extracted from written texts or telephone conversations like in \[BOU 02\]. According to the terminology of the Message Understanding Conference (MUC), each event is characterized by a scenario template that contains a set of slots that must be instantiated.

Just like the extraction of named entities and relations, supervised \[SOD 99, YAN 00\], semi-supervised \[SEK 07\] and unsupervised \[SHI 06\] learning approaches were used for the extraction. Several rule-based and pattern-based systems were created like the Fastus system by \[APP 93\] and the REES system by \[AON 00\]. For example, to extract events, \[AON 00\] proposed an architecture that conducts a processing in three main steps: a tagging module, a coreference resolution module and a pattern generation module (see [Figure 4.48](#fig4_48)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_48.jpg)

Figure 4.48. DFD of the REES system

The tagging module itself conducts a three-step processing: tagging of names, Noun Phrases (NP) and events. These three components use the same processing engine but different templates for each component. The coreference module then proceeds with labeling the nominal groups that correspond to organizations, people, places, etc. The template generation module is based on declarative rules. It results in a template whose format is compatible with the MUC recommendations, as shown in [Figure 4.49](#fig4_49).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_49.jpg)

Figure 4.49. Example of an event template

Then, REES concatenates the templates that are associated with the same event. This occurs using a set of declarative rules designed based on world knowledge. For example, as the birth and death of a person are unique events, there is a rule that makes it possible to concatenate templates relating to such events when they have the same subject.

#### 4.4.4.4. Sentiment analysis and opinion mining

While working on interactive systems like virtual agents or robots, researchers realized that some affective information processing is inevitable because it represents a very important implicit and subjective part of all human communication. For example, a virtual guide in an airport would be too monotonic and therefore not very useful if it could not detect the emotions of its interlocutor and adapt its tone \[SLO 81, SMI 10, OCH 12\]. In terms of generating answers on the part of the agent, many processes also play a role in expressing a sentiment or an opinion in an appropriate manner: lexical choices, syntactic constructions, prosody, etc. These elements play an important role in controlling the interaction, for example, by making it possible to prolong the dialogue or by participating in managing the focus (see, for example, \[JAN 16\]).

Similar applications have also been created to extract opinions expressed in a text or a forum, to observe investment tendencies and to detect criminal or terrorist communications. This is particularly important to automatically survey opinions about a given commercial product or even a political question. The popularity of social media like Facebook and Twitter has made the use of such practices on texts produced by users of these media particularly attractive \[RUS 14a\].

It should be noted that, given the constraints on the form as well as the content of these media, processing emotions is not as easy. Processing messages on Twitter is easier, given the concise nature of these messages and their direct character \[PAK 12\]. Processing product reviews is also facilitated by the direct aspect of these reviews and by the relatively minimal quantity of irrelevant information. On the other hand, blogs and forums are more difficult because they can address a number of important questions, they can make implicit or explicit comparisons, and there are also many digressions and sarcastic comments.

Currently, there is an abundance of literature concerning these questions under various names. For example, this includes opinion mining, opinion extraction, emotion analysis or extraction, subjectivity analysis, affection analysis and emotion detection. As noted in \[RIL 06\], the domain of subjectivity is quite vast and includes allegations, opinions, desires, beliefs, suspicions and speculations. Among these definitions, the notion of the opinion seems particularly pertinent. An opinion is a sentiment, attitude, emotion, an evaluation of an entity or a topic, or an aspect of these \[KIM 04, LIU 11\]. An opinion can be positive, negative or neutral (see, for example, [\[4.23\]](#eq4.23) for a positive opinion).

> Paul thinks that “Le Monde” is the best newspaper that covers political life in France. [\[4.23\]](#ieq4.23)

This is called the semantic orientation of the opinion, or the polarity of the opinion. Formally, an opinion can be expressed by a quintuplet (e <sub>j</sub>, a <sub>jk</sub>, so <sub>ijkl</sub>, s <sub>i</sub>, t <sub>l</sub>), where \[LIU 11\]:

- – e <sub>j</sub> is the entity intended by the opinion;
- – a <sub>jk</sub> is an aspect or a feature of the entity e <sub>j</sub>;
- – so <sub>ijkl</sub> is the value of an opinion of a source *s <sub>i</sub>* on a feature a <sub>jk</sub> of the entity e <sub>j</sub> at a moment t <sub>l</sub>. This value can be positive, negative or neutral;
- – s <sub>i</sub> is the source of the opinion;
- – t <sub>l</sub> is the time of expression of this opinion.

It consists of a generic definition that can apply to the political, commercial, social, or intellectual domains, and so on. It should also be noted that the correlations between these five elements are rather important: ideally, all five elements should be there to maximize the utility of the analysis. An opinion without an intended entity or its features has only a little importance. If we analyze the opinions expressed in sentence [\[4.23\]](#eq4.23), we find the following elements:

- – the entity intended by the opinion (ej): the newspaper “Le Monde”;
- – aspect (ajk): political;
- – value (soijkl): best/positive;
- – source (si): Paul;
- – time (si): present.

Since processing sentiments is inherently connected to subjectivities, it is not always possible to decide which sentiment provokes a given sentence in an absolute way. Consider sentence [\[4.24\]](#eq4.24). The sentiment that provokes this sentence could be the fear of being contaminated for someone who lives in Africa or sadness for someone who lives outside of Africa. Moreover, an African whose family is vaccinated against cholera will have a different sentiment compared to someone whose family is not vaccinated. To solve the problem of relative stance, in the early work, researchers simply avoided considering this variety of angles about sentiments and adopted a single perspective that they judged to be standard or representative of the majority of people. However, recent works have begun to consider the relative stance of the author who expressed the opinion (see, for example, \[RAJ 16, EBR 16 and JAN 16\]).

> Cholera is devastating Africa this year. [\[4.24\]](#ieq4.24)

Psychologists define emotions as complex states of sensations that give rise to psychic or physiological changes that affect thought and behavior. Emotions are associated with a fairly important level of phenomena like temperament, personality, humor and motivation.

Historically, the study of emotions started by at least the 19th Century, notably with the works of William James in the domain of psychology. Since then, several theoretical models have been proposed. Some models, known as dimensional models, consider that emotional states are connected by a set of dimensions shared between all emotions. They also include intensity parameters. From a cognitive perspective, these models postulate the existence of a neurophysiological system that is centrally responsible for all affective states. This contradicts the point of view supported by basic emotion theories, which consider that emotions emanate from different neurophysiological systems. Despite the objectives of cultural or physiological universalism, several psychologists and anthropologists find that it is not possible to define a universal framework to classify emotions. It is known that some cultures encourage the expression of emotions while others judge such expression to be unacceptable. The divergence between the starting postulations is reflected even more significantly in the models, a few of which will be presented here.

The semantic differential model proposed by Osgood focuses on scaling the connotations of objects, events and concepts \[OSG 57\]. These connotations are used to derive an attitude with regard to an event, an object or a concept. After having studied several semantic differential scales, Osgood and his colleagues succeeded in identifying three recurrent attitudes to evaluate words. These consist of evaluating with the pair of adjectives: good/bad, the power: strong/weak and the activity: active/passive. They also showed in a study of about 10 cultures that these three dimensions are universally present throughout the studied cultures \[OSG 75\].

In turn, the categorical model of Ekman starts from the perspective that there are six discrete categories of sentiments that are expressed by words: anger, disgust, fear, joy, sadness and surprise. As he considered that these sentiments are universally translated by distinct facial expressions, Ekman concluded that these sentiments have a biological origin. Although these categories have been adopted by many works in the domain of automatic processing of sentiments, some researchers have postulated that these categories are dependent on the domain of application \[DME 07\].

The circumplex model was initially developed by \[RUS 80\]. This model considers that emotions are distributed in a circular bidimensional space with arousal and valence values, where the arousal represents the vertical axis while the valence represents the horizontal axis (see [Figure 4.50](#fig4_50)). The point of intersection of the two axes is the center of the virtual circle of emotions and represents a neutral state. Thus, the different emotions can have different values of emotions or affections whose value is zero.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_50.jpg)

Figure 4.50. The representation of emotions according to Russell’s circumplex model

Finally, the cubic model developed by Lövheim is distinguished by its biological inspiration because it relates the rates of three neurotransmitters, which are dopamine, noradrenaline and serotonin, with the eight basic emotions identified by Silvan Tomkins \[LÖV 12\]. Each of these emotions is associated with these neurotransmitters in varying degrees, as shown in [Table 4.10](#tab4_10).

**[Table 4.10](#itab4_10).** *The basic emotions and corresponding neurotransmitter rates*

| **Base emotion** | **serotonin** | **dopamine** | **Noradrenaline** |
| --- | --- | --- | --- |
| Shame/humiliation | Low | Low | Low |
| Distress/Anguish | Low | Low | High |
| Fear/Terror | Low | High | Low |
| Anger/Rage | Low | High | High |
| Contempt/disgust | High | Low | Low |
| Surprise | High | Low | High |
| Pleasure/Joy | High | High | Low |
| Interest/excitation | High | High | High |

The direct connection between neurotransmitters and emotions makes it possible to give biological explanations for emotions. For example, depression can be seen as a situation that causes a decrease in serotonin, thus limiting the possible emotions to Shame/Humiliation, Distress/Anguish, Fear/Terror and Anger/Rage. An inverse vision of this state would be to consider that it is impossible for someone with depression to have the emotions of surprise, joy or interest, which require higher levels of serotonin.

Tridimensional, Lövheim’s model places Tomkin’s eight basic emotions in the corners of a cube and uses the following three axes: noradrenaline, serotonin and dopamine.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_51.jpg)

Figure 4.51. Lövheim’s cube of emotions

The advantage of this classification is that it offers a way to account for differences between emotions that it is not possible to distinguish with bidimensional models.

Finally, the Hourglass model developed by Cambria is worth mentioning as well. It is a model based on the works of Plutshik on human emotions \[PLU 01\]. The fundamental idea of this model is that the mind is made of several independent sources and that emotional states result from the activation or deactivation of these resources \[MIN 07\]. Each of these resource combinations changes the brain’s activities, thereby affecting our way of thinking. For example, the state of anger seems to select resources that allow for reacting quickly and with more force while suppressing other resources that cause a person to act cautiously. This idea is also confirmed by the results of research in the domain of cerebral imaging that show that a different pattern of cerebral activity accompanies each emotion (see \[CAM 12, CAM 16\] for more details about this model).

An emotion can be expressed using explicit linguistic means such as the use of verbs and expressions of opinions have extremely varied forms. For example, in English, this includes expressions like *I think, I believe, I consider, it seems to me, in my opinion* and *I am of the opinion*. Verbs that serve to express taste can also serve to express an opinion. In English, this includes following verbs like *cherish, adore, love, please, appreciate, detest, displease, prefer* and *be favorable*. However, the use of an explicit element of opinion expression is not a necessary condition for expressing an opinion. Opinions are very often expressed implicitly, and the use of a linguistic indicator only has the function of underscoring the subjective character of the opinion or, in certain cases, highlighting the person uttering it.

To express an opinion, three forms of expression can be distinguished: direct expression, indirect expression and comparative opinion.

A direct opinion consists of an explicit qualification of an entity, a topic or an action. This qualification can take the form of a qualificative adjective or epithet, or a lexical choice (see examples in [Table 4.11](#tab4_11)).

**[Table 4.11](#itab4_11).** *Examples of opinions with different types of qualifications*

| **Opinions** | **Type of qualification** |
| --- | --- |
| This software is really efficient. | With an adjective |
| In this racer, it only takes an hour to get to Paris. | With a noun that has a positive connotation |
| Jules’ company is just getting by after last year’s losses. | With a verb that has a negative connotation |

Indirect opinions, in turn, are often formulated as the logical consequence of an action or a means (use of an entity), as in sentence [\[4.25\]](#eq4.25):

> After using this detergent, Adeline’s dishes shone like diamonds. [\[4.25\]](#ieq4.25)

Comparative opinions are used to compare entities, ideas or topics to express preferences. Linguistically, this occurs using comparatives and superlatives. Again, the comparison can be explicit or implicit as in [\[4.26a\]](#eq4.26) and [\[4.26b\]](#eq4.26), respectively:

1. a) Ferraris are less practical than Fords.
2. b) The left is the political current that defends workers’ rights the most (implicitly more than the right and the center). [\[4.26\]](#ieq4.26)

To process the lexical level of opinions, an extension of the WordNet base was created at the IRST Institute in Italy to equip definitions of words in this base with an affective value. It is called WordNetAffect and it covers the entire lexicon of the English language \[STR 04\]. The words are classified according to the approach of \[ORT 87\] given in [Table 4.12](#tab4_12). The words are annotated with a polarity (positive or negative) as well as degrees to designate the force of an emotion. The 2004 version of WordNetAffect includes 1,314 synsets and 3,340 words. Several other projects intended to create lexical databases or dictionaries with emotions have been created. Each of these projects is distinguished by its method of annotating words (automatic, manual or semi-automatic), its size or taxonomy adopted (see, for example, \[KAM 04b\] and SentiWordNet [](#ch4en22) \[ESU 06\]).

**[Table 4.12](#itab4_12).** *Categories of terms in WordNetAffect \[STR 04\]*

| **Category** | **Examples of terms in English and French** |
| --- | --- |
| Emotion | Anger – fear |
| Cognitive state | Doubt – dazed |
| Feature | Aggressiveness *–* competitive |
| Behavior | Cry – offense |
| Attitude | Skepticism – intolerance |
| Emotion | Pleasure – feel |

In terms of syntax, two syntactic forms directly affect the expression of sentiments and emotions: negation and dislocation. Negation makes it possible to inverse the polarity of an opinion or to restrict this opinion to a precise entity (see sentences [\[4.27\]](#eq4.27)):

1. a) I do not like cream cheese. (Negative opinion) [\[4.27\]](#ieq4.27)
2. b) She only likes white roses. (Restriction)

Another syntactic construction that affects the expression of emotions is dislocation. It consists of displacing a phrase in order to highlight it (see [Table 4.13](#tab4_13)). The focus attracts the attention of several opinion elements and therefore has various functions. Naturally, a good module of opinion extraction should consider these syntactic variations in order to be able to process the opinions correctly. Moreover, several works concern the role of the discursive structure in the expression of opinions, notably including that of \[POL 04c\], that studied the effect of discursive connectors on the polarity of an opinion. Consider sentences [\[4.28\]](#eq4.28):

| Michael is good at networks. | (Positive opinion) [\[4.28\]](#ieq4.28) |
| --- | --- |
| Although Michael is good at networks, he is not very good at algorithms and programming. | (Negative opinion) |

**[Table 4.13](#itab4_13).** *Relation between syntactic structures and the elements of an opinion*

| **Sentences** | **Syntactic role of the element in focus** | **Opinion element in focus** |
| --- | --- | --- |
| It’s this song that I like. | Agent | Intended entity |
| It is Jacqueline’s dress that I adore. | Patient | Intended entity |
| It’s John who likes red roses. | Agent | Source of the opinion |
| With much recognition and gratitude, he accepted your gift. | Prepositional group expressing the manner | Opinion |

The works of \[VOL 07\] highlighted the role of the summative evaluation of an entity that comes at the end to summarize the previous evaluations that concern several aspects of an entity or a topic. These researchers showed that attributing a more significant weight to these evaluations made it possible to improve the analysis results. Consider passage [\[4.29\]](#eq4.29). The evaluation given includes several elements that can be judged to be positive (new, specialized, effective service, rich menu), but the location of negative elements at the end gives them a conclusion value and attributes a globally negative aspect to the evaluation. Sometimes, explicit markers can be used to indicate the conclusion such as *in short*, *in sum* and *in summary*. Finally, it is also useful to mention that a large number of annotated linguistic resources are available for researchers (see \[PAN 08\] for a review of these resources):

> Located in a bright new building just steps from the Atlanta Marta train station, a restaurant specialized in Mexican cuisine recently opened its doors in our city. The service is very fast and the menu is fairly large. However, the lack of basic services like parking and its location close to the train station as well as music playing too loudly breaks the ambiance and brings to mind fast food restaurants. [\[4.29\]](#ieq4.29)

Subjectivity extraction is a very promising domain from a research point of view, especially from an industrial applications perspective. Making a detailed presentation of all of the applications is far beyond the scope of the present section, so this text will be limited to quickly presenting the vectorial approach (sometimes called categorical) that is one of the most commonly adopted approaches. Very similar to the approach of the same name in information retrieval, the analysis according to this approach occurs in four main steps (see [Figure 4.52](#fig4_52)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_52.jpg)

Figure 4.52. DFD of a categorical system for extracting subjectivities

First, the most characteristic elements in the document are identified. Many terms in a text are not useful for its categorization because they are shared by a large number of texts in diverse categories (see [section 3.1.8](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch03.xhtml#sec33)). Another disadvantage is the computational cost related to processing all of the words in a text, whose numbers can be quite considerable. To overcome these two problems, emotion-processing systems, like information retrieval systems, proceed to a pre-processing phase whose role is to morphosyntactically annotate words, filter non-distinctive words and create a matrix of all significant words in a document (see [section 4.3.2](#sec59) for more details). The reduction in dimensions occurs through latent semantic indexing whose role is to break down the matrix obtained with the Singular Value Decomposition (SVD) process. The WordNetAffect module in turn enriches the simplified matrix with information related to emotions. Finally, the cosine distance is used to calculate the distance between the vector obtained and the emotional vectors.

[^1]: One example of an NLP software developed with an object-oriented architecture is the GATE (General Architecture for Text Engineering) system. Intended to process texts of all forms and sizes, GATE is an open-source software developed by a fairly large community. It was launched in 1994 by the Natural Language Processing Group at the University of Sheffield under the initiative of Yorick Wilks, Rob Gaizauskas and Hamish Cunningham. This system contains a large number of tools including an integrated development tool (GATE Developer) for NLP applications, which is widely used in the domain of information extraction; a collaborative annotation tool (GATE Teamwear) for the semantic annotation of data on an industrial scale and a process for the creation of robust services.

[^2]: The GATE architecture is designed to take over the most important part of the engineering work to allow users to focus on developing their linguistic software. It also includes tools for syntactic analysis, labeling parts of discourse, information retrieval, information extraction, generating finite-state transducers for morphological and superficial syntactic analysis, evaluation and, most recently, interfacing with temporal expression extraction platforms \[DER 16\]. It is also possible to integrate tools used in the domain of automatic learning such as Weka \[EIB 16\] and SVM Lite [](#ch4en4)

[^3]: Utterances similar to [\[4.2b\]](#eq4.2) were judged to be grammatical more frequently than utterances similar to [\[4.2a\]](#eq4.2). The semantic difference between the two utterances seems to be the reason for this difference in judgment, given that it is more probable that a child will be taught than a teacher. The researchers also showed that semantic cues intervene before the end of the utterance or even before a group boundary. Therefore, \[CRA 85\] concluded by considering the garden path as a contextual phenomenon, which can be avoided by knowledge of the context in which the utterance is produced. For example, according to the researchers, utterances such as [\[4.3a\]](#eq4.3) were judged to be ungrammatical because their semantic bias distanced them from the hypothesis of a relative structure and led them to a *garden path*, when they encountered the verb *passed*. This garden path was avoided in utterances similar to [\[4.3b\]](#eq4.3), where the semantic context made it possible to guide the subjects toward a relative structure that was syntactically correct. A similar study to that of Crain and Steedman was conducted by \[TRU 92\] from a discourse analysis perspective. The researchers used utterances with ambiguous verbs (whose form is identical to equivalent past participles) as in [\[4.3\]](#eq4.3):

1. a) The fossil examined…. [\[4.3\]](#ieq4.3)
2. b) The archeologist examined….

In these utterances, the verb *examined* has the same form as the past participle of the same verb. As in \[CRA 85\], the researchers found that semantic knowledge directly influenced the choice of syntactic structure and sometimes led to garden paths.

\[CAR 88\] conducted a study of eye movement during reading. This work showed that the duration of fixation on words that were semantically abnormal to the context was longer than that of equivalent words (in terms of length, frequency and syntactic adaptation compared to the rest of the utterance) that were semantically normal. This shows that the semantic analysis occurs in parallel with the reading process (and therefore with the syntactic analysis). Several experiments aiming to clarify the role of the discursive context in comprehension have been conducted \[SPI 93, BOL 95\]. In his study, \[ALT 99\] described two experiments concerning this problem. In these two experiments, the subjects had to read utterances similar to [\[4.4\]](#eq4.4). These utterances were used in contexts that introduced possible objects. The idea was that after the verb *drank*, the subjects were supposed to think that the utterance did not make sense if the object of the verb was not a drinkable element. After asking the subjects to examine different groups of utterances, he observed that the negative answers (i.e. that the utterance did not make sense) required more time when the anterior context was ambiguous. The author concluded that the semantic roles (agent, patient, recipient, etc.) associated with arguments that are discursively anterior to a verb (arguments located in a prior conversational turn) are selected at the moment of perceiving the verbal head by considering the available roles (i.e. roles that have not yet been associated with a lexical unit), even when the entity that refers explicitly to these antecedents (anaphoric pronouns) is in a post-verbal position and this entity has not yet been processed by the subjects. This shows that the discursive context intervenes in the syntactic analysis of an utterance and that this intervention occurs in parallel with the syntactic analysis, given that its effect is detected before the end of processing the utterance:

He drank some…. [\[4.4\]](#ieq4.4)

The disagreement between the results of these experimental studies can be interpreted in two different ways. On the one hand, it could be the result of methodological or technological issues in the investigation of the considered problems. On the other hand, it could be the reflection of the existence of a variety of strategies whose triggering is produced by specific conditions. This divergence in the cognitive domain has affected the divergence of the architectures of NLP systems that are divided into three main forms: sequential, integrated and parallel \[MAH 95\] (see examples in [Figure 4.6](#fig4_6)). The architectures (a) and (b) in [Figure 4.6](#fig4_6) are relatively simple to explain because they are the direct translation of syntax first or semantics first strategies, respectively. They presuppose the existence of independent knowledge sources and independent processing methods for both syntax and semantics. The interaction between the modules occurs unidirectionally from the source toward the destination. The integrated architectures (c and d in [Figure 4.6](#fig4_6)) in turn start from the premise that there is a unified framework for the representation of syntactic and semantic knowledge as well as for their processing. In practice, the use of modules based on rich formalisms such as HPSG, which integrates morphological, syntactical and semantic knowledge, is an example of an integrated architecture.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_6.jpg)

Figure 4.6. Some software configurations for integrating syntax and semantics ↩

More complex, parallel approaches use independent knowledge sources and processing that occurs on two axes simultaneously. These can be realized in more varied forms than sequential or integrated approaches, as in the four forms, (e), (f), (g) and (h), shown in [Figure 4.6](#fig4_6). The main reason for this divergence is the mode of coordination between the two parallel axes. Some architectures implement a blackboard-based coordination whose role is to coordinate efforts, while others implement an arbitration that attributes a fixed or context-dependent weight to resolve potential conflict between the two knowledge sources. Non-controlled parallel architectures presuppose the adoption of a single generic framework for syntax and semantics that makes direct communication impossible. When the two modules have different theoretical backgrounds, a module to translate formats or convert content is required for all interactions between these two modules.

[^4]: For an NLP specialist, what make Python an attractive language are the data structures such as lists and dictionaries that facilitate the processing of character sequences. External tools developed with Python make it even more attractive, including the NLTK toolbox, which includes morphological, syntactic and semantic analysis tools. Particularly easy to use and well documented, it is used in research as a support for practical works in NLP courses \[BIR 09\] and in the industry. In Python, the availability of other tools and generic libraries related to the domains of artificial intelligence and machine learning that also apply to NLP, for example Orange, Scikit Learn [](#ch4en7), PyBrain [](#ch4en8), PyML [](#ch4en9), LibSvm [](#ch4en10) and Neurolab [](#ch4en11), make this language even more attractive. The major disadvantage of Python is its relative slowness compared to languages like C. As an indication, an informal comparison of the speed of loop processing was conducted between three languages: C (reputedly the most efficient of the high-level languages) with the MinGW compiler (a minimalist version of the GNU compiler for Windows), Python (2.7) and Prolog (Swi-Prolog). Realized on a machine with a Pentium III processor and Windows 2000, the experiment had the following results: the code written in C was 28 times faster than the code written in Python, and Python was, in turn, 10 times faster than the code in Prolog.

[^5]: Today, globalization has made enormous quantities of information accessible, for example, in the form of web documents or texts scanned and transcribed with OCR software, but use of this information sometimes faces a linguistic barrier. New multinational organizations are being added to many existing organizations such as the World Trade Organization (WTO) and the European Union. This need has grown even more with the arrival on the global stage of certain Asian countries whose languages are little-known outside their national borders. It should also be noted that, far from its ideals, MT is an excellent means of technical and industrial spying. Human translation, the natural response to all these needs, suffers from several disadvantages, notably its high cost and the need for a foreign human presence which is not necessarily possible or desirable depending on location (translation of military texts or conversations, for example), the time of day or year or the subject in question. Hence, there is a need for a software system that is capable of taking the input of a text in a source language and producing an equivalent text in a target language. The advantage of these systems compared to human translation is the spatial and temporal availability (a telephone or internet connection is sufficient to access the system when it is deployed in the form of Software As a Service (SaaS)). For a general introduction to machine translation, see \[HUT 92, ARN 94, ACL 16\].

### 4.2.1. Why is translation difficult?

Translation is a very difficult task and, whatever the skill level of the human translator, translation errors are always possible. The constantly changing dynamics of language is a common reason for these errors. In addition, some texts require extra-linguistic knowledge related to the content that the translator does not necessarily have. This contributes to an incomplete or even incorrect understanding of the original text and, consequently, a bad translation.

#### 4.2.1.1. Linguistic divergences

From a lexical point of view, cases of polysemy where a single word can have several different meanings are probably the most important. For example, the verb *know* can be translated as *savoir* or *connaîtr* *e* in French depending on the context (see examples [\[4.6\]](#eq4.6)).

| 1) I know the book you’re talking about. | 3) Je **connais** le livre dont tu parles. |
| --- | --- |
| 2) I know how to go to England. | 4) Je **sais** comment aller en Angleterre. [\[4.6\]](#ieq4.6) |

In addition, certain cases of homonymy can also be a source of problems. For example, the British words *pound* (unit of weight and currency) are impossible to distinguish. Sometimes the context makes it possible to disambiguate the meaning but not always. Similarly, the French word *langue* is one example that linguists know well. This word does not have a direct equivalent in English, which is why English linguists are obliged to borrow the French word for their texts, notably when they are discussing the famous Saussurian distinction of langue/parole. Many words or expressions do not have an equivalent in other languages. For example, the notion of the *weekend* does not exist in the Arab world in the same way as in the Western world. Consequently, there is no clear equivalent in Arabic of the French word *weekend*, which is itself borrowed from English [](#ch4en13). Moreover, the locutions *right away*, *see you soon* and *see you in half an hour* do not have an exact equivalent in Arabic. Obviously, a more or less equivalent expression can always be found; however, as the concept itself is not familiar, this expression will seem unexpected or even bizarre.

Given the syntactic differences, the correspondence between two sentences belonging to two different languages, regardless of their degree of similarity, seems impossible. Word order differs from one language to the next. For example, French and English are languages where the preferred sentence order is Subject Verb Object (SVO), German is a SOV language and Arabic is a VSO language. Similarly, agreement does not have the same form in all languages. In French, for example, the verb agrees with its subject in number but not in gender, unlike Arabic, where the verb agrees in number and gender. Note that there are also particular forms like the subject pronoun that are not given in sentences in Italian (see [\[4.7\]](#eq4.7)):

> Parlo bene l’italiano [\[4.7\]](#ieq4.7)
> 
> I speak Italian well.

The binary in Arabic, a particular form of the plural that, to my knowledge, does not have an equivalent in European languages, is another example of these particular cases.

#### 4.2.1.2. Ambiguities in the source text

Ambiguity is one of the key problems in NLP. Ambiguities concern all linguistic levels from the words to the text. Resolving these ambiguities is not a simple task. Even humans with a good understanding of the context sometimes have difficulties.

#### 4.2.1.3. Errors in the source text

In real applications, notably on the Internet, the level of formality and therefore of grammaticality of texts can vary substantially, which can lead to reduced performance of machine translation which makes manual correction necessary.

### 4.2.2. History of MT systems

#### 4.2.2.1. The early days: (late 1940s–1965)

The beginnings of machine translation go back to the late 1940s, with the work of W. Weaver among others, who proposed using cryptographic decoding techniques to translate texts automatically \[WEA 55\]. In 1952, the first conference on machine translation was held at the Massachusetts Institute of Technology (MIT). This conference occurred in the context of the American–Soviet rivalry during the Cold War. The first prototype called the Georgetown Automatic Translation (GAT) was created at Georgetown University by the team of D. Dorstert and R. McDonald. The hopes elicited by MT systems were quickly diminished. These systems, called the first generation or direct translation, were based on a word-for-word translation model that only made recourse to a dictionary, without using syntactic or semantic representations. Critics of the systems during this period continuously emphasized the errors that these systems produced during the translation of two English proverbs into Russian and back into English, to ridicule MT (see, for example, [\[4.8\]](#eq4.8) for a French adaptation):

| The spirit is willing but the flesh is weak | La vodka est bonne mais la viande est pourrie. [\[4.8\]](#ieq4.8) |
| --- | --- |
|  | *The vodka is good but the meat is rotten*. |
| Out of sight, out of mind | Invisible et fou. |
|  | *Invisible and insane* |

At the same time as the work conducted in the United States, Soviet researchers focused more on theoretical and linguistic subjects. Already at that time, their work considered the possibility of creating a universal formal language that could serve as a bridge between the source language and the target language.

Following the controversy over the performances and use of MT systems, the American government agencies who had funded the research work of about 20 teams in MT created a special commission called the Automatic Language Processing Advisory Committee (ALPAC) in order to evaluate the progress made by the teams in question. Under the direction of John R. Pierce, this committee wrote a report that can be summarized by the following points \[ALP 66\]. First, the mediocre quality of the translation obtained by these systems often required human intervention to obtain a good translation. Next, because microcomputing was non-existent at the time, the development of such systems was particularly expensive. Finally, it seemed necessary to consider the linguistic factors and consequently increase support for computational linguistics. However, it was the negative content that the readers of this report retained and it resulted in a decrease in funding for MT projects and MT research was set on the back burner for several years.

#### 4.2.2.2. The second generation (1965–1975)

During this period, despite the decline in funding, some teams nevertheless managed to continue their work on MT systems, including:

- – the METAL system (University of Texas);
- – the SYSTRAN system;
- – the TAUM system (University of Montreal);
- – the CETA/GETA system in Grenoble directed by Bernard Vauquois.

Most of the systems in this generation adopted an “indirect” approach where intermediary semantic representations independent of language served as a point of passage between the source language and the target language. From an architectural point of view, these systems opted for a strict separation between linguistic resources, notably syntax and semantics on the one hand, and software resources on the other hand. Aiming for better translation than the first-generation systems was also an objective of this generation of systems, which were characterized by these features:

- – The syntactic analysis was gradually enriched by a semantic and even contextual analysis.
- – The domain of application was restricted, for example, to the translation of weather reports, like the TAUM-METEO system from the University of Montreal.
- – The vocabulary and syntactic constructions were relatively small in number and therefore easily catalogued and the risks of ambiguities decreased.
- – The languages covered diversified and expanded beyond the Russian–English pair.

#### 4.2.2.3. Resurgence in interest (1975–1990)

After 1975, there was an increase in the need for translation systems by companies. This resurgence in interest was also supported by the development of new computer and electronic tools, such as programming languages and modeling, and the availability of more powerful computers. The systems developed at this time were mainly the most advanced and most sophisticated second-generation systems. The pace of work on MT accelerated in the early 1980s, as demonstrated by these projects:

- – the PN-TAO project between 1983 and 1987 (France);
- – the EUROTRA project launched by the European Commission in 1982 that covered its nine majority languages;
- – the national Canadian program launched in 1985;
- – the programs of fifth- and sixth-generation systems launched by the University of Kyoto in Japan;
- – the SYSTRAN software was adapted for MS-DOS and ran on the IBM PC in its version with two disk drives, meaning without a hard drive.

With developments in linguistics, notably in syntax, several researchers explored the adoption of new linguistic formalisms based on unification or constraints in machine translation. The advantage of these formalisms was their capacity to incorporate several levels of representation with a single formalism.

#### 4.2.2.4. The recent period

The power of computers made it possible to imagine a different solution: drawing from immense corpora of computerized databases to reuse fragments of already-translated sentences. Notably initiated by IBM, the approach grew in the 2000s with Google, which collects all the translations on the Internet, marking a turning point in the history of MT. This period has also seen the launch of initiatives to create large-scale linguistic resources. It is also distinguished by the creation of collection and distribution centers of resources such as the Linguistic Data Consortium (LDC) (University of Pennsylvania, USA) and the European Language Resource Agency (ELRA) (Paris, France). It has also seen the launch of the first conference dedicated to NLP resources, the Language Resources and Evaluation Conferences (LREC) (see [Chapter 1](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch01.xhtml) of the first volume of this book \[KUR 16\] for more details).

### 4.2.3. Typology of MT systems

The number of languages covered by an MT system is an important criterion when drawing up a typology of MT systems. From this perspective, two types of systems can be distinguished: bilingual systems and multilingual systems. Bilingual systems are divided into two groups: reversible or bidirectional systems, where translation can occur between the source language and the target language and vice versa, and unidirectional systems. The number of languages plays a very important role in the choice of technique to adopt for the translation.

Beyond the purely quantitative aspects, the number of languages concerned by a system affects the software aspects, the approach adopted for the translation. Another criterion for classifying an MT system is the input media. In fact, the input of an MT system can be a scanned text that is transcribed automatically by an OCR software. With the progress with OCR, this task is doable with the current technology except that some transcription errors can occur especially when dealing with a handwritten text. Other types of MT systems are designed to deal with spoken conversations. In this case, they should not only handle speech recognition errors but also the specific phenomena that can occur within spoken language such as extragrammaticality. It should be noted here that prosody is not usually accounted for by MT systems.

Regarding the sharing of tasks between the machine and the human translator, these types can be distinguished: human translation, machine translation assisted by humans and machine translation.

In the case of human translation, all of the translation steps are completed manually. The only possible assistance by machine in this case is the level of formatting of the translation (word-processing software) or the level of access to lexical information (electronic dictionary or translation memories). It is important to note that purely human translation does not preclude the intervention of other human experts during or after the translation. This intervention is sometimes formalized by the addition of the name of the translator and the reviser in the meta-data of the translation.

Moreover, metalinguistic information, sometimes necessary to translate a text well, is also accessible through electronic encyclopedias or on the Internet. In some cases, a translator can use computer resources, which is known as Computer-Assisted Translation (CAT).

Regarding automatic translation assisted by humans, the input text can be modified by a human at three different steps. The first type of intervention can occur before the intervention of the machine, when a translator quickly reads through the text to correct potential spelling or grammar errors. Depending on the system, lexical processing can sometimes be carried out, for instance the replacement of words outside of the system’s vocabulary. A first translation of the text toward a controlled natural language can also be done. In this type of language, the vocabulary and the syntactic constructions are limited in advance to control the ambiguities. The second type of intervention occurs during translation by the machine. Some MT software interacts with the user through dialogue to resolve certain ambiguities that the software could not resolve on its own. Requiring an alert user, this process becomes cumbersome when the text contains many ambiguities because the translation time increases considerably. Finally, the third type of intervention occurs after the machine intervention in post-processing to correct errors or improve style. Some MT software produce several alternative translations in cases of structural or semantic ambiguities, giving the translator the responsibility of choosing which one should be retained during this last step.

Machine Translation itself is an entirely automated process where the machine carries out all steps of the translation without any external intervention.

### 4.2.4. The use of MT

From a functional point of view, J. Carbonell established the distinction between two processes: assimilation and dissemination (see [Figure 4.9](#fig4_9)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_9.jpg)

Figure 4.9. Functional typology of MT systems according to Carbonell

Assimilation consists of formulating a synthesis of what is written about a subject like a political, economic or sporting event in different languages ([Figure 4.10](#fig4_10)) from a set of documents that often come from a collection on the Internet. Given the wide variety of topics that can be addressed, this cannot involve high-level knowledge, notably semantic and pragmatic knowledge, in the translation system. Consequently, it is expected that the quality of the translation will require human post-editing.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_10.jpg)

Figure 4.10. General diagram of the assimilation process

Dissemination, on the other hand, occurs from a given language toward several languages (see diagram in [Figure 4.11](#fig4_11)). A typical example of this process is the translation of product catalogues intended to be exported. In general, this consists of translations that concern a limited domain. This makes it possible to carry out deep linguistic analyses and therefore allows for a better-quality translation that requires little or no post-editing.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_11.jpg)

Figure 4.11. General diagram of the dissemination process

The translation of literary works, especially poetry, is distinguished from the two abovementioned types by the fact that the form and poetic function must be transposed. This type of translation requires very advanced skill in the target language. Generally, translators of this kind of literature are themselves bilingual authors or poets. In some cases, the translation is done by two people: a translator provides a translation of the meaning into the target language and an editor reformulates it in the target language in an appropriate literary style. For example, the most famous Arabic translation of *Paul et Virginie [](#ch4en14)* by Bernardin de Saint-Pierre was formulated by Egyptian author Mustapha-Lutfi al-Manfalouti, who did not speak French. An MT software can thus be used to obtain drafts whose final formulation will be done by a professional in the target language without necessarily needing to have perfect mastery of the source language.

### 4.2.5. MT techniques

It is possible to carry out a translation using several levels of linguistic knowledge. The more diverse the knowledge, the better the quality of the translation, but the more complex the development process. To represent this diversity of systems, Bernard Vauquois proposed the triangle given in [Figure 4.12](#fig4_12) \[VAU 68\].

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_12.jpg)

Figure 4.12. The Vauquois triangle with some modifications \[VAU 68\]

Four different approaches can be distinguished from the triangle: the direct approach, the transfer approach (syntactic and semantic) and the pivot approach.

#### 4.2.5.1. Direct approach

Adopted by the majority of the first-generation systems, the direct approach is the most intuitive and the simplest. The translation process consists of finding an equivalent in the target language for each word in the source sentence to form the target sentence (see [Figure 4.13](#fig4_13)). First of all, a superficial morphological analysis phase makes it possible to find the basic forms of words: lemmas. They are then used to find an equivalent in the target language with a bilingual dictionary, without any consideration for syntax or semantics. Finally, some local rules make it possible to order the words obtained, for example, by moving the adjectives or prepositions.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_13.jpg)

Figure 4.13. Architecture of a system using the direct approach

Because it does not consider the context, this approach comes up against all kinds of ambiguities. Moreover, the local rules for re-ordering are not sufficient and sentences obtained in the target language are often not correctly formulated.

#### 4.2.5.2. Transfer approach

These systems are less ambitious than the pivot systems, because they provide two distinct representations *R* and *R’* whose level of abstraction is lower than the pivot language (see [Figure 4.14](#fig4_14)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_14.jpg)

Figure 4.14. Architecture of the transfer approach. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

The targeted representations are often syntactic–semantic constructions of sentences instantiated by words in the language. They are therefore concrete linguistic representations rather than abstract conceptual representations. The transfer module has the goal of transforming the representation of the input text in the source language into an equivalent representation that serves as a point of departure for a translation into the target language. A special module is necessary for each language pair as shown in [Figure 4.15](#fig4_15).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_15.jpg)

Figure 4.15. Architecture of a transfer-based system with three languages

Many translation systems have adopted this easily implemented approach. The complexity of the system increases considerably with an increase in the number of languages. For example, for *n* languages, we need *n* analysis modules and *n* generation modules as well as n \* (*n−1*) transfer modules. This adds up to a total of n \* (*n+1*) modules in the system. For example, for a value of *n* equal to 3, there is a total of 12 modules. For *n* equals 6, the total number of modules is 42, 30 of which are transfer modules.

The syntactic transfer is a particular form of this approach. It consists of connecting two surface syntax structures, one in each language. Three main steps are necessary to realize a translation system in this case. First, the syntactic analysis tree of the input sentence is constructed. Then, the constituents are rearranged. Finally, the words are translated and the tree of the sentence is constructed in the target language. In the example in [Figure 4.16](#fig4_16), the syntactic parsing of the input group is shown. The syntactic transfer is a rearrangement of the elements in the sentence.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_16.jpg)

Figure 4.16. An example of a syntactic transfer

In reality, it is not always this simple. Often, the translation results in deeper changes. For example, the subject becomes the object, or vice versa. Consider the following pair: *You(subject) like \[the house\](object), \[La maison\](subject) te(object) plaît*. The subject of the sentence in French becomes the object of the sentence in English, as shown in [Figure 4.17](#fig4_17).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_17.jpg)

Figure 4.17. Syntactic transfer with order inversion

The introduction of syntactic knowledge resolves issues with the order, but the semantics of the translations obtained are often inappropriate, in particular because the formulation of fixed expressions from one language to another can pose problems for this kind of translation.

Semantic transfer approaches consider the translation as a relation between two semantic representations of the input sentence and the output sentence, respectively. Several semantic formalisms have been used such as the QLF (quasi-logical form), based on predicate logic. To make the syntax–semantics interaction more explicit within the LTAG formalism, \[SHI 90\] proposed parallelizing the syntactical structure, represented by elementary trees, and an argument predicate structure that serves as a semantic interpretation skeleton for the elementary tree with which it is associated. The semantic representation also has the form of a tree structure. Thus, at least one semantic tree is associated to each elementary tree and the links are defined between the nodes of the two trees that restrict the possible derivations. The main innovation of this formalism is that the syntactic and semantic derivations must be synchronized. Thus, the derivation of two trees < *α <sub>1</sub>*, *α <sub>2</sub>* > follows these steps:

1. 1) In a non-deterministic way, choose a link between two nodes (*n <sub>1</sub>* to *α <sub>1</sub>* and *n <sub>2</sub>* to *α <sub>2</sub>*).
2. 2) In a non-deterministic way, choose a pair of trees < *β <sub>1</sub>*, *β <sub>2</sub>* > of the grammar.
3. 3) Create the pair < *β <sub>1</sub>* < *α <sub>1</sub>*, *n <sub>1</sub>* >, *β <sub>2</sub>* < *α <sub>2</sub>*, *n <sub>2</sub>* >> where *β* < *α*, *n>* is the result of a primitive relation on *α* at node *n* using *β*.
![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_18.jpg)

Figure 4.18. Example of a synchronized syntactic tree and semantic tree

Machine translation is the most common application of this formalism. The basic principle of these applications is to use the transfer rules from one language to another. For each derivation tree in the source language, a corresponding derivation tree is constructed in the target language. This is done by establishing a link between each node on both sides and by preserving the relations of dominance between the nodes in the source derivation tree. The transfer diagram is presented in [Figure 4.19](#fig4_19). A modified version of this formalism has been proposed for the automatic translation of speech \[CAV 98\].

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_19.jpg)

Figure 4.19. Diagram of a simple transfer \[PRI 94\]

From an engineering perspective, transfer-based approaches are not an elegant way to carry out translation. As shown, there are many modules for each language pair. Despite this design problem, this approach remains a fast way to construct translation systems. The transfer-based approach closely resembles the pivot-based approach if attempting to obtain deep linguistic representations.

#### 4.2.5.3. The pivot or interlingua approach

In 1629, René Descartes proposed this approach using mathematics as a universal language. It was this very principle that was taken up in the second half of the last century as a solution to machine translation problems. In the interlingua approach, processing occurs in two steps, as shown in [Figure 4.20](#fig4_20):

- – *An analysis module* that produces a representation of the input text in the source language in a pivot language (designed to be independent of all language).
- – *A generation module* that generates a well-formed sequence of words from the semantic representations obtained in the pivot language. An automatic translation system involves practically all components of linguistic knowledge: morphological analysis, syntactic analysis and semantic analysis.
![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_20.jpg)

Figure 4.20. Architecture of pivot-based systems

Contrary to semantic transfer approaches, pivot-based analysis also involves pragmatic knowledge that allows for a better consideration of the context. However, this depth also has a cost, which is the requirement of analysis at several levels. On the one hand, this weighs down the development process considerably (requires more work). On the other, in terms of processing, this increases the translation time, which is crucial for some applications (especially in speech translation, where the translation must be instantaneous). An example of a pivot from the European project NESPOLE is given in [Figure 4.21](#fig4_21).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_21.jpg)

Figure 4.21. Example of a pivot in the domain of the translation of hotel reservations

Adopted in several machine translation systems (ARIANE by GETA, 1961–1971 and CSTAR, 2000s), this approach appeals to researchers for several reasons. On the one hand, it is ideal for typologically distant language pairs like (French–Arabic) and (English–Chinese). On the other hand, it stands out for its economy because the pivot can be developed once for all (regardless of the languages pairs intended). Finally, from a theoretical point of view, it relies on the idea, which is not unanimously agreed upon in linguistics, of the existence of language universals.

Imperfect, pivot translation suffers from limits that are known in the literature. It requires deep analyses that are difficult to implement such as the consideration of global textual phenomena, including inter-sentential phenomena. The multiplication of modules increases the sources of errors that can spread from one module to another. For example, a morphological analysis error causes a syntactic analysis error, which in turn leads to a semantic interpretation error. Due to the complexity of implementation, pivot translation is practically only used in closed domains like the translation of tourism texts like the CSTAR, VERBMOBIL and NESPOLE projects.

#### 4.2.5.4. Example-based translation (EBT)

The use of search engines by human translators to find the translation of an unknown expression is a common practice today. For example, to find the English equivalent of the expression *fait pour servir et valoir ce que de droit* [](#ch4en15), an Internet search of some French sites can lead to the correct response. Sometimes, however, the search results in a variety of possible translations with different meanings. To transform this empirical process into an efficient algorithm, a parallel corpus should be used in practice. In this kind of corpus, the sentences are associated with their translations considered in their original context. These sentences are preferred to minimal pairs, that is, sentences where one element is changed at a time (see sentences [\[4.9\]](#eq4.9)):

| How much is that **big watch**? | Combien coute **cette grosse montre**? [\[4.9\]](#ieq4.9) |
| --- | --- |
| How much is **that yellow bike**? | Combien coute **ce vélo jaune**? |

Example-based translation was first proposed by the Japanese \[NAG 84\]. Particularly appropriate for representing the context, this approach is well equipped to resolve ambiguities because verbal groups are particularly dependent on context by nature. It generally consists of a verb potentially followed by an adverb or a nominal or prepositional group, or sometimes both. The different forms that the arguments of the verb can take considerably affect its meaning and are sources of ambiguities, for example, the verb *ask* whose meaning changes significantly depending on the nature of its arguments. In general, most of the example-based translation approaches follow these steps:

- – Matching: searching for fragments of the input sentence in the corpus.
- – Alignment: identification of corresponding translations in the corpus. This step has the most variety between the EBT approaches. It can consist of the alignment of pairs of character strings or pairs of more complex forms: syntactic trees with context-independent grammar or formalisms like LFG and LTAG.
- – Recombination: this consists of the assembly of the fragments into a correct sentence in the target language.

From the point of view of performance, example-based systems give satisfactory results when the data used are well aligned and have good coverage of phenomena that are likely to be encountered in the target language, which is difficult to obtain except where it concerns limited applicative domains. That is why this approach is not used by commercial systems that prefer statistical approaches whose results are more easily controlled and are therefore better suited for their needs. However, EBT remains a promising domain and many teams of researchers are working on possible improvements.

#### 4.2.5.5. Statistical approach

Like the example-based approach, this approach is based on prior experiences through a parallel corpus. The basic principle of statistical translation is the following [](#ch4en16): suppose that there is a sentence in French *f* that we want to translate into Arabic to obtain sentence *a*. Depending on the translators, we can obtain different formulations that are more or less equivalent for *a*. The question is then to choose the best one of these forms. One possible response to this question is provided by probabilities. We can calculate the probabilities of possible translations pr(a|f) knowing the sentence *f* and selecting the more probable one. These probabilities are calculated starting from a parallel corpus. Of course, the quality of the translation model will directly depend on the quality of translations present in the base corpus. To infer probabilities from the base corpus, the Bayes formula is traditionally used ([equation \[4.10\]](#eq4.10)):

[\[4.10\]](#ieq4.10) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_2.jpg)

We can ignore the probability of the input sentence *p* (*f*) because it is shared by all of the translations. Thus, finding a better translation comes down to finding the value of *a* that will maximize *p* (*f* | *a*) *p* (*a*).

The idea of statistical MT is closely linked to the alignment of units of translation in the source language and the target language. These units can concern the sentence, the group or the word. To do this, several models have been proposed by IBM (see \[KNI 99, LOP 08\] for an overview). Finally, note that since 2006 statistical translation has had its own annual international workshop [](#ch4en17).

### 4.2.6. Example of a translation system: Verbmobil

The German project Verbmobil is, to my knowledge, the largest project ever realized in the world on the translation of speech in real time. As indicated by its name, this project is intended to process spoken conversations through mobile telephones \[WAH 00b\]. The main objective of the system constructed over the course of this project is the automatic translation of speech, but automatic dialogue summary functions have been added as well, for example, to generate a general reminder of what the two interlocutors have said during their negotiation and thereby validate the information exchanged in the dialogue.

Processing these dialogues occurs in an entirely centralized way in the main server of the system. As [Figure 4.22](#fig4_22) shows, the first locutor emits his utterance via his mobile phone. The signal emitted is then transmitted by satellite to the central server that carries out the automatic translation and produces a synthesized utterance in the target language that corresponds to the utterance received. Finally, the synthesized utterance is transmitted via the satellite to the addressee’s mobile phone. Users only need a mobile phone to use this translation service in this model that is known as Software As a Service (SAS).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_22.jpg)

Figure 4.22. Diagram of a mediated dialogue in Verbmobil \[WAH 00a\]

One of the specificities of Verbmobil is the parallelization of different modules that have the same function and merging the results to combine their advantages without their disadvantages.

The following paragraphs will present the main components of Verbmobil that are relevant to this book. [Figure 4.23](#fig4_23) presents the system interface as well as its main functionalities, but it does not provide its real architecture, which is much more complex. The final version of Verbmobil contains 69 modules, each of which interacts with at least one other module. Given the parallel processing approach and the constraints of real-time processing, the communication requirements between the different modules are enormous from the point of view of the quantity of information. Given the non-sequential aspect of Verbmobil, this implies that the modules exchange not only the input and the output of each module but also the attempts of the high-level modules to synchronize the flow of information, constraints, alternatives, confidence scores, probabilities, etc.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_23.jpg)

Figure 4.23. The interface of the Verbmobil system \[WAH 00a\]. For a color version of this figure, see www.iste.co.uk/kurdi/language2.zip

To meet these requirements, a multi-blackboard architecture has been implemented. This architecture contains three different types of components \[KLÜ 00\]. There is a set of independent modules called knowledge sources. These modules are the main element of the Verbmobil system. Unlike most blackboard-based architectures, Verbmobil uses a series of boards which are each used to represent the intermediary results of each step of the processing. Finally, there is a control module whose function is to allocate resources to optimize the runtime and module sequencing. The adoption of a central blackboard-based architecture makes it possible to add or remove modules without significant repercussions in the other modules. For example, two recognition modules for German are used to process multi-lateral conversations involving two Germans. Despite its complexity, this architecture has proven to be more effective and more appropriate than a multi-agent architecture that was used in the first phase of the project. Concerning the syntactic analysis, the system adopts a multi-engine approach to guarantee robustness. Thus, three syntactic parsers have been used in the processing: a stochastic LR parser, a chunker and a HPSG-based deep parser.

The stochastic LR parser adopts an incremental approach \[RUL 00\]. It was inspired, among others, by the works of Ted Brisoe at the University of Cambridge on LR parsers and their extension for processing unification-based grammars. The choice of the LR algorithm was essentially motivated by its efficiency and its adaptation for processing the word trellis in the graph provided by the recognition system. To improve the analysis quality, this module uses a post-processing phase with tree transformation rules. These rules are learned automatically from a corpus with the transformation-based learning method \[BRI 93\].

Based on the CASS system developed by Steven Abney, the partial parser uses memory-based learning techniques (see \[DAE 05\] for an introduction). In order to satisfy the constraints imposed by Verbmobil, this parser adopted an incremental approach \[HIN 00\]. Particular attention was paid to the assembly of segments, a subject that is addressed relatively rarely in the context of partial parsing approaches. The objective was to facilitate the task of the semantic analysis module as much as possible and consequently obtain a better-quality analysis. Compared to other approaches, the evaluation showed that this approach produced better analysis results in terms of robustness but with the shallowest analysis.

A deep syntactic parser based on the HPSG formalism, this parser was realized in the context of a collaboration between the DFKI at Saarbrücken, the CSLI at Stanford and the Language Processing Lab at the University of Tokyo \[USZ 00\]. One of the main problems faced by this parser was the reduction in necessary runtime. The features used to represent the linguistic constraints in the framework of the HPSG formalism require many calculations that make the parser’s runtime too slow to be integrated in the framework of a real-time application. Two solutions have been combined to solve this problem: 1) elimination of features that are not central to the processing as well as disjunctive features that increase the complexity of the processing, and 2) the testing of several types of implementation like, among others, the grammar approximation of finite-state automata. Finally, this problem was overcome by researchers in the Computational Linguistics department at the University of Saarbrücken, who combined several solutions proposed by different participants and managed to satisfy the analysis time constraints, which are about 0.45 s for a 10-word utterance. As expected, the evaluation results showed that this system, compared to the two others, provides the deepest analysis but the least robust analysis of problems of recognition or extra-grammaticalities of speech (see \[MÜL 00, FLI 00, SIE 00\] for the final results of this parser on German, English and Japanese, respectively).

The three parsers process the same graph of words enriched with prosodic annotations produced by the recognition system. The three parsers are also guided by an A\* algorithm to choose the most likely paths from a speech recognition perspective \[ULR 00\]. The three parsers use a specific analysis module to construct a semantic representation corresponding to the output of each one. This applies to complete parses as well as partial ones. The data exchanged between the different modules are represented in the Verbmobil Interface Terms (VIT) format, which is, as the name indicates, a special format intended to standardize the output of the parsers. The conversion of the output of the parsers into a standardized semantic representation makes if possible to carry out the post-processing operations intended to select the best analysis from the candidates \[RUP 00\].

As with the ALPAC report, the difficulty of the semantic approach has been known since the 1960s. Thirty years later, the statistical method has tentatively given the impression of solving the problem; however, after the leap forward that it has allowed, specialists in machine translation are now faced with the same difficulty, because although enormous progress has been made in a relatively short amount of time, the expectations of users have also progressed with the technology.

[^6]: In addition, certain cases of homonymy can also be a source of problems. For example, the British words *pound* (unit of weight and currency) are impossible to distinguish. Sometimes the context makes it possible to disambiguate the meaning but not always. Similarly, the French word *langue* is one example that linguists know well. This word does not have a direct equivalent in English, which is why English linguists are obliged to borrow the French word for their texts, notably when they are discussing the famous Saussurian distinction of langue/parole. Many words or expressions do not have an equivalent in other languages. For example, the notion of the *weekend* does not exist in the Arab world in the same way as in the Western world. Consequently, there is no clear equivalent in Arabic of the French word *weekend*, which is itself borrowed from English. Moreover, the locutions *right away*, *see you soon* and *see you in half an hour* do not have an exact equivalent in Arabic. Obviously, a more or less equivalent expression can always be found; however, as the concept itself is not familiar, this expression will seem unexpected or even bizarre.

Given the syntactic differences, the correspondence between two sentences belonging to two different languages, regardless of their degree of similarity, seems impossible. Word order differs from one language to the next. For example, French and English are languages where the preferred sentence order is Subject Verb Object (SVO), German is a SOV language and Arabic is a VSO language. Similarly, agreement does not have the same form in all languages. In French, for example, the verb agrees with its subject in number but not in gender, unlike Arabic, where the verb agrees in number and gender. Note that there are also particular forms like the subject pronoun that are not given in sentences in Italian (see [\[4.7\]](#eq4.7)):

> Parlo bene l’italiano [\[4.7\]](#ieq4.7)
> 
> I speak Italian well.

The binary in Arabic, a particular form of the plural that, to my knowledge, does not have an equivalent in European languages, is another example of these particular cases.

[^7]: The translation of literary works, especially poetry, is distinguished from the two abovementioned types by the fact that the form and poetic function must be transposed. This type of translation requires very advanced skill in the target language. Generally, translators of this kind of literature are themselves bilingual authors or poets. In some cases, the translation is done by two people: a translator provides a translation of the meaning into the target language and an editor reformulates it in the target language in an appropriate literary style. For example, the most famous Arabic translation of *Paul et Virginie* by Bernardin de Saint-Pierre was formulated by Egyptian author Mustapha-Lutfi al-Manfalouti, who did not speak French. An MT software can thus be used to obtain drafts whose final formulation will be done by a professional in the target language without necessarily needing to have perfect mastery of the source language.

[^8]: The use of search engines by human translators to find the translation of an unknown expression is a common practice today. For example, to find the English equivalent of the expression *fait pour servir et valoir ce que de droit*, an Internet search of some French sites can lead to the correct response. Sometimes, however, the search results in a variety of possible translations with different meanings. To transform this empirical process into an efficient algorithm, a parallel corpus should be used in practice. In this kind of corpus, the sentences are associated with their translations considered in their original context. These sentences are preferred to minimal pairs, that is, sentences where one element is changed at a time (see sentences [\[4.9\]](#eq4.9)):

| How much is that **big watch**? | Combien coute **cette grosse montre**? [\[4.9\]](#ieq4.9) |
| --- | --- |
| How much is **that yellow bike**? | Combien coute **ce vélo jaune**? |

Example-based translation was first proposed by the Japanese \[NAG 84\]. Particularly appropriate for representing the context, this approach is well equipped to resolve ambiguities because verbal groups are particularly dependent on context by nature. It generally consists of a verb potentially followed by an adverb or a nominal or prepositional group, or sometimes both. The different forms that the arguments of the verb can take considerably affect its meaning and are sources of ambiguities, for example, the verb *ask* whose meaning changes significantly depending on the nature of its arguments. In general, most of the example-based translation approaches follow these steps:

- – Matching: searching for fragments of the input sentence in the corpus.
- – Alignment: identification of corresponding translations in the corpus. This step has the most variety between the EBT approaches. It can consist of the alignment of pairs of character strings or pairs of more complex forms: syntactic trees with context-independent grammar or formalisms like LFG and LTAG.
- – Recombination: this consists of the assembly of the fragments into a correct sentence in the target language.

From the point of view of performance, example-based systems give satisfactory results when the data used are well aligned and have good coverage of phenomena that are likely to be encountered in the target language, which is difficult to obtain except where it concerns limited applicative domains. That is why this approach is not used by commercial systems that prefer statistical approaches whose results are more easily controlled and are therefore better suited for their needs. However, EBT remains a promising domain and many teams of researchers are working on possible improvements.

[^9]: Like the example-based approach, this approach is based on prior experiences through a parallel corpus. The basic principle of statistical translation is the following: suppose that there is a sentence in French *f* that we want to translate into Arabic to obtain sentence *a*. Depending on the translators, we can obtain different formulations that are more or less equivalent for *a*. The question is then to choose the best one of these forms. One possible response to this question is provided by probabilities. We can calculate the probabilities of possible translations pr(a|f) knowing the sentence *f* and selecting the more probable one. These probabilities are calculated starting from a parallel corpus. Of course, the quality of the translation model will directly depend on the quality of translations present in the base corpus. To infer probabilities from the base corpus, the Bayes formula is traditionally used ([equation \[4.10\]](#eq4.10)):

[\[4.10\]](#ieq4.10) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_2.jpg)

We can ignore the probability of the input sentence *p* (*f*) because it is shared by all of the translations. Thus, finding a better translation comes down to finding the value of *a* that will maximize *p* (*f* | *a*) *p* (*a*).

[^10]: The idea of statistical MT is closely linked to the alignment of units of translation in the source language and the target language. These units can concern the sentence, the group or the word. To do this, several models have been proposed by IBM (see \[KNI 99, LOP 08\] for an overview). Finally, note that since 2006 statistical translation has had its own annual international workshop

[^11]: However, as Big Data is a new form of input, it entailed changes to data-processing strategies. The abundance of data facilitated the use of statistical or, more generally, machine learning algorithms. In addition, this same abundance required the use of unsupervised or lightly supervised learning algorithms in order to reduce efforts related to annotating the data that are necessary for supervised learning approaches. This involves adapting these algorithms, which were initially designed to process thousands of cases, to process millions of cases. The parallelization required by environments constructed on Hadoop, even for high-level environments like the ESB (Enterprise Service Bus) TALEND that offer an integrated graphic programming interface from the base code (java, Spark) to the project management, requires revising the design of NLP algorithms to adapt them to the MapReduce model.

Moreover, because the data is distributed in clouds, this requires adopting new strategies to process them. The distribution of data on different servers can also be accompanied by a topical distribution. For example, the data in one particular server can pertain only or mainly to the medical domain, while the data in other servers may concern biology or the environment. This requires algorithms that are capable of extracting general principles independent of the task while being able to merge the parameters related to the applicative domains distributed over different servers.

[^12]: As shown in [Figure 4.40](#fig4_40), the main difference between an information extraction system and a question answering system is the existence of two analysis and generation modules that are capable of processing open questions produced by users and generating responses in natural language, respectively. It should be noted that, in order to facilitate the comparison, in the case shown, the analysis and generation modules use schema-based semantic representation; however, in reality, other forms of semantic representations are also possible, such as representations based on different types of logic (modal logic, fuzzy logic [](#ch4en20), etc.) (see [section 2.2.2](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch02.xhtml#sec22)) or even word embeddings on a large scale (see \[MIK 13\]).

#### 4.4.4.1. Extraction of named entities (NEs)

The extraction of NEs consists of identifying and classifying proper nouns in pre-defined categories based on the needs of a given application. Typically, three basic categories are used: person, place and organization. In addition to these three large categories, sometimes emails, temporal expressions, measurement expressions like monetary amounts, distances or weight, bibliographic references, etc. are added. Without needing to create connections between the identified entities, entity extraction can be used as a module in a larger information extraction system. As demonstrated with the Prolex proper noun database presentation, proper nouns are an important part of a text, especially in journalistic and scientific domains, where they account for about 10% of words according to some studies. For an overview of works related to this question, see \[NAD 07\].

The extraction of NEs seems to be a simple task at first glance, but in practice there are many rhetorical phenomena, including notably metonymy, that make identifying them problematic. As an example, consider the set of sentences [\[4.18\]](#eq4.18) (for more details, see the section on metonymy in [Chapter 2](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch02.xhtml)).

| Team vs. country | France won the World Cup. |
| --- | --- |
|  | The World Cup was organized in France. |
| Location vs. authority | The President of France officially resides at the Elysée. |
|  | The Elysée declared that elections would not take place next month. |
| Company vs. product | He drinks Coca Cola every morning, he’s crazy! |
|  | Coca Cola just launched a new advertising campaign. [\[4.18\]](#ieq4.18) |

According to the approach of Message Understanding Conference (MUC) evaluation campaigns, it could be considered that *France* is always a place but this does not seem to be an ideal solution. At the same time, it is not always possible to count on general ontological knowledge in order to distinguish the different uses of a term. The simplest method of processing NEs consists of using an appropriate dictionary like Prolex. Despite its speed and simplicity, this approach suffers from a major inconvenience, which is the updating required for the dictionary to reflect the current changes that, naturally, have an impact on the proper noun dictionaries in a much more substantial way than on ordinary dictionaries. Moreover, such a dictionary is not sufficient to resolve ambiguity, because its resolution requires using contextual information. Another approach consists of using regular expressions to consider internal and external indicators. Internal indicators are morphemes, which are part of the proper noun, but through their semantic nature, they indicate a location. Common examples of internal indicators are lake, river, airport, city, street and boulevard. This makes it possible to predict the role of the rest of the sequence like in the segments in italics in sentences [\[4.19\]](#eq4.19):

1. a) John lives on *Lexington Avenue*.
2. b) The *Saint Louis Lambert Airport* is one of the prettiest airports in the US. [\[4.19\]](#ieq4.19)
3. c) The *Riverside Park* is located along *Hudson river*.
4. d) The *city of Knoxville* is located in the *south of the US*.

External indicators are not part of the noun properly speaking but rather part of the cotext. They indicate that an NE will follow. As an example, consider the following indicators: in the south of, in the north of, beside and very close to.

Pattern-based methods, despite their simplicity, are very limited and do not make it possible to resolve many cases of ambiguity (e.g. John F. Kennedy, the airport or the person). This pushed researchers to adopt learning-based approaches like HMMs \[BIK 97, BOU 02\], SVM \[TJO 03\], naive, semi-supervised \[PAS 08\] or unsupervised \[NAD 06\] Bayesian networks.

As an example, consider the KnowItAll system developed by Oren Etzioni and his collaborators at the University of Washington \[ETZ 05\]. This system uses an unsupervised approach that is based on a three-step processing (see [Figure 4.41](#fig4_41)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_41.jpg)

Figure 4.41. DFD of KnowItAll

First, the system proceeds to the start-up phase that consists of providing a set of predicates that represent classes of entities like movieActor, city and brand of car. Each of these predicates is associated with a set of labels that are the surface forms that can take an entity in an utterance. For example, consider the predicates for the domains of geography and films given in [Figure 4.42](#fig4_42).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_42.jpg)

Figure 4.42. Examples of predicates in the domains of geography and films

Inspired by a Hearst pattern-based approach, the second step consists of labeling using eight generic patterns to produce candidates. The labels identified in the start-up step can serve to instantiate patterns with the appropriate classes. As an example, consider sentence [\[4.20\]](#eq4.20). In this sentence, the word city serves to indicate the class of entities that follow. Using the pattern “NP such as ListNP”, we can analyze sentence [\[4.20\]](#eq4.20) and propose four candidates for the class of city: Richmond, Charlottesville, Lynchburg and Roanoke.

> Our buses stop at cities like Richmond, Charlottesville, Lynchburg and Roanoke. [\[4.20\]](#ieq4.20)

Based on the Pointwise Mutual Information (PMI) algorithm developed by David Turney \[TUR 01\], the system then tests the plausibility of each hypothesis using the Web as a corpus. Thus, the system uses a search engine to bring up pages that contain entities that it intends to verify. For example, to verify that Lynchburg is the name of a city, the system seeks to verify that there is a mutual information (PMI) between Lynchburg and discriminating sequences (or discriminators) that indicate that it really is a city, such as: -is a city, the city of-, etc. Formally, the PMI score is calculated using [equation \[4.21\]](#eq4.21):

[\[4.21\]](#ieq4.21)

The PMI score is the number of results for a query that combines the discriminator D and the instance I divided by the number of results for the instance itself. To transform PMI scores into a co-occurrence probability, the system takes a set of *k* positive cases and *k* negative cases for each class and defines the threshold that serves to divide all of the cases. Then, another set of *k* positive cases and *k* negative cases is used to estimate the following probabilities:

| P(PMI > threshold \| class), | P(PMI ≤ threshold \| class), |
| --- | --- |
| P(PMI > threshold \| ¬class), | P(PMI ≤ threshold \| ¬class), |

It should be noted that in the experiments described, the value of *k* is equal to 10. The probabilities obtained are then used as input features for a naive Bayesian classifier according to [equation \[4.22\]](#eq4.22), which shows the probability of a fact given the features t <sub>1</sub>, t <sub>2</sub>, ……t <sub>n</sub>:

[\[4.22\]](#ieq4.22) ![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_10.jpg)

As emphasized in \[ETZ 05\], the use of PMIs presents problems that merit further reflection, like rare data for some cases, even with the Web as a corpus, and the case of homonyms.

#### 4.4.4.2. Extraction of relations

The relations between the entities in a text can be useful for many applications. For example, in a bibliographic information extraction application, it is essential to associate the articles with their authors and institutions. In medical applications, it is possible to extract relations between the genes that cause certain illnesses \[CHU 06\]. The extraction of relations can have the goal of the automatic construction of ontologies \[WON 09\].

The task of extracting relations can be described as the construction, from raw texts, of predicates, whose diagram is: relation (e <sub>1</sub>, e <sub>2</sub>, …e <sub>n</sub>), where *e* represents an entity cited in the text. Here are a few examples:

| Emmanuel Macron is the president of France. | president (Emmanuel Macron, France) |
| --- | --- |
| Ouagadougou is the capital of the African Republic of Burkina Faso. | capital (Ouagadougou, Burkina) |
| The discus is a very pretty fish that lives in the Amazon. | lives (discus, Amazon) |
| Nadine is the mother of Celine and Amandine. | mother (Nadine, Celine, Amandine) |

The simplest approaches are based on pattern recognition. \[HEA 92\] proposed five patterns to extract hyponyms (see [Table 4.9](#tab4_9)).

**[Table 4.9](#itab4_9).** *Hearst’s extraction patterns for hyponyms*

| **Patterns** | **Examples** |
| --- | --- |
| Y such as X <sub>1</sub>, X <sub>2</sub>,..., X <sub>n</sub> | A sports car like a Ferrari, Bugatti or Porsche. |
| X <sub>1</sub>, X <sub>2</sub>,..., X <sub>n</sub> and/or/among others Y | Car, train, plane among other modes of transportation |
| Y, including X <sub>1</sub>, X <sub>2</sub>, …, X <sub>n</sub> | Combat sports, including karate, judo and boxing |
| Y, in particular X <sub>1</sub>, X <sub>2</sub>, …, X <sub>n</sub> | Planes, in particular the F22 and F35. |
| Some Y such as X <sub>1</sub>, X <sub>2</sub>, …, X <sub>n</sub> | Programmers like John, Patrick and Will |

The idea behind supervised approaches is to manually annotate a corpus and automatically extract patterns and rules. The general diagram of this process is shown in [Figure 4.43](#fig4_43).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_43.jpg)

Figure 4.43. Induction of rules from examples

To make the process of writing rules less demanding, it is possible to start by annotating a certain number of cases manually in order to start the system of automatic rule induction. The system obtained can then be used to annotate new cases. The idea is to define a confidence threshold in order to select only cases annotated by the system whose confidence score is greater than the threshold. Over the course of the system’s development, its performance improves and the percentage of cases annotated with an acceptable score increases until a maximum is reached (a plateau on the performance curve), where the system’s performance stagnates even after the addition of new learning cases.

In the literature, two learning-based approaches are opposed (see \[BAC 07\] for an overview): feature methods and kernel methods \[LOD 02\]. In feature-based approaches, an input sequence analysis is used to attempt to identify the disposition patterns of the entities that are found in this sequence (see, for example, \[KAM 04\]), for example, the number of words that separate two entities and the types of entities (person, place or institution). Some approaches go further by using dependency trees for a sentence. For example, to extract relations from the sentence *John invented a new steam engine in his garage*, we can use a decision tree like the one in [Figure 4.44](#fig4_44).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_44.jpg)

Figure 4.44. Dependency tree to extract relations

In general, a set of features is the result of a process of trial and error. More formally, a sentence *S* with *n* entities and *k* words is presented in this way: *P* = *w <sub>1</sub>, w <sub>2</sub>, e <sub>1</sub>, w <sub>i</sub>, e <sub>2</sub>,..., w <sub>l</sub>, …, e <sub>n</sub>, …, w <sub>k-1</sub>, w <sub>k</sub>*, where *k* > *n* ≥ *i*. The sentence thus represented is analyzed by a classification function *f <sub>R</sub>* that provides two defined outputs according to these criteria:

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/D-4_11.jpg)

The classification function can be realized by any classification algorithm, for example, a variation of an entropy-based statistical algorithm.

Kernel-based approaches use structural representations with similarity scores to guide the classifier and thereby considerably reduce problems related to the choice of similarity features. The principle of these approaches is to use a function K(X, Y) that defines the similarity relation between the objects *X* and *Y*. For example, when considering the level of character sequences, the similarity of two sequences increases with the number of sub-sequences shared between these two sequences. Thus, the similarity between the sequences is sim(livre, livrent) > sim(livre, livarot) [](#ch4en21).

The integration of supplementary knowledge resources such as parts of speech and syntactic analysis in segments or dependency trees has also been used to complete this task \[ZEL 03, CUL 04, ZHA 05\]. For example, to calculate the similarity between two analysis trees, a relatively simple algorithm can be used (see [Figure 4.45](#fig4_45)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_45.jpg)

Figure 4.45. Algorithm to calculate tree similarity

Given the cost of preparing data in supervised learning-based approaches, researchers gradually began to explore semi-supervised and unsupervised learning approaches \[BUN 07, BOL 11\]. Semi-supervised approaches are a compromise between the minimal effort of unsupervised approaches and the performance of supervised approaches. The principle of semi-supervised learning consists of annotating a limited number of cases to avoid the effort required to annotate an entire corpus and using them to construct groups of cases that are called *sentence bags*. A sentence bag is constructed like this: first, some entities that are related or not by a known semantic relation are identified. For example, \[BUN 07\] considers the case of companies acquired by multi-nationals (see examples in [Figure 4.46](#fig4_46)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_46.jpg)

Figure 4.46. Pairs of acquisition by multi-nationals

Then, a search is done on the Web using the two entities in each predicate as keywords. The results that the search engine provides are verified in a large number of pages but not necessarily all pages. Moreover, some pages may discuss the acquisition of YouTube by Google more or less explicitly while others may provide information related to these two entities without necessarily evoking their mutual relationships. It can also be assumed that the relation between these two entities will not be verified in practically all of the results where it is not a proven fact. More concretely, it can reasonably be assumed that the number of pages that a search engine will present that discuss the acquisition of Yahoo by Google is zero. Therefore, the number of pages serves as a factuality indicator for the supposed relation between the entities. The set of results for a pair of entities is called a *case bag*. Some examples of search results with the acquisition pairs are given in [Figure 4.47](#fig4_47).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_47.jpg)

Figure 4.47. Examples of search results

Finally, it is important to note that the way to proceed corresponds to the Multiple Instance Learning (MIL) paradigm that was initially proposed by \[DIE 97\] (see \[AMO 13\] for a general presentation of this paradigm).

#### 4.4.4.3. Event extraction

Event extraction was one of the first applications in the domain of information extraction. The events concerned were as varied as terrorist attempts, road accidents and announcements. The events could be extracted from written texts or telephone conversations like in \[BOU 02\]. According to the terminology of the Message Understanding Conference (MUC), each event is characterized by a scenario template that contains a set of slots that must be instantiated.

Just like the extraction of named entities and relations, supervised \[SOD 99, YAN 00\], semi-supervised \[SEK 07\] and unsupervised \[SHI 06\] learning approaches were used for the extraction. Several rule-based and pattern-based systems were created like the Fastus system by \[APP 93\] and the REES system by \[AON 00\]. For example, to extract events, \[AON 00\] proposed an architecture that conducts a processing in three main steps: a tagging module, a coreference resolution module and a pattern generation module (see [Figure 4.48](#fig4_48)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_48.jpg)

Figure 4.48. DFD of the REES system

The tagging module itself conducts a three-step processing: tagging of names, Noun Phrases (NP) and events. These three components use the same processing engine but different templates for each component. The coreference module then proceeds with labeling the nominal groups that correspond to organizations, people, places, etc. The template generation module is based on declarative rules. It results in a template whose format is compatible with the MUC recommendations, as shown in [Figure 4.49](#fig4_49).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_49.jpg)

Figure 4.49. Example of an event template

Then, REES concatenates the templates that are associated with the same event. This occurs using a set of declarative rules designed based on world knowledge. For example, as the birth and death of a person are unique events, there is a rule that makes it possible to concatenate templates relating to such events when they have the same subject.

#### 4.4.4.4. Sentiment analysis and opinion mining

While working on interactive systems like virtual agents or robots, researchers realized that some affective information processing is inevitable because it represents a very important implicit and subjective part of all human communication. For example, a virtual guide in an airport would be too monotonic and therefore not very useful if it could not detect the emotions of its interlocutor and adapt its tone \[SLO 81, SMI 10, OCH 12\]. In terms of generating answers on the part of the agent, many processes also play a role in expressing a sentiment or an opinion in an appropriate manner: lexical choices, syntactic constructions, prosody, etc. These elements play an important role in controlling the interaction, for example, by making it possible to prolong the dialogue or by participating in managing the focus (see, for example, \[JAN 16\]).

Similar applications have also been created to extract opinions expressed in a text or a forum, to observe investment tendencies and to detect criminal or terrorist communications. This is particularly important to automatically survey opinions about a given commercial product or even a political question. The popularity of social media like Facebook and Twitter has made the use of such practices on texts produced by users of these media particularly attractive \[RUS 14a\].

It should be noted that, given the constraints on the form as well as the content of these media, processing emotions is not as easy. Processing messages on Twitter is easier, given the concise nature of these messages and their direct character \[PAK 12\]. Processing product reviews is also facilitated by the direct aspect of these reviews and by the relatively minimal quantity of irrelevant information. On the other hand, blogs and forums are more difficult because they can address a number of important questions, they can make implicit or explicit comparisons, and there are also many digressions and sarcastic comments.

Currently, there is an abundance of literature concerning these questions under various names. For example, this includes opinion mining, opinion extraction, emotion analysis or extraction, subjectivity analysis, affection analysis and emotion detection. As noted in \[RIL 06\], the domain of subjectivity is quite vast and includes allegations, opinions, desires, beliefs, suspicions and speculations. Among these definitions, the notion of the opinion seems particularly pertinent. An opinion is a sentiment, attitude, emotion, an evaluation of an entity or a topic, or an aspect of these \[KIM 04, LIU 11\]. An opinion can be positive, negative or neutral (see, for example, [\[4.23\]](#eq4.23) for a positive opinion).

> Paul thinks that “Le Monde” is the best newspaper that covers political life in France. [\[4.23\]](#ieq4.23)

This is called the semantic orientation of the opinion, or the polarity of the opinion. Formally, an opinion can be expressed by a quintuplet (e <sub>j</sub>, a <sub>jk</sub>, so <sub>ijkl</sub>, s <sub>i</sub>, t <sub>l</sub>), where \[LIU 11\]:

- – e <sub>j</sub> is the entity intended by the opinion;
- – a <sub>jk</sub> is an aspect or a feature of the entity e <sub>j</sub>;
- – so <sub>ijkl</sub> is the value of an opinion of a source *s <sub>i</sub>* on a feature a <sub>jk</sub> of the entity e <sub>j</sub> at a moment t <sub>l</sub>. This value can be positive, negative or neutral;
- – s <sub>i</sub> is the source of the opinion;
- – t <sub>l</sub> is the time of expression of this opinion.

It consists of a generic definition that can apply to the political, commercial, social, or intellectual domains, and so on. It should also be noted that the correlations between these five elements are rather important: ideally, all five elements should be there to maximize the utility of the analysis. An opinion without an intended entity or its features has only a little importance. If we analyze the opinions expressed in sentence [\[4.23\]](#eq4.23), we find the following elements:

- – the entity intended by the opinion (ej): the newspaper “Le Monde”;
- – aspect (ajk): political;
- – value (soijkl): best/positive;
- – source (si): Paul;
- – time (si): present.

Since processing sentiments is inherently connected to subjectivities, it is not always possible to decide which sentiment provokes a given sentence in an absolute way. Consider sentence [\[4.24\]](#eq4.24). The sentiment that provokes this sentence could be the fear of being contaminated for someone who lives in Africa or sadness for someone who lives outside of Africa. Moreover, an African whose family is vaccinated against cholera will have a different sentiment compared to someone whose family is not vaccinated. To solve the problem of relative stance, in the early work, researchers simply avoided considering this variety of angles about sentiments and adopted a single perspective that they judged to be standard or representative of the majority of people. However, recent works have begun to consider the relative stance of the author who expressed the opinion (see, for example, \[RAJ 16, EBR 16 and JAN 16\]).

> Cholera is devastating Africa this year. [\[4.24\]](#ieq4.24)

Psychologists define emotions as complex states of sensations that give rise to psychic or physiological changes that affect thought and behavior. Emotions are associated with a fairly important level of phenomena like temperament, personality, humor and motivation.

Historically, the study of emotions started by at least the 19th Century, notably with the works of William James in the domain of psychology. Since then, several theoretical models have been proposed. Some models, known as dimensional models, consider that emotional states are connected by a set of dimensions shared between all emotions. They also include intensity parameters. From a cognitive perspective, these models postulate the existence of a neurophysiological system that is centrally responsible for all affective states. This contradicts the point of view supported by basic emotion theories, which consider that emotions emanate from different neurophysiological systems. Despite the objectives of cultural or physiological universalism, several psychologists and anthropologists find that it is not possible to define a universal framework to classify emotions. It is known that some cultures encourage the expression of emotions while others judge such expression to be unacceptable. The divergence between the starting postulations is reflected even more significantly in the models, a few of which will be presented here.

The semantic differential model proposed by Osgood focuses on scaling the connotations of objects, events and concepts \[OSG 57\]. These connotations are used to derive an attitude with regard to an event, an object or a concept. After having studied several semantic differential scales, Osgood and his colleagues succeeded in identifying three recurrent attitudes to evaluate words. These consist of evaluating with the pair of adjectives: good/bad, the power: strong/weak and the activity: active/passive. They also showed in a study of about 10 cultures that these three dimensions are universally present throughout the studied cultures \[OSG 75\].

In turn, the categorical model of Ekman starts from the perspective that there are six discrete categories of sentiments that are expressed by words: anger, disgust, fear, joy, sadness and surprise. As he considered that these sentiments are universally translated by distinct facial expressions, Ekman concluded that these sentiments have a biological origin. Although these categories have been adopted by many works in the domain of automatic processing of sentiments, some researchers have postulated that these categories are dependent on the domain of application \[DME 07\].

The circumplex model was initially developed by \[RUS 80\]. This model considers that emotions are distributed in a circular bidimensional space with arousal and valence values, where the arousal represents the vertical axis while the valence represents the horizontal axis (see [Figure 4.50](#fig4_50)). The point of intersection of the two axes is the center of the virtual circle of emotions and represents a neutral state. Thus, the different emotions can have different values of emotions or affections whose value is zero.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_50.jpg)

Figure 4.50. The representation of emotions according to Russell’s circumplex model

Finally, the cubic model developed by Lövheim is distinguished by its biological inspiration because it relates the rates of three neurotransmitters, which are dopamine, noradrenaline and serotonin, with the eight basic emotions identified by Silvan Tomkins \[LÖV 12\]. Each of these emotions is associated with these neurotransmitters in varying degrees, as shown in [Table 4.10](#tab4_10).

**[Table 4.10](#itab4_10).** *The basic emotions and corresponding neurotransmitter rates*

| **Base emotion** | **serotonin** | **dopamine** | **Noradrenaline** |
| --- | --- | --- | --- |
| Shame/humiliation | Low | Low | Low |
| Distress/Anguish | Low | Low | High |
| Fear/Terror | Low | High | Low |
| Anger/Rage | Low | High | High |
| Contempt/disgust | High | Low | Low |
| Surprise | High | Low | High |
| Pleasure/Joy | High | High | Low |
| Interest/excitation | High | High | High |

The direct connection between neurotransmitters and emotions makes it possible to give biological explanations for emotions. For example, depression can be seen as a situation that causes a decrease in serotonin, thus limiting the possible emotions to Shame/Humiliation, Distress/Anguish, Fear/Terror and Anger/Rage. An inverse vision of this state would be to consider that it is impossible for someone with depression to have the emotions of surprise, joy or interest, which require higher levels of serotonin.

Tridimensional, Lövheim’s model places Tomkin’s eight basic emotions in the corners of a cube and uses the following three axes: noradrenaline, serotonin and dopamine.

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_51.jpg)

Figure 4.51. Lövheim’s cube of emotions

The advantage of this classification is that it offers a way to account for differences between emotions that it is not possible to distinguish with bidimensional models.

Finally, the Hourglass model developed by Cambria is worth mentioning as well. It is a model based on the works of Plutshik on human emotions \[PLU 01\]. The fundamental idea of this model is that the mind is made of several independent sources and that emotional states result from the activation or deactivation of these resources \[MIN 07\]. Each of these resource combinations changes the brain’s activities, thereby affecting our way of thinking. For example, the state of anger seems to select resources that allow for reacting quickly and with more force while suppressing other resources that cause a person to act cautiously. This idea is also confirmed by the results of research in the domain of cerebral imaging that show that a different pattern of cerebral activity accompanies each emotion (see \[CAM 12, CAM 16\] for more details about this model).

An emotion can be expressed using explicit linguistic means such as the use of verbs and expressions of opinions have extremely varied forms. For example, in English, this includes expressions like *I think, I believe, I consider, it seems to me, in my opinion* and *I am of the opinion*. Verbs that serve to express taste can also serve to express an opinion. In English, this includes following verbs like *cherish, adore, love, please, appreciate, detest, displease, prefer* and *be favorable*. However, the use of an explicit element of opinion expression is not a necessary condition for expressing an opinion. Opinions are very often expressed implicitly, and the use of a linguistic indicator only has the function of underscoring the subjective character of the opinion or, in certain cases, highlighting the person uttering it.

To express an opinion, three forms of expression can be distinguished: direct expression, indirect expression and comparative opinion.

A direct opinion consists of an explicit qualification of an entity, a topic or an action. This qualification can take the form of a qualificative adjective or epithet, or a lexical choice (see examples in [Table 4.11](#tab4_11)).

**[Table 4.11](#itab4_11).** *Examples of opinions with different types of qualifications*

| **Opinions** | **Type of qualification** |
| --- | --- |
| This software is really efficient. | With an adjective |
| In this racer, it only takes an hour to get to Paris. | With a noun that has a positive connotation |
| Jules’ company is just getting by after last year’s losses. | With a verb that has a negative connotation |

Indirect opinions, in turn, are often formulated as the logical consequence of an action or a means (use of an entity), as in sentence [\[4.25\]](#eq4.25):

> After using this detergent, Adeline’s dishes shone like diamonds. [\[4.25\]](#ieq4.25)

Comparative opinions are used to compare entities, ideas or topics to express preferences. Linguistically, this occurs using comparatives and superlatives. Again, the comparison can be explicit or implicit as in [\[4.26a\]](#eq4.26) and [\[4.26b\]](#eq4.26), respectively:

1. a) Ferraris are less practical than Fords.
2. b) The left is the political current that defends workers’ rights the most (implicitly more than the right and the center). [\[4.26\]](#ieq4.26)

To process the lexical level of opinions, an extension of the WordNet base was created at the IRST Institute in Italy to equip definitions of words in this base with an affective value. It is called WordNetAffect and it covers the entire lexicon of the English language \[STR 04\]. The words are classified according to the approach of \[ORT 87\] given in [Table 4.12](#tab4_12). The words are annotated with a polarity (positive or negative) as well as degrees to designate the force of an emotion. The 2004 version of WordNetAffect includes 1,314 synsets and 3,340 words. Several other projects intended to create lexical databases or dictionaries with emotions have been created. Each of these projects is distinguished by its method of annotating words (automatic, manual or semi-automatic), its size or taxonomy adopted (see, for example, \[KAM 04b\] and SentiWordNet [](#ch4en22) \[ESU 06\]).

**[Table 4.12](#itab4_12).** *Categories of terms in WordNetAffect \[STR 04\]*

| **Category** | **Examples of terms in English and French** |
| --- | --- |
| Emotion | Anger – fear |
| Cognitive state | Doubt – dazed |
| Feature | Aggressiveness *–* competitive |
| Behavior | Cry – offense |
| Attitude | Skepticism – intolerance |
| Emotion | Pleasure – feel |

In terms of syntax, two syntactic forms directly affect the expression of sentiments and emotions: negation and dislocation. Negation makes it possible to inverse the polarity of an opinion or to restrict this opinion to a precise entity (see sentences [\[4.27\]](#eq4.27)):

1. a) I do not like cream cheese. (Negative opinion) [\[4.27\]](#ieq4.27)
2. b) She only likes white roses. (Restriction)

Another syntactic construction that affects the expression of emotions is dislocation. It consists of displacing a phrase in order to highlight it (see [Table 4.13](#tab4_13)). The focus attracts the attention of several opinion elements and therefore has various functions. Naturally, a good module of opinion extraction should consider these syntactic variations in order to be able to process the opinions correctly. Moreover, several works concern the role of the discursive structure in the expression of opinions, notably including that of \[POL 04c\], that studied the effect of discursive connectors on the polarity of an opinion. Consider sentences [\[4.28\]](#eq4.28):

| Michael is good at networks. | (Positive opinion) [\[4.28\]](#ieq4.28) |
| --- | --- |
| Although Michael is good at networks, he is not very good at algorithms and programming. | (Negative opinion) |

**[Table 4.13](#itab4_13).** *Relation between syntactic structures and the elements of an opinion*

| **Sentences** | **Syntactic role of the element in focus** | **Opinion element in focus** |
| --- | --- | --- |
| It’s this song that I like. | Agent | Intended entity |
| It is Jacqueline’s dress that I adore. | Patient | Intended entity |
| It’s John who likes red roses. | Agent | Source of the opinion |
| With much recognition and gratitude, he accepted your gift. | Prepositional group expressing the manner | Opinion |

The works of \[VOL 07\] highlighted the role of the summative evaluation of an entity that comes at the end to summarize the previous evaluations that concern several aspects of an entity or a topic. These researchers showed that attributing a more significant weight to these evaluations made it possible to improve the analysis results. Consider passage [\[4.29\]](#eq4.29). The evaluation given includes several elements that can be judged to be positive (new, specialized, effective service, rich menu), but the location of negative elements at the end gives them a conclusion value and attributes a globally negative aspect to the evaluation. Sometimes, explicit markers can be used to indicate the conclusion such as *in short*, *in sum* and *in summary*. Finally, it is also useful to mention that a large number of annotated linguistic resources are available for researchers (see \[PAN 08\] for a review of these resources):

> Located in a bright new building just steps from the Atlanta Marta train station, a restaurant specialized in Mexican cuisine recently opened its doors in our city. The service is very fast and the menu is fairly large. However, the lack of basic services like parking and its location close to the train station as well as music playing too loudly breaks the ambiance and brings to mind fast food restaurants. [\[4.29\]](#ieq4.29)

Subjectivity extraction is a very promising domain from a research point of view, especially from an industrial applications perspective. Making a detailed presentation of all of the applications is far beyond the scope of the present section, so this text will be limited to quickly presenting the vectorial approach (sometimes called categorical) that is one of the most commonly adopted approaches. Very similar to the approach of the same name in information retrieval, the analysis according to this approach occurs in four main steps (see [Figure 4.52](#fig4_52)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_52.jpg)

Figure 4.52. DFD of a categorical system for extracting subjectivities

First, the most characteristic elements in the document are identified. Many terms in a text are not useful for its categorization because they are shared by a large number of texts in diverse categories (see [section 3.1.8](https://learning.oreilly.com/library/view/natural-language-processing/9781848219212/ch03.xhtml#sec33)). Another disadvantage is the computational cost related to processing all of the words in a text, whose numbers can be quite considerable. To overcome these two problems, emotion-processing systems, like information retrieval systems, proceed to a pre-processing phase whose role is to morphosyntactically annotate words, filter non-distinctive words and create a matrix of all significant words in a document (see [section 4.3.2](#sec59) for more details). The reduction in dimensions occurs through latent semantic indexing whose role is to break down the matrix obtained with the Singular Value Decomposition (SVD) process. The WordNetAffect module in turn enriches the simplified matrix with information related to emotions. Finally, the cosine distance is used to calculate the distance between the vector obtained and the emotional vectors.

[^13]: Kernel-based approaches use structural representations with similarity scores to guide the classifier and thereby considerably reduce problems related to the choice of similarity features. The principle of these approaches is to use a function K(X, Y) that defines the similarity relation between the objects *X* and *Y*. For example, when considering the level of character sequences, the similarity of two sequences increases with the number of sub-sequences shared between these two sequences. Thus, the similarity between the sequences is sim(livre, livrent) > sim(livre, livarot)

The integration of supplementary knowledge resources such as parts of speech and syntactic analysis in segments or dependency trees has also been used to complete this task \[ZEL 03, CUL 04, ZHA 05\]. For example, to calculate the similarity between two analysis trees, a relatively simple algorithm can be used (see [Figure 4.45](#fig4_45)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_45.jpg)

Figure 4.45. Algorithm to calculate tree similarity ↩

Given the cost of preparing data in supervised learning-based approaches, researchers gradually began to explore semi-supervised and unsupervised learning approaches \[BUN 07, BOL 11\]. Semi-supervised approaches are a compromise between the minimal effort of unsupervised approaches and the performance of supervised approaches. The principle of semi-supervised learning consists of annotating a limited number of cases to avoid the effort required to annotate an entire corpus and using them to construct groups of cases that are called *sentence bags*. A sentence bag is constructed like this: first, some entities that are related or not by a known semantic relation are identified. For example, \[BUN 07\] considers the case of companies acquired by multi-nationals (see examples in [Figure 4.46](#fig4_46)).

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_46.jpg)

Figure 4.46. Pairs of acquisition by multi-nationals

Then, a search is done on the Web using the two entities in each predicate as keywords. The results that the search engine provides are verified in a large number of pages but not necessarily all pages. Moreover, some pages may discuss the acquisition of YouTube by Google more or less explicitly while others may provide information related to these two entities without necessarily evoking their mutual relationships. It can also be assumed that the relation between these two entities will not be verified in practically all of the results where it is not a proven fact. More concretely, it can reasonably be assumed that the number of pages that a search engine will present that discuss the acquisition of Yahoo by Google is zero. Therefore, the number of pages serves as a factuality indicator for the supposed relation between the entities. The set of results for a pair of entities is called a *case bag*. Some examples of search results with the acquisition pairs are given in [Figure 4.47](#fig4_47)

![image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781848219212/files/images/fig-4_47.jpg)

Figure 4.47. Examples of search results

Finally, it is important to note that the way to proceed corresponds to the Multiple Instance Learning (MIL) paradigm that was initially proposed by \[DIE 97\] (see \[AMO 13\] for a general presentation of this paradigm).