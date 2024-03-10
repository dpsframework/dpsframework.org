---
layout:           note
ref:              genAI
lang:             en
idiom:            en_US
imagepath:        'images/genAI/'
images:           
  -  'genAI_docker.png'
  -  'genAI_docker27.png'
  -  'genAI_nvidiaDriverGPU.png'
  -  'genAI_lastBuild.png'
  -  'genAI_running.png'

menu:             false
citation:         'Docker. Accelerated Development with AI & ML. Available at: https://www.docker.com/blog/introducing-a-new-genai-stack/ and, https://neo4j.com/developer-blog/genai-app-how-to-build/'
toc:              true
title:            'GenAI Stack Walkthrough: Behind the Scenes With Neo4j, LangChain, and Ollama in Docker'
headtitle:        'Stack GenAI con Docker, Neo4J, LangChain y Ollama.'
shorttitle:       'Installing Generative Artificial Intelligence Assistant, with an example from the Docker Team, for Windows 10.21H2, with GeForce GT 710 GPU: AI/MLearning integration made easy.'
year:             '2023'
author:           'Docker Team'
department:       ''
keywords:         
  -  'Generative AI; Docker; ChatGPT'

status:           'In process'
license:          '© 2024 Docker Inc. All rights reserved'
pubdate:          '2023-10-05'
modified_date:    '2024-03-11'
traductor:        'FJ Aguayo'
---





Control de citas: [^1], [^2], [^3], [^4], [^5], [^6], [^7], [^8], [^9], [^10], [^11], [^12], [^13], [^14], [^15], [^16], [^17], [^18], [^19], [^20], [^21], [^22], [^23], [^24], [^25], [^26], [^27], [^28], [^29], [^30], [^31], [^32], [^33], [^34], [^35], [^36], [^37], [^38], [^39], [^40], [^41], [^42], [^43], [^44], [^45], [^46], [^47], [^48], [^49], [^50], [^51], [^52], [^53], [^54], [^55], [^56], [^57], [^58], [^59], [^60], [^61], [^62], [^63], [^64], [^65], [^66], [^67], [^68], [^69], [^70], [^71], [^72], [^73], [^74], [^75], [^76], [^77], [^78], [^79], [^80], [^81], [^82], [^83], [^84], [^85], [^86], [^87], [^88].





> **{{ site.data.i18n[page.lang].abstract }}:**  At DockerCon 2023, with partners Neo4j, LangChain, and Ollama, we announced a new GenAI Stack. We have brought together the top technologies in the generative artificial intelligence (GenAI) space to build a solution that allows developers to deploy a full GenAI stack with only a few clicks.

**{{ site.data.i18n[page.lang].keywords}}:**  GenAI Stack, Docker, Neo4j, Ollama, LangChain, Generative Artificial Intelligence.

