---
layout: post
title: "Una introducción breve al Marco de Trabajo dpsFramework (revisión: 2019)"
headtitle: "Una introducción breve al Marco de Trabajo dpsFramework (revisión: 2019)"
author: "Aguayo-Canela, F.J.<br><small>Department of Electrical and Systems Engineering and Automation (2012-17)<br>School of Industrial Engineering and Information Technology. <b>University of Leon</b> (SPAIN)</small>"
date: 2019-09-10 11:07:56:49:44 +0100
ref: newBrief
tags: infront featured
categories: drafts
lang: es
---





> **_Resumen:_** Este borrador ofrece una descripción genérica de cinco micro-utilidades desarrolladas para ser utilizadas en la plataforma multiagente JADE. Se encuentran desarrolladas en Lenguaje Java y presentan dos funcionalidades principales: la primera, facilitar el despliegue de agentes-complejos que pertenecen a las réplicas de una aplicación distribuida; la segunda función, es permitir la configuración, adaptación y posterior depuración de los agentes en tiempo de ejecución una vez desplegados en la plataforma JADE. A este pequeño conjunto de utilidades se le ha denominado **_dpsFramework_**.



**Palabras-clave:** 
Sistemas multiagente, Agentes-complejos, plataforma JADE, Java, CLIPS, Jess, Prolog

<hr>{:width="256px" align="center"}

(Borrador...)

<br>

## 1. Introducción




&nbsp;&nbsp;El entorno de trabajo denominado _dpsFramework_ está formado por un conjunto de micro-utilidades desarrolladas en Lenguaje _Java[^ORACLE]_. Esas micro-utilidades han sido creadas con dos funciones principales: la primera facilitar el despliegue de agentes complejos o, comunidades de agentes-complejos que pertenecen a las réplicas de una aplicación distribuida; la segunda permitir la configuración, adaptación y posterior depuración de los agentes en tiempo-de-ejecución. Al primer grupo de utilidades de _dpsFramework_ pertenecen: _framework_, _launcher_, _generate_ y _shell_. Todas ellas son ejecutadas desde la línea-de-comandos de un terminal. Este primer grupo de utilidades tiene como misión crear la infraestructura de directorios de las réplicas de la aplicación distribuida. En esas réplicas se almacena el conocimiento de los agentes de la aplicación. Cada réplica creada con _dpsFramework_ puede ser desplegada en uno o en varios _Contenedores_ gestionados por la plataforma multiagente JADE[^TILAB] sobre distintos servidores. Las propiedades incorporadas por _dpsFramework_ a esas réplicas de la aplicación, permiten llevar a cabo el movimiento de agentes-complejos; incluidos sus conocimientos acumulados y sus capacidades de inferencia y resolución de problemas. Con esa capacidad, las réplicas de la aplicación permiten a los desarrolladores y arquitectos distribuir procesos en los agentes especializados o, realizar la distribución de las cargas de cálculo generadas por los razonamientos más pesados. 




&nbsp;&nbsp;El segundo grupo de utilidades de _dpsFramework_ está formado por un agente con una interfaz gráfica enriquecida mediante componentes SWING de Java y por componentes de terceros. Esta micro-utilidad se ha denominado agente _stage-node_. Está destinada a adherirse al agente-complejo en estudio y facilitar la edición de propiedades del agente, su especialización y su depuración en tiempo de ejecución. Con el agente _stage-node_ es posible además, tener acceso a los intérpretes del compilador de Java, las librerías de JADE y los motores de inferencia CLIPS[^CLIPS] o Jess[^JESS], utilizados por el agente en estudio.   




