---
layout:  proposal
toc:  true
author:  'Ernest J. Friedman-Hill'
license:  'Sandia National Laboratories'
ref:  p49-jess-80
lang:  en
date:  '2013-08-01'
modified:  '2022-08-31'
status:  'In progress: final checks'
title:  'Proposal: compile and review Jess 8.0a1'
subtitle:  'Jess 8.0a1 revision proposal to be compiled with Java 1.8 at 32bit and with OpenJDK 11 or higher at 64bit.'
headtitle:  'Jess is a rule engine for the Java platform. To use it, you specify logic in the form of rules using one of two formats: the Jess rule language (prefered) or XML. You also provide some of your own data for the rules to operate on. When you run the rule engine, your rules are carried out. Rules can create new data, or they can do anything that the Java programming language can do. '
imagepath:  'images/jess-8/'
images:
  -  'jess.gif'
  
---

##  To-Do List:
- [x]  \(1) Preparing Jess-8.0a1 to be compiled with Java SE-1.8 and JDK-17
- [x]  \(2) List Java compiler recommendations on Jess's code. Document and organize.
- [x]  \(3) Initiate releases as changes are made to bring code from Java-1.6 through Java-11
- 
- 
- 
- 
- 
- 








  

##   Section 1: Identification
-  Responsible for the proposal: _FJ Aguayo_.
-  Proposal date: August, 2022.
-  Results location: GitHub repo.

##   Section 2: Processes
-  
-  

###  2.1. Description of the proposal:

-  
-  

###  2.2. target platform
-  Java JDK-11[^java] through JDK-18[^migra17]. OpenJDK-18[^openJDK].
  
-  JADE PS-Agents, version 1.9 or higher (2022)




###  23. What does the proposal need for its execution?
-  ECLIPSE IDE 2022-R3.
-  
-  JADE PS Agents version 1.9 or higher.
-  

###  2.4. Why this proposal?
-  
-  






###  2.5. Underlying technology or technologies:
-  
-  
-  
-  








###  2.6. Name of the generated library?
-    jess-8.0b1-x86.jar
-    jess-8.0b1-x64.jar
-    
-    
-    
-    









###  2.7. Dependencies on specific operating systems
-  












###  2.8. Security issues due to the current security model
-  














###  2.9. Internationalization or localization problems?
-  















###  2.10. Any need for revision as a result of this work?
-  
















###  2.11. Schedule for the development of this proposal
-   Start: **August 2022**
-   End: **--**
















##   Section 3: Contributions
-    



###  3.1. Documents, proposals or implementations that describe the technology.















###  3.2. Starting point of the work.
-   



















##   Section 4: Additional Information (Optional)












###  4.1. Additional information to include in the Improvement Proposal
  
  








##  _References_



[^java]: ORACLE Java 17 is the latest long-term support (LTS) release under Java's six-month release cadence and is the result of extensive collaboration between Oracle engineers and other members of the worldwide Java developer community via the OpenJDK Community and the Java Community Process (JCP). Verificada con la versioón jdk-17.0.3.1 (junio, 2022). https://www.oracle.com/news/announcement/oracle-releases-java-17-2021-09-14/.

[^jade]:    JADE Platform. jade - Revision 6867: /trunk. https://jade.tilab.com/svn/jade/trunk/  Login/passwod: jade/jade. Version 4.5.4 (abril, 2022).

[^migra17]: Significant Changes in JDK 17 Release. Notes for additional descriptions of the new features and enhancements, and API specification in JDK 17. Updates in Java SE 17 and JDK 17: https://docs.oracle.com/en/java/javase/17/migrate/significant-changes-jdk-release.html

[^openJDK]: OpenJDK 17 is the open-source reference implementation of version 17 of the Java SE Platform, as specified by by JSR 390 in the Java Community Process. JDK 17 reached General Availability on 14 September 2021. URL for OpenJDK-11 is: https://openjdk.java.net/projects/jdk/11/. URL for OpenJDK-17 is: https://openjdk.java.net/projects/jdk/17/.


