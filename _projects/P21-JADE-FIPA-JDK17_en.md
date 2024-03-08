---
layout:  project
toc:  true
author:  'TILAB Telecom'
license:  'GNU Lesser General Public License v2.1'
ref:  'JADE-FIPA-4.6.1'
lang:  en
date:  '2022-12-21'
modified:  '2024-02-19'
status:  'Finished'
title:  'JADE-4.6.1 compiled with Java OpenJDK-17 LTS'
subtitle:  'Creating specific `pom.xml` to build `jade-4.6.1.jar` with CORBA, Apache Commons and Java OpenJDK-17 or higher.'
headtitle:  'Compilation and unification of libraries used by JADE 4.6.1 (2023/07/11), reorganization of the directory structure in the MAVEN model and preparation of `pom.xml` and `pom8.xml` files to obtain functional JADE versions without the need for two Java OpenJDK installations for libraries in version 8 and code in version 17LTS or higher of JAVA on the same machine or Docker container.'
imagepath:  'images/jade-fipa/'
images:  
  -  'jade-rotated.png'
  -  'jade.png'
  -  'fipa.png'


---







  

##   Section 1: Identification
-  Responsible for the proposal: _FJ Aguayo_.
-  Proposal date: January 2023.
-  Results location: GitHub repo.

##   Section 2: Description of the proposal
-  OpenJDK-11 to OpenJDK-18 compiler.
-  JADE Revision 6871 version 4.6.0 of December 19, 2022 is used

###  2.1. Resume

-  
-  

###  2.2. destination platform
-  Java SE 17, OpenJDK-17 or higher, Java JDK-17 or higher. This implies that it can be used in Desktop or Server environments, with different architectures and operating systems.
  
-  The final objective is its integration in JADE 4.6.0, and to wait for a future revision of JADE for JAVA 11 or higher.




###  23. What does the update proposal need?
-  Access to the JADE Platform code. Found at: <https://jade.tilab.com/svn/jade/trunk/>
-  A development environment. Eclipse 2021-12 has been used.
-  A detailed compilation of the errors provided by the OpenJDK-17/Java JDK-17 compiler; its progressive correction; the incorporation of the Java Platform Module System to allow the later integration of JADE with its FIPA module under the Java module system.


###  2.4. Why this proposal?
-  Because the evolution of the Java compiler has removed the CORBA libraries from the Java core.
-  Because it is not possible to compile the JADE Platform on Java OpenJDK-17. The only way is to incorporate the GlassFish CORBA ORB libraries into the CLASSPATH. Demanding, in turn, the distribution of JADE with these specific libraries.






###  2.5. Underlying technology or technologies:
-  OpenJDK-9 to OpenJDK18.
-  Oracle Java JDK-9 through Oracle Java JDK-18.
-  GlassFish CORBA ORB 2.4
-  apache-commons








###  2.6. Package name for API proposal?
-  File: **jade-4.6.0.jar**
-  Package: **jade**













###  2.7. Dependencies on specific operating systems
-  Those corresponding to the version and architecture of the Java compiler.












###  2.8. Security issues due to the current security model
-  They have not been analysed.














###  2.9. Internationalization or localization problems?
-  They have not been implemented.















###  2.10. Any need for revision as a result of this work?
-  It has not been foreseen. Awaiting review.
















###  2.11. Schedule for the development of this proposal
-   Start: **December 2022**
-   End: **January 2023**
















##   Section 3: Contributions




###  3.1. Documents, proposals, or implementations that describe the technology.















###  3.2. Starting point of the work.
-   JADE-4.6.0 Patch 6871.



















##   Section 4: Additional Information (Optional)












###  4.1. Additional information to include in the Improvement Proposal
  