-  _Agent Oriented Programming_ (AOP)[^SHOHAM]
-  _FIPA_[^FIPA] 
-  _Multiagent Technology_[^WOOL]
-  _Universidad de León_ (Spain)[^UNILEON]
-  _(.OWL)[^PROTEGEE] 
-  _Ontologies Reasoner_[^RAZON]
-  _C++_[^CPLUS]
-  _Java_[^ORACLE]
-  _Expert System Software Tool_[^JESS] 
-  _Rule-based programming language Expert System Tool CLIPS_[^CLIPS] 
-  _Prolog_[^PROLOG]
-  _JADE_[^TILAB]
-  _Hyper-Sonic SQL Engine_[^HSQL]
-  _Raspbian-Pi Operating Systems_[^PI]
-  _Java BeanShell_[^BEANSHEL]
-  _Yellow Page JADE Service_[^YELLOW]
-  _Ontologies Rule-Based Reasoner_[^RAZON]
-  _Java Third-party RSyntaxTextArea_[^RSYNTAX]




<br>


## 1.1 Crear réplicas de la aplicación distribuida con _dpsFramework_



<br>


## 1.2 El _agente Stage-node_ de _dpsFramework_





- ![Stage-Node](/assets/images/logoPsStageBussy.gif){:width="98px"  hspace="10px"  border="0px"} **Stage-node** agent. 




<br>



## Bibliografía


[^TILAB]: **JADE Platform**. <http://jade.tilab.com/>. CSELT, S. & TILab, S. (2017). Jade - java agent development framework. is a framework to develop multi-agent systems in compliance with the fipa specifications. jade 4.5.0 - revision 6825 of 23-05-2017 10:06:04. Open Source, under LGPL restrictions.

[^SHOHAM]: **Agent Oriented Programming**. Shoham, Y. (2005). Agent oriented programming: An overview of the framework and summary of recent research. <https://link.springer.com/chapter/10.1007/3-540-58095-6_9>


[^FIPA]: **FIPA IP**. [FIPA00025] FIPA Interaction Protocol Library Specification. Foundation for Intelligent Physical Agents, 2002. <http://www.fipa.org/specs/fipa00025/> 



[^HSQL]: **HyperSQL**: HSQLDB - 100% Java Database. <http://hsqldb.org/>



[^WOOL]: **Multi-Agent Systems**. [**1**] Wooldridge, M. (2002). An Introduction to Multi-Agent Systems. John Wiley & Sons Ltd. [**2**] Ishida, T. (1994). Parallel, distributed and multiagent production systems. Springer-Verlag Berlin. [**3**] Ishida, T. (1995). Parallel, distributed and multi-agent production systems: a research foundation for distributed artificial intelligence. In ICMAS (pp. 416–422). [**4**] Mas, Ana. (2005). Agentes Software y Sistemas Multiagente. Conceptos, Arquitecturas y Aplicaciones. Prentice Hall.



[^PI]: **Raspbian-Pi Operating Systems**. [**1**] Molloy, Derek. <http://exploringrpi.com/>: Exploring Raspberry Pi. John Wiley Sons, Inc. (2016). [**2**] Raspbian OS for Raspberry-Pi (2018) <https://www.raspberrypi.org/downloads/raspbian/>


[^ORACLE]: **ORACLE Java**. Java(TM) Platform Standard and JDK, versions: 7. and 8. API Spec. <http://www.oracle.com/technetwork/java/javase/downloads/index.html> (2017).


[^PROTEGEE]: **Protégé software**. [**1**] Protégé Community, D. T. & Stanford University, S. o. M. (2014). Protégé,A free, open-source ontology editor and framework for building intelligent systems. Stanford Center for Biomedical Informatics Research (BMIR), Stanford University. Stanford, California 94305. [**2**] Eriksson, H. (2003). Using jesstab to integrate protégé and jess. IEEE Intelligent Systems, 18(2), 43–50. [**3**] Hoffman, O., Bellifemine, F., & Friedman-Hill, E. (2001). Software: Jadejessprotege, package example for closer integration of jade with jess, optionally also with protege. Available in: <https://jade.tilab.com/documentation/examples/jadejessprotege>


[^GITREPO]: **_dpsFramework_ GitHub Repositories**. <https://github.com/dpsframework>




