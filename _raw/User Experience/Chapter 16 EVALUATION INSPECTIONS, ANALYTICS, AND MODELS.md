---
title: "Chapter 16: EVALUATION: INSPECTIONS, ANALYTICS, AND MODELS"
source: "https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c16.xhtml"
author:
  - "Helen Sharp"
  - "Jennifer Preece"
  - "Yvonne Rogers"
published: 2026-08-01
created: 2026-10-18
description: "Chapter 16EVALUATION: INSPECTIONS, ANALYTICS, AND MODELS16.1 Introduction16.2 Inspections: Heuristic Evaluation and Walk-Throughs16.3 Analytics and A/B testing16.4 Predictive Models..."
tags:
  - "ux"
citation: "Sharp, H., Preece, J., Rogers, Y., Preece, J. (2019). Interaction Design: Beyond Human-Computer Interaction. United Kingdom: Wiley."
---
## 16.1 Introduction

The evaluation methods described in this book so far have involved interaction with, or direct observation of, users. In this chapter, we introduce methods that are based on understanding users through one of the following:

- Knowledge codified in heuristics
- Data collected remotely
- Models that predict users' performance

None of these methods requires users to be present during the evaluation. Inspection methods often involve a researcher, sometimes known as an *expert*, role-playing the users for whom the product is designed, analyzing aspects of an interface, and identifying potential usability problems. The most well-known methods are *heuristic evaluation* and *walk-throughs*. *Analytics* involves user interaction logging, and *A/B testing* is an experimental method. Both analytics and A/B testing are usually carried out remotely. *Predictive modeling* involves analyzing the various physical and mental operations that are needed to perform particular tasks at the interface and operationalizing them as quantitative measures. One of the most commonly used predictive models is *Fitts' law*.

## 16.2 Inspections: Heuristic Evaluation and Walk-Throughs

Sometimes, it is not practical to involve users in an evaluation because they are not available, there is insufficient time, or it is difficult to find people. In such circumstances, other people, often referred to as *experts* or *researchers*, can provide feedback. These are people who are knowledgeable about both interaction design and the needs and typical behavior of users. Various inspection methods were developed as alternatives to usability testing in the early 1990s, drawing on software engineering practice where code and other types of inspections are commonly used. Inspection methods for interaction design include heuristic evaluations and walk-throughs, in which researchers examine the interface of an interactive product, often role-playing typical users, and suggest problems that users would likely have when interacting with the product. One of the attractions of these methods is that they can be used at any stage of a design project. They can also be used to complement user testing.

### 16.2.1 Heuristic Evaluation

In *heuristic evaluation*, researchers, guided by a set of usability principles known as *heuristics*, evaluate whether user-interface elements, such as dialog boxes, menus, navigation structure, online help, and so on, conform to tried-and-tested principles. These heuristics closely resemble high-level design principles (such as making designs consistent, reducing memory load, and using terms that users understand). Heuristic evaluation was developed by Jakob Nielsen and his colleagues (Nielsen and Mohlich, 1990; Nielsen, 1994a) and later modified by other researchers for evaluating the web and other types of systems (see Hollingshead and Novick, 2007; Budd, 2007; Pinelle et al., 2009; Harley, 2018). In addition, many researchers and practitioners have converted design guidelines into heuristics that are then applied in heuristic evaluation.

