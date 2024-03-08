---
layout:  project
toc:  true
author:  'TILAB Telecom'
license:  'GNU Lesser General Public License v2.1'
ref:  p20-jade-fipa
lang:  en
date:  '2022-07-24'
modified:  '2022-08-28'
status:  'Finished'
title:  'Compilation of JADE-FIPA with OpenJDK-18'
subtitle:  'JADE-FIPA enhancement request to allow compilation with OpenJDK-18, JDK-17 LTS, and earlier versions of Java.'
headtitle:  'Unify the libraries used by the JADE 4.5.4 core: This is a proposal to update the compilation mechanism so that it can be done with OpenJDK-11 to 18 or higher. And allow future adoption of the Java Platform Module System in the JADE core.'
imagepath:  'images/jade-fipa/'
images:  
  -  'jade-rotated.png'
  -  'jade.png'
  -  'fipa.png'



---







  

##   Section 1: Identification
-  Responsible for the proposal: _FJ Aguayo_.
-  Proposal date: August 2022.
-  Results location: GitHub repo.

##   Section 2: Update
-  OpenJDK-11 to OpenJDK-18 compiler are used.
-  Revision 6868 of JADE version 4.5.4 of July 17, 2002 (by, G. Caire) is used.

###  2.1. Description of the proposal:

-  It is proposed to use the Java Module System on top of the JADE 4.5.4 (2022) platform core. And connect JADE to the FIPA module internally through the declaration of the file org.tilab.jade to org.fipa.
-  Once the unification with the FIPA module with the JADE 4.5.4 (2022) kernel has been carried out, it will be possible to know the scope of the necessary changes in the JADE kernel; know what are the additional necessary libraries required by JADE 4.5.4 and allow JADE to be compiled with OpenJDK-17 or higher.

###  2.2. target platform
-  Java SE 17, OpenJDK-17 or higher, Java JDK-17 or higher. This implies that it can be used in Desktop or Server environments, with different architectures and operating systems.
  
-  The final objective is its integration in JADE 4.5.4, and to wait for a future revision of JADE.




###  23. What does the update proposal need?
-  Access to the JADE Platform code. Found at: <https://jade.tilab.com/svn/jade/trunk/>
-  A development environment. Eclipse 2021-12 has been used.
-  A detailed compilation of the errors offered by the OpenJDK-17/ Java JDK-17 compiler; its progressive correction; the incorporation of the Java Platform System of Modules to allow later integration of JADE with its FIPA module under the Java system of modules.


###  2.4. Why this proposal?
-  Because the evolution of the Java compiler has removed the CORBA libraries from the Java core.
-  Because it is not possible to compile the JADE Platform on top of Java OpenJDK-17. The only way is to add the GlassFish CORBA ORB libraries to the CLASSPATH. Requiring, in turn, the distribution of JADE with these specific libraries.






###  2.5. Underlying technology or technologies:
-  OpenJDK-9 to OpenJDK18.
-  Oracle Java JDK-9 through Oracle Java JDK-18.
-  GlassFish CORBA ORB 2.4
-  Apache Commons








###  2.6. Package name for API proposal?
-  File: **com.tilab.jade-2002.jar**
-  Package: **jade**













###  2.7. Dependencies on specific operating systems
-  Those corresponding to the version and architecture of the Java compiler.












###  2.8. Security issues due to the current security model
-  They have not been analyzed.














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
-   JADE Revision 6868.



















##   Section 4: Additional Information (Optional)












###  4.1. Additional information to include in the Improvement Proposal
  
  