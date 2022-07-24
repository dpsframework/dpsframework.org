---
layout: proposal
toc: true
author: 'Francisco J. Aguayo' 
date: 2022-07-16 11:07:56:49:44 +0100
keywords: 
  - 'FIPA'
  - 'JADE'



ref: fipa2022
lang: en
categories: jade
tags: FIPA protocols ACL
metadata: '' 


title: 'FIPA & JSR 87Specification Requests JSR 87: JavaTM Agent Services'
headtitle: 'FIPA & JSR 87 Propuestas de actualización a JDK-17 LTS'
shorttitle: 'FIPA & JSR 87 updated to JDK-17'
--- 


> **_Resumen:_**
> 

<br>**_Palabras clave:_**   
{% include keywords-list.html %}


Specification Requests JSR 87: JavaTM Agent Services

Stage   Access  Start   Finish
Withdrawn       25 Jan, 2011   
Public Review   Download page   20 Mar, 2002  19 May, 2002
Community Draft Ballot  View results  20 Nov, 2001  26 Nov, 2001
Community Review  Login page  16 Oct, 2001  26 Nov, 2001
Expert Group Formation      17 Oct, 2000  19 Jan, 2001
JSR Review Ballot   View results  03 Oct, 2000  16 Oct, 2000
Status: Withdrawn
Reason: Withdrawn at the request of the Specification Lead.
JCP version in use: 2.1
Java Specification Participation Agreement version in use: 1.0


## Description:
This specification defines a set of objects and service interfaces to support the deployment and operation of autonomous communicative agents.

Please direct comments on this JSR to the Spec Lead(s)
Team

Specification Leads
>  Francis G. McCabe   Fujitsu Limited
Expert Group
>  Fujitsu Limited   Hewlett-Packard   IBM
>  Spydell, Andy   Suguri, Hiroki  Sun Microsystems, Inc.
>  Tolety, Siva Perraju  University of West Florida Institute of Human-Machine Cognition

This JSR has been Withdrawn
Reason: Withdrawn at the request of the Specification Lead.

Original Java Specification Request (JSR)

Identification | Request | Contributions | Additional Information

Section 1: Identification
Submitting Participant: Fujitsu Ltd.
Name of Contact Person: Francis G. McCabe
E-Mail Address: fgm@fla.fujitsu.com
Telephone Number: +1 408 530 4549
Fax Number: +1 408 530 4515

Initial Expert Group Membership:

Fujitsu, Hewlett-Packard, IBM, Sun Microsystems


# Section 2: Request
## 2.1 Please describe the proposed Specification:
This specification defines a set of objects and service interfaces to support the deployment and operation of autonomous communicative agents.

It is based upon the Abstract Architecture developed by FIPA, the Foundation for Intelligent Physical Agents (see section 3.1). This Abstract Architecture defines how agents may register and discover each other, and how agents interact by exchanging intentional messages which are grounded in speech-act theory and first-order predicate logic.

The specification defines two kinds of entities:

>  Java classes for objects corresponding to the various elements of ACL (agent communication language) and SL (content language), as well as FIPA agent names and descriptions.
>  Java interfaces corresponding to the agent services for agent registration, discovery, and communication.

It is intended that the service interfaces may be implemented in terms of a number of different technologies, including both existing Java standards and proprietary systems. (In this respect the specification is similar to previous specifications such as JMS, the Java Message Service.)
## 2.2 What is the target Java platform? (i.e., desktop, server, personal, embedded, card, etc.)
It is highly desirable that this specification be usable for agent systems for a wide range of applications and target platforms. Therefore it is intended that the basic specifications should be usable on all Java platforms, from J2ME to J2EE. It is likely, however, that some instantiations of the specification will be based upon Java technologies that are restricted to particular Java platforms.
## 2.3 What need of the Java community will be addressed by the proposed specification?
The autonomous communicative agent model has been adopted by many researchers and software developers, in application areas as diverse as e-commerce, process control, air traffic control, systems management, and workflow. The rate of adoption has been slowed by the lack of standards, and a concomitant lack of tools and optimized platform systems. The vast majority of agent-related work is being done in Java, and there is a significant demand for standard specifications in this area.
## 2.4 Why isn't this need met by existing specifications?
The Java programming language is well suited to the development of agent systems. However the rich set of data representations and platform services in Java means that independently developed agent systems are unlikely to interoperate. Furthermore the lack of standards has inhibited the development of agent-specific tools and components.
## 2.5 Please give a short description of the underlying technology or technologies:
The FIPA Abstract Architecture covers two closely related areas:

>  The registration and location of agents
>  Communication between agents using asynchronous messages expressed in ACL, the FIPA agent communication language

In each of these areas, there are two kinds of specifications:

>  Services provided by an agent platform - a container in which an agent executes. These services may be implemented using a variety of underlying technologies. For example, agent message transport may be accomplished using HTTP, IIOP, or a proprietary mechanism; it may also be provided by a Java Message Service provider, such as IBM MQ-Series or Sun JMQ. The various services are defined as Java interfaces, which may be implemented by a variety of different agent platforms.
>  Java objects that define agent descriptions, agent messages, and the components of each. These objects are used in all implementations of the API. Different agents platforms and service implementations may require different types of serialization. Backward compatibility with FIPA97 systems will require the use of IIOP as a message transport and messages encoded using a LISP-like string syntax.