The original set of heuristics for HCI evaluation were empirically derived from the analysis of 249 usability problems (Nielsen, 1994b); a revised version of these heuristics follows (Nielsen, 2014: [useit.com](http://useit.com/)):

- **Visibility of System Status** The system should always keep users informed about what is going on, through appropriate feedback and within reasonable time.
- **Match Between System and the Real World** The system should speak the users' language, with words, phrases, and concepts familiar to the user, rather than system-oriented terms. It should follow real-world conventions, making information appear in a natural and logical order.
- **User Control and Freedom** Users often choose system functions by mistake and will need a clearly marked emergency exit to leave the unwanted state without having to go through an extended dialog. The system should support undo and redo.
- **Consistency and Standards** Users should not have to wonder whether different words, situations, or actions mean the same thing. The system should follow platform conventions.
- **Error Prevention** Rather than just good error messages, the system should incorporate careful design that prevents a problem from occurring in the first place. Either eliminate error-prone conditions or check for them and present users with a confirmation option before they commit to the action.
- **Recognition** Rather Than Recall Minimize the user's memory load by making objects, actions, and options visible. The user should not have to remember information from one part of the dialog to another. Instructions for use of the system should be visible or easily retrievable whenever appropriate.
- **Flexibility and Efficiency of Use** Accelerators—unseen by the novice user—may often speed up the interaction for the expert user such that the system can cater to both inexperienced and experienced users. Allow users to tailor frequent actions.
- **Aesthetic and Minimalist Design** Dialogs should not contain information that is irrelevant or rarely needed. Every extra unit of information in a dialog competes with the relevant units of information and diminishes their relative visibility.
- **Help Users Recognize, Diagnose, and Recover from Errors** Error messages should be expressed in plain language (not codes), precisely indicate the problem, and constructively suggest a solution.
- **Help and Documentation** Even though it is better if the system can be used without documentation, it may be necessary to provide help and documentation. Any such information should be easy to search, focused on the user's task, list concrete steps to be carried out, and not be too large.

Designers and researchers evaluate aspects of the interface against the appropriate heuristics. For example, if a new social media system is being evaluated, the designer might consider how users would add friends to their networks. Those doing the heuristic evaluation go through the interface several times, inspecting the various interaction elements and comparing them with the list of usability heuristics. During each iteration, usability problems will be identified and ways of fixing them may be suggested.

Although many heuristics apply to most products (for example, be consistent and provide meaningful feedback, especially if an error occurs), some of the core heuristics are too general for evaluating products that have come onto the market more recently, such as mobile devices, digital toys, social media, ambient devices, web services, and IoT. Many designers and researchers have therefore developed their own heuristics by tailoring Nielsen's heuristics with other design guidelines, market research, results from research studies, and requirements documents. The Nielsen/Norman Group has also taken a more detailed look at particular heuristics, such as the first heuristic listed above, “visibility of system status,” (Harley, 2018a), which focuses on communication and transparency.

Exactly which heuristics are appropriate and how many are needed for different products is debatable and depends on the goals of the evaluation. However, most sets have between 5 and 10 items. This number provides a good range of usability criteria by which to judge the various aspects of a product's design. More than 10 items become difficult for those doing the evaluation to manage, while fewer than 5 items tend not to be sufficiently discriminating.

Another concern is the number of researchers needed to carry out a thorough heuristic evaluation that identifies the majority of usability problems. Empirical tests were conducted suggesting that 3–5 can typically identify up to 75 percent of the total usability problems, as shown in [Figure 16.1](#c16-fig-0001) (Nielsen, 1994a). However, employing several researchers can be resource intensive. Therefore, the overall conclusion is that while more researchers might be better, fewer can be used—especially if the researchers are experienced and knowledgeable about the product and its intended users.

![Graphical representation of the proportion of usability problems in an interface found in heuristic evaluation using various numbers of evaluators.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c16f001.jpg)

Figure 16.1 Curve showing the proportion of usability problems in an interface found by heuristic evaluation using various numbers of evaluators Source: Nielsen and Mack (1994). Used courtesy of John Wiley & Sons, Inc.

#### Heuristic Evaluation for Websites

A number of different heuristic sets for evaluating websites have been developed based on Nielsen's original 10 heuristics. One of these was developed by Andy Budd after discovering that Nielsen's heuristics did not address the problems of the continuously evolving web. He also found that there was overlap between several of the guidelines and that they varied widely in terms of their scope and specificity, which made them difficult to use. An extract from these heuristics is shown in [Box 16.1](#c16-fea-0001). Notice that a difference between these and Nielsen's original heuristics is that they place more emphasis on information content.

A similar approach to Budd's is also taken by Leigh Howells in her article entitled “A guide to heuristic website reviews” (Howells, 2011). In this article and in a more recent one by Toni Granollers (2018), techniques for making the results of heuristic evaluation more objective are proposed. This can be done either to show the occurrence of different heuristics from an evaluation or to compare the results of different researchers' evaluations, as shown in [Figure 16.2](#c16-fig-0002). First, a calculation is done to estimate the percentage of usability problems identified by each researcher, which is then displayed around the diagram (in this case there were seven researchers). Then a single value representing the mean of all of the researchers' individual means is calculated and displayed in the center of the diagram. In addition to being able to compare the relative performance of different researchers and the overall usability of the design, a version of this procedure can be used to compare the usability of different prototypes or for comparisons with competitors' products.

![Diagrammatic representation of radar diagram showing the mean number of problems identified by each of the seven researchers and the overall mean shown in the center of the diagram.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c16f002.jpg)

Figure 16.2 Radar diagram showing the mean number of problems identified by each of the seven researchers and the overall mean shown in the center of the diagram Source: Granollers (2018). Used courtesy of Springer Nature

#### Doing Heuristic Evaluations

Doing a heuristic evaluation can be broken down into three main stages (Nielsen and Mack, 1994; Muniz, 2016).

- A *briefing session*, in which the user researchers are briefed about the goal of the evaluation. If there is more than one researcher, a prepared script may be used to ensure that each person receives the same briefing.
- The *evaluation period*, in which the user researchers typically spend 1–2 hours independently inspecting the product, using the heuristics for guidance.

Typically, the researchers will take at least two passes through the interface. The first pass gives a feel for the flow of the interaction and the product's scope. The second pass allows them to focus on specific interface elements in the context of the whole product and to identify potential usability problems.

If the evaluation is for a functioning product, the researchers will typically have some specific user tasks in mind so that their exploration is focused. Suggesting tasks may be helpful, but many UX researchers suggest their own tasks. However, this approach is more difficult if the evaluation is done early in design when there are only screen mock-ups or a specification. Therefore, the approach needs to be adapted for the evaluation circumstances. While working through the interface, specification, or mock-ups, a second researcher may record the problems identified, while the other researcher may think aloud, which can be video recorded. Alternatively, each researcher may take notes.

- The *debriefing session*, in which the researchers come together to discuss their findings with designers and to prioritize the problems they found and give suggestions for solutions.

The heuristics focus the researchers' attention on particular issues, so selecting appropriate heuristics is critically important. Even so, sometimes there is disagreement among researchers, as discussed in the next “Dilemma.”

Another important issue when designing and evaluating web pages, mobile apps, and other types of products is their accessibility to a broad range of users, for example, people with sight, hearing, and mobility challenges. Many countries now have web content accessibility guidelines (WCAG) to which designers must pay attention, as discussed in [Box 16.2](#c16-fea-0004).

Some researchers have created heuristics specifically to ensure that websites and other products are accessible to users with disabilities. For example, Jenn Mankoff et al. (2005) discovered that developers who did heuristic evaluation using a screen reader found 50 percent of known usability problems. Although, admirably, much research focuses on accessibility for people with sight problems, research to support other types of disabilities is also needed. An example is the research by Alexandros Yeratziotis and Panayiotis Zaphiris (2018), who created a method comprising 12 heuristics for evaluating deaf users' experiences with websites.

While automated software testing tools have been developed in an attempt to apply WCAG guidelines to web pages, this approach had limited success because there are so many accessibility requirements that are not currently machine-testable. Human inspection using the WCAG, or user testing involving people with disabilities, are still the superior methods for evaluating web compliance with WCAG 2.1 standards.

#### Turning Design Guidelines, Principles, and Golden Rules into Heuristics

An approach to developing heuristics for evaluating the many different types of digital technologies is to convert design guidelines into heuristics. Often this is done by just using guidelines as though they are heuristics, so guidelines and heuristics are assumed to be interchangeable. A more principled approach is for designers and researchers to translate the design guidelines into questions. For example, Kaisa Väänänen-Vainio-Mattila and Minna Wäljas (2009) adopted this approach when developing heuristics for evaluating user experience with a web service. They identified what they called *hedonic heuristics*, which directly addressed how users feel about their interactions. These were based on design guidelines concerning whether the user feels that the web service provides a lively place where it is enjoyable to spend time and whether it satisfies a user's curiosity by frequently offering interesting content. When stated as questions, these become: Is the service a lively place where it is enjoyable to spend time? Does the service satisfy users' curiosity by frequently offering interesting content?

In a critique of Nielsen's *Heuristics* (1994) and a similar set of heuristics proposed by Bruce Tognazzini's known as “First Principles of HCI Design and Usability” (Tognazzini, 2014), Toni Granollers points out the need for revising these heuristics. She claims that there is considerable overlap both within each of the two sets of heuristics and between them. Furthermore, she stresses the need for more guidance in using heuristics and advocates for developing questions as a way to provide this support. Granollers suggests first converting the heuristics into principles, and then, as was suggested earlier, identifying pertinent questions to ground the principles so that they are useful. For example, consider the heuristic “visibility and system state,” which is a composite between Nielsen's and Tognazzini's heuristics. Granolles suggests the following questions:

> ***Does the application include a visible title page, section or site? Does the user always know where they are located? Does the user always know what the system or application is doing? Are the links clearly defined? Can all actions be visualized directly (i.e., no other actions are required)?***
> 
> **Granollers, 2018, p. 62**

Each heuristic is therefore decomposed into a set of questions like these, which could be further adapted for evaluating specific products.

Heuristics (some of which may be guidelines or rules) have been created for designing and evaluating a wide range of products including shared groupware (Baker et al., 2002), video games (Pinelle et al., 2008), multiplayer games (Pinelle et al., 2009), online communities (Preece and Shneiderman, 2009), information visualization (Forsell and Johansson, 2010), captchas (Reynaga et al., 2015), and e-commerce sites (Hartley, 2018b). David Travis (2016), a consultant from Userfocus, has compiled 247 guidelines that are used in evaluations. These include 20 guidelines for home page usability, 20 for search usability, 29 for navigation and information architecture, 23 for trust and credibility, and more.

In the mid-1980s Ben Shneiderman also proposed design guidelines that are frequently used as heuristics for evaluation. These are called the “eight golden rules.” They were slightly revised recently (Shneiderman et al., 2016) and are now stated as follows:

1. Strive for consistency.
2. Seek universal usability.
3. Offer informative feedback.
4. Design dialogs to yield closure.
5. Prevent errors.
6. Permit easy reversal of actions.
7. Keep users in control.
8. Reduce short-term memory load

### 16.2.2 Walk-Throughs

Walk-throughs offer an alternative approach to heuristic evaluation for predicting users' problems without doing user testing. As the name suggests, *walk-throughs* involve walking through a task with the product and noting problematic usability features. While most walk-through methods do not involve users, others, such as pluralistic walk-throughs, involve a team that may include users, as well as developers and usability specialists.

In this section, we consider cognitive and pluralistic walk-throughs. Both were originally developed for evaluating desktop systems, but, as with heuristic evaluation, they can be adapted for other kinds of interfaces.

#### Cognitive Walk-Throughs

*Cognitive walk-throughs* involve simulating how users go about problem-solving at each step in a human-computer interaction. A cognitive walk-through, as the name implies, takes a cognitive perspective in which the focus is on evaluating designs for ease of learning—a focus that is motivated by observations that users learn by exploration. This well-established method (Wharton et al., 1994) is now often integrated with a range of other evaluation and design processes. See, for example, the Jared Spool blog at [https://medium.com/@jmspool](https://medium.com/@jmspool), (Spool 2018).

The main steps involved in cognitive walk-throughs are as follows:

1. The characteristics of typical users are identified and documented, and sample tasks are developed that focus on the aspects of the design to be evaluated. A description, mock-up, or prototype of the interface to be developed is also produced, along with a clear sequence of the actions needed for the users to complete the task.
2. A designer and one or more UX researchers come together to do the analysis.
3. The UX researchers walk through the action sequences for each task, placing it within the context of a typical scenario. As they do this, they try to answer the following questions:
	1. Will the correct action be sufficiently evident to the user?
		*(Will the user know what to do to achieve the task?)*
		2. Will the user notice that the correct action is available?
		*(Can users see the button or menu item that they should use for the next action? Is it apparent when it is needed?)*
		3. Will the user associate and interpret the response from the action correctly?
		*(Will users know from the feedback that they have made a correct or incorrect choice of action?)*
	In other words, will users know what to do, see how to do it, and understand from feedback whether the action was completed correctly or not?
4. As the walk-through is being done, a record of critical information is compiled.
	1. The assumptions about what would cause problems and why are identified.
		2. Notes about side issues and design changes are made.
		3. A summary of the results is compiled.
5. The design is then revised to fix the problems presented. Before making the fix, insights derived from the walk-through are often checked by testing them with real users.

When doing a cognitive walk-through, it is important to document the process, keeping account of what works and what doesn't. A standardized feedback form can be used in which answers are recorded to each question. Any negative answers are carefully documented on a separate form, along with details of the product, its version number, and the date of the evaluation. It is also useful to document the severity of the problems. For example, how likely a problem is to occur, and how serious it will be for users. The form can also be used to record the process details outlined in steps 1–4.

Brad Dalrymple (2017) describes doing a walk-through with himself as the user in three steps. Notice that there are fewer steps and they are a bit different from those previously listed.

1. Identify the user goal you want to examine.
2. Identify the tasks you must complete to accomplish that goal.
3. Document the experience while completing the tasks.

Dalrymple provides an example of the actions that he needs to go through to create a Spotify playlist (the task) of music for guests who will attend his dinner party (the goal).

Compared with heuristic evaluation, walk-throughs focus more closely on identifying specific user problems at a detailed level. Another type of walk-through that takes a semiotic engineering perspective is described in [Box 16.3](#c16-fea-0006).

A variation of a cognitive walk-through was developed by Rick Spencer (2000) to overcome some problems that he encountered when using the original form of a cognitive walk-through for a design team. The first problem was that answering the questions and discussing the answers took too long. Second, the designers tended to be defensive, often invoking long explanations of cognitive theory to justify their designs. This was particularly difficult because it undermined the efficacy of the method and the social relationships of team members. To cope with these problems, he adapted the method by asking fewer detailed questions and curtailing discussion. This meant that the analysis was more coarse-grained but could normally be completed in about 2.5 hours, depending on the task being evaluated by the cognitive walk-through. He also identified a leader and set strong ground rules for the session, including a ban on defending a design, debating cognitive theory, or doing designs on the fly.

More recently, Valentina Grigoreanu and Manal Mohanna (2013) modified the cognitive walk-through so that it could be used effectively within an agile design process in which a quick turnaround in design-evaluate-design cycles is needed. Their method involves an informal, simplified *streamlined cognitive walk-through* (SSCW) followed by an informal pluralistic walk-through (discussed next). When compared to a traditional user study on the same user interface, they found that approximately 80 percent of the findings from the user study were also revealed by the SSCW.

#### Pluralistic Walk-Throughs

*Pluralistic walk-throughs* are another type of well-established walk-through in which users, developers, and usability researchers work together to step through a task scenario. As they do this, they discuss usability issues associated with dialog elements involved in the scenario steps (Nielsen and Mack, 1994). In a pluralistic walk-through, each person is asked to assume the role of a typical user. Scenarios of use, consisting of a few prototype screens, are given to each person who writes down the sequence of actions that they would take to move from one screen to another, without conferring with each other. Then they all discuss the actions they each suggested before moving on to the next round of screens. This process continues until all of the scenarios have been evaluated (Bias, 1994).

The benefits of pluralistic walk-throughs include a strong focus on users' tasks at a detailed level, that is, looking at the steps taken. This level of analysis can be invaluable for certain kinds of systems, such as safety-critical ones, where a usability problem identified for a single step could be critical to its safety or efficiency. The approach lends itself well to participatory design practices, as discussed in [Chapter 12](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c12.xhtml), “Design, Prototyping, and Construction,” by involving a multidisciplinary team in which users play a key role. Furthermore, the researchers bring a variety of expertise and opinions for interpreting each stage of the interaction. The limitations with this approach include having to get the researchers together at one time and then proceed at the rate of the slowest. Furthermore, only a limited number of scenarios, and hence paths through the interface, can usually be explored because of time constraints.

## 16.3 Analytics and A/B Testing

A variety of users' actions can be recorded by software automatically, including key presses, mouse or other pointing device movements, time spent searching a web page, looking at help systems, and task flow through software modules. A key advantage of logging activity automatically is that it is unobtrusive provided the system's performance is not affected, but it also raises ethical concerns about observing participants if this is done without their knowledge, as discussed in [Chapter 10](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c10.xhtml), “Data at Scale.” Another advantage is that large volumes of data can be logged automatically and then explored and analyzed using visualization and other tools.

### 16.3.1 Web Analytics

*Web analytics* is a form of interaction logging that was specifically created to analyze users' activity on websites so that designers could modify their designs to attract and retain customers. For example, if a website promises users information about how to plant a wildflower garden but the home page is unattractive and it only shows gardens in arid and tropical regions, then users from more temperate zones will not look any further because the information they see isn't relevant to them. These users become one-time visitors and leave to look for other websites that contain the information they need to create their gardens. If the website is used by thousands of users and a small number of users do not return, this loss of users may not be noticed by the web designers and web owners unless they track users' activities.

Using web analytics, web designers and developers can trace the activity of the users who visit their website. They can see how many people came to the site, how many stayed and for how long, and which pages they visited. They can also find out about where the users came from and much more. Web analytics is therefore a powerful evaluation tool for web designers that can be used on its own or in conjunction with other types of evaluations, particularly user testing. For instance, web analytics can provide a “big-picture” overview of user interaction on a website, whereas user testing with a few typical users can reveal details about UX design problems that need to be fixed.

Because the goal of using web analytics is to enable designers to optimize users' usage of the website, web analytics is especially valued by businesses and market research organizations. For example, web analytics can be used to evaluate the effectiveness of a print or media advertising campaign by showing how traffic to a website changes during and after the campaign.

Web analytics are also used in evaluating non-transactional products such as information and entertainment websites, including hobby, music, games, blogs, and personal websites (refer to Sleeper et al., 2014), and for learning. When analytics are used in learning, they are often referred to as *learning analytics* (for example, Oviatt et al., 2013; Educause, 2016). Learning analytics play a strong role in evaluating learners' activities in massive open online courses (MOOCs) and with Open Education Resources (OERs). The designers of these systems are interested in questions such as at what point do learners tend to drop out and why?

Other types of specialist analytics have also been developed that can be used in evaluation studies, such as *visual analytics* (discussed in [Chapter 10](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c10.xhtml), “Data at Scale, in which thousands and often millions of data points are displayed and can be manipulated visually, as in social network analysis (Hansen et al., 2019).

[Box 16.5](#c16-fea-0011) and [Box 16.6](#c16-fea-0012) contain two short case examples of web analytics being used in different evaluation contexts. The first is an early example designed to evaluate visitor traffic to a website for Mountain Wines of California. The second shows the use of Google Analytics for evaluating the use of a community website for air monitoring.

#### Using Web Analytics

There are two types of web analytics: on-site and off-site analytics. *On-site analytics* are used by website owners to measure visitor behavior. *Off-site analytics* measure a website's visibility and potential to acquire an audience on the Internet regardless of who owns the website. In recent years, however, the difference between off-site and on-site analytics has blurred but some people still use these terms. Additional sources may also be used to augment the data collected about a website, such as email, direct mail campaign data, sales, and history data, which can be paired with web traffic data to provide further insights into users' behavior.

#### Google Analytics

Even as early as 2012, Google Analytics was the most widely used on-site web analytics and statistics service. More than 50 percent of the 10,000 most popular websites at that time (Empson, 2012) used Google Analytics, and its popularity continues to soar.

[Figure 16.5](#c16-fig-0005) shows parts of the Google Analytics dashboard for the accompanying website for the previous edition of this book, [id-book.com](http://id-book.com/), for the week starting at the end of November 2018 until the beginning of December 2018. The first segment (a) shows information about who accessed the site and how long they stayed, the second segment (b) shows the devices used to view the website and the pages visited, and the third segment (c) shows the languages spoken by the users.

![Screenshot of Segments of the Google Analytics dashboard for id-book.com in December 2018: (a) audience overview, (b) the devices used to access the site.](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781119547259/files/images/c16f005a.jpg)

Figure 16.5 Segments of the Google Analytics dashboard for id-book.com in December 2018: (a) audience overview, (b) the devices used to access the site, and (c) the languages of the users

### 16.3.2 A/B Testing

Another way to evaluate a website, part of a website, an application, or an app running on a mobile device is by carrying out a large-scale experiment to evaluate how two groups of users perform using two different designs—one of which acts as the control and the other as the experimental condition, that is, the new design being tested. This approach is known as *A/B testing*, and it is basically a controlled experiment but one that often involves hundreds or thousands of participants. Like the experimental design discussed in [Chapter 15](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c15.xhtml), “Evaluation Studies: From Controlled to Natural Settings,” A/B testing involves a “between subjects” experimental design in which two similar groups of participants are randomly selected from a single large user population (Kohavi and Longbotham, 2015), for instance, from users of social media sites such as Twitter, Facebook, or Instagram. The main differences between A/B testing and the experiments discussed in [Chapter 15](https://learning.oreilly.com/library/view/interaction-design-5th/9781119547259/c15.xhtml) is one of scale and that typically A/B testing is done online.

To do A/B testing, a variable of interest is identified, such as the design of an advertisement. Group A is served design A, the existing design, and group B is served design B, the new design. A dependent measure is then identified, such as how many times participants in each group, A and B, click the advertisement that they are presented over a particular period of time, such as a day, week, or a month. Because this is a controlled experiment, the results can be analyzed statistically to establish the probability that if a difference is observed, it is because of the treatment (in this case, the design) and not because of chance.

As Ron Kohavi (2012) mentions, A/B testing provides a valuable data-driven approach for evaluating the impact of small or large differences in the designs of web and social media sites. From front-end user-interface changes to backend algorithms, from search engines (such as Google, Bing, and Yahoo!) to retailers (for example, Amazon, eBay, and Etsy) to social networking services (such as Facebook, LinkedIn, and Twitter) to travel services (for instance, Expedia, Airbnb, and [Booking.com](http://booking.com/)) to many startups, online controlled experiments are now utilized to make data-driven decisions at a wide range of companies (Deng et al., 2017).

To get the most benefit from running an online A/B test, Ron Kohavi and Roger Longbotham (2015) recommend first running an *A/A test*. This is a test in which both populations of participants see the same design and should have the same experience. The results of the A/A test are then examined, and they should show no statistically significant difference. Following this procedure ensures that the two randomly selected populations are indeed random and that the conditions under which the experiment is running are indeed similar. This is important because the Internet is complex, and users' interactions can be influenced in ways that researchers do not expect (for example by bots or the way browsers refresh or redirect), which could reduce the value of the A/B test, possibly even invalidating it.

Powerful though A/B testing may be, researchers are advised to check their plans in detail to ensure that they are testing what they expect to test. For example, Ron Kohabi and Roger Longbottom carried out an A/B test on two versions of a design for early versions of the Microsoft Office 2007 home page. The idea was to test the effectiveness of a new and more modern-looking home page with the primary objective of increasing the number of download clicks. However, instead of the number of download clicks going up as expected, it actually decreased by 64 percent. The researchers wondered what caused such an unexpected result. Upon closer examination of the two designs, they noticed the words in the new design were “Buy now” with a $149.95 price, whereas the old design said, “Try 2007 for free” and “Buy now”. The impact of being asked to pay $149.95 distorted the experiment, even though the new design might have actually been better. Microsoft Office has gone through many revisions since testing the 2007 version, but this example is included because it demonstrates the care that is needed when setting up A/B testing to ensure that it is actually testing the intended design features. Other design features, particularly ones that involve payments by users, can have powerful unexpected consequences that even experienced researchers like Ron Kohabi and Roger Longbottom may overlook when setting up the test.

## 16.4 Predictive Models

Like inspection methods and analytics, *predictive models* can be used to evaluate a product without users being present. Rather than user researchers being involved in role-playing during inspections, or tracking their behavior using analytics, predictive models use formulas to derive various measures of user performance. *Predictive modeling* provides estimates of the efficiency of different systems for various kinds of tasks. For example, a smartphone designer may choose to use a predictive model because it enables them to determine accurately, which is the optimal sequence of keys for performing a particular operation.

### 16.4.1 Fitts' Law

One kind of predictive model that has been influential in HCI and interaction design over the years is Fitts' law. *Fitts' law* (Fitts, 1954) predicts the time it takes to reach a target using a pointing device. It was originally used in human factors research to model the relationship between speed and accuracy when moving toward a target on a display. In interaction design, it has been used to model the time it takes to point at a target (for example, an icon on a screen), based on the size of the object and the distance to the object (Mackenzie, 1992). One of its main benefits is that it can help designers decide where to locate physical or digital buttons, what size to make them, and how close together to put them on a touch display or a physical device. In the early days, it was most useful for designing physical laptop/PC keyboard layouts and the placement of physical keys on mobile devices, such as smartphones, watches, and remote controls. It has also been used for designing the layout of digital displays for input on touchscreen interfaces.

Fitts' law states that:

where

- *T* = time to move the pointer to a target
- *D* = distance between the pointer and the target
- *S* = size of the target
- *k* is a constant of approximately 200 ms/bit.

In a nutshell, the bigger the target, the easier and quicker it is to reach it. This is why interfaces that have big buttons are easier to use than interfaces that present lots of tiny buttons crammed together. Fitts' law also predicts that the targets accessed most quickly on any computer display are positioned at the four corners of the screen. This is because of their *pinning action*; in other words, the sides of the display constrain the user from over-stepping the target.

Fitts' law can be useful for evaluating systems where the time to locate an object physically is critical to the task at hand. In particular, it can help designers think about where to locate objects on the screen in relation to each other. This is especially useful for mobile devices, where there is limited space for placing icons and buttons on the screen. For example, in an early study carried out by Nokia, Fitts' law was used to predict text entry rates for several input methods on a 12-key cell phone keypad (Silverberg et al., 2000). The study helped the designers make decisions involving trade-offs about the size of keys, their positioning, and the sequences of keypresses to perform common tasks.

Scott MacKenzie and Robert Teather (2012) used Fitts' law in several studies including one deigned to evaluate tilt as an input method for devices with built-in accelerometers, such as touchscreen phones and tablet computers. It was also used to examine the effect of the size of the physical gap between displays and the proximity of targets in multiple-display environments (Hutchings, 2012). In addition, Fitts' law has been used to compare eye-tracking input with manual input for visual targets (Vertegaal, 2008), different ways of mapping Chinese characters to the keypad of cell phones (Liu and Räihä, 2010); and gestural, touch, and mouse interaction (Sambrooks and Wilkinson, 2013). More recently, Fitts' law has been used for considering the effectiveness of new ways of input such as different game controllers (Ramcharitar and Teather, 2017), cursor positions for 3D selections in VR (Li et al., 2018), and gaze input on large displays with touch and mouse input (Rajanna and Hammond, 2018). Another creative use of Fitts' law is to evaluate the efficacy of simulating users with motor impairments interacting with a head-controlled mouse pointer system (Ritzvi et al., 2018). This application of Fitts' law was especially useful because it can be difficult to recruit participants with motor impairments to take part in user tests.