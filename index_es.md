---
layout: home
title: "Inicio"
headtitle: "Resolución Distribuida de Problemas con Agentes de JADE (DPS-Agents Framework)"
author: Aguayo-Canela, F.J.
pos: 1 
menu: true
list_title: Table of Contents
date: 2019-09-05 16:21:49:44 +0100
ref: index
lang: es
---

### Descripción


>  El **_Marco de Agentes-DPS_** está formado por cuatro Agentes de **JADE**[^TILAB] y por un Micro-Entorno de desarrollo (denominado **_dpsFramework_**) que permite adaptar, depurar y desplegar múltiples _Agentes-DPS_ sobre la plataforma JADE para implementar _Aplicaciones orientadas a agentes_[^SHOHAM].



{:.caption-left}
<br>**Tabla 1**. Metadatos del Proyecto de Investigación (2012-2017) asociado al _{{ site.title[page.lang] | escape }}_.

{:.table-left}
| Institución  | Proyecto de investigación   | 
|:--------------------------------- |:--------------------- |
| ![UniLeon](/assets/images/marca-logo-color.jpg){:width="90px" align="left" hspace="2px"  border="0px"}  | **Institución**: Universidad de León[^UNILEON]. <br>**Departamento**: Departamento de Ingeniería Eléctrica y de Sistemas y Automática[^UNILEONDEPT].  <br> <br> **Nombre de investigación**:  _Técnicas para despliegue de arquitectura distribuida en sistemas expertos basados en reglas empleando el paradigma multi-agente_. (2012-2017) <br>**Depósito**: [_DIALNET_](https://dialnet.unirioja.es/servlet/tesis?codigo=124344). **Estado**: Finalizado. <br>**Autores**: {{ site.author | escape }} y {{ site.author2 | escape }}[^IGARCIA].  | 



{:.caption-left}
<br>**Fig. 1**. Ejemplo de Interfaz Gráfica de Usuario de un Agente-DPS clase _Monitor_ en modo _depuración_.
![](/assets/images/psMonitorAgent00.png){:width="580px"  border="0px" }



## Objetivos del proyecto _{{ site.title[page.lang] | escape }}_


La ejecución del proyecto `**{{ site.title[page.lang] | escape }}**' se encuentra pendiente de aprobación y en búsqueda de financiación. Tiene un alcance estimado de dos años (Dic.2019 -- Dic.2021) y sus objetivos son los siguientes :

1.  Evolucionar el código de los cuatro **Agentes-DPS** para su explotación en los  **Dominios**: 
    - _Sistemas Educativos_
    - _Aplicaciones centradas en el usuario_ 
    - Capacidad y fiabilidad para actuar como _Agentes Asistenciales_ autónomos.
1.  Establecer la **Licencia MIT** a partir de Dic.2019 y emplear el modelo de desarrollo de proyectos **Open-Source**.
1.  Adaptar el código-fuente para aprovechar las capacidades modulares de **JAVA/openJDK 11.x**[^ORACLE] o superiores.

![DPS-Agentes Framework Logo](/assets/images/logo_dpsframework_bw.png){:width="280px"  hspace="2px"  border="0px"} 



## Versiones disponibles

En la actualidad hay dos versiones disponibles: **v0.9.1** (SOCO) y **v1.7** (EUMAS) (véase, Tabla.2). Estas distribuiciones han sido empaquetadas en un archivo de tipo .JAR con la nomenclatura: **dpsFrameworkBuilder-X.Y.jar**. Estos archivos .JAR, permiten crear e inicializar un entorno de desarrollo básico con librerías y componentes necesarios para el desarrollo de la aplicación. Además, generan la estructura de directorios mínima para poner en funcionamiento el esqueleto de una _Aplicación Basada en Agentes_[^SHOHAM] operativa. 


{:.caption-left}
**Tabla 2**. Número de versión, nemónico y características principales de la distribución.

{:.table-left}
| Versión   | Descripción   | 
|:--------------------------------- |:--------------------- |
| **v0.9.1** (SOCO) <br>![Stage-Node](/assets/images/logoPsStageBussy.gif){:width="28px" align="left" hspace="4px"  border="0px"}   | **Fecha**: Dic. 2017<br>**Nombre  instalador**: dpsFrameworkBuilder-RC1.jar. (The official version).<br> **Compilador / Componentes**: Java JDK 7 y 8. JADE JADE 4.4.0. BeanShell 2.0b4. RSyntaxTextArea Text Editor. HyperSQL v2.3.4. CLIPS 6.30. CLIPSJNI 0.5. Jess 8.0a1.  | 
| **v1.7** (EUMAS) <br>  ![Stage-Node](/assets/images/logo_dpsframework_bw.png){:width="180px" align="left" hspace="2px"  border="0px"} | **Fecha**: Sep. 2018<br>**Nombre  instalador**: dpsFrameworkBuilder-1.7.jar.<br> **Compilador / Componentes**: <br>Java/openJDK 8.x compiler.<br>JADE 4.5.0 - revision 6825 of 23-05-2017  <br>BeanShell v:2.0b4 (patched at, 2016). <br>RSyntaxTextArea Text Editor. <br>HyperSQL® HyperSQL Database Engine v:2.3.4 <br>CLIPS 6.31. <br>Six compiled libraries CLIPSJNI 0.5 to: Raspbian-Pi, Linux 32/64, Microsoft Windows 32/64 and, Apple iOS-X <br>Jess 8.0a1.<br>Apache JENA | 


    

Ambas distribuciones han sido compiladas con JAVA y han sido comprobados sobre los sistemas operativos: Ms-Windows, Apple OS-X y Linux. Destacar que, la versión v1.7 (EUMAS) permite desplegar Agentes-DPS con el motor de Sistemas Expertos CLIPS[^CLIPS] y/o JESS[^JESS] sobre arquitecturas **ARM** (e.g. RaspberryPI[^PI]). 



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



[^IGARCIA]: **Professor**: Dr. Isaías García Rodríguez. <https://dialnet.unirioja.es/servlet/autor?codigo=1448367>.


[^RUSSELL]: **Inteligencia Artificial: un enfoque moderno**. Russell, S.J. and Norvig P. 2nd Edition (2004). Pearson Prentice Hall.


[^UNILEONDEPT]: **Departamento de Ingeniería Eléctrica y de Sistemas y Automática**. Universidad de León. <https://departamentos.unileon.es/ingenieria-electrica-y-de-sistemas-y-automatica/>




