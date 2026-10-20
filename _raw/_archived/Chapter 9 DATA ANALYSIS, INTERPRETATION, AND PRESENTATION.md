---
title: "Chapter 9: DATA ANALYSIS, INTERPRETATION, AND PRESENTATION"
source: "https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c09.xhtml"
author:
  - "Helen Sharp"
  - "Jennifer Preece"
  - "Yvonne Rogers"
published: 2026-08-01
created: 2026-10-18
description: "Chapter 9DATA ANALYSIS, INTERPRETATION, AND PRESENTATION9.1 Introduction9.2 Qualitative and Quantitative9.3 Basic Quantitative Analysis9.4 Basic Qualitative Analysis9.5 What Kind of..."
tags:
  - "ux"
citation: "Sharp, H., Preece, J., Rogers, Y., Preece, J. (2019). Interaction Design: Beyond Human-Computer Interaction. United Kingdom: Wiley."
---
## 9.1 Introduction

The kind of analysis that can be performed on a set of data will be influenced by the goals identified at the outset and the data gathered. Broadly speaking, a qualitative analysis approach, a quantitative analysis approach, or a combination of qualitative and quantitative approaches may be taken. The last of these is very common, as it provides a more comprehensive account of the behavior being observed or the performance being measured.

Most analysis, whether it is quantitative or qualitative, begins with the initial reactions or observations from the data. This may involve identifying patterns or calculating simple numerical values such as ratios, averages, or percentages. For all data, but especially when dealing with large volumes of data (that is, Big Data), it is useful to look over the data to check for any anomalies that might be erroneous. For example, people who are 999 years old. This process is known as *data cleansing*, and there are often digital tools to help with the process. This initial analysis is followed by more detailed work using structured frameworks or theories to support the investigation.

Interpretation of the findings often proceeds in parallel with analysis, but there are different ways to interpret results, and it is important to make sure that the data supports any conclusions. A common mistake is for the investigator's existing beliefs or biases to influence the interpretation of results. Imagine that an initial analysis of the data has revealed a pattern of responses to customer care questionnaires that indicates that inquiries from customers routed through the Sydney office of an organization take longer to process than those routed through the Moscow office. This result can be interpreted in many different ways. For example, the customer care operatives in Sydney are less efficient, they provide more detailed responses, the technology supporting the inquiry process in Sydney needs to be updated, customers reaching the Sydney office demand a higher level of service, and so on. Which one is correct? To determine whether any of these potential interpretations is accurate, it would be appropriate to look at other data such as customer inquiry details and maybe to interview staff.

Another common mistake is to make claims that go beyond what the data can support. This is a matter of interpretation and of presentation. Using words such as *many* or *often* or *all* when reporting conclusions needs to be carefully considered. An investigator needs to remain as impartial and objective as possible if the conclusions are to be trusted. Showing that the conclusions are supported by the results is an important skill to develop.

Finally, finding the best way to present findings is equally skilled, and it depends on the goals but also on the audience for whom the study was performed. For example, a formal notation may be used to report the results for the requirements activity, while a summary of problems found, supported by video clips of users experiencing those problems, may be better for presentation to the team of developers.

This chapter introduces a variety of methods, and it describes in more detail how to approach data analysis and presentation using some of the common approaches taken in interaction design.

## 9.2 Quantitative and Qualitative

*Quantitative data* is in the form of numbers, or data that can easily be translated into numbers. Examples are the number of years' experience the interviewees have, the number of projects a department handles at a time, or the number of minutes it takes to perform a task. *Qualitative data* is in the form of words and images, and it includes descriptions, quotes from interviewees, vignettes of activity, and photos. It is possible to express qualitative data in numerical form, but it is not always meaningful to do so (see [Box 9.1](#c09-fea-0001)).

It is sometimes assumed that certain forms of data gathering can only result in quantitative data and that others can only result in qualitative data. However, this is a fallacy. All forms of data gathering discussed in the previous chapter may result in qualitative and quantitative data. For example, on a questionnaire, questions about the participant's age or number of software apps they use in a day will result in quantitative data, while any comments will result in qualitative data. In an observation, quantitative data that may be recorded includes the number of people involved in a project or how many hours someone spends sorting out a problem, while notes about feelings of frustration, or the nature of interactions between team members, are qualitative data.

*Quantitative analysis* uses numerical methods to ascertain the magnitude, amount, or size of something; for example, the attributes, behavior, or strength of opinion of the participants. For example, in describing a population, a quantitative analysis might conclude that the average person is 5 feet 11 inches tall, weighs 180 pounds, and is 45 years old. *Qualitative analysis* focuses on the nature of something and can be represented by themes, patterns, and stories. For example, in describing the same population, a qualitative analysis might conclude that the average person is tall, thin, and middle-aged.

### 9.2.1 First Steps in Analyzing Data