#   1. Introduction
  
  
  The requirements for deploying the Generative Artificial Intelligence application in a Docker container are found in **[^2]** on the Docker Documentation page. On Windows, the GenAI application can benefit from GPU acceleration only if the latest graphics card driver is installed. To do this, it is necessary to consult **[^3]** the Official NVidia Drivers Page. And they must be updated before beginning this installation and subsequent deployment. In the case of Linux, it will be necessary to proceed in the same way and perform a native installation (compiling) of the Docker Engine itself so that the GPUs work correctly. (See, https://docs.docker.com/guides/use-case/genai-pdf-bot/containerize/#prerequisites)
  
  
  
  With respect to other reviews and surveys on APL in the literature **[^3]**, **[^5]-[^10]**, our review focuses on recent developments and considers works presenting new APL, as well as works that focus on extending or comparing existing APLs. Furthermore, we consider both theoretical and practical aspects; This helps to have a better understanding of the reality gap between theoretical and practical APL. Finally, with respect to previous reviews, we focus on the entire class of APL, and not on a specific area of APL as in **[^6]**, where only the engineering aspects are considered, or in **[ ^7]**, where only APL platforms are considered, or in **[^8]**, where only agent-based simulation literature is discussed, or in **[^3]**,* *[^5]**, where their focus is on a specific model of agency (Belief-Desire-Intention—BDI).
  
  
  
  
  
  
  
  
  
#   2. History of agent-based programming
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
**{{ site.data.i18n[page.lang].figure  }}    1**.  The BDI model.<br>
![]( {{ page.imagepath }}{{  page.images[  1]  }} )
  
  
  
  
  
  
  
  Situation Calculus **[^16]** is a first-order language designed to represent changes in dynamic environments. A situation is a first-order term that represents a sequence of actions. An initial situation is when no actions have yet occurred. The function do(a, s) results in a successor situation of s after executing action a, similar to state transition systems. Dynamic environments play an important role in agent-based programming and as such Situation Calculus has been used to model how the world changes as a result of the execution of actions.
  
  
  
  
  
  
  
  
  As we will see in Section 4, there are many other models that have inspired agent-based programming languages, however, these three were the most influential in the past history of agent-based programming. Some agent languages share similarities or even mix concepts from other programming paradigms, such as procedural, imperative, object-oriented, functional, actor, concurrent, etc. Comparing the differences or going into detail about these other paradigms is outside the scope of this review, or a specific area of APL as in **[^6]**, where only the engineering aspects are considered, or in ** [^7]**, where only APL platforms are considered, or in **[^8]**, where only agent-based simulation literature is discussed, or in **[^3]**, **[^5]**, where their focus is on a specific model of agency (Belief-Desire-Intention—BDI).
  
  
  
  
  This document is structured as follows. A brief history of agent-based programming is provided in Section 2. In Section 3, the systematic review process followed in this document is presented. Section 4 contains the findings of the review with the articles found in our literature search. In Section 5, the results of the review are discussed and future directions are suggested. Finally, in Section 6, the conclusions of the work are reported.
  
  
  
  
  
  
#   3. Review methodology
  
  
  
  
  
  
  
  We conducted a systematic literature review on agent programming languages over the last 5 years (2015-2020). A diagram illustrating our review methodology is shown in Figure 2. For each searched term, we consider the first 10 pages (100 entries) retrieved by Google Scholar (sorted by relevance), for a total of 400 entries (including duplicates).
  
  
  
  
  The terms used in our search were:
  
  
  
  
  - Agent-based programming languages
  - Agent-based scheduling extensions
  - Agent-Based Scheduling Comparison
  - Agent-based scheduling applications
  
  
  
  
  
  
  
  
**{{ site.data.i18n[page.lang].figure  }}    2**.  Systematic review flowchart.<br>
![]( {{ page.imagepath }}{{  page.images[  2]  }} )
  
  
  
  
  
  
  After removing duplicates, we had 250 documents remaining. To these, we added 16 entries from external sources; mostly old references that wouldn't show up in the search, plus a few others found in paper citations and other sources. Of the 16 external entries, eight were influential APLs that were developed before 2015 and were recently updated (i.e., 2017-2020).
  
  
  
#  4. Review the findings on agent-based programming for Mas
  
  
  
  
  
  In this section, we cover all the research found in our systematic literature review. We begin with agent programming languages and their extensions, then continue to discuss existing comparisons in agent-based programming, and close the section with a brief review of applications in the area.
  
  
  
  
##  4.1. Agent programming languages
  
  
  
  
  We report the agent programming languages found in the systematic review in Table 1. As we mentioned in Section 2, we can see that BDI is clearly the most popular agency model, although is used in 7 of the 15 languages. Most of the implemented languages have been implemented in Java, probably to take advantage of Java's cross-platform through its Java virtual machine. The table contains only the high-level general-purpose languages that can be used to develop domain-independent MAS. While other approaches, such as agent-based modeling and simulation (ABMS) and cognitive agents in robotics, are not included in the table, we briefly report some of the novel research that has been conducted in those areas below.
  
  
  
  
  
**{{ site.data.i18n[page.lang].table  }}    1**.  Table 1. A collection of recent (or recently updated) agent programming languages. Languages that do not have a publicly available implementation are represented by an X. In case there are multiple implementation branches, the Last Update column refers to the last update in the master branch.<br>
![]( {{ page.imagepath }}{{  page.images[  3]  }} )
  
  
  
###  4.1.1. General Purpose APL
  
  
  
  
  
  A survey on agent-oriented programming from a software engineering perspective can be found in **[^6]**. One of the main challenges reported in the survey for APL developers is the need to close the cognitive gap that exists between the concepts that underpin conventional languages and those that underpin AOP. In **[^21]** the authors attempt to fill this gap by focusing on understanding the relationship between AgentSpeak(L) **[^15]** and OOP with the goal of trying to reduce the perceived cognitive gap. Such work proposes a new programming language for statically typed agents called ASTRA.
  
  
  
  
  
  In **[^22]** the authors present Chromar, a rule-based notation with stochastic semantics that produces a continuous-time Markov chain. Chromar is built into Haskell, giving it greater expressive power and accommodating the availability of rich types. In Chromar, rules are first-order abstractions that can describe a (possibly partial) behavior of an individual agent and a synchronized action of two or more agents.
  
  
  
  
  GOAL **[^23]** is a declarative agent programming language that uses knowledge-based beliefs and goals to support the decision making of its cognitive agents. Despite sharing similar concepts with the BDI model (beliefs, desires/goals), the GOAL language is more focused on rule-based decision making. Agent programs are written in GOAL-specific syntax, but agent knowledge (e.g. rules) is usually represented in Prolog.
  
  
  
  
  Jason **[^24]** is an extension of the AgentSpeak(L) language, based on the BDI agent model. Jason agents react to system events by executing actions in the environment, according to the plans available in each agent's plan library. One of Jason's extensions is the addition of Prolog-like rules that can be added and used in the agents' belief base.
  
  
  
  The JaCaMo platform **[^25]**,**[^26]** is composed of three technologies, Jason, CArtAgO **[^27]** and Moise **[^28]**, each of which represents a different level of abstraction. Jason is used for programming the agent level, CARtAgO is responsible for the environment level and Moise is responsible for the organization level. JaCaMo integrates these three technologies by defining a semantic link between concepts at different levels of abstraction (agent, environment and organization). The end result is the JaCaMo MAS development platform. It provides first-class, high-level support for the development of agents, environments, and organizations, enabling the development of more complex multi-agent systems.
  
  
  
  
  Gwendolen **[^29]** initially started out as a small subset of Jason in hopes of developing testable agent programs, but has since grown into its own syntax and semantics. Because it is a language that has been built to support agent verification from scratch, it is limited in the features it can support; however, the basics of AgentSpeak (L) and BDI are all present. There is a vast literature on agent program verification and MAS, but we consider them outside the scope of this review. Gwendolen, in addition to being testable, remains a viable language for developing general-purpose MAS.
  
  
  
  JADE **[^30]** is an open source platform for developing peer-to-peer agent-based applications. In addition to agent abstraction, it also provides: task composition and execution model, peer-to-peer agent communication based on asynchronous message passing, and a yellow pages service that supports publish-subscribe discovery mechanism. JADE based systems can be distribute between machines with different operating systems and have been used in many languages (e.g. Jason and JaCaMo) as a distribution infrastructure.
  
  
  
  In **[^31]** the authors present JADEL (JADE Language), an extension to JADE that provides support for building agents and MAS on top of JADE without having to use Java directly; later, in **[^32]**, the authors present Jadescript, an extension of JADEL. Jadescript is characterized by strong expressive syntax largely inspired by modern scripting languages to promote readability and make agent programs more pseudocode-like.
  
  
  
  
  Jadex **[^33]** enables the programming of intelligent software agents in XML and Java. Agent abstraction is based on the BDI model and provides several features, such as: a runtime infrastructure for agents, multiple interaction styles, simulation support, automatic formation of overlay networks, and a rich set of runtime tools. .
  
  
  
  
  LightJason, a highly scalable Java-based platform for BDI agent-oriented programming and simulation, is presented in **[^34]**. LightJason is based on a logic language that extends AgentSpeak(L) with lambda expressions, multiple plan and rule definition, explicit repair actions, multivariable assignments, parallel execution, and thread-safe variables. Although the language is inspired by AgentSpeak(L) and Jason, LightJason is implemented from scratch.
  
  
  
  In **[^35]**, an AOP language called Planning-Based Language for Agents and Computing Environments (PLACE) adds AI planning capability to agents. PLACE has a syntactic structure close to BDI, while scheduling is done in a Hierarchical Task Network (HTN) scheduler. Unlike other AOP languages, actions in PLACE have durations associated with them, so they require the scheduler to be able to handle temporal information. Agents in PLACE have the ability to recover from failures by adapting their activities to new situations. For this purpose, a plan repair mechanism is added that repairs a plan if unanticipated events in the environment cause the plan to become infeasible.
  
  
  
  In **[^36]** the Programming Language for Synchronous Agents (PLASA) is proposed. PLASA is platform independent and facilitates rapid deployment of cooperative applications on multiple physical robots and in dynamic environments. Essentially, PLASA implements a variant of the Wait-Look-Compute-Move model proposed in **[^37]**, where the robots move synchronously. It is designed as a high-level programming language, allowing users to specify the instructions that robots should perform in a human-readable language.
  
  
  Relational Model Multi-Agent System (RMAS) **[^38]** is a database-centric approach to multi-agent systems suitable for incorporating reasoning and control into cyber-physical systems (CPS). The initial implementation of RMAS is proposed by coupling the Matlab environment and the SQLite database language.
  
  
  
  
  SARL's **[^39]** approach is to provide an extensible language that is equipped with the minimum number of concepts (i.e. key concepts) required to support AOP. The language aims to provide abstractions for concurrency, distribution, interaction, decentralization, reactivity, autonomy, and dynamic reconfiguration. To do this, it is not based on any model, but rather creates its own Domain Specific Language (DSL) in order to provide a reduced and lighter core.
  
  
  
  
###  4.1.2. ABMS, robotics and others
  
  
  
  
  
  As recognized in **[^40]**, there is a gap between Agent Oriented Software Engineering (AOSE) methodologies and ABMS development. To overcome this problem, an AOSE process called Process for the Development of Efficient Agent-Based Simulators (PEABS) is proposed in **[^41]**. It uses the INGENIAS **[^42]** methodology to model the specification and design its structure. It applies an adaptive framework that allows ABMS developers to obtain highly efficient simulations for large amounts of data. Another approach to developing ABMS is presented in **[^43]**,**[^44]**, where the authors propose a new cognitive agent architecture based on the BDI model and integrated into the GAMA modeling language * *[^45]**. With respect to previous integration work between BDI and ABMS, in **[^43]** the proposed architecture aims to be flexible and easy to use for non-expert users. Other work that aims to integrate BDI and ABMS is presented in **[^46]**, where the authors present a framework that allows BDI cognitive agents to be embedded in an ABMS system. In Compared to **[^43]**, reference **[^46]** is more general as its goal is to integrate any BDI-based system with ABMS. The only requirement is that the percepts (or environmental observations/events) of interest to each agent and the actions that the agent can execute in the simulation environment can be identified a priori.
  
  
  
  
  ALLEGRO (=ALGOL in PREGO **[^47]**,**[^48]**) is a programming formalism based on a belief architecture for stochastic domains that aims to be an alternative to GOLOG **[^49 ]** for high-level control in robotic applications. Another language that is based on GOLOG and situation calculus is presented in **[^50]**, where a prototype implementation of Yet Another GOLOG Interpreter (YAGI), an action-based robot and agent programming language, is presented. . YAGI offers links for popular robotics frameworks such as Robot Operating System (ROS) **[^51]** and Fawkes.
  
  
  
  
  In **[^52]** the authors present a Cognitive Affective Agent Programming Framework (CAAF), a framework based on belief and desire theory of emotions that enables the computation of emotions for cognitive agents (i.e. that is, converting them into cognitive-affective agents). The authors present a semantics that shows the programming constructs of these agents. Using these constructs, a programmer can create an agent program with cognitive agents that automatically calculate emotions during executions.
  
  
  
  
##  4.2. Agent Programming Language Extensions
  
  
  
  
  In the previous section, we report works presenting novel APLs (2015–2020), along with works presenting the most influential APLs (≤2015) that remain. Now, we consider the most influential works that have extended existing APLs. We refer to APL extensions as work that has changed existing APLs internally, either by adding new features or building on top of existing APLs, for example by customizing the APL for a new, specific scenario.
  
  
  
  An improved version of the Multiple Agent System for Competitive Electricity Markets (MASCEM) **[^53]** is presented in **[^54]**. This extended version of the MASCEM simulator aims to support the integration of new and complementary models. Important structural implementation decisions provide the facility to accommodate different tools and mechanisms, making MASCEM able to deal with the constantly changing and highly demanding environment of electricity markets. In particular, the new MASCEM extension brings the use of ontologies to support player communications.
  
  
  
  In **[^55]**, the authors present TABSAOND, an extension of PEABS **[^41]**. The main difference between TABSAOND and PEABS is that the former focuses on the design and implementation of decision-making processes in non-deterministic scenarios. Additionally, simulators are now implemented as mobile applications and online tools.
  
  
  
  A conservative synchronization model for the SARL language and its Janus runtime platform is proposed in **[^56]**. Since Janus does not make any assumptions about the order of events that agents exchange, it is not possible to use the Janus platform for agent-based simulation involving time without providing the platform with a specific synchronization mechanism. A model for such a mechanism is described in its extension.
  
  
  
  
  
  
  The authors of **[^57]** propose new programming constructs to integrate an advanced but rule-based emotion model, EMIA **[^58]**, in line with the 2APL agent language **[^ 59]**. The combination of both has been carried out by redefining the syntax, semantics and deliberation cycle of 2APL. This combination focuses primarily on the generation of event-based emotions, and the resulting simulation shows high credibility in the emotions expressed by the agent when responding to real-life scenarios.
  
  
  
  
  ARGO **[^60]** is a custom Jason architecture for programming embedded robotic agents using Javino middleware and perception filters.
  
  
  
  
  In **[^61]**, the authors show how procedural reflection in the meta-APL agent programming language **[^62]** can be used to allow a direct implementation of some of the steps in the reflection cycle. deliberation of a BDI agent, by allowing both the agent programs and the agent's deliberation strategy to be coded in the same programming language.
  
  
  
  
  An extension **[^63]** by Jason and Gwendolen allows agents in these languages to communicate with ROS, thus supporting the programming of autonomous agents that can control and make high-level decisions in robotic applications developed in ROS. The extension is done through of an interface that is used as an environment between the agent and ROS, and communication between the environment and the ROS nodes is done using the rosbridge library. The main difference between their work and previous attempts to extend traditional APLs to support ROS is that their approach does not require additional modifications to either APL or ROS, making it usable and portable for different versions of these tools. Similarly, **[^64]** presents a framework for using Jason with ROS in embedded systems and introduces a new architecture to support low-level interactions between ROS and the agent.
  
  
  
  
  Finally, in **[^65]** a model for a BDI agent programming framework that integrates reinforcement learning and an implementation based on the Jason programming language is presented. The approach supports the design of BDI agents where some plans can be programmed explicitly and others can be learned by the agent during the development/engineering stage.
  
  
  
  
  
  
  
  
  
##  4.3. Comparison of Agent Programming Languages
  
  
  
  From the research described in the previous two sections, we can see that there are many APLs for developing MAS available in the agent-based programming community. Unfortunately, very often the evaluation of a language is partially or even completely missed. In the past some studies such as **[^66]** have been carried out to compare agent languages with other paradigms, in that case the comparison was with actor-based languages. In their results, the authors have shown that agent languages (specifically Jason in that work) can compete with lighter languages such as actors.
  
  
  
  In **[^67]**, the authors present an evaluation framework for evaluating existing or newly defined domain-specific modeling languages for MAS. The assessment focuses on both language and corresponding tools and provides both qualitative and quantitative results.
  
  
  
  
  
  **[^68]** shows a comparison between the pseudocode of a well-known algorithm for solving distributed constraint satisfaction problems and the implementation of such algorithm in JADEL.
  
  
  
  The work in **[^69]** focuses on comparing parallel platforms that support multi-agent simulations and their execution on high-performance resources such as parallel clusters.
  
  
  
  The authors of **[^70]** perform a systematic evaluation of ABMS approaches by differentiating the concepts of how complex the model behavior is and how complicated the model structure is, and illustrate the nonlinear relationship between them. Next, they evaluate trade-offs between simple models (often theoretical) and complicated models (often empirically based).
  
  
  
  
  
##  4.4. Agent-based applications
  
  
  
  
  In this section we list some of the latest applications that use agent-based programming. Our goal here is to show the wide variety of application domains in which agents can be useful, so this list is not exhaustive and is not the main focus of our review.
  
  
  
  The Multiagent Programming Contest (https://multiagentcontest.org/) (MAPC) is an annual international competition that has occurred since 2005. Its purpose is to stimulate research in multiagent programming by introducing complex reference scenarios that require coordinated action and can be used to test and compare programming languages, platforms, and multi-agent tools. Implementations using different agent-based platforms and languages have been used in recent years; like JaCaMo **[^71]**–**[^73]**, Jason **[^74]**,**[^75]**, GOAL **[^76]**.
  
  
  
  
  In **[^77]**,**[^78]** agent-based models were proposed to simulate and evaluate the transmission of coronavirus disease (COVID-19). There is an entire area of research focused on the use of agent-based technologies in the energy industry. For example, in **[^79]**, MAS technologies are used for Microgrid control, its optimization and distribution in the market. For further reading, there is a survey **[^80]** on the applications of MAS in the control and operation of Microgrids, and a review **[^81]** of the state of the art in the application of MAS to problems energy optimization.
  
  
  
  In **[^82]**, an application of ABMS is presented to study the relationships between human activities and changes in land use and land cover to support scientific decisions regarding reasonable land use and planning. floor. The model is implemented based on the Repast **[^83]** modeling platform.
  
  
  
  In **[^84]**, the authors present and illustrate FlowLogo, an interactive modeling environment for developing water models. underground s based on coupled agents. FlowLogo is implemented in NetLogo and is the first integrated software that offers a simple way to represent agent behaviors that evolve with groundwater conditions. A systematic survey of ABMS tools and applications can be found in **[^8]**.
  
  
  
  
  A methodological guide for using BDI agents in social simulations and an overview of existing methodologies and tools for using them are provided in **[^10]**.
  
  
  
  
  
  
  Agents can be used to develop self-managing Internet of Things (IoT) systems due to their distributed nature, context awareness, and self-adaptation (for more information on using microservices as agents in IoT **[^85]** ,**[^86]**). In **[^87]**, the authors aim to improve IoT application development using agents and software product lines in self-managing systems.
  
  
  
  
  In **[^88]** experiments are presented to validate the programming of autonomous robots using Jadescript. Introduces novel support for perception handlers that has recently been introduced into the language to address the high data rate of sensors in robotic applications.
  
  
  
  
#   5. Discussion and Future Directions
  
  
  
  
  As we have shown, there is a wide variety of options for agent-based programming, from more traditional approaches (e.g. BDI) to simulation or planning. Some languages have also attempted to combine concepts from agent-based programming with other programming paradigms, especially object-oriented programming. One of the main drawbacks of trying to achieve a broader community of programmers in agent-based programming is the lack of knowledge and familiarity with its concepts, which are significantly different from other more common paradigms. Agent-based programming languages that use some of the concepts from these other paradigms can help bring in new programmers who might otherwise be too intimidated. These hybrid languages have their own niche of applications depending on the concepts they use, which can sometimes overlap with more "pure" agent programming languages, but "pure" approaches are still necessary to fully address all agent programming abstractions. agents (agent, environment). , organization, interaction, etc.).
  
  
  
  
  
  Of the 15 agent programming languages listed in Table 1, five do not have a publicly available implementation (i.e., the code is not hosted in a public/accessible domain). This represents a major problem, as it limits the practical usability of the proposed language and makes quantitative comparison with other languages difficult. Not all extensions to existing languages require an implementation to be useful, however, having one available is always a positive for the community.
  
  
  
  
  Although there are several qualitative comparisons (e.g., concepts, features) in the literature, the use of different agency models makes it difficult to provide a fair comparison between the features present in these languages. Further study should be conducted to identify the fundamental characteristics of agent-oriented programming and, more importantly, how these characteristics fit into the different agency models that use existing programming languages.
  
  
  
  
  Quantitative comparisons (e.g., performance) of programming languages are more complicated due to the development cycle of having constant updates, which is even more common in programming languages developed in academia (as most are). of agent programming languages). However, it is important to develop agent-specific benchmarks that the community can easily use to evaluate new programming languages or extensions to existing languages.
  
  
  
  
  Most languages offer a variety of different examples that show their characteristics and strengths. While these examples are certainly useful for better understanding and learning the language, they are usually not enough to convince new users of the language's applicability in real-world applications. It is difficult to develop complex, realistic case studies, but the agent community has a set of complex scenarios available as part of the annual MAPC that could be better leveraged to test and compare agent programming languages.
  
  
  
  
  Two recent surveys **[^3]**,**[^5]** focused on BDI agent scheduling describe the limitations and challenges in the area. In a manifesto **[^3]**, the author argues that it is necessary to expand the feature set of current APLs to enable broader adoption of agent technology. The author also disagrees with previous surveys that the lack of more polished methodologies and tools is not the main factor (although it contributes) in the limited adoption of APL; Instead, the author suggests that there is little to no incentive for developers to make the switch to AOP, since the behaviors currently shown in applications in the literature can be implemented in more conventional languages with limited effort. The survey in **[^5]** summarizes the history so far and the state of the art in agent programming with a focus on BDI-based approaches. They identify as a great challenge for future research the integration of AI techniques in agent programming languages as an important and necessary step for the wide acceptance and adoption of AOP.
  
  
  
  
