---
layout: note
ref:  biblio
lang:  es
idiom:  
imagepath:  'assets/imgs/'
images:
  -  'dpsframework-logo.png'









date:  '2022-07-24 08:28:40:49:44 +0100'
menu: false
toc:  false


title:  'Bibliografía de dpsFramework'
headtitle:  'Bibliografía de dpsFramework'
shorttitle:  'Bibliografía (2022)'
year:  '2022'
author:  'Aguayo, FJ'
department:  '2022-07-24 08:28:40:49:44 +0100'
authors:



keywords:
  -  'Mendeley'
  -  'Zotero'


doi:  
url:  'https://dpsframework.org/'
editor:  'dpsFramerwork project'
pubdate:  '2022-07-24 08:28:40:49:44 +0100'
license:  'GNU Lesser General Public License v3.0.  Permissions of this copyleft license are conditioned on making available complete source code of licensed works and modifications under the same license or the GNU GPLv3. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights. However, a larger work using the licensed work through interfaces provided by the licensed work may be distributed under different terms and without source code for the larger work.'




last_updated:  '2022-07-24 08:28:40:49:44 +0100'
ndt:  '2022-07-24 08:28:40:49:44 +0100'



---









#   Conceptos y componentes utilizados






1.  Complementos de Jekyll; Lenguaje de Templates Liquid, GitHub-Themes para sitios web:
   -   _Solución TOC desarrollada en Liquid; Complementos recomendados de GitHub-Page para SEO; Filtros de Lenguaje de Templates Liquid, Flujo de Control, Interacciones, etc; Tema Minima para GitHub._
   -  **TOC Jekyll plugin**.  [^jekyllTOC]
   -  **Liquid Template Language**.  [^liquid]
   -  **Minima GitHub-Pages Theme**.  [^minima]

1.  Entorno de desarrollo de agentes y plataforma MAS de implementación de agentes utilizada:
   -   _Paradigmas de desarrollo para construir Aplicaciones Orientadas a Agentes; Kit de herramientas de widgets para Java diseñado para proporcionar acceso eficiente y portátil a las instalaciones de la interfaz de usuario de los sistemas operativos en los que se implementa para cada PS-Agent desarrollado; Estándares de lenguaje de comunicaciones de agentes; Herramienta de gestión y comprensión de proyectos de software como Apache Maven; Intérprete de Java para la integración en aplicaciones Java; Editor avanzado para iluminación de sintaxis y programación asistida; Estándar del Protocolo de Interacción para Agentes inteligentes; etc._
   -  **Eclipse IDE for Java Developers**.  [^eclipse2022]
   -  **SWT: The Standard Widget Toolkit**.  [^SWT]
   -  **Java Agent DEvelopment environment (JADE)**.  [^TILAB]
   -  **Foundation for Intelligent Physical Agents (FIPA)**.  [^FIPAfoundation]
   -  **Agent Oriented Programming (AOP)**.  [^SHOHAM]
   -  **Apache Maven**.  [^maven]
   -  **Java Platform Compiler and Development Kit**.  [^ORACLE]
   -  **Java Shell Interpreter and Scripting Java Languaje**.  [^BEANSHEL]
   -  **FIPA Interaction Protocol for Physical Agents (IP)**.  [^FIPA]
   -  **Apache JENA**.  [^jena]





1.  Librería Java de Agentes JADE para Resolución de Problemas:
   -   _Agentes de resolución de problemas distribuidos (PS-Agents) para JADE y su conexión a sus Sistemas Expertos autónomos integrados (ver **Tabla 1**). El proyecto dpsFramework incorpora propuestas, con soluciones probadas, para adaptar PS-Agents-1.8-full.jar a: JADE 4.5.4 (2022) y su módulo FIPA implementado con librerías CORBA; una propuesta de la biblioteca CLIPSJNI para la actualización de CLIPS-6.31 y CLIPS-6.40 a OpenJDK-18 o superior, así como la revisión mínima del núcleo del motor basado en reglas JESS y adaptaciones breves de la biblioteca de interfaz nativa Java swiProlog JPL-7._
   -  **PS-Agents-1.8-full.jar (current version)**.  [^GITREPO]




1.  Sistemas Expertos utilizados por los agentes tipo PS-Agents:
   -   _Herramientas de construcción de Sistemas Expertos para encadenamiento hacia delante y hacia atrás. Entornos de depuración y compilación de Librerías y de código desarrollado en C++ para Windows, OS-X y GNU Linux; Documentación sobre arquitecturas habituales en dispositivos IoT; etc._
   -  **Raspberry-PI -ARM Architecture**.  [^PI]
   -  **CLIPS Expert System Tool and CLIPSJNI Library**.  [^CLIPS]
   -  **JESS Java Expert System Software (Rule-Based)**.  [^JESS]
   -  **SWI-Prolog and JPL Library**.  [^PROLOG]