Having collected the data, some initial processing is normally required before data analysis can begin in earnest. For example, audio data may be transcribed by hand or by using an automated tool, such as Dragon; quantitative data, such as time taken or errors made, is usually entered into a spreadsheet, like Excel. Initial analysis steps for data typically collected through interviews, questionnaires, and observation are summarized in [Table 9.1](#c09-tbl-0001).

[**Table 9.1**](#R_c09-tbl-0001) Data gathered and typical initial processing steps for interviews, questionnaires, and observation

|  | Usual raw data | Example qualitative data | Example quantitative data | Initial processing steps |
| --- | --- | --- | --- | --- |
| Interviews | Audio recordings.   Interviewer notes.   Video recordings. | Responses to open-ended questions.   Video pictures.   Respondent's opinions. | Age, job role, years of experience.   Responses to close-ended questions. | Transcription of recordings.   Expansion of notes.   Entry of answers to close-ended questions into a spreadsheet |
| Questionnaires | Written responses.   Online database. | Responses to open-ended questions.   Responses in “further comments” fields.   Respondent's opinions. | Age, job role, years of experience.   Responses to close-ended questions. | Clean up data.   Filter into different data sets.   Synchronization between data recordings. |
| Observation | Observer's notes.   Photographs.   Audio and video recordings.   Data logs.   Think-aloud   Diaries. | Records of behavior.   Description of a task as it is undertaken.   Copies of informal procedures. | Demographics of participants.   Time spent on a task.   The number of people involved in an activity.   How many different types of activity are undertaken. | Expansion of notes.   Transcription of recordings. |

#### Interviews

Interviewer notes need to be written up and expanded as soon as possible after the interview has taken place so that the interviewer's memory is clear and fresh. An audio or video recording may be used to help in this process, or it may be transcribed for more detailed analysis. Transcription takes significant effort, as people talk more quickly than most people can type (or write), and the recording is not always clear. It is worth considering whether to transcribe the whole interview or just sections of it that are relevant. Deciding what is relevant, however, can be difficult. Revisiting the goals of the study to see which passages address the research questions can guide this process.

Close-ended questions are usually treated as quantitative data and analyzed using basic quantitative analysis (see [Section 9.3](#head-2-186) “Basic Quantitative Analysis”). For example, a question that asks for the respondent's age range can easily be analyzed to find out the percentage of respondents in each. More complicated statistical techniques are needed to identify relationships between responses that can be generalized, such as whether there is an interaction between the condition being tested and a demographic. For example, do people of different ages use Facebook for different lengths of time when first logging on in the morning or at night before they go to bed? Open-ended questions typically result in qualitative data that might be searched for categories or patterns of response.

#### Questionnaires

Increasingly, questionnaire responses are provided using online surveys, and the data is automatically stored in a database. The data can be filtered according to respondent subpopulations (for instance, everyone under 16) or according to a particular question (for example, to understand respondents' reactions to one kind of robot personality rather than another). This allows analyses to be conducted on subsets of the data and hence to draw specific conclusions for more targeted goals. To conduct this kind of analysis requires sufficient data from a large enough sample of participants.

#### Observation

Observation can result in a wide variety of data including notes, photographs, data logs, think-aloud recordings (often called *protocols*), video, and audio recordings. Taken together, these different types of data can provide a rich picture of the observed activity. The difficult part is working out how to combine the different sources to create a coherent narrative of what has been recorded; analytic frameworks, discussed in [section 9.5](#head-2-193), can help with this. Initial data processing includes writing up and expanding notes and transcribing elements of the audio and video recordings and the think-aloud protocols. For observation in a controlled environment, initial processing might also include synchronizing different data recordings.

Transcriptions and the observer's notes are most likely to be analyzed using qualitative approaches, while photographs provide contextual information. Data logs and some elements of the observer's notes would probably be analyzed quantitatively.

## 9.3 Basic Quantitative Analysis

Explaining statistical analysis requires a whole book on its own (for example, see Cairns, 2019). Here, we introduce two basic quantitative analysis techniques that can be used effectively in interaction design: averages and percentages. Percentages are useful for standardizing the data, particularly to compare two or more large sets of responses.

Averages and percentages are fairly well-known numerical measures. However, there are three different types of average, and using the wrong one can lead to the misinterpretation of the results. These three are: mean, median, and mode. *Mean* refers to the commonly understood interpretation of average; that is, add together all the figures and divide by the number of figures with which you started. Median and mode averages are less well-known but are very useful. The *median* is the middle value of the data when the numbers are ranked. The *mode* is the most commonly occurring number. For example, in a set of data (2, 3, 4, 6, 6, 7, 7, 7, 8), the median is 6 and the mode is 7, while the mean is 50/9 = 5.56. In this case, the difference between the different averages is not that great. However, consider the set (2, 2, 2, 2, 450). Now the median is 2, the mode is 2, and the mean is 458/5 = 91.6!

![Cartoon illustration of an job application and the interviewer.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09uf001.jpg)

Cartoon illustration of an job application and the interviewer.

Use of simple averages can provide useful overview information, but they need to be used with caution. Evangelos Karapanos et al. (2009) go further and suggest that averaging treats diversity among participants as error and proposes the use of a multidimensional scaling approach instead.

Before any analysis can take place, the data needs to be collated into analyzable data sets. Quantitative data can usually be translated into rows and columns, where one row equals one record, such as respondent or interviewee. If these are entered into a spreadsheet such as Excel, this makes simple manipulations and data set filtering easier. Before entering data in this way, it is important to decide how to represent the different possible answers. For example, “don't know” represents a different response from no answer at all, and they need to be distinguished, for instance, with separate columns in the spreadsheet. Also, if dealing with options from a close-ended question, such as job role, there are two different possible approaches that affect the analysis. One approach is to have a column headed “Job role” and to enter the job role as it is given by the respondent or interviewee. The alternative approach is to have a column for each possible answer. The latter approach lends itself more easily to automatic summaries. Note, however, that this option will be open only if the original question was designed to collect the appropriate data (see [Box 9.2](#c09-fea-0002)).

For simple collation and analysis, spreadsheet software such as Excel or Google Sheets is often used as it is commonly available, is well understood, and offers a variety of numerical manipulations and graphical representations. Basic analysis might involve finding out averages and identifying *outliers*, in other words, values that are significantly different from the majority, and hence not common. Producing a graphical representation provides an overall view of the data and any patterns it contains. Other tools are available for performing specific statistical tests, such as online t-tests and A/B testing tools. Data visualization tools can create more sophisticated representations of the data such as heatmaps.

For example, consider the set of data shown in [Table 9.2](#c09-tbl-0002), which was collected during an evaluation of a new photo sharing app. This data shows the users' experience of social media and the number of errors made while trying to complete a controlled task with the new app. It was captured automatically and recorded in a spreadsheet; then the totals and averages were calculated. The graphs in [Figure 9.1](#c09-fig-0001) were generated using the spreadsheet package. They show an overall view of the data set. In particular, it is easy to see that there are no significant outliers in the error rate data.

[**Table 9.2**](#R_c09-tbl-0002) Data gathered during a study of a photo sharing app

<table><thead><tr><td></td><td colspan="6">Social media use</td></tr><tr><td>User</td><td>More than once a day</td><td>Once a day</td><td>Once a week</td><td>Two or three times a week</td><td>Once a month</td><td>Number of errors made</td></tr></thead><tbody><tr><td>1</td><td></td><td>1</td><td></td><td></td><td></td><td>4</td></tr><tr><td>2</td><td>1</td><td></td><td></td><td></td><td></td><td>2</td></tr><tr><td>3</td><td></td><td></td><td>1</td><td></td><td></td><td>1</td></tr><tr><td>4</td><td>1</td><td></td><td></td><td></td><td></td><td>0</td></tr><tr><td>5</td><td></td><td></td><td></td><td>1</td><td></td><td>2</td></tr><tr><td>6</td><td></td><td>1</td><td></td><td></td><td></td><td>3</td></tr><tr><td>7</td><td>1</td><td></td><td></td><td></td><td></td><td>2</td></tr><tr><td>8</td><td></td><td>1</td><td></td><td></td><td></td><td>0</td></tr><tr><td>9</td><td></td><td></td><td></td><td></td><td>1</td><td>3</td></tr><tr><td>10</td><td>1</td><td></td><td></td><td></td><td></td><td>2</td></tr><tr><td>11</td><td></td><td></td><td></td><td>1</td><td></td><td>1</td></tr><tr><td>12</td><td></td><td></td><td>1</td><td></td><td></td><td>2</td></tr><tr><td>13</td><td></td><td>1</td><td></td><td></td><td></td><td>4</td></tr><tr><td>14</td><td></td><td>1</td><td></td><td></td><td></td><td>2</td></tr><tr><td>15</td><td></td><td></td><td></td><td></td><td></td><td>1</td></tr><tr><td>16</td><td></td><td></td><td></td><td>1</td><td></td><td>1</td></tr><tr><td>17</td><td></td><td>1</td><td></td><td></td><td>1</td><td>0</td></tr><tr><td>18</td><td></td><td>1</td><td></td><td></td><td></td><td>0</td></tr><tr><td><b>Totals</b></td><td>4</td><td>7</td><td>2</td><td>3</td><td>2</td><td>30</td></tr><tr><td></td><td></td><td></td><td></td><td></td><td><b>Mean</b></td><td><b>1.67</b></td></tr><tr><td colspan="7">(to 2 decimal places)</td></tr></tbody></table>

![Graphical representations of (top) the distribution of errors made. (Bottom) The figure depicts the spread of social media experience within the participant group.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f001.jpg)

Figure 9.1 Graphical representations of the data in Table 9.2 (a) The distribution of errors made (take note of the scale used in these graphs, as seemingly large differences may be much smaller in reality). (b) The spread of social media experience within the participant group.

Adding one more user to [Table 9.2](#c09-tbl-0002) with an error rate of 9 and plotting the new data as a scatter graph (see [Figure 9.2](#c09-fig-0002)) illustrates how graphs can help to identify outliers. Outliers are usually removed from the main data set because they distort the general patterns. However, outliers may also be interesting cases to investigate further in case there are special circumstances surrounding those users and their session.

![Scatter diagram with user on the x axis and number of errors made on the y axis.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f002.jpg)

Figure 9.2 Using a scatter diagram helps to identify outliers in your data quite quickly

These initial investigations also help to identify other areas for further investigation. For example, is there something special about users with error rate 0 or something distinctive about the performance of those who use the social media only once a month?

It is fairly straightforward to compare two sets of results, for instance from the evaluation of two interactive products, using these kinds of graphical representations of the data. Semantic differential data can also be analyzed in this way and used to identify trends, provided that the format of the question is appropriate. For example, the following question was asked in a questionnaire to evaluate two different smartphone designs:

> *For each pair of adjectives, place a cross at the point between them that reflects the extent to which you believe the adjectives describe the smartphone design. Please place only one cross between the marks on each line*.

![Screenshot of a questionnaire to evaluate two different smartphone designs.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09uf004.jpg)

Screenshot of a questionnaire to evaluate two different smartphone designs.

[Table 9.3](#c09-tbl-0003) and [Table 9.4](#c09-tbl-0004) show the tabulated results from 100 respondents. Note that the responses have been translated into five categories, numbered from 1 to 5, based on where the respondent marked the line between each pair of adjectives. It is possible that respondents may have intentionally put a cross closer to one side of the box than the other, but it is acceptable to lose this nuance in the data, provided that the original data is not lost, and any further analysis could refer back to it.

[**Table 9.3**](#R_c09-tbl-0003) Phone 1

|  | 1 | 2 | 3 | 4 | 5 |  |
| --- | --- | --- | --- | --- | --- | --- |
| Annoying | 35 | 20 | 18 | 15 | 12 | Pleasing |
| Easy to use | 20 | 28 | 21 | 13 | 18 | Difficult to use |
| Value-for-money | 15 | 30 | 22 | 27 | 6 | Expensive |
| Attractive | 37 | 22 | 32 | 6 | 3 | Unattractive |
| Secure | 52 | 29 | 12 | 4 | 3 | Not secure |
| Helpful | 33 | 21 | 32 | 12 | 2 | Unhelpful |
| Hi-tech | 12 | 24 | 36 | 12 | 16 | Lo-tech |
| Robust | 44 | 13 | 15 | 16 | 12 | Fragile |
| Inefficient | 28 | 23 | 25 | 12 | 12 | Efficient |
| Modern | 35 | 27 | 20 | 11 | 7 | Dated |

[**Table 9.4**](#R_c09-tbl-0004) Phone 2

|  | 1 | 2 | 3 | 4 | 5 |  |
| --- | --- | --- | --- | --- | --- | --- |
| Annoying | 24 | 23 | 23 | 15 | 15 | Pleasing |
| Easy | 37 | 29 | 15 | 10 | 9 | Difficult to use |
| Value-for-money | 26 | 32 | 17 | 13 | 12 | Expensive |
| Attractive | 38 | 21 | 29 | 8 | 4 | Unattractive |
| Secure | 43 | 22 | 19 | 12 | 4 | Not secure |
| Helpful | 51 | 19 | 16 | 12 | 2 | Unhelpful |
| Hi-tech | 28 | 12 | 30 | 18 | 12 | Lo-tech |
| Robust | 46 | 23 | 10 | 11 | 10 | Fragile |
| Inefficient | 10 | 6 | 37 | 29 | 18 | Efficient |
| Modern | 3 | 10 | 45 | 27 | 15 | Dated |

The graph in [Figure 9.3](#c09-fig-0003) shows how the two smartphone designs varied according to the respondents' perceptions of how modern the design is. This graphical notation shows clearly how the two designs compare.

![A bar graph that compares two smartphone designs according to whether they are perceived as modern or dated](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f003.jpg)

Figure 9.3 A graphical comparison of two smartphone designs according to whether they are perceived as modern or dated

Data logs that capture users' interactions automatically, such as with a website or smartphone, can also be analyzed and represented graphically, thus helping to identify patterns in behavior. Also, more sophisticated manipulations and graphical images can be used to highlight patterns in collected data.

## 9.4 Basic Qualitative Analysis

Three basic approaches to qualitative analysis are discussed in this section: identifying themes, categorizing data, and analyzing critical incidents. *Critical incident analysis* is a way to isolate subsets of data for more detailed analysis, perhaps by identifying themes or applying categories. These three basic approaches are not mutually exclusive and are often used in combination, for example, when analyzing video material critical incidents may first be identified and then a thematic analysis undertaken. Video analysis is discussed further in [Box 9.3](#c09-fea-0004).

As with quantitative analysis, the first step in qualitative analysis is to gain an overall impression of the data and to start looking for interesting features, topics, repeated observations, or things that stands out. Some of these will have emerged during data gathering, and this may already have suggested the kinds of pattern to look for, but it is important to confirm and re-confirm findings to make sure that initial impressions don't bias analysis. For example, you might notice from the logged data of people visiting [TripAdviser.com](http://tripadviser.com/) that they often look for reviews for hotels that are rated “terrible” first. Or, you might notice that a lot of respondents all say how frustrating it is to have to answer so many security questions when logging onto an online banking service. During this first pass, it is not necessary to capture all of the findings but instead to highlight common features and record any surprises that arise (Blandford, 2017).

For observations, the guiding framework used in data gathering will give some structure to the data. For example, the practitioner's framework for observation introduced in [Chapter 8](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c08.xhtml), “Data Gathering,” will have resulted in a focus on who, where, and what, while using the more detailed framework will result in patterns relating to physical objects, people's goals, sequences of events, and so on.

Qualitative data can be analyzed inductively, that is, extracting concepts from the data, or deductively, in other words using existing theoretical or conceptual ideas to categorize data elements (Robson and McCartan, 2016). Which approach is used depends on the data obtained and the goal of the study, but the underlying principle is to classify elements of the data in order to gain insights toward the study's goal. Identifying themes (thematic analysis) takes an *inductive approach*, while categorizing data takes a *deductive approach*. In practice, analysis is often performed iteratively, and it is common for themes identified inductively then to be applied deductively to new data, and for an initial, pre-existing categorization scheme, to be enhanced inductively when applied to a new situation or new data. One of the most challenging aspects of identifying themes or new categories is determining meaningful codes that are orthogonal (that is, codes which do not overlap). Another is deciding on the appropriate granularity for them, for example at the word, phrase, sentence, or paragraph level. This is also dependent on the goal of the study and the data being analyzed.

Whether an inductive or deductive approach is used, an objective is to produce a reliable analysis, that is, one that can be replicated by someone else if they were to use the same type of approach. One way to achieve this is to train another person to do the coding. When training is complete, both researchers analyze a sample of the same data. If there is a large discrepancy between the two analyses, either training was inadequate or the categorization is not working and needs to be refined. When a high level of reliability is reached between the two researchers, it can be quantified by calculating the inter-rater reliability. This is the percentage of agreement between the analyses of the two researchers, defined as the number of items of agreement, for example the number of categories or themes arising from the data that have been identified consistently by both researchers, expressed as a percentage of the total number of items examined. An alternative measure where two researchers have been used is Cohen's kappa, (κ), which considers the possibility that agreement has occurred due to chance (Cohen, 1960).

Using more sophisticated analytical frameworks to structure the analysis of qualitative data can lead to additional insights that go beyond the results of these basic techniques. [Section 9.5](#head-2-193) introduces frameworks that are commonly used in interaction design.

### 9.4.1 Identifying Themes

*Thematic analysis* is considered an umbrella term to cover a variety of different approaches to examining qualitative data. It is a widely used analytical technique that aims to identify, analyze, and report patterns in the data (Braun and Clarke, 2006). More formally, a *theme* is something important about the data in relation to the study goal. A theme represents a pattern of some kind, perhaps a particular topic or feature found in the data set, which is considered to be important, relevant, and even unexpected with respect to the goals driving the study. Themes that are identified may relate to a variety of aspects: behavior, a user group, events, places or situations where those events happen, and so on. Each of these kinds of themes may be relevant to the study goals. For example, descriptions of typical users may be an outcome of data analysis that focuses on participant characteristics. Although thematic analysis is described in this section on qualitative analysis, themes and patterns may also emerge from quantitative data.

After an initial pass through the data, the next step is to look more systematically for themes across participants' transcripts, seeking further evidence both to confirm and disconfirm initial impressions in all of the data. This more systematic analysis focuses on checking for consistency; in other words, do the themes occur across all participants, or is it only one or two people who mention something? Another focus is on finding further themes that may not have been noticed first time. Sometimes, the refined themes resulting from this systematic analysis form the primary set of findings for the analysis, and sometimes they are just the starting point.

The study's goal provides an orienting focus for the identification and formulation of themes in the first and subsequent passes through the data. For example, consider a survey to evaluate whether the information displayed on a train travel website is appropriate and sufficient. Several of the respondents suggest that the station stops in between the origin and destination stations should be displayed. This is relevant to the study's goal and would be reported as a main theme. In another part of the survey, under further comments you might notice that several respondents say the company's logo is distracting. Although this too is a theme in the data, it is not directly relevant to the study's goals and may be reported only as a minor theme.

Once a number of themes have been identified, it is usual to step back from the set of themes to look at the bigger picture. Is an overall narrative starting to emerge, or are the themes quite disparate? Do some seem to fit together with others? If so, is there an overarching theme? Can you start to formulate a meta-narrative, that is, an overall picture of the data? In doing this, some of the original themes may not seem as relevant and can be removed. Are there some themes that contradict each other? Why might this be the case? This can be done individually, but more often this is applied in a group using brainstorming techniques with sticky notes.

A common technique for exploring data, identifying themes, and looking for an overall narrative is to create an *affinity diagram*. The approach seeks to organize individual ideas and insights into a hierarchy showing common structures and themes. Notes are grouped together when they are similar in some fashion. The groups are not predefined, but rather they emerge from the data. This process was originally introduced into the software quality community from Japan, where it is regarded as one of the seven quality processes. The affinity diagram is built gradually. One note is put up first, and then the team searches for other notes that are related in some way.

Affinity diagrams are used in Contextual Design (Beyer and Holtzblatt, 1998; Holtzblatt, 2001), but they have also been adopted widely in interaction design (Lucero, 2015). For example, Madeline Smith et al. (2018) conducted interviews to design a web app for co-watching videos across a distance, and they used affinity diagramming to identify requirements from interviewee transcripts (see [Figure 9.4](#c09-fig-0004)). Despite the prevalence of digital collaboration tools, the popularity of physical affinity diagramming using sticky notes drawn by hand, has persisted for many years (Harboe and Huang, 2015).

![Photo depicts section of an affinity diagram built during an investigation of web app development.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f004.jpg)

Figure 9.4 Section of an affinity diagram built during the design of a web application Source: Smith (2018). Used courtesy of Madeline Smith

### 9.4.2 Categorizing Data

Inductive analysis is appropriate when the study is exploratory, and it is important to let the themes emerge from the data itself. Sometimes, the analysis frame (the set of categories used) is chosen beforehand, based on the study goal. In that case, analysis proceeds deductively. For example, in a study of novice interaction designer behavior in Botswana, Nicole Lotz et al. (2014) used a set of predetermined categories based on Schön (1983)'s design and reflection cycle: naming, framing, moving, and reflecting. This allowed the researchers to identify detailed patterns in the designers' behavior, which provided implications for education and support.

To illustrate categorization, we present an example derived from a set of studies looking at the use of different navigation aids in an online educational setting (Ursula Armitage, 2004). These studies involved observing users working through some online educational material (about evaluation methods), using the think-aloud technique. The think-aloud protocol was recorded and then transcribed before being analyzed from various perspectives, one of which was to identify usability problems that the participants were having with the online environment known as Nestor Navigator (Zeiliger et al., 1997). An excerpt from the transcription is shown in [Figure 9.5](#c09-fig-0005).

> I'm thinking that it's just a lot of information to absorb from the screen. I just I don't concentrate very well when I'm looking at the screen. I have a very clear idea of what I've read so far … but it's because of the headings I know OK this is another kind of evaluation now and before it was about evaluation which wasn't anyone can test and here it's about experts so it's like it's nice that I'm clicking every now and then coz it just sort of organizes the thoughts. But it would still be nice to see it on a piece of paper because it's a lot of text to read.  
> 
> Am I supposed to, just one question, am supposed to say something about what I'm reading and what I think about it the conditions as well or how I feel reading it from the screen, what is the best thing really?  
> 
> *Observer: What you think about the information that you are reading on the screen … you don't need to give me comments … if you think this bit fits together*.  
> 
> There's so much reference to all those previously said like I'm like I've already forgotten the name of the other evaluation so it said unlike the other evaluation this one like, there really is not much contrast with the other it just says what it is may be … so I think I think of …  
> 
> Maybe it would be nice to have other evaluations listed to see other evaluations you know here, to have the names of other evaluations other evaluations just to, because now when I click previous I have to click it several times so it would be nice to have this navigation, extra links.

[**Figure 9.5**](#R_c09-fig-0005) Excerpt from a transcript of a think-aloud protocol when using an online educational environment. Note the prompt from the observer about halfway through.

*Source*: Armitage (2004). Used courtesy of Ursula Armitage

This excerpt was analyzed using a categorization scheme derived from a set of negative effects of a system on a user (van Rens, 1997) and was iteratively extended to accommodate the specific kinds of interaction observed in these studies. The categorization scheme is shown in [Figure 9.6](#c09-fig-0006).

1. **Interface Problems**
	1. 1.1. Verbalizations show evidence of dissatisfaction about an aspect of the interface.
		2. 1.2. Verbalizations show evidence of confusion/uncertainty about an aspect of the interface.
		3. 1.3. Verbalizations show evidence of confusion/surprise at the outcome of an action.
		4. 1.4. Verbalizations show evidence of physical discomfort.
		5. 1.5. Verbalizations show evidence of fatigue.
		6. 1.6. Verbalizations show evidence of difficulty in seeing particular aspects of the interface.
		7. 1.7. Verbalizations show evidence that they are having problems achieving a goal that they have set themselves, or the overall task goal.
		8. 1.8. Verbalizations show evidence that the user has made an error.
		9. 1.9. The participant is unable to recover from error without external help from the experimenter.
		10. 1.10. The participant suggests a redesign of the interface of the electronic texts.
2. **Content Problems**
	1. 2.1. Verbalizations show evidence of dissatisfaction about aspects of the content of the electronic text.
		2. 2.2. Verbalizations show evidence of confusion/uncertainty about aspects of the content of the electronic text.
		3. 2.3. Verbalizations show evidence of a misunderstanding of the electronic text content (the user may not have noticed this immediately).
		4. 2.4. The participant suggests re-writing the electronic text content.
	**Identified problems should be coded as \[UP, << problem no. >>\].**

[**Figure 9.6**](#R_c09-fig-0006) Criteria for identifying usability problems from verbal protocol transcriptions

*Source*: Armitage (2004). Used courtesy of Ursula Armitage

This scheme developed and evolved as the transcripts were analyzed and more categories were identified inductively. [Figure 9.7](#c09-fig-0007) shows the excerpt from [Figure 9.5](#c09-fig-0005) coded using this categorization scheme. Note that the transcript is divided up using square brackets to indicate which element is being identified as showing a particular usability problem.

\[I'm thinking that it's just a lot of information to absorb from the screen. **UP 1.1\]** \[ I just I don't concentrate very well when I'm looking at the screen **UP 1.1\]**. I have a very clear idea of what I've read so far … \[but it's because of the headings **UP 1.1\]** I know OK this is another kind of evaluation now and before it was about evaluation which wasn't anyone can test and here it's about experts so it's like it's nice that I'm clicking every now and then coz it just sort of organises the thoughts. **\[**But it would still be nice to see it on a piece of paper **UP 1.10\] \[**because it's a lot of text to read **UP 1.1\]**.  

Am I supposed to, just one question, am supposed to say something about what I'm reading and what I think about it the conditions as well or how I feel reading it from the screen, what is the best thing really?  

*Observer: What you think about the information that you are reading on the screen … you don't need to give me comments … if you think this bit fits together*.  

\[There's so much reference to all those previously said **UP2.1\] \[** like I'm like I've already forgotten the name of the other evaluation so it said unlike the other evaluation this one like, there really is not much contrast with the other it just says what it is may be … so I think I think of … **UP 2.2\]**  

\[Maybe it would be nice to have other evaluations listed to see other evaluations you know here, to have the names of other evaluations other evaluations **UP 1.10\]** just to, **\[**because now when I click previous I have to click it several times **UP 1.1, 1.7\] \[**so it would be nice to have this navigation, extra links UP 1.10\].

[**Figure 9.7**](#R_c09-fig-0007) The excerpt in [Figure 9.5](#c09-fig-0005) coded using the categorization scheme in [Figure 9.6](#c09-fig-0006)

*Source*: Armitage (2004). Used courtesy of Ursula Armitage

Having categorized the data, the results can be used to answer the study goals. In the earlier example, the study allowed the researchers to be able to quantify the number of usability problems encountered overall by participants, the mean number of problems per participant for each of the test conditions, and the number of unique problems of each type per participant. This also helped to identify patterns of behavior and recurring problems. Having the think-aloud protocol meant that the overall view of the usability problems could take context into account.

### 9.4.3 Critical Incident Analysis

Data gathering sessions can often result in a lot of data. Analyzing all of this data in any detail is very time-consuming and often not necessary. *Critical incident analysis* is one approach that helps to identify significant subsets of the data for more detailed analysis. This technique is a set of principles that emerged from work carried out in the United States Army Air Forces where the goal was to identify the critical requirements of good and bad performance by pilots (Flanagan, 1954). It has two basic principles: “(a) reporting facts regarding behavior is preferable to the collection of interpretations, ratings, and opinions based on general impressions; (b) reporting should be limited to those behaviors which, according to competent observers, make a significant contribution to the activity” (Flanagan, 1954, p. 355). In the interaction design context, the use of well-planned observation sessions satisfies the first principle. The second principle refers to critical incidents, that is, incidents that are significant or pivotal to the activity being observed, in either a desirable or an undesirable way.

In interaction design, critical incident analysis has been used in a variety of ways, but the main focus is to identify specific incidents that are significant and then to focus on these and analyze them in detail, using the rest of the data collected as context to inform interpretation. These may be identified by the users during a retrospective discussion of a recent event or by an observer either through studying video footage or in real time. For example, in an evaluation study, a critical incident may be signaled by times when users were obviously stuck—usually marked by a comment, silence, looks of puzzlement, and so on. These are indications only. Whether the incident is significant enough to be worthy of further investigation depends on the severity of the problem identified.

Tuomas Kari et al. (2017) used the critical incident technique in a study of the location-based augmented reality game Pokémon GO. They were interested in identifying the types of behavior change that playing the game induced in players. To do this, they distributed a survey through social media channels asking experienced players to identify and describe one outstanding positive or negative experience. The 262 valid responses were themed and categorized into eight groups. Apart from expected behavior change such as increased physical activity, they also found that players were more social, found their routines more meaningful, expressed more positive emotions, and were more motivated to explore their surroundings. In another study, Elise Grison et al. (2013) used the critical incident technique to investigate specific factors that influence travelers' choices of transport mode in Paris in order to adapt new tools and services for mobility, such as dynamic route planners. Participants were asked to report on positive and negative real events they experienced in the context of their route to work or study, and whether they regretted or were satisfied with this choice of transport. Their findings included that contextual factors have a great influence on choice, that people were more likely to choose an alternative route to return home than when setting out, and that emotional state is important when planning a route.

## 9.5 Which Kind of Analytic Framework to Use?

There are several different analytical frameworks that can be used to analyze and interpret data from a qualitative study. In this section, six different approaches are outlined, ordered roughly in terms of their granularity, that is, the level of detail involved. For example, conversation analysis has a fine level of granularity, and it allows the details of what is said and how during a short fragment of conversation to be examined, while systems-based frameworks take a broader scope and have a coarser level of granularity, such as what happens when a new digital technology is introduced into an organization, like a hospital. Conversation analysis may result in insights related to users' interactions through a collaboration technology, while systems-based analyses may result in insights related to changes in work practices, worker satisfaction, improvements in workflow, impact on an office culture, and so on. [Table 9.5](#c09-tbl-0005) lists the six approaches in terms of the main types data, focus, expected outcomes, and level of granularity.

[**Table 9.5**](#R_c09-tbl-0005) Overview of analytical frameworks used in interaction Design

| Framework | Data | Focus | Expected outcomes | Level of granularity |
| --- | --- | --- | --- | --- |
| Conversation analysis | Recordings of spoken conversations | How conversations are conducted | Insights into how conversations are managed and how they progress | Word-level, or finer, for instance, pauses and inflection |
| Discourse analysis | Recordings of speech or writing from individuals or several participants | How words are used to convey meaning | Implicit or hidden meanings in texts | Word, phrase, or sentence-level |
| Content analysis | Any form of “text” including written pieces, video and audio recordings, or photographs | How often something is featured or is spoken about | Frequency of items appearing in a text | A wide range of levels from words, to feelings or attitudes, to artifacts or people |
| Interaction analysis | Video recordings of a naturally-occurring activity | Verbal and non-verbal interactions between people and artifacts | Insights about how knowledge and action are used within an activity | At the level of artifact, dialogue, and gesture |
| Grounded theory | Empirical data of any kind | Constructing a theory around the phenomenon of interest | A theory grounded in empirical data | Varying levels, depending on the phenomenon of interest |
| Systems-based frameworks | Large-scale and heterogeneous data | Large-scale involving people and technology, such as a hospital or airport | Insights about organizational effectiveness and efficiency | Macro-level, organizational level |

### 9.5.1 Conversation Analysis

*Conversation analysis* (CA) examines the semantics of a conversation in fine detail. The focus is on how a conversation is conducted (Jupp, 2006). This technique is used in sociological studies, and it examines how conversations start and how turn-taking is structured, together with other rules of conversation. It has been used to analyze interactions in a range of settings, and it has influenced designers' understanding of users' needs in these environments. It can also be used to compare conversations that take place through different media, for example, face-to-face conversations versus those conducted through social media. More recently, it has been used to analyze the conversations that take place with voice-assisted technologies and chatbots.

*Voice assistants* (also called smart speakers), like Amazon Echo, have become increasingly popular in domestic settings, providing a limited kind of conversational interaction, mainly by answering questions and responding to requests. But how do families orient and adapt to them? Does using this device change the way they talk, or do they talk to the device as if it was another human being?

Martin Porcheron et al. (2018) carried out a study examining how such devices were being used by families in their own homes, and they used conversation analysis with excerpts from selected conversations. A sample fragment of a conversation they analyzed is presented in [Figure 9.8](#c09-fig-0008). This uses a particular type of syntax for marking up the minutiae of interactions and speech that took place during an approximate 10-second period. Square parentheses are used to show overlapping talk, round parentheses to indicate a pause, and physical spacing to show temporal sequencing of what is said. This level of detail enables the analysis to reveal subtle cues and mechanisms that are used during the conversations.

```
01  SUS   i’d like to play beat the intro in a minute
02  LIA     [ oh no: ]
03  SUS   [ alexa   ][ (1.1)  ] beat the in[tro
04  CAR                [   °yeah°; ] 
05  LIA                                                   [°no:::…°
06  CAR   (0.6) it’s mother’s day? (0.4)
07  SUS   it’s (     ) yep (.) listen (.) you need to keep
08        on eating your orange stuff (.) liam
09        (0.7)
10  CAR   and your green stuff
11  SUS   alexa (1.3) alexa (0.5)=
12  CAR                                       =°and your brown stuff
13  SUS   play beat the intro
```

[**Figure 9.8**](#R_c09-fig-0008) An extract of the conversation between the family and Alexa, marked up for conversation analysis

*Source*: Porcheron et al. (2018), fragment 1. Reproduced with permission of ACM Publications

In this fragment, Susan (who is the mother) announces to Liam (her son) and Carl (the father) her desire to play a particular game (called Beat the Intro) with their Amazon Echo. Liam does not want to play (expressed by his long “no” cry in response). Susan, however, has already called “Alexa” to wake up the device. Carl shows his support for her, as indicated by his quick “yeah” during the pause after she says “Alexa.” Alexa, however, appears not to respond. At this point, Susan returns to the ongoing family conversation, telling Liam to keep eating his “orange stuff.” Carl also chips in after her and says to Liam that he should also eat the “green stuff.” At the same time, Susan has another go at getting Alexa to wake up. She calls out “Alexa” twice in a questioning voice. In the pause between Susan's two calls to Alexa, Carl tells Liam to keep eating again, but this time the “brown stuff.” Having succeeded in waking up Alexa, Susan then asks it to play the game.

So, what insights does this fine level of analysis provide? Martin Porcheron et al. (2018) point out that it demonstrates how a family's interaction with the Amazon Echo is seamlessly interwoven with other ongoing activities, in this case, the parents trying to get their child to eat his food. At a more general level, it illustrates how our conversations with each other and voice-assisted technologies interleave in nuanced ways rather than being separate conversations between members of the family or the family and the device, which jump from one to another. They also show how their analysis led them to think that the term *conversational interaction* fails to distinguish between the interactional embeddedness of voice-assisted interfaces and human conversation. Instead, they suggest that current voice-assisted technologies be designed using a conceptual model, more akin to instructing rather than conversing.

### 9.5.2 Discourse Analysis

*Discourse analysis* focuses on dialogue, in other words, the meaning of what is said and how words are used to convey meaning. Discourse analysis is strongly interpretive, pays great attention to context, and views language not only as reflecting psychological and social aspects but also as constructing them (Coyle, 1995). An underlying assumption of discourse analysis is that there is no objective scientific truth. Language is a form of social reality that is open to interpretation from different perspectives. In this sense, the underlying philosophy of discourse analysis is similar to that of ethnography. Language is viewed as a constructive tool, and discourse analysis provides a way of focusing on how people use language to construct versions of their worlds (Fiske, 1994).

Small changes in wording can change meaning, as the following excerpts indicate (Coyle, 1995):

> ***Discourse analysis is what you do when you are saying that you are doing discourse analysis…***
> 
> ***According to Coyle, discourse analysis is what you do when you are saying that you are doing discourse analysis…***

By adding just three words, “According to Coyle,” the sense of authority changes, depending on what the reader knows about Coyle's work and reputation.

Discourse analysis is useful when trying to identify subtle and implicit meaning in what people are writing about, what is trending, what is fake news, and so on. It can be used with data from interviews; in social media such as Facebook, Twitter, and WhatsApp; and in emails. For example, Carlos Roberto Teixeira et al. (2018) proposed a taxonomy for analyzing tweets as a way of understanding the types of conversations that take place online and identifying patterns of behavior within them. The tweets they analyzed were those posted during the political scandals that were happening in Brazil during 2016. Using discourse analysis and by understanding the cultural background and how technology was adopted and used by the Brazilian society, they were able to interpret the meaning of the tweets, beyond the words that were said.

They scraped the raw data of the tweets from the web and ranked them in order of those most retweeted. Then they selected 100 of the most influential postings, which were messages that had been retweeted between 9,000 and 47,000 times. Finally, they manually classified the tweets using Excel spreadsheets, identifying the most dominant discourse characteristics. They note, however, that since the most retweeted messages are often captured out of context (that is, outside the conversational thread), they had problems sometimes interpreting what was the context, such as the particular news story associated with a tweet.

The tweets were then classified into a number of provisional themes that were whittled down to five general ones. These were (1) “support” (tweets that promote either side of the political dispute); (2) “criticism and protest” (tweets that showed disapproval or an objection); (3) “humor” (tweets that were witty and had cartoons or jokes in them); (4) “news” (tweets that refer to the news that were neutral in tone); and (5) “neutral” (tweets that were indifferent or their position could not be inferred). For reliability, two different researchers classified each tweet using these themes. Once classified, the data was analyzed using descriptive statistics and simple visualizations, like word (or tag) clouds and pie charts. These allowed them to draw conclusions about the tweets that they had analyzed, including the relative size of the different themes and how the size changed over time. Tweets in the criticism and protest theme were the most popular overall, followed by humor. More generally, they discuss how this kind of discourse analysis shows that humor, protest, and criticism are highly dominant in this kind of online discourse. They suggest that people who tweet often express their feelings about ongoing political events, in terms of criticism and humor, in equal measures. Moreover, they found that tweets including images, videos, and animated GIFs were most frequently classified as humor.

This kind of analysis of public discourse, when done by hand, is extremely time-consuming. To help, there are new software tools being developed that can automatically process computer-mediated discourses (Ecker, 2016). The advantage, as you will see in the next chapter, is that much larger data sets can be analyzed. The downside is that the analyst is no longer “hands-on” and loses touch with the surrounding context, meaning different interpretations arise.

### 9.5.3 Content Analysis

*Content analysis* typically involves classifying the data into themes or categories and then studying the frequency of category occurrences (Krippendorff, 2013). The technique can be used for any text, where “text” refers to a range of media including video, newspapers, advertisements, survey responses, images, sounds, and so on. It can be used to analyze any online content, including the text of tweets, links, animated gifs, videos, and images. For example, Mark Blythe and Paul Cairns (2009) analyzed 100 videos from a YouTube search by relevance for “iPhone 3G” using content analysis. They categorized the videos into seven categories: review, reportage, “unboxing,” demonstration, satire, advertisement, and vlog commentaries (such as, complaints about queues). Similar to discourse analysis, an important aspect of content analysis is how it considers the wider context.

Content analysis is often used in conjunction with other analysis techniques as well. For example, Weixin Zhai and Jean-Claude Thill (2017) analyzed social media data from Weibo (the Chinese equivalent of Twitter) to investigate the emotions, attitudes, and views of citizens around a rainstorm that hit Beijing on July 21, 2012, causing 79 deaths. They used content analysis alongside *sentiment analysis*, an approach that extracts emotional and subjective information from natural language. From their results, they found how feelings of sorrow and sadness were shared across the entire city because of the trauma associated with entrapment indoors during the deluge.

### 9.5.4 Interaction Analysis

*Interaction analysis* was developed by Brigitte Jordan and Austin Henderson (1995) as a way of investigating and understanding the interactions of human beings with each other and objects in their environment. The technique focuses on both talk and nonverbal interactions with artifacts and technologies, and it is based on video recordings. An underlying assumption of this approach is that knowledge and action are fundamentally social. The goal is to derive generalizations from videos of naturally occurring activities, focusing on how the people being observed make sense of each other's actions and their collective achievements.

Interaction analysis is an inductive process, where teams of researchers suggest statements about general patterns from multiple examples of empirical observations. Rather than individual researchers conducting separate analyses and then comparing their results for consistency, interaction analysis is conducted collaboratively; teams discuss together their observations and interpretations of the videos being watched as they watch them. The first step involves creating a content log, comprising headings and rough summaries of what has been observed. No predetermined categories are used during this stage. Instead, they emerge from repeated playing and discussion of the video material. Hypotheses are also generated by group members about what they think is happening. This process includes suggesting the intentions, motivations, and understandings of the people who are being viewed in the videos. These suggestions have to be tied to the actions of the people rather than being purely speculative. For example, if an analyst thinks someone's motivation is to take control during a board meeting, they need to provide actual examples that demonstrate how the person is achieving this (for instance, taking over the data projector, as the locus of control, for long periods of time and presenting their ideas for others to view).

The videos are then *cannibalized*, as it is called, by extracting interesting materials, reclassifying some of them in terms of what they represent, while removing others. Instances of a salient event are assembled and played one after another to determine whether a phenomenon is a robust theme or a one-off incident. An example Brigitte Jordon and Austin Henderson (1995) use to illustrate this process is their study of people around a pregnant woman who was having her first contraction. They noticed that, at the point of the first contraction, the medical staff and family all shifted their attention away from the woman to the monitoring equipment. They were able to find many more examples of this phenomenon, providing strong evidence that the presence of high-tech equipment changes the practice of caregiving, specifically that caregiving is mediated by the real-time data presented through the equipment.

An example of where interaction analysis has been used in HCI is Anna Xambo et al.'s (2013) study of how groups of musicians improvise and learn to play together when using a novel collaborative tabletop technology. Video data was collected for four groups of musicians using this technology in a number of jamming sessions. Representative video extracts were repeatedly viewed and discussed by a team of researchers, focusing on verbal communication and nonverbal communication themes. These themes were categorized into whether they were musical, physical, or interface-related. The themes that arose during the repeated video viewing process were diverse, including error/repair situations, territory-related behaviors, emergent coordination mechanisms, and mimicking behaviors. Anna Xambo et al. (2013) then transformed these into a set of design considerations for developing tabletop technologies to support hands-on collaborative learning.

### 9.5.5 Grounded Theory

The goal of *grounded theory* is to develop theory from a systematic analysis and interpretation of empirical data; that is, the derived theory is grounded in the data. In this respect, it is an inductive approach to developing theory. The approach was originally developed by Barney Glaser and Anselm Strauss (1967) and since then has been adopted by several researchers, with some adaptations to different circumstances. In particular, both of them have individually (and with others) developed grounded theory in slightly different ways, but the objective of this approach remains the same. Barney Glaser (1992) provides further information about the differences and areas of controversy.

In this context, theory is: “a set of well-developed concepts related through statements of relationship, which together constitute an integrated framework that can be used to explain or predict phenomena” (Strauss and Corbin, 1998). Development of a “grounded” theory progresses through alternating data collection and data analysis: first data is collected and analyzed to identify themes, then that analysis may lead to further data collection and analysis to extend and refine the themes, and so on. During this cycle, parts of the data may be reanalyzed in more detail. Data gathering and subsequent analysis are hence driven by the emerging theory. This approach continues until no new insights emerge and the theory is well-developed. During this process, the researcher seeks to maintain a balance between objectivity and sensitivity. Objectivity is needed to maintain accurate and impartial interpretation of events; sensitivity is required to notice the subtleties in the data and identify relationships between concepts.

The thrust of the analysis undertaken is to identify and define the properties and dimensions of relevant themes called *categories* in grounded theory. According to Juliet Corbin and Anselm Strauss (2014), this coding has three aspects, which are iteratively performed through the cycle of data collection and analysis:

1. *Open coding* is the process through which categories, their properties, and dimensions are discovered in the data. This process is similar to our discussion of thematic analysis above, including the question of granularity of coding (at the word, line, sentence, conversation level, and so on).
2. *Axial coding* is the process of systematically fleshing out categories and relating them to their subcategories.
3. *Selective coding* is the process of refining and integrating categories to form a larger theoretical scheme. The categories are organized around one central category that forms the backbone of the theory. Initially, the theory will contain only an outline of the categories, but as more data is collected, they are refined and developed further.

Early books on grounded theory say little about what data collection techniques should be used but focus instead on the analysis. Some later books place more emphasis on data collection. For example, Kathy Charmaz (2014) discusses interviewing techniques and collection and analysis of documents for grounded theory analysis. When analyzing data, Juliet Corbin and Anselm Strauss (2014) encourage the use of written records of analysis and diagrammatic representations of categories (which they call *memos* and *diagrams*). These memos and diagrams evolve as data analysis progresses. Some researchers also look to digital tools such as spreadsheets and diagramming tools, but many like to develop their own physical code books such as the one Dana Rotman et al. (2014) constructed in a study to understand the motivations of citizens to contribute to citizen science projects. The data that she analyzed was derived from in-depth semistructured interviews of 33 citizen scientists and 11 scientists from the United States, India, and Costa Rica (see [Figure 9.9](#c09-fig-0009)).

![Screenshot of code book used in a grounded theory analysis of citizens' motivations to contribute to citizen science.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f009.jpg)

Figure 9.9 Code book used in a grounded theory analysis of citizens' motivations to contribute to citizen science Source: Jennifer Preece

The following analytic tools are used to help stimulate the analyst's thinking and identify and characterize relevant categories:

1. The Use of Questioning: In this context, this refers to questioning the data, not your participants. Questions can help an analyst to generate ideas or consider different ways of looking at the data. It can be useful to ask questions when analysis appears to be in a rut.
2. Analysis of a Word, Phrase, or Sentence: Considering in detail the meaning of an utterance can also help to trigger different perspectives on the data.
3. Further Analysis Through Comparisons: Comparisons may be made between objects or between abstract categories. In either case, comparing one with the other brings alternative interpretations.

Grounded theory uses thematic analysis that is, themes are identified from the data, but as data analysis informs data collection, it also relies on categorizing new data according to the existing thematic set and then evolving that set to accommodate new findings. As Victoria Braun and Victoria Clarke (2006) point out, “Thematic analysis differs from other analytic methods that seek to describe patterns across qualitative data … such as grounded theory \<which is> theoretically bounded… the goal of a grounded theory analysis is to generate a plausible—and useful—theory of the phenomena that is grounded in the data.”

#### A Grounded Theory Example

So-called idle games are rising in popularity (Cutting et al., 2019). *Idle games* are minimalist games that require little or even no interaction in order for the game to progress. For example, an idle game may involve repeating a simple action like clicking an icon to accumulate resources. Example games include the Kittens Game, which is a text-based (that is, it has no graphical user interface) game that involves managing a village of kittens, while Cookie Clicker involves baking and selling cookies. Idle games also include mechanisms to automate game play so that progress may continue for extended periods of time without the player doing anything (Purkiss and Khaliq, 2015). An extreme example studied by Joe Cutting et al. (2019) is Neko Atsume, a game about collecting cats, in which progress can be made only if the game is switched off. In their study, they were interested in the notion of “engagement” and the implications of this new genre of games for current theories of engagement.

To understand more about the idle games genre, Sultan Alharthi et al. (2018) used grounded theory, specifically to develop a taxonomy and a set of characteristics for them. By defining the essential features of this genre of games and clustering them, the authors hoped to produce design implications for each type of game.

The three stages of coding, open, axial, and selective are illustrated in [Figure 9.10](#c09-fig-0010). Note that, in this case, the research started by the researchers playing each of the games under study.

![Flow chart depicting the process used by Alharthi et al., showing Phase 2 and Phase 3 using the three stages of grounded theory coding.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f010.jpg)

Figure 9.10 The process used by Alharthi et al., showing Phase 2 and Phase 3 using the three stages of grounded theory coding

Each game was played by two researchers who recorded their observations in a spreadsheet. These observations focused on gameplay, game mechanics, rewards, interactivity, progress rate, and game interface. Then they rated the games using an 11-point interactivity scale (0–10) where 0 meant that play progressed without any interaction of the player, while 10 meant that the game progressed only slowly without player interaction. Progress through the levels of the game were also rated on the same scale.

At the end of each game session and observation, the researchers wrote a brief overview of the game and conducted preliminary open coding of their observations (see [Figure 9.11](#c09-fig-0011) for an example of preliminary open coding).

| Game Feature | Observations |
| --- | --- |
| Game name | *AdVenture Capitalist* \[G38\] |
| Play description | You start CLICKING on a lemonade stand and collect money. Spend money to make upgrades, INCREASE PRODUCTION PER CLICK. Start hiring workers and INCREASE PRODUCTION PER SECOND. When you have enough money, you can buy new businesses, automate all your businesses to INCREMENT more money, and leave the game progress. |
| Game mechanics | Click to gain money, AUTOMATE production, make upgrades to DAMAGE/SEC. |
| Rewards | ONE CURRENCY, which is money, is rewarded in return. |
| Interface | GRAPHICAL |
| Interactivity level | 7 |
| Progress rate | 9 |
| Overview | This is a SINGLE-PLAYER game, which requires LONG CYCLES OK CLICKING at the start, and making a number of upgrades. Production rate reaches $390/sec in less that 10 minutes and you gain 1M in cash making the game progress faster. |

[**Figure 9.11**](#R_c09-fig-0011) An illustration of preliminary open coding. Words in small capitals are identified by the researcher as potential codes.

Axial and selective coding progressed iteratively. The researchers held several discussion sessions to explore the relationship between the codes, the emergent concepts, and the initial categories. During this process, some of the games were re-observed, and related literature was drawn upon to help refine the concepts. For example, existing literature on game taxonomies, prior terms, and definitions related to idle games were incorporated into the analysis. Based on this analysis, Sultan Alharthi et al. produced a taxonomy with two basic ways to characterize the games: one based on key features and one based on interactivity. From the former, they defined incremental games as idle games in which a player selects resources to generate, waits for them to accumulate, and spends the resources to automate resource generation. [Figure 9.12](#c09-fig-0012) illustrates the open codes, resulting concepts, and categories developed for incremental games. This shows that four categories of incremental games emerge from this analysis: micromanagement, derivative, single-resource, and multiplayer.

![Flow chart depicting the grounded theory process showing the development of open coding, through concepts to categories.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f012.jpg)

Figure 9.12 The grounded theory process showing the development of open coding, through concepts to categories

One of the surprises from their analysis is that the resulting taxonomy is based on game rules and their basic underlying structure rather than mechanisms in the game. This is in contrast to other gaming taxonomies that feature interactivity and interaction strategies. Of course, idle games are minimal, and so they don't have much interaction. However, the grounded theory approach allowed the development of a taxonomy that reflects the style and purpose of the genre.

### 9.5.6 Systems-Based Frameworks

For large projects where the researcher is interested in investigating how a new technology should best be introduced and what its impact is afterward, it is necessary to analyze many sources of data collected over a long period of time. Conducting analyses of small fragments of conversation or identifying themes from interviews may be useful for highlighting specific working practices, but understanding how a whole socio-technical system (for example a hospital, corporation, local council, or airport) works at scale requires a different kind of analytical framework. Two such frameworks are introduced next: socio-technical systems theory (Eason, 1987) and distributed cognition (Hutchins, 1995), as applied through the Distributed Cognition of Teamwork framework (Furniss and Blandford, 2006).

#### Socio-technical Systems Theory

*Socio-technical systems (STS) theory* makes explicit the fact that the technology and the people in a work system are interdependent (Klein, 2014). Rather than trying to optimize either the technical system or the social system independently of each other, STS suggests that this interdependency be recognized, and the “system” be treated as a whole. The ideas behind socio-technical theory were first conceptualized around coal mining in the 1950s (see Trist and Bamford, 1951, for example), but it also has a long history of being applied in hospitals and healthcare settings (Waterson, 2014) as well as manufacturing and social media systems. Martin Maguire (2014) highlights the importance of the socio-technical perspective with the rise of virtual organizations. Ken Eason (2014) identifies five significant and enduring aspects of STS theory (Eason, 2014):

1. **Task interdependencies:** If people are focused on one large task, then the division of subtasks between them inevitably sets up interdependencies that are critical to understand. Understanding these interdependencies is particularly useful for recognizing the implications of change.
2. **Socio-technical systems are “open systems”:** STS are influenced by environmental factors including physical disturbances and financial, market, regulatory, and technical developments.
3. **Heterogeneity of system components:** The overall task is undertaken by humans in the social subsystem using technical resources in the technical subsystem. Both need to be resilient. Technical components can evolve while humans can learn, develop, and change the technical components to address challenges of the future.
4. **Practical contributions:** STS theory is making practical contributions in analysis of existing systems, summative evaluation of a major change, through potentially predicting challenges before changes are made, and in designing socio-technical systems that are co-optimized.
5. **Fragmentation of design processes:** In a complex socio-technical system, there are different design processes, and these can result in fragmentation. Flexibility in specification, local focus in design, user-centered design, and system evolution will help overcome these.

STS is a philosophy rather than a concrete set of methods or analytical tools. But several socio-technical design methods provide more concrete tools for using a socio-technical framework. For example, see Baxter and Sommerville (2011) and Mumford (2006).

#### Distributed Cognition of Teamwork

*Distributed cognition and Distributed Cognition of Teamwork* (DiCoT) were introduced in [Chapter 4](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c04.xhtml), “Cognitive Aspects,” as an approach to studying the nature of cognitive phenomena across individuals, artifacts, and internal and external representations. Investigating how information is propagated through different media is a key goal of this approach, and while distributed cognition provides a good theoretical framework for analyzing systems, it can be difficult to apply in practice. The DiCoT framework was developed as a method to support the application of distributed cognition. It provides a framework of models that can be constructed from a set of collected data, for example ethnographic, interview transcripts, artifacts, photographs, and so on. Underlying each model is a set of principles distilled from the distributed cognition theory. The models are as follows:

- *An information flow model that shows how information flows through the system and is transformed*. This model captures the information channels and hubs together with the sequence of activities and communication between different team roles.
- *A physical model that captures how physical structures support communication between the team roles and facilitates access to artifacts*. This model helps to describe the factors that influence the performance of the system at a physical level.
- *An artifact model that captures how artifacts in this system support cognition*. This model can be used to represent the key characteristics of an artifact and how its design, structure, and use can support team members.
- *A social structure model that examines how cognition is socially distributed*. This model maps the social structures to the goal structures, shows how work is shared, and can be used to consider the robustness of the system.
- *A system evolution model that depicts how the system has evolved over time*. This model provides some explanation for why the work is the way it is. Any design recommendations need to take this context into account.

While the form of the models is not prescribed, the underlying principles support the models' development. For example, underlying the physical model are principles such as the following:

- **Horizon of observation:** What an individual can see or hear.
- **Perceptual:** How spatial representations aid computation.
- **Arrangement of equipment:** How the physical arrangement of the environment affects access to information.

DiCoT has been used to understand collaborative work in remote and co-located software development teams, as shown in [Figure 9.13](#c09-fig-0013) (Deshpande et al., 2016; Sharp et al. 2009), and has been found to be especially useful for studying how medical teams work and manage with ever-changing technologies that are introduced into their work environment. For example, Atish Rajkomar and Ann Blandford (2012) examined how healthcare technologies are used; specifically, they examined the use of infusion pumps by nurses in an intensive care unit (ICU). They gathered data through ethnographic observations and interviews, which they analyzed by constructing representational models that focused on information flows, physical layouts, social structures, and artifacts. They note that “the findings showed that there was significant distribution of cognition in the ICU: socially, among nurses; physically, through the material environment; and through technological artefacts.” Based on the results of this study, they were able to suggest changes that would improve the safety and efficiency of the nurses' interactions with the infusion technology.

![Screenshot of an information flow diagram from a DiCoT analysis of software development remote work, based on ethnographic data.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c09f013.jpg)

Figure 9.13 An information flow diagram from a DiCoT analysis of software development remote work, based on ethnographic data

## 9.6 Tools to Support Data Analysis

While it is possible to perform these kinds of data analysis using only manual techniques, most people would agree that it is quicker, easier, and more accurate to use a software tool of some kind in the majority of cases. Using a simple spreadsheet application is surprisingly effective, but there are other more sophisticated tools available to support the organization, coding, and manipulation of data, and to perform statistical tests.

Tools in the former category (to support the organization of data) include facilities for categorization, theme-based analysis, and quantitative analysis. These typically provide facilities to associate labels (categories, themes, and so on) with sections of data, search the data for key words or phrases, investigate the relationships between different themes or categories, and help to develop the coding scheme further. Some tools can also generate graphical representations. In addition, some provide help with techniques such as content analysis and sometimes mechanisms to show the occurrence and co-occurrence of words or phrases. In addition, searching, coding, project management, writing and annotating, and report generation facilities are common.

Two well-known tools that support some of these data analysis activities are Nvivo and Dedoose. For example, Nvivo supports the annotation and coding of data including PDF documents, photos, and video and audio files. Using Nvivo, field notes can be searched for key words or phrases to support coding or content analysis; codes and data can be explored, merged, and manipulated in several ways. The information can also be printed in a variety of forms such as a list of every occasion a word or phrase is used in the data, and a tree structure showing the relationships among codes. Like all software packages, Nvivo has advantages and disadvantages, but it is particularly powerful for handling large sets of data and can generate output for statistical packages such as SAS and SPSS.

Statistical Analysis Software (SAS) and Statistical Package for the Social Sciences (SPSS) are popular quantitative analysis packages that support the use of statistical tests. SPSS, for example, is a sophisticated package offering a wide range of statistical tests such as frequency distributions, rank correlations (to determine statistical significance), regression analysis, and cluster analysis. SPSS assumes that the user knows and understands statistical analysis.

Additional tools to support the analysis of very large sets of data are discussed in [Chapter 10](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c10.xhtml), “Data at Scale.”

## 9.7 Interpreting and Presenting the Findings

Previous sections in this chapter have illustrated a range of different ways to present findings—as tables of numbers and text, through various graphical devices and diagrams, as a set of themes or categories, and so on. Choosing an appropriate way to present the findings of a study is as important as choosing the right analytical approach. This choice will depend on the data gathering and analysis techniques used as well as the audience and the original goals of the study. In some situations, the details of data collection and analysis will be needed, for example, when working with others to make sense of a large collection of data, or when trying to convince an audience about a controversial conclusion. This detail may include snippets of data such as photographs of the context of use or videos of participants using the product. In other situations, only the salient trends, headlines, and overall implications are needed, so the style of presentation can be leaner. Where possible, a set of different complementary representations will be chosen to communicate the findings since any one representation will emphasize some aspects and de-emphasize others.

This section focuses on three kinds of presentation styles that haven't yet been emphasized to this point: using structured notations, stories, and summarizing.

### 9.7.1 Structured Notations

A number of *structured notations* have been developed to analyze, capture, and present information for interaction design. These notations follow a clear syntax and semantics, which have been developed to capture particular viewpoints. Some are relatively straightforward, such as the work models promoted in contextual design (Beyer and Holtzblatt, 1998) that use simple conventions for representing flows, breakdowns, individual roles, and so on. Others, such as the modeling language Unified Modeling Language (UML), have stricter and more precise syntax to be followed and are often used to represent requirements (see [Chapter 11](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c11.xhtml), “Discovering Requirements”); the activity diagrams, for example, are very expressive when detailed interactions need to be captured.

Advantages of using a structured notation are that the meaning of different symbols is well-defined, and so it provides clear guidance on what to look for in the data and what to highlight and that it enforces precision in expression. Disadvantages include that by highlighting specific elements, it inevitably de-emphasizes or ignores other aspects, and the precision expressed by the notation may be lost on an audience if they don't know the notation well. Producing diagrams or expressions in these notations may require further analysis of the findings in order to identify the specific characteristics and properties that the notation highlights. To overcome these disadvantages, structured notations are usually used in combination with stories or other easily accessible formats.

### 9.7.2 Using Stories

*Storytelling* is an easy and intuitive approach for people to communicate ideas and experiences. It is not surprising then that stories (also called *narratives*) are used extensively in interaction design, both to communicate findings of investigative studies and as the basis for further development, such as product design or system enhancements.

Storytelling may be employed in three different ways. First, participants (such as interviewees, questionnaire respondents, and those you have observed) may have told stories of their own during data gathering. These stories can be extracted, can be compared, and may be used to communicate findings to others, for example, to illustrate points.

Second, stories (or narratives) based on observation, such as ethnographic field studies, may be employed for further data gathering. For example, Valeria Righi et al. (2017) used stories as the basis of co-design workshops in their study to explore the design and use of technologies to support older people. The scenarios were developed on the basis of ethnographic studies and previous co-design activities and were presented through storytelling to facilitate understanding. Note that, in this case, the audience was a group of participants in the ongoing study.

Including specific stories gives authenticity to the findings, and it can add to its credibility provided the conclusions are not overstated. Making a multimedia presentation of the story by adding video or audio excerpts and photographs will illustrate the story further. This kind of approach can also be effective if presenting data from an evaluation study that involves observation, as it is hard to contest well-chosen video excerpts of users interacting with technology or extracts from interview transcripts.

Third, stories may be constructed from smaller snippets or repeated episodes that are found in the data. In this case, stories provide a way of rationalizing and collating data to form a representative account of a product's use or a certain type of event.

Any stories collected through data gathering may be used as the basis for constructing scenarios that can then be used for requirements and design activities. See [Chapters 11](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c11.xhtml) and [12](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c12.xhtml) for more information on scenarios.

### 9.7.3 Summarizing the Findings

Presentation styles will usually be used in combination to produce a summary of the findings; for instance, a story may be expanded with graphical representations of activity or demographics, and data excerpts from transcripts or videos may be used to illustrate particular points. Tables of numerical data may be represented as graphs, diagrams, or rigorous notations, together with workflows or quotations.

Careful interpretation and presentation of the study results is just as important as choosing the right analysis technique so that findings are not over-emphasized, and evidence is not misrepresented. Over-generalizing results without good evidence is a common pitfall, especially with qualitative analyses’ for example, think carefully before using words such as *most*, *all*, *majority*, and *none*, and be sure that the justifications reflect the data. As discussed in [Box 9.1](#c09-fea-0001), even statistical results can be interpreted in a misleading way. For example, if 8 out of 10 users preferred design A over design B, this does not mean that design A is 80 percent more attractive than design B. If you found 800 out of 1,000 users preferred design A, then you have more evidence to suggest that design A is better, but there are still other factors to consider.