_  Recommendation for future research_
  
  
  
  
  Considering the last 5 years of research on APL, many novel frameworks, platforms and models have been proposed. Each of these, along with new extensions, enriched the agent-based literature and expanded the spectrum of possible applications. However, as correctly observed in **[^3]**,**[^5]**, the main problem with current APLs is not in their feature set, but in their usability. There is generally no desire to learn new languages when the benefits are not straightforward. In our review, we looked at APLs that were both expressive and powerful, but with significant usability issues; such as the absence of a (maintained) tool, documentation and qualitative and quantitative comparisons with other languages. In our opinion, further research on APL will have to address these usability issues to try to spread the use of APL outside the agent community.
  
  
  
  
  
  
  
#   6. Conclusions
  
  
  
  
  Agent-based programming is a thriving research area of artificial intelligence. In this review article, we have classified both veteran and recent contributions according to four different categories: agent-based programming languages, their extensions, comparisons between languages, and lastly, some of the applications that use these languages. For each contribution, we briefly review the content and outline key findings. To better understand the current state of the art, we not only focus on the latest approaches, but also briefly review the most prominent agent-based programming languages that are still around.
  
  
  
  
  Every year there are many extensions to existing languages and even completely new languages are proposed, however, most of them are limited to formal descriptions without any implementation to support the formal theory. The small subset of approaches with implementation lacks effective evaluation. Comparing new approaches with the state of the art is one of the main steps necessary to advance the area of agent-based programming. Qualitative and quantitative comparisons can help identify gaps in existing languages, which can lead to improvements or new approaches that can address the challenges raised. Furthermore, in our review we have also identified a lack of real-world applications. To expand the use of these languages, it is important that their real-world usability is well documented, therefore we encourage and recommend more application-based articles that can demonstrate the features of agent-based programming in the real world. . .
  
  
  