1.  Antiguos documentos del doctorado y sus enlaces:
   -   _El Proyecto de Investigación; Director de tesis doctoral y buen amigo, Supervisión-proceso docente; Enlace a la publicación en el Depósito Oficial de Tesis doctorales (ver **Tabla 2.**)._


























{:.caption-left}
**Tabla 1**. Versión y alias de distribución, y componentes utilizados por dpsFramework.

{:.table-left}
| Versión   | Descripción   |
|:--------------------------------- |:--------------------- |
| **v0.9.1** (SOCO) <br>![Stage-Node]({{ site.baseurl }}/assets/imgs/logoPsStageBussy.gif){:width="40px" align="left" hspace="4px"  border="0px"}   | **Fecha**: Dic. 2017<br>**Nombre  instalador**: dpsFrameworkBuilder-RC1.jar. (The official version).<br> **Compilador / Componentes**: Java JDK 7 y 8. JADE JADE 4.4.0. BeanShell 2.0b4. RSyntaxTextArea Text Editor. HyperSQL v2.3.4. CLIPS 6.30. CLIPSJNI 0.5. Jess 8.0a1.  |
| **v1.7** (EUMAS) <br>  ![Stage-Node]({{ site.baseurl }}/assets/imgs/logoPsStageBussy.gif){:width="40px" align="left" hspace="2px"  border="0px"} | **Fecha**: Sep. 2018<br>**Nombre  instalador**: dpsFrameworkBuilder-1.7.jar.<br> **Compilador / Componentes**: . Java/openJDK 8.x compiler.. JADE 4.5.0 - revision 6825 of 23-05-2017  . BeanShell v:2.0b4 (patched at, 2016). . RSyntaxTextArea Text Editor. . HyperSQL® HyperSQL Database Engine v:2.3.4 . CLIPS 6.31. . Six compiled libraries CLIPSJNI 0.5 to: Raspbian-Pi, Linux 32/64, Microsoft Windows 32/64 and, Apple iOS-X . Jess 8.0a1.. Apache JENA |
| **v1.8** (JOURNAL)[^GITREPO] <br>  ![Stage-Node]({{ site.baseurl }}/assets/imgs/logoPsNode.gif){:width="40px" align="left" hspace="2px"  border="0px"} | **Fecha**: Sep. 29, 2021<br>**Nombre  instalador**: dpsFrameworkBuilder-1.8-full.jar.<br> **Compilador / Componentes**: . Java/openJDK 8.x compiler.. BeanShell v:2.0b6 (https://github.com/beanshell/beanshell). .      HyperSQL® HyperSQL Database Engine v:2.3.4 (https://sourceforge.net/projects/hsqldb/) .      CLIPS 6.31 (https://sourceforge.net/projects/clipsrules/files/CLIPS/) .      CLIPSJNI 0.5 compiled to: Raspbian-Pi, Linux 32/64, Microsoft Windows 32/64, Apple OS-X .      Jess, the Rule Engine for the Java Platform. Copyright (C) 2013 Sandia Corporation .      Jess Version 8.0a1 9/25/2013 (http://www.jessrules.com) .      Apache JENA (https://jena.apache.org/) .      JADE 4.5.0 (release 6825 of 23-05-2017 10:06:04 at http://jade.tilab.com/) |


{:.caption-left}
**Tabla 2**. Metadatos del Proyecto de Investigación (2012-2017) asociado al _{{ site.data.dpsFramework.title[page.lang]  | escape }}_.

{:.table-left}
| Institución  | Proyecto de investigación   |
|:--------------------------------- |:--------------------- |
| ![UniLeon]({{ site.baseurl }}/assets/imgs/marca-logo-color.jpg){:width="90px" align="left" hspace="2px"  border="0px"}  | **Institución**: Universidad de León[^UNILEON]. <br>**Departamento**: Departamento de Ingeniería Eléctrica y de Sistemas y Automática[^UNILEONDEPT].  <br> <br> **Nombre de investigación**:  _Técnicas para despliegue de arquitectura distribuida en sistemas expertos basados en reglas empleando el paradigma multi-agente_. (2012-2017) <br>**Depósito**: [_DIALNET_](https://dialnet.unirioja.es/servlet/tesis?codigo=124344). **Estado**: Finalizado. <br>**Autor**: Aguayo-Canela, FJ[^TESIS]. **Director**: García-Rodríguez, I [^IGARCIA].   | 

























[^TILAB]: **JADE Platform**. <http://jade.tilab.com/>. CSELT, S. & TILab, S. (2017). Jade - java agent development framework. is a framework to develop multi-agent systems in compliance with the fipa specifications. jade 4.5.0 - revision 6825 of 23-05-2017 10:06:04. Open Source, under LGPL restrictions.

[^SHOHAM]: **Agent Oriented Programming**. Shoham, Y. (2005). Agent oriented programming: An overview of the framework and summary of recent research. <https://link.springer.com/chapter/10.1007/3-540-58095-6_9>


[^FIPA]: **FIPA IP**. [FIPA00025] FIPA Interaction Protocol Library Specification. Foundation for Intelligent Physical Agents, 2002. <http://www.fipa.org/specs/fipa00025/>



[^HSQL]: **HyperSQL**: HSQLDB - 100% Java Database. <http://hsqldb.org/>



[^WOOL]: **Multi-Agent Systems**. [**1**] Wooldridge, M. (2002). An Introduction to Multi-Agent Systems. John Wiley & Sons Ltd. [**2**] Ishida, T. (1994). Parallel, distributed and multiagent production systems. Springer-Verlag Berlin. [**3**] Ishida, T. (1995). Parallel, distributed and multi-agent production systems: a research foundation for distributed artificial intelligence. In ICMAS (pp. 416–422). [**4**] Mas, Ana. (2005). Agentes Software y Sistemas Multiagente. Conceptos, Arquitecturas y Aplicaciones. Prentice Hall.



[^PI]: **Raspbian-Pi Operating Systems**. [**1**] Molloy, Derek. <http://exploringrpi.com/>: Exploring Raspberry Pi. John Wiley Sons, Inc. (2016). [**2**] Raspbian OS for Raspberry-Pi (2018) <https://www.raspberrypi.org/downloads/raspbian/>


[^ORACLE]: **ORACLE Java**. Java(TM) Platform Standard and JDK, versions: 7. and 8. API Spec. <http://www.oracle.com/technetwork/java/javase/downloads/index.html> (2017).


[^PROTEGEE]: **Protégé software**. [**1**] Protégé Community, D. T. & Stanford University, S. o. M. (2014). Protégé,A free, open-source ontology editor and framework for building intelligent systems. Stanford Center for Biomedical Informatics Research (BMIR), Stanford University. Stanford, California 94305. [**2**] Eriksson, H. (2003). Using jesstab to integrate protégé and jess. IEEE Intelligent Systems, 18(2), 43–50. [**3**] Hoffman, O., Bellifemine, F., & Friedman-Hill, E. (2001). Software: Jadejessprotege, package example for closer integration of jade with jess, optionally also with protege. Available in: <https://jade.tilab.com/documentation/examples/jadejessprotege>


[^GITREPO]: **dpsFramework_ Releases**: GitHub Repository. <https://github.com/dpsframework/dpsFrameworkBuilder/releases/tag/1.8>




[^CLIPS]: **CLIPS**. [**1**] Giarratano, J. C. P. (2014). CLIPS User’s Guide. Version 6.30. CLIPS.  [**2**] Riley, G. (2016). Clips rule based programming language expert system tool clips (6.31) and CLIPSJNI (0.5), clips rule based programming language web site. Available in: <https://sourceforge.net/projects/clipsrules/>.





[^JESS]: **JESS**.  [**1**]Friedman-Hill, E.: JESS, Expert System Software Tool (8.0a1 (alfa)). Sandia National Laboratories. <https://www.jessrules.com/> (2016). [**2**] Friedman-Hill, E. (2003). JESS in Action. Manning Greenwich, CT. [**3**] Cardoso, H. L. (2007). Integrating jade and jess. available in: <https://jade.tilab.com/documentation/examples/jess/>.




[^PROLOG]: **Prolog Language**. [**1**] Merritt, D. (2012). Building expert systems in Prolog. Springer Science & Business Media. [**2**]  SWI-Prolog <https://www.swi-prolog.org/>. [**3**] Fred Dushin and J. Wielemaker. University of Amsterdam. JPL.pl Java Interface. A Java interface for SWI-Prolog.




[^UNILEON]: **Universidad de León** (SPAIN). <http://www.unileon.es>.




[^TESIS]: **PhD Thesis**. Aguayo, F.J., García I. (2017) Techniques for deployment of distributed architecture in rule-based expert systems using the multi-agent paradigm. <https://dialnet.unirioja.es/servlet/tesis?codigo=124344> Department of Electrical and Systems Engineering and Automation. Leon University (SPAIN).




[^BEANSHEL]: **BeanShell**. [**1**] Niemeyer, P.: Lightweight Scripting for Java. <http://www.beanshell.org/> (2014). [**2**] Nick Lombard, BeanShell at GitHub <https://github.com/beanshell/beanshell>.





[^RSYNTAX]: **RSyntaxTexArea**. A syntax highlighting, code folding text editor for Java Swing applications. . <https://github.com/bobbylight/RSyntaxTextArea/> (2017).
[^FIPAACL]: **FIPA ACL**. [FIPA00008] FIPA Agent Communication Language Specification. Foundation for Intelligent Physical Agents, 2000. <http://www.fipa.org/specs/fipa00008/>





[^RAZON]: **Ontologies Reasoner**. [**1**] Luger, G. & Chakrabarti, C. (2011). Knowledge-based probabilistic reasoning from expert systems to graphical models: Report <https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.157.9652>. [**2**] Meditskos, G. & Bassiliades, N. (2011). Clips–owl: A framework for providing object-oriented extensional ontology queries in a production rule engine. Data & Knowledge Engineering, 70(7), 661–681. Report <https://www.sciencedirect.com/science/article/pii/S0169023X11000577> [**3**] Meditskos, G. & Bassiliades, N. (2008). A rule-based object-oriented owl reasoner. Knowledge and Data Engineering, IEEE Transactions on, 20(3), 397–410. Report <https://ieeexplore.ieee.org/document/4378372>.



[^CPLUS]: **The C++ Programming Language**. Bjarne Stroustrup (2000). 3rd Addison-Wesley Longman Publishing Co., Inc. Boston, MA, USA. <https://dl.acm.org/citation.cfm?id=518791>.



[^YELLOW]: **Yellow pages JADE Service**. [**1**] Bellifemine, F.L., Caire, G., Greenwood, D.: Developing Multi-Agent Systems with JADE. Wiley Series in Agent Technology. (2007). [**2**] Cancedda, P. & Caire, G. (2010). JADE Tutorial Creating Ontologies by means of the Bean-Ontology Class, volume 15-April-2010 - JADE 4.0. Telecom Italia S.p.A. [**3**] Yellow Pages examples: <https://jade.tilab.com/documentation/examples/yellow-pages/>



[^IGARCIA]: **Professor**: Dr. Isaías García Rodríguez. Department of Electrical and Systems Engineering and Automation. Leon University (SPAIN).  <https://dialnet.unirioja.es/servlet/autor?codigo=1448367>.


[^RUSSELL]: **Inteligencia Artificial: un enfoque moderno**. Russell, S.J. and Norvig P. 2nd Edition (2004). Pearson Prentice Hall.


[^UNILEONDEPT]: **Departamento de Ingeniería Eléctrica y de Sistemas y Automática**. Universidad de León. <https://departamentos.unileon.es/ingenieria-electrica-y-de-sistemas-y-automatica/>



[^FIPAfoundation]: **FIPA**. Foundation for Intelligent Physical Agents, 2002. <http://www.fipa.org/>











[^jena]: **Apache JENA**. A Java framework for building Semantic Web and Linked Data applications. <https://jena.apache.org/>.

[^eclipse2022]: **Eclipse IDE for Java Developers**: Available at: <https://www.eclipse.org/downloads/packages/>.


[^SWT]: **SWT: The Standard Widget Toolkit**: SWT is an open source widget toolkit for Java designed to provide efficient, portable access to the user-interface facilities of the operating systems on which it is implemented. <https://www.eclipse.org/swt/>.



[^jekyllTOC]: **jekyll-toc**: GitHub Pages can't run custom Jekyll plug-ins so when generating Tables of Contents (TOCs), you're stuck with either a JavaScript solution or using kramdown's :toc option. Available at: <https://github.com/allejo/jekyll-toc>.  (2022)


[^maven]: **Maven**: Apache Maven is a software project management and comprehension tool. Based on the concept of a project object model (POM), Maven can manage a project's build, reporting and documentation from a central piece of information. Available at: <https://maven.apache.org/>.  (2022).


[^minima]: **Minima Jekyll Theme**: Minima is a one-size-fits-all Jekyll theme for writers. It's Jekyll's default (and first) theme. Available at: <https://github.com/jekyll/>.  (2022).

[^liquid]: **Liquid**: Safe, customer-facing template language for flexible web apps. Liquid is an open-source template language created by Shopify and written in Ruby. Available at: <https://shopify.github.io/liquid/>. (2022)

[^sitemap]: **jeckyl-sitemap plugin**: This is a GitHub-Pages plugin. Available at: <https://github.com/jekyll/jekyll-sitemap>