As in specifications such as JMS, the Java Agents API will not require or define mechanisms for interoperability between different types of agent platform.

At this point, it is anticipated that the specification may include the following elements:

>  Java classes for ACL (agent communication language) based on FIPA-ACL
>  Java classes for Agent naming
>  Java classes for Agent descriptions
>  Java interfaces for Agent Directory services
>  Java interfaces for Agent Messaging actions
>  Specification for the serialization of agent related objects (ACL, names, descriptions) in accordance with current FIPA specifications
>  Specification for the serialization of agent related objects (ACL, names, descriptions) in XML
>  Specification for a JNDI schema for Agent descriptions
>  Specification for the mapping of the Agent Messaging service in terms of the Java Message Service (JMS) specification
>  Specification for the mapping of the Agent Messaging service in terms of other transport services, such as IIOP and HTTP, using Java ORB services

## 2.6 Is there a proposed package name for the API Specification? (i.e. org.something, etc.)
javax.agent
## 2.7 Does the proposed specification have any dependencies on specific operating systems, CPUs, or I/O devices that you know of?
No
## 2.8 Are there any security issues that cannot be addressed by the current security model?
As the JMS security model is likely to evolve with J2EE Ver.2 a revision for the agent model is likely to be required.
## 2.9 Are there any internationalization or localization issues?
No
## 2.10 Are there any existing specifications that might be rendered obsolete, deprecated, or in need of revision as a result of this work?
No

## 2.11 Please describe the anticipated schedule for the development of this specification.

Initiation September 2000
Community draft July 2001

Public and Final drafts will be dependent upon the review process.



# Section 3: Contributions
## 3.1 Please list any existing documents, specifications, or implementations that describe the technology. Please include links to the documents if they are publicly available.
1. [FIPA00001] FIPA Abstract Architecture (http://www.fipa.org/fipa00001/),
1. [FIPA00061] FIPA ACL Parameters Specification (http://www.fipa.org/fipa00061/),
1. Java2 Platform, Standard Edition (http://java.sun.com/j2se/1.3/index.html)
1. Java2 Platform, Micro Edition (http://java.sun.com/j2me/index.html)
1. Java2 SDK, Enterprise Edition (http://java.sun.com/j2ee/overview.html)
1. Java Message Service (JMS) (http://java.sun.com/products/jms/index.html)
1. Java Naming and Directory Service (JNDI) (http://java.sun.com/products/jndi/index.html)
1. Extensible Markup Language (XML) (http://www.w3c.org/XML/)
## 3.2 Explanation of how these items might be used as a starting point for the work.
The FIPA Abstract Architecture describes the basic services that must be provided by an agent platform, as well as the relationships between them. It also describes the agent communication language and content language. As its name implies, it presents these architectural elements as abstractions, independent of particular technologies, encodings, and so forth. As such, it is explicitly intended to be a starting point for concrete specifications such as that proposed by this JSR.

# Section 4: Additional Information (Optional)
## 4.1 This section contains any additional information that the submitting Participant wishes to include in the JSR.
Other relevant documents include the following FIPA documents, which may be found at http://www.fipa.org
1. [FIPA00003] FIPA Agent Communication Language Specification (http://www.fipa.org/fipa00003/),
1. [FIPA00007] FIPA Content Languages Specification (http://www.fipa.org/fipa00007/),
1. [FIPA00008] FIPA SL Content Language Specification (http://www.fipa.org/fipa00008/),
1. [FIPA00009] FIPA CCL Content Language Specification (http://www.fipa.org/fipa00009/),
1. [FIPA00010] FIPA KIF Content Language Specification (http://www.fipa.org/fipa00010/),
1. [FIPA00011] FIPA RDF Content Language Specification (http://www.fipa.org/fipa00011/),
1. [FIPA00067] FIPA Message Transport Service Specification (http://www.fipa.org/fipa00067/),
1. [FIPA00068] FIPA ACL Message Representation Library Specification (http://www.fipa.org/fipa00068/),
1. [FIPA00069] FIPA ACL Message Representation in Bit-efficient Encoding Specification (http://www.fipa.org/fipa00069/),
1. [FIPA00070] FIPA ACL Message Representation in String Specification (http://www.fipa.org/fipa00070 /),
1. [FIPA00071] FIPA ACL Message Representation in XML Specification (http://www.fipa.org/fipa00071/),
1. [FIPA00072] FIPA Agent Message Transport Envelope Representation Library Specification (http://www.fipa.org/fipa00072/),
1. [FIPA00073] FIPA Agent Message Transport Envelope Representation in String Specification (http://www.fipa.org/fipa00073/),
1. [FIPA00074] FIPA Agent Message Transport Protocol Library Specification (http://www.fipa.org/fipa00074/),
1. [FIPA00075] FIPA Agent Message Transport Protocol for IIOP Specification (http://www.fipa.org/fipa00075/),
1. [FIPA00076] FIPA Agent Message Transport Protocol for WAP Specification (http://www.fipa.org/fipa00076/).