>   **Funding**: This research was funded by the UK Industrial Strategy Challenge Fund (ISCF), provided by UK Research and Innovation (UKRI) and managed by the Engineering and Physical Sciences Research Council (EPSRC) under Robotics and AI for Extreme. Environments Program with grants Robotics and AI in Nuclear (RAIN) Hub (EP/R026084/1), Future AI and Robotics for Space (FAIR-SPACE) Hub (EP/R026092/1) and Offshore Robotics for Certification of Assets (ORCA ) Bushing (EP/R026173/1).
  
  
  
  
>  **Conflicts of interest**: The authors declare that they have no conflicts of interest. The funders had no role in the study design; in the collection, analysis or interpretation of data; in the writing of the manuscript, or in the decision to publish the results.
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  






















































































#  Abbreviations



The following abbreviations are used:

| Acron.  | Concept    |  
|  :---:     |  :---    |  
|  AI  |  Artificial Intelligence  | 
|  AOP  |  Agent-Oriented Programming  | 
|  AOSE  |  Agent-Oriented Software Engineering  | 
|  APL  |  Agent Programming Language  | 
|  BDI  |  Belief-Desire-Intention  | 
|  CPS  |  Cyber-Physical Systems  | 
|  DSL  |  Domain Specific Language  | 
|  HTN  |  Hierarchical Task Network  | 
|  Iot  |  Internet of Things  | 
|  MAPC  |  Multi-Agent Programming Contest  | 
|  MAS  |  Multi-Agent System  | 
|  OOP  |  Object-Oriented Programming  | 
|  PRS  |  Procedural Reasoning System  | 