[^CLIPS]: **CLIPS**. [**1**] Giarratano, J. C. P. (2014). CLIPS User’s Guide. Version 6.30. CLIPS.  [**2**] Riley, G. (2016). Clips rule based programming language expert system tool clips (6.31) and CLIPSJNI (0.5), clips rule based programming language web site. Available in: <https://sourceforge.net/projects/clipsrules/>.





[^JESS]: **JESS**.  [**1**]Friedman-Hill, E.: JESS, Expert System Software Tool (8.0a1 (alfa)). Sandia National Laboratories. <https://www.jessrules.com/> (2016). [**2**] Friedman-Hill, E. (2003). JESS in Action. Manning Greenwich, CT. [**3**] Cardoso, H. L. (2007). Integrating jade and jess. available in: <https://jade.tilab.com/documentation/examples/jess/>.




[^PROLOG]: **Prolog Language**. [**1**] Merritt, D. (2012). Building expert systems in Prolog. Springer Science & Business Media. [**2**]  SWI-Prolog <https://www.swi-prolog.org/>. [**3**] Fred Dushin and J. Wielemaker. University of Amsterdam. JPL.pl Java Interface. A Java interface for SWI-Prolog.



[^UNILEON]: **Universidad de León** (SPAIN). <http://www.unileon.es>.





[^TESIS]: **PhD Thesis**. Aguayo, F.J., García I. (2017) Deploying production systems on distributed using the Multi-Agent paradigm: applied techniques. <https://dialnet.unirioja.es/servlet/tesis?codigo=124344> Department of Electrical and Systems Engineering and Automation. Leon University (SPAIN).




[^BEANSHEL]: **BeanShell**. [**1**] Niemeyer, P.: Lightweight Scripting for Java. <http://www.beanshell.org/> (2014). [**2**] Nick Lombard, BeanShell at GitHub <https://github.com/beanshell/beanshell>. 





[^RSYNTAX]: **RSyntaxTexArea**. A syntax highlighting, code folding text editor for Java Swing applications. . <https://github.com/bobbylight/RSyntaxTextArea/> (2017).
[^FIPAACL]: **FIPA ACL**. [FIPA00008] FIPA Agent Communication Language Specification. Foundation for Intelligent Physical Agents, 2000. <http://www.fipa.org/specs/fipa00008/>





[^RAZON]: **Ontologies Reasoner**. [**1**] Luger, G. & Chakrabarti, C. (2011). Knowledge-based probabilistic reasoning from expert systems to graphical models: Report <https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.157.9652>. [**2**] Meditskos, G. & Bassiliades, N. (2011). Clips–owl: A framework for providing object-oriented extensional ontology queries in a production rule engine. Data & Knowledge Engineering, 70(7), 661–681. Report <https://www.sciencedirect.com/science/article/pii/S0169023X11000577> [**3**] Meditskos, G. & Bassiliades, N. (2008). A rule-based object-oriented owl reasoner. Knowledge and Data Engineering, IEEE Transactions on, 20(3), 397–410. Report <https://ieeexplore.ieee.org/document/4378372>. 



[^CPLUS]: **The C++ Programming Language**. Bjarne Stroustrup (2000). 3rd Addison-Wesley Longman Publishing Co., Inc. Boston, MA, USA. <https://dl.acm.org/citation.cfm?id=518791>.



[^YELLOW]: **Yellow pages JADE Service**. [**1**] Bellifemine, F.L., Caire, G., Greenwood, D.: Developing Multi-Agent Systems with JADE. Wiley Series in Agent Technology. (2007). [**2**] Cancedda, P. & Caire, G. (2010). JADE Tutorial Creating Ontologies by means of the Bean-Ontology Class, volume 15-April-2010 - JADE 4.0. Telecom Italia S.p.A. [**3**] Yellow Pages examples: <https://jade.tilab.com/documentation/examples/yellow-pages/>




