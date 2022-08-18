---
layout:  proposal
toc:  true
author:  'Aguayo, FJ'
license:  'GNU Lesser General Public License v2.1'
ref:  p40-clipsjni-051
lang:  en
date:  '2022-04-27'
modified:  '2022-08-17'
status:  'In process'
title:  'CLIPS JNI v0.51 (Java Native Interface) Specification Request'
subtitle:  'A modification of CLIPS-JNI-0.51 to detect the architecture of the machine at runtime and additional security options.'
headtitle:  'CLIPS JNI (Java Native Interface) Specification proposal for version 0.51. This proposal provides a modification of CLIPS-JNI-0.51 to detect machine architecture at runtime and other additional security options. This release provides more stable integration between JADE PS-Agents with troubleshooting capabilities and expert systems developed for CLIPS 6.31 running these agents.'
imagepath:  'images/clipsjni-051/'
images:
  -  'clips_logo.png'
  
---







  

##   Section 1: Identification
-  Responsible for the proposal: _FJ Aguayo_.
-  Proposal date: April, 2022.
-  Results location: GitHub repo.

##   Section 2: Proposed Update
-  CLIPS-JNI version 0.51 native Java interface for CLIPS 6.31 has been reviewed by _Gary Riley_ on 2019-08-06, comp can be checked on Source forge, at <https://sourceforge.net/projects/clipsrules/files/ CLIPS/6.31/>.
-  JADE agents capable of integrating and executing autonomous Expert Systems on the Multi-Agent platform require prior knowledge of the architecture of the Java machine and the hardware on which they are executed.

###  2.1. Description of the proposal:

-  Carry out a development on CLIPS-JNI-0.51 so that this interface detects which is the Java machine and the hardware architecture of the node where the Multi-Agent system is executed, and in this way, the CLIPSJNI Library itself associates and links with its library native in C++.
-  The development of the additional security elements was carried out by adjusting the visibility of the fundamental Objects that make up the CLIPS-JNI-0.51 library.

###  2.2. target platform
-  Java JDK-11 through JDK-18. OpenJDK-18. CLIPS 6.31
  
-  JADE Troubleshooting Agents, version 1.9 or higher.




###  23. What does the proposal need for its execution?
-  ECLIPSE IDE 2022.
-  CLIPS 6.31 source-code. CLIPS-JNI-0.51 source-code.
-  JADE PS Agents version 1.9 or higher.


###  2.4. Why this proposal?
-  Because the dpsAgents-1.8-full.jar library, developed for JAVA 1.8, is not capable of linking the autonomous expert systems of JADE agents, with the CLIPS 6.31 kernel, nor with CLIPS 6.40.
-  Because the detection and link mechanism between the Agent and CLIPS or Prolog must be done by the native library, in an early link, eliminating the need for the agent to locate the location of the Native Library for OS-X, Gnu-Linux , Windows 32bits or Windows 64bits.






###  2.5. Underlying technology or technologies:
-  CLIPS
-  COOL
-  Java
-  lisp








###  2.6. Name of the generated library?
-    clipsjni-051ps-i586.jar
-    clipsjni-051ps-amd64.jar
etc.












###  2.7. Dependencies on specific operating systems
-  None.












###  2.8. Security issues due to the current security model
-  Does not apply to this project














###  2.9. Internationalization or localization problems?
-  They have not been implemented.















###  2.10. Any need for revision as a result of this work?
-  It has not been planned. Awaiting review.
















###  2.11. Schedule for the development of this proposal
-   Start: **April 2022**
-   End: **August 2022**
















##   Section 3: Contributions




###  3.1. Documents, proposals or implementations that describe the technology.















###  3.2. Starting point of the work.
-   CLIPSJNI-051 on Source Forge at: https://sourceforge.net/projects/clipsrules/files/CLIPS/6.31/clips_jni_051.tar.gz/download



















##   Section 4: Additional Information (Optional)












###  4.1. Additional information to include in the Improvement Proposal
  