#  References

[^1]:  **[1]**. Introducing a New GenAI Stack: Streamlined AI/ML Integration Made Easy. Visited (2024) https://www.docker.com/blog/introducing-a-new-genai-stack/.

[^2]:  **[2]**. Containerize a generative AI application. Visited (2024) https://docs.docker.com/guides/use-case/genai-pdf-bot/containerize/.


[^3]:  **[3]**. Logan, B. An agent programming manifesto. Int. J. Agent-Oriented Softw. Eng. 2018, 6, 187–210. [CrossRef]


[^4]:  **[4]**. Russell, S.J.; Norvig, P. Artificial Intelligence: A Modern Approach, 3rd ed.; Prentice Hall: Upper Saddle River, NJ, USA, 2010.


[^5]:  **[5]**. Bordini, R.H.; Seghrouchni, A.E.F.; Hindriks, K.V.; Logan, B.; Ricci, A. Agent programming in the cognitive era. Auton. Agents Multi Agent Syst. 2020, 34, 37. [CrossRef]


[^6]:  **[6]**. Mao, X.; Wang, Q.; Yang, S. A survey of agent-oriented programming from software engineering perspective. Web Intell. 2017, 15, 143–163. [CrossRef]


[^7]:  **[7]**. Kravari, K.; Bassiliades, N. A Survey of Agent Platforms. J. Artif. Soc. Soc. Simul. 2015, 18. [CrossRef]


[^8]:  **[8]**. Abar, S.; Theodoropoulos, G.K.; Lemarinier, P.; O’Hare, G.M.P. Agent Based Modelling and Simulation tools: A review of the state-of-art software. Comput. Sci. Rev. 2017, 24, 13–33. [CrossRef]


[^9]:  **[9]**. Isern, D.; Moreno, A. A systematic literature review of agents applied in healthcare. J. Med Syst. 2016, 40, 43. [CrossRef]


[^10]:  **[10]**. Adam, C.; Gaudou, B. BDI agents in social simulations: a survey. Knowl. Eng. Rev. 2016, 31, 207–238. [CrossRef]


[^11]:  **[11]**. Shoham, Y. Agent-oriented Programming. Artif. Intell. 1993, 60, 51–92. [CrossRef]


[^12]:  **[12]**. Georgeff, M.; Lansky, A. Procedural Knowledge. Proc. IEEE (Spec. Issue Knowl. Represent.) 1986, 74, 1383–1398. [CrossRef]


[^13]:  **[13]**. Bratman, M.E. Intentions, Plans, and Practical Reason; Center for the Study of Language and Information: Stanford, CA, USA, 1999.


[^14]:  **[14]**. Rao, A.S.; Georgeff, M. BDI Agents: From Theory to Practice. In Proceedings of the First International Conference on Multiagent Systems (ICMAS), San Francisco, CA, USA, 12–14 June 1995; pp. 312–319.


[^15]:  **[15]**. Rao, A.S. AgentSpeak(L): BDI Agents Speak Out in a Logical Computable Language. In Agents Breaking Away, Proceedings of the 7th European Workshop on Modelling Autonomous Agents in a Multi-Agent World, Eindhoven, The Netherlands, 22–25 January 1996; Lecture Notes in Computer Science; de Velde, W.V., Perram, J.W., Eds.; Springer: Berlin/Heidelberg, Germany, 1996; Volume 1038, pp. 42–55. [CrossRef]


[^16]:  **[16]**. McCarthy, J.; Hayes, P.J. Some Philosophical Problems from the Standpoint of Artificial Intelligence. In Machine Intelligence 4; Meltzer, B., Michie, D., Eds.; Edinburgh University Press: Edinburgh, UK, 1969; pp. 463–502. reprinted in McC90.


[^17]:  **[17]**. Issicaba, D.; Rosa, M.A.; Prostejovsky, A.M.; Bindner, H.W. Experimental validation of BDI agents for distributed control of electric power grids. In Proceedings of the 2017 IEEE PES Innovative Smart Grid Technologies Conference Europe (ISGT-Europe), Torino, Italy, 26–29 September 2017; pp. 1–6. [CrossRef]


[^18]:  **[18]**. Sorici, A.; Boissier, O.; Picard, G.; Santi, A. Exploiting the JaCaMo Framework for Realising an Adaptive Room Governance Application. In Proceedings of the Compilation of the Co-Located Workshops on DSM’11, TMC’11, AGERE! 2011, AOOPES’11, NEAT’11, and VMIL’11; New York, NY, USA, 1–31 October 2011; pp. 239–242. [CrossRef]


[^19]:  **[19]**. Persson, C.; Picard, G.; Ramparany, F.; Boissier, O. A JaCaMo-Based Governance of Machine-to-Machine Systems. In Advances on Practical Applications of Agents and Multi-Agent Systems; Demazeau, Y., Müller, J.P., Rodríguez, J.M.C., Pérez, J.B., Eds.; Springer: Berlin/Heidelberg, Germany, 2012; pp. 161–168.


[^20]:  **[20]**. Krupa, Y.; Vercouter, L. Handling Privacy as Contextual Integrity in Decentralized Virtual Communities: The PrivaCIAS Framework. Web Intelli. Agent Syst. 2012, 10, 105–116. [CrossRef]


[^21]:  **[21]**. Collier, R.W.; Russell, S.E.; Lillis, D. Reflecting on Agent Programming with AgentSpeak(L). In Proceedings of the PRIMA 2015: Principles and Practice of Multi-Agent Systems—18th International Conference, Bertinoro, Italy, 26–30 October 2015; Lecture Notes in Computer Science; Chen, Q., Torroni, P., Villata, S., Hsu, J.Y., Omicini, A., Eds.; Springer: Cham, Switzerland, 2015; Volume 9387, pp. 351–366. [CrossRef]


