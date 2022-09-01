---
layout:  proposal
toc:  true
author:  'Gary Riley'
license:  'GNU Lesser General Public License v2.1'
ref:  p41-clipsjni-640
lang:  en
date:  '2021-05-14'
modified:  '2022-08-24'
status:  'In progress: final checks'
title:  'Proposal: auto-localization of native library for CLIPSJNI-6.40'
subtitle:  'Proposal to update CLIPS-JNI-6.40 to facilitate the detection of the machine architecture and the location of the native library at runtime'
headtitle:  'The component developed in Java CLIPSJNI-6.40 allows connecting Java to the CLIPS core developed in C++. This update proposal provides a solution to detect the architecture of the machine at runtime, as well as incorporating other additional security improvements, variable declaration adjustment and CLIPS engine Router deletion errors. This minor evolution of CLIPSJNI-6.40 is oriented to JADE PS-Agents. These agents manage and execute expert systems, and exchange their facts, rules and conclusions. However, this evolution of CLIPSJNI-6.40 may be useful in any application that requires connectivity to CLIPS 6.40 from Java.'
imagepath:  'images/clipsjni-640/'
images:
  -  'clips.gif'
  
---

##  To-Do List:
- [x]  \(1) Prepare CLIPSJNI-6.40 to be compiled with Java SE-1.8 and with the Java JPMS[^migra17] module system.
- [x]  \(2) Check that after the modifications, it can be compiled with versions of Oracle Java[^java] JDK-11 up to JDK-17 LTS (2022-2029) and higher. And also, allow compilation with versions of OpenJDK[^openJDK] from openJDK-11 to OpenJDK-18.
- [x]  \(3) Check the 90 new methods provided by the new version of CLIPSJNI-6.40. And its behavior on agents of the JADE platform. Specifically, the profound modifications made to the Router.
- [x]  \(4) Incorporate build sequence files for the different architectures.
- [x]  \(5) Carry out the CLIPS 6.40 tests on a Node-type Agents console.
- [x]  \(6) Prepare as a GitHub repository to allow analysis and evaluation of the proposal.
- [x]  \(7) Tune the deleteRouter() method
- [x]  \(8) Create and adjust the Native Library selection mechanism through JAR Path or through operating system PATH.
- [x]  \(9) Elimination of static declarations. Object changes: ExternalAddressValue, InstanceAddresValue, Router, and Shell object creation.








  

##   Section 1: Identification
-  Responsible for the proposal: _FJ Aguayo_.
-  Proposal date: April, 2022.
-  Results location: GitHub repo.

##   Section 2: Processes
-  CLIPS-JNI version 6.40 native Java interface for CLIPS 6.40[^1] has been reviewed by _Gary Riley_ on 2021-04-29. The source code is available on Source forge at <https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/>.
-  JADE[^jade] agents with the ability to integrate and run autonomous Expert Systems on the Multi-Agent platform require prior knowledge of the architecture of the Java machine and the hardware on which they run.

###  2.1. Description of the proposal:

-  Incorporate in CLIPS-JNI-6.40 a method to detect which is the Java machine and the hardware architecture of the node where the Multi-Agent system is executed, and in this way, the CLIPSJNI Library itself can associate and link with its native library in C++.
-  The development of the additional security elements was carried out by adjusting the visibility of the fundamental Objects that make up the CLIPS-JNI-6.40 library.

###  2.2. target platform
-  Java JDK-11[^java] through JDK-18[^migra17]. OpenJDK-18[^openJDK]. CLIPS 6.40
  
-  JADE PS-Agents, version 2.1 or higher (2022)




###  23. What does the proposal need for its execution?
-  ECLIPSE IDE 2022-R3.
-  CLIPS 6.40 source-code. CLIPS-JNI-6.40 source-code.
-  JADE PS Agents version 1.9 or higher.
-  CLIPS 6.40 test[^cool]

###  2.4. Why this proposal?
-  Because Gary D. Riley, author of the library, has made a profound transformation of this software component. The total number of methods in the main Object (Environment()) has been multiplied by 5. This modification has altered Interfaces and declarations, which makes it impossible to integrate them with the same or previous versions of Agents-PS 1.8.
-  Because the improvements in the CLIPS 6.40 version of the Expert Systems Construction Tool are very relevant, as well as in the CLIPSJNI.JAR library. Therefore, this proposal is also a mechanism for internal documentation and research.






###  2.5. Underlying technology or technologies:
-  CLIPS
-  COOL
-  Java
-  lisp








###  2.6. Name of the generated library?
-    clipsjni-6.40-amd32.jar --> libclipsjni-6.40-amd32.so
-    clipsjni-6.40-amd64.jar --> libclipsjni-6.40-amd64.so
-    clipsjni-6.40-x86.jar --> clipsjni-6.40-x86.dll
-    clipsjni-6.40-x64.jar --> clipsjni-6.40-x64.dll
-    clipsjni-6.40-osx64.jar --> libclipsjni-6.40-osx64.jnilib
-    clipsjni-6.40-arm64.jar --> libclipsjni-6.40-arm64.so









###  2.7. Dependencies on specific operating systems
-  None. It is the library itself that is adapted and compiled for each system, JVM and hardware architecture.












###  2.8. Security issues due to the current security model
-  Does not apply to this project














###  2.9. Internationalization or localization problems?
-  They have not been implemented. It is documented following the research process of each new method incorporated into CLIPSJNI-6.40















###  2.10. Any need for revision as a result of this work?
-  It has not been planned. The proposal and the result provided remain in a GitHub Repository for study and assessment.
















###  2.11. Schedule for the development of this proposal
-   Start: **April 2022**
-   End: **August 2022**
















##   Section 3: Contributions
-    FJ Aguayo (2022).



###  3.1. Documents, proposals or implementations that describe the technology.















###  3.2. Starting point of the work.
-   CLIPSJNI-6.40 on Source Forge at: https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40



















##   Section 4: Additional Information (Optional)












###  4.1. Additional information to include in the Improvement Proposal
  
  








##  _References_

[^1]: CLIPS Rule Based Programming Language Files. Expert System Tool. Gary, Riley D. (Ed. 2022). URL: https://sourceforge.net/projects/clipsrules/.

[^java]: ORACLE Java 17 is the latest long-term support (LTS) release under Java's six-month release cadence and is the result of extensive collaboration between Oracle engineers and other members of the worldwide Java developer community via the OpenJDK Community and the Java Community Process (JCP). Verificada con la versioón jdk-17.0.3.1 (junio, 2022). https://www.oracle.com/news/announcement/oracle-releases-java-17-2021-09-14/.

[^jade]:    JADE Platform. jade - Revision 6867: /trunk. https://jade.tilab.com/svn/jade/trunk/  Login/passwod: jade/jade. Version 4.5.4 (abril, 2022).

[^migra17]: Significant Changes in JDK 17 Release. Notes for additional descriptions of the new features and enhancements, and API specification in JDK 17. Updates in Java SE 17 and JDK 17: https://docs.oracle.com/en/java/javase/17/migrate/significant-changes-jdk-release.html

[^openJDK]: OpenJDK 17 is the open-source reference implementation of version 17 of the Java SE Platform, as specified by by JSR 390 in the Java Community Process. JDK 17 reached General Availability on 14 September 2021. URL for OpenJDK-11 is: https://openjdk.java.net/projects/jdk/11/. URL for OpenJDK-17 is: https://openjdk.java.net/projects/jdk/17/.

[^cool]: COOL is the acronym for CLIPS Object Oriented Language.