[^22]:  **[22]**. Honorato-Zimmer, R.; Millar, A.J.; Plotkin, G.D.; Zardilis, A. Chromar, a language of parameterised agents. Theor. Comput. Sci. 2019, 765, 97–119. [CrossRef]


[^23]:  **[23]**. Hindriks, K.V.; de Boer, F.S.; van der Hoek, W.; Meyer, J.J.C. Agent Programming with Declarative Goals. In Proceedings of the 7th International Workshop on Agent Theories, Architectures, Boston, MA, USA, 7–9 July 2020; pp. 228–243.


[^24]:  **[24]**. Bordini, R.H.; Wooldridge, M.; Hübner, J.F. Programming Multi-Agent Systems in AgentSpeak Using Jason; John Wiley & Sons: Hoboken, NJ, USA, 2007.


[^25]:  **[25]**. Boissier, O.; Bordini, R.H.; Hübner, J.F.; Ricci, A.; Santi, A. Multi-agent oriented programming with JaCaMo. Sci. Comput. Program. 2013, 78, 747–761. [CrossRef]


[^26]:  **[26]**. Boissier, O.; Bordini, R.; Hubner, J.; Ricci, A. Multi-Agent Oriented Programming: Programming Multi-Agent Systems Using JaCaMo; Intelligent Robotics and Autonomous Agents Series; MIT Press: Cambridge, MA, USA, 2020.


[^27]:  **[27]**. Ricci, A.; Piunti, M.; Viroli, M.; Omicini, A. Environment Programming in CArtAgO. In Multi-Agent Programming: Languages, Tools and Applications; Multiagent Systems, Artificial Societies, and Simulated Organizations; Springer: Boston, MA, USA, 2009; Chapter 8, pp. 259–288. [CrossRef]


[^28]:  **[28]**. Hübner, J.F.; Sichman, J.S.; Boissier, O. Developing organised multiagent systems using the MOISE+ model: programming issues at the system and agent levels. Int. J. Agent-Oriented Softw. Eng. 2007, 1, 370–395. [CrossRef]


[^29]:  **[29]**. Dennis, L.A. Gwendolen Semantics: 2017; Technical Report ULCS-17-001; University of Liverpool, Department of Computer Science: Liverpool, UK, 2017.


[^30]:  **[30]**. Bellifemine, F.L.; Caire, G.; Greenwood, D. Developing Multi-Agent Systems with JADE (Wiley Series in Agent Technology); John Wiley & Sons: Hoboken, NJ, USA, 2007.


[^31]:  **[31]**. Bergenti, F.; Iotti, E.; Monica, S.; Poggi, A. Agent-oriented model-driven development for JADE with the JADEL programming language. Comput. Lang. Syst. Struct. 2017, 50, 142–158. [CrossRef]


[^32]:  **[32]**. Bergenti, F.; Monica, S.; Petrosino, G. A scripting language for practical agent-oriented programming. In Proceedings of the 8th ACM SIGPLAN International Workshop on Programming Based on Actors, Agents, and Decentralized Control, AGERE!@SPLASH 2018, Boston, MA, USA, 5 November 2018; pp. 62–71. [CrossRef]


[^33]:  **[33]**. Pokahr, A.; Braubach, L.; Lamersdorf, W., Jadex: A BDI Reasoning Engine. In Multi-Agent Programming: Languages, Platforms and Applications; Springer: Boston, MA, USA, 2005; pp. 149–174. [CrossRef]


[^34]:  **[34]**. Aschermann, M.; Dennisen, S.; Kraus, P.; Müller, J.P. LightJason, a Highly Scalable and Concurrent Agent Framework: Overview and Application. In Proceedings of the 17th International Conference on Autonomous Agents and MultiAgent Systems, AAMAS   2018, Stockholm, Sweden, 10–15 July 2018; pp. 1794–1796.


[^35]:  **[35]**. Hashmi, M.A.; Seghrouchni, A.E.F.; Akram, M.U. A Planning Based Agent Programming Language Supporting Environment Modeling. In Proceedings of the IEEE/WIC/ACM International Conference on Web Intelligence and Intelligent Agent Technology, WI-IAT 2015, Singapore, 6–9 December 2015; pp. 76–83. [CrossRef]


[^36]:  **[36]**. Kilaru, J. PLASA: Programming Language for Synchronous Agents. Master’s Thesis, California State University, Long Beach, CA, USA, 2018.


[^37]:  **[37]**. Flocchini, P.; Prencipe, G.; Santoro, N.; Widmayer, P. Gathering of asynchronous robots with limited visibility. Theor. Comput. Sci.   2005, 337, 147–168. [CrossRef]


[^38]:  **[38]**. Bonci, A.; Pirani, M.; Bianconi, C.; Longhi, S. RMAS: Relational Multiagent System for CPS Prototyping and Programming. In Proceedings of the 14th IEEE/ASME International Conference on Mechatronic and Embedded Systems and Applications, MESA 2018, Oulu, Finland, 2–4 July 2018; pp. 1–6. [CrossRef]


[^39]:  **[39]**. Rodriguez, S.; Gaud, N.; Galland, S. SARL: A General-Purpose Agent-Oriented Programming Language. In Proceedings of the 2014 IEEE/WIC/ACM International Joint Conferences on Web Intelligence (WI) and Intelligent Agent Technologies (IAT), Warsaw, Poland, 11–14 August 2014; Volume III, pp. 103–110; [CrossRef]


[^40]:  **[40]**. Molesini, A.; Casadei, M.; Omicini, A.; Viroli, M. Simulation in agent-oriented software engineering: The SODA case study. Sci. Comput. Program. 2013, 78, 705–714. [CrossRef]


[^41]:  **[41]**. García-Magariño, I.; Gómez-Rodríguez, A.; Moreno, J.C.G.; Navarro, G.P. PEABS: A Process for developing Efficient Agent-Based Simulators. Eng. Appl. Artif. Intell. 2015, 46, 104–112. [CrossRef]


[^42]:  **[42]**. Pavón, J.; Gómez-Sanz, J.; Fuentes-Fernández, R., The INGENIAS methodology and tools. In Agent-Oriented Methodol; IGI Global: Hershey, PA, USA, 2005; pp. 236–276. [CrossRef]


[^43]:  **[43]**. Caillou, P.; Gaudou, B.; Grignard, A.; Truong, Q.C.; Taillandier, P. A Simple-to-Use BDI Architecture for Agent-Based Mod- eling and Simulation. In Proceedings of the European Social Simulation Association 2015, Groningen, The Netherlands,   14–18 September 2015; Volume 528, pp. 15–28. [CrossRef]


[^44]:  **[44]**. Taillandier, P.; Bourgais, M.; Caillou, P.; Adam, C.; Gaudou, B. A BDI Agent Architecture for the GAMA Modeling and Simulation Platform. In Proceedings of the Multi-Agent Based Simulation XVII—International Workshop, MABS 2016, Singapore, 10 May   2016; Volume 10399, pp. 3–23. [CrossRef]


[^45]:  **[45]**. Grignard, A.; Taillandier, P.; Gaudou, B.; Vo, D.; Huynh, N.Q.; Drogoul, A. GAMA 1.6: Advancing the Art of Complex Agent- Based Modeling and Simulation. In Proceedings of the PRIMA 2013: Principles and Practice of Multi-Agent Systems—16th International Conference, Dunedin, New Zealand, 1–6 December 2013; Volume 8291, pp. 117–131. [CrossRef]


[^46]:  **[46]**. Singh, D.; Padgham, L.; Logan, B. Integrating BDI Agents with Agent-Based Simulation Platforms. Auton. Agents Multi Agent Syst. 2016, 30, 1050–1071. [CrossRef]


[^47]:  **[47]**. Belle, V.; Levesque, H.J. PREGO: An Action Language for Belief-Based Cognitive Robotics in Continuous Domains. In Proceedings of the Twenty-Eighth AAAI Conference on Artificial Intelligence, Québec City, QC, Canada, 27–31 July 2014; pp. 989–995.


[^48]:  **[48]**. Belle, V.; Levesque, H.J. ALLEGRO: Belief-Based Programming in Stochastic Dynamical Domains. In Proceedings of the Twenty-Fourth International Joint Conference on Artificial Intelligence, IJCAI 2015, Buenos Aires, Argentina, 25–31 July 2015; pp. 2762–2769.


[^49]:  **[49]**. Levesque, H.J.; Reiter, R.; Lespérance, Y.; Lin, F.; Scherl, R.B. GOLOG: A Logic Programming Language for Dynamic Domains. J. Log. Program. 1997, 31, 59–83. [CrossRef]


[^50]:  **[50]**. Ferrein, A.; Maier, C.; Mühlbacher, C.; Niemueller, T.; Steinbauer, G.; Vassos, S. Controlling Logistics Robots with the Action-Based Language YAGI. In Proceedings of the Intelligent Robotics and Applications—9th International Conference, ICIRA 2016, Tokyo, Japan, 22–24 August 2016; Volume 9834, pp. 525–537. [CrossRef]


[^51]:  **[51]**. Quigley, M.; Conley, K.; Gerkey, B.; Faust, J.; Foote, T.; Leibs, J.; Wheeler, R.; Ng, A. ROS: An open-source Robot Operating System. In Proceedings of the Workshop on Open Source Software at the International Conference on Robotics and Automation, Kobe, Japan, 12–13 May 2009; p. 5.


[^52]:  **[52]**. Kaptein, F.; Broekens, J.; Hindriks, K.V.; Neerincx, M.A. CAAF: A Cognitive Affective Agent Programming Framework. In Proceedings of the Intelligent Virtual Agents—16th International Conference, IVA 2016, Los Angeles, CA, USA, 20–23 September   2016; Volume 10011, pp. 317–330. [CrossRef]


[^53]:  **[53]**. Praça, I.; Ramos, C.; Vale, Z.; Cordeiro, M. MASCEM: A multiagent system that simulates competitive electricity markets. IEEE Intell. Syst. 2003, 18, 54–60. [CrossRef]


[^54]:  **[54]**. Santos, G.; Pinto, T.; Praça, I.; Vale, Z. MASCEM: Optimizing the performance of a multi-agent system. Energy 2016, 111, 513–524. [CrossRef]


[^55]:  **[55]**. García-Magariño, I.; Navarro, G.P.; Lacuesta, R. TABSAOND: A technique for developing agent-based simulation apps and online tools with nondeterministic decisions. Simul. Model. Pract. Theory 2017, 77, 84–107. [CrossRef]


[^56]:  **[56]**. Cich, G.; Galland, S.; Knapen, L.; Yasar, A.; Bellemans, T.; Janssens, D. Addressing the Challenges of Conservative Event Synchronization for the SARL Agent-Programming Language. In Proceedings of the Advances in Practical Applications of Cyber-Physical Multi-Agent Systems, PAAMS Collection—15th International Conference, PAAMS 2017, Porto, Portugal, 21–23 June 2017; Volume 10349, pp. 31–42. [CrossRef]


[^57]:  **[57]**. Jain, S.; Asawa, K. Programming an expressive autonomous agent. Expert Syst. Appl. 2016, 43, 131–141. [CrossRef]


[^58]:  **[58]**. Jain, S.; Asawa, K. EMIA: emotion model for intelligent agent. J. Intell. Syst. 2015, 24, 449–465. [CrossRef]


[^59]:  **[59]**. Dastani, M. 2APL: A practical agent programming language. Auton. Agents Multi-Agent Syst. 2008, 16, 214–248. [CrossRef]


[^60]:  **[60]**. Pantoja, C.E.; Stabile, M.F.; Lazarin, N.M.; Sichman, J.S. ARGO: An Extended Jason Architecture that Facilitates Embedded Robotic Agents Programming. In Proceedings of the Engineering Multi-Agent Systems—4th International Workshop, EMAS   2016, Singapore, 9–10 May 2016; Volume 10093, pp. 136–155. [CrossRef]


[^61]:  **[61]**. Leask, S.; Logan, B. Programming deliberation strategies in meta-APL. In Proceedings of the International Conference on Principles and Practice of Multi-Agent Systems, Bertinoro, Italy, 26–30 October 2015; pp. 433–448.


[^62]:  **[62]**. Doan, T.T.; Yao, Y.; Alechina, N.; Logan, B. Verifying heterogeneous multi-agent programs. In Proceedings of the International conference on Autonomous Agents and Multi-Agent Systems, AAMAS ’14, Paris, France, 5–9 May 2014; pp. 149–156.


[^63]:  **[63]**. Cardoso, R.C.; Ferrando, A.; Dennis, L.A.; Fisher, M. An Interface for Programming Verifiable Autonomous Agents in ROS. In Proceedings of the European Conference on Multi-Agent Systems (EUMAS), Thessaloniki, Greece, 14–15 September 2020.


[^64]:  **[64]**. Onyedinma, C.; Gavigan, P.; Esfandiari, B. Toward Campus Mail Delivery Using BDI. J. Sens. Actuator Netw. 2020, 9, 56. [CrossRef]


[^65]:  **[65]**. Bosello, M.; Ricci, A. From Programming Agents to Educating Agents - A Jason-Based Framework for Integrating Learning in the Development of Cognitive Agents. In Proceedings of the Engineering Multi-Agent Systems—7th International Workshop, EMAS   2019, Montreal, QC, Canada, 13–14 May 2019; Volume 12058, pp. 175–194. [CrossRef]


[^66]:  **[66]**. Cardoso, R.C.; Zatelli, M.R.; Hübner, J.F.; Bordini, R.H. Towards Benchmarking Actor- and Agent-Based Programming Languages. In Proceedings of the Workshop on Programming Based on Actors, Agents, and Decentralized Control, Indianapolis, IN, USA,   27 October 2013; pp. 115–126.


[^67]:  **[67]**. Challenger, M.; Kardas, G.; Tekinerdogan, B. A systematic approach to evaluating domain-specific modeling language environ- ments for multi-agent systems. Softw. Qual. J. 2016, 24, 755–795. [CrossRef]


[^68]:  **[68]**. Bergenti, F.; Iotti, E.; Monica, S.; Poggi, A. A Comparison between Asynchronous Backtracking Pseudocode and its JADEL Implementation. In Proceedings of the 9th International Conference on Agents and Artificial Intelligence, ICAART, Porto, Portugal, 24–26 February 2017; Volume 2, pp. 250–258. [CrossRef]


[^69]:  **[69]**. Rousset, A.; Herrmann, B.; Lang, C.; Philippe, L. A survey on parallel and distributed multi-agent systems for high performance computing simulations. Comput. Sci. Rev. 2016, 22, 27–46. [CrossRef]


[^70]:  **[70]**. Sun, Z.; Lorscheid, I.; Millington, J.D.A.; Lauf, S.; Magliocca, N.R.; Groeneveld, J.; Balbi, S.; Nolzen, H.; Müller, B.; Schulze, J.; et al. Simple or complicated agent-based models? A complicated issue. Environ. Model. Softw. 2016, 86, 56–67. [CrossRef]


[^71]:  **[71]**. Cardoso, R.C.; Krausburg, T.; Baségio, T.L.; Engelmann, D.C.; Hübner, J.F.; Bordini, R.H. SMART-JaCaMo: An organization-based team for the multi-agent programming contest. Ann. Math. Artif. Intell. 2018, 84, 75–93. [CrossRef]


[^72]:  **[72]**. Krausburg, T.; Cardoso, R.C.; Damasio, J.; Peres, V.; Farias, G.P.; Engelmann, D.C.; Hübner, J.F.; Bordini, R.H. SMART–JaCaMo: An Organisation-Based Team for the Multi-Agent Programming Contest. In The Multi-Agent Programming Contest 2018; Ahlbrecht, T., Dix, J., Fiekas, N., Eds.; Springer International Publishing: Cham, Switzerland, 2019; pp. 72–100.


[^73]:  **[73]**. Cardoso, R.C.; Ferrando, A.; Papacchini, F. LFC: Combining Autonomous Agents and Automated Planning in the Multi-Agent Programming Contest. In Multi-Agent Progamming Contest; Springer: Cham, Switzerland, 2019; pp. 31–58.


[^74]:  **[74]**. Vezina, M.; Esfandiari, B. The Requirement Gatherers’ Approach to the 2019 Multi-Agent Programming Contest Scenario. In The Multi-Agent Programming Contest 2019; Ahlbrecht, T., Dix, J., Fiekas, N., Krausburg, T., Eds.; Springer International Publishing: Cham, Switzerland, 2020; pp. 106–150.


[^75]:  **[75]**. Villadsen, J.; Bjørn, M.O.; From, A.H.; Henney, T.S.; Larsen, J.B. Multi-Agent Programming Contest 2018—The Jason-DTU Team. In The Multi-Agent Programming Contest 2018; Ahlbrecht, T., Dix, J., Fiekas, N., Eds.; Springer International Publishing: Cham, Switzerland, 2019; pp. 41–71.


[^76]:  **[76]**. Jensen, A.B.; Villadsen, J. GOAL-DTU: Development of Distributed Intelligence for the Multi-Agent Programming Contest. In The Multi-Agent Programming Contest 2019; Ahlbrecht, T., Dix, J., Fiekas, N., Krausburg, T., Eds.; Springer International Publishing: Cham, Switzerland, 2020; pp. 79–105.


[^77]:  **[77]**. Wolfram, C. An Agent-Based Model of COVID-19. Complex Syst. 2020, 29. [CrossRef]


[^78]:  **[78]**. Prudhomme, C.; Cruz, C.; Cherifi, H. An Agent based model for the transmission and control of the COVID-19 in Dijon (extended abstract). In Proceedings of MARAMI 2020—Modèles & Analyse des Réseaux: Approches Mathématiques & Informatiques—The   11th Conference on Network Modeling and Analysis, Virtual Conference, Montpellier, France, 14–15 October 2020; Volume 2750.


[^79]:  **[79]**. Khan, M.W.; Wang, J. The research on multi-agent system for microgrid control and optimization. Renew. Sustain. Energy Rev.   2017, 80, 1399–1411. [CrossRef]


[^80]:  **[80]**. Kantamneni, A.; Brown, L.E.; Parker, G.G.; Weaver, W.W. Survey of multi-agent systems for microgrid control. Eng. Appl. Artif. Intell. 2015, 45, 192–203. [CrossRef]


[^81]:  **[81]**. González-Briones, A.; De La Prieta, F.; Mohamad, M.S.; Omatu, S.; Corchado, J.M. Multi-agent systems applications in energy optimization problems: A state-of-the-art review. Energies 2018, 11, 1928. [CrossRef]


[^82]:  **[82]**. QuanLi, X.; Kun, Y.; GuiLin, W.; YuLian, Y. Agent-based modeling and simulations of land-use and land-cover change according to ant colony optimization: A case study of the Erhai Lake Basin, China. Nat. Hazards 2015, 75, 95–118. [CrossRef]


[^83]:  **[83]**. North, M.; Collier, N.; Ozik, J.; Tatara, E.; Macal, C.; Bragen, M.; Sydelko, P. Complex Adaptive Systems Modeling with Repast Simphony. Complex Adapt. Syst. Model. 2013, 1, 1–26. [CrossRef]


[^84]:  **[84]**. Castilla-Rho, J.C.; Mariethoz, G.; Rojas-Mujica, R.; Andersen, M.S.; Kelly, B.F.J. An agent-based platform for simulating complex human-aquifer interactions in managed groundwater systems. Environ. Model. Softw. 2015, 73, 305–323. [CrossRef]


[^85]:  **[85]**. Savaglio, C.; Fortino, G.; Ganzha, M.; Paprzycki, M.; Badica, C.; Ivanovic, M. Agent-Based Computing in the Internet of Things: A Survey. In Proceedings of the Intelligent Distributed Computing XI—11th International Symposium on Intelligent Distributed Computing—IDC 2017, Belgrade, Serbia, 11–13 October 2017; Volume 737, pp. 307–320. [CrossRef]


[^86]:  **[86]**. Krivic, P.; Skocir, P.; Kusek, M.; Jezic, G. Microservices as Agents in IoT Systems. In Proceedings of the Agent and Multi-Agent Systems: Technology and Applications, 11th KES International Conference, KES-AMSTA 2017, Vilamoura, Algarve, Portugal, 21–23 June 2017; Volume 74, pp. 22–31. [CrossRef]


[^87]:  **[87]**. Ayala, I.; Amor, M.; Fuentes, L.; Troya, J.M. A Software Product Line Process to Develop Agents for the IoT. Sensors 2015, 15, 15640–15660. [CrossRef]


[^88]:  **[88]**. Iotti, E.; Petrosino, G.; Monica, S.; Bergenti, F. Exploratory Experiments on Programming Autonomous Robots in Jadescript. In Proceedings of the First Workshop on Agents and Robots for reliable Engineered Autonomy, AREA@ECAI 2020, Virtual Event, Santiago de Compostela, Spain, 4 September 2020; Volume 319, pp. 55–67. [CrossRef]

