---
layout: post
title: "Breve introducción al entorno dpsFramework"
headtitle: "Breve introducción al entorno dpsFramework"
author: "Aguayo-Canela, F.J.<br><small>Department of Electrical and Systems Engineering and Automation (2012-17)<br>School of Industrial Engineering and Information Technology. <b>University of Leon</b> (SPAIN)</small>"
date: 2018-06-19 23:56:49:44 +0100
ref: brief
tags: infront featured
categories: drafts
lang: es
translate: false
---

>  **_Resumen:_** _dpsFramework_ es un _entorno integrado de desarrollo_ (IDE), de muy bajo peso. Este entorno está formado por directorios y librerías para facilitar el despligue de Agentes-DPS sobre la plataforma JADE y aportar la garantía de conectividad entre los Agentes-DPS y sus motores de inferencia. Las funciones de _dpsFramework_ se ejecutan desde la línea de comandos de la consola, invocando al compilador JAVA. Pueden lanzarse uno o múltiples agentes de la aplicación en desarrollo.


**Palabras clave:** 
Sistemas Multi-Agente, Lenguajes de programación, Java, CLIPS, Jess, Prolog, Plataforma JADE

<hr>{:width="256px" align="center"}


### Borrador 


<br>

## 1. Introducción


Con este micro-Entorno de Desarrollo (_dpsFramework_) es posible construir comportamientos complejos e incorporar o eliminar esos comportamientos del agente sin necesidad de retirar, re-compilar e ingresar de nuevo al agente en la plataforma multi-agente. _dpsFramework_ mejora la capacidad de depuración del código fuente porque ofrece funcionalidades características de un entorno integrado de desarrollo y funcionalidades específicas para facilitar la _programación orientada a agentes_ (AOP)[^SHOHAM].<br>


_dpsFramework_ permite además, ejecutar procesos de análisis; redactar _scripts_ para automatizar la repetición de ensayos; facilita la observación en tiempo real de los fenómenos asíncronos generados por comportamientos aislados o por los protocolos FIPA[^FIPA] empleados en  diálogos de comunicación y negociación entre Agentes cuando --el agente-- se encuentra sometido a los retrasos de comunicación en una red de ordenadores; y, por encima de esas capacidades, _dpsFramework_ es una herramienta excelente para enseñar y para estudiar en profundidad la _programación orientada a agentes_, incluso para avanzar en las técnicas de distribución de _sistemas expertos basados en reglas_ mediante la tecnología multi-agente[^WOOL].


_dpsFramework_ es abreviatura de ( **d**istributed **p**roduction **s**ystems **Framework**). El _IDE-dpsFramework_  fue desarrollado como instrumento auxiliar para facilitar la reproducción de los análisis y ensayos efectuados durante la tesis de investigación realizada en el Departamento de Ingeniería Eléctrica y de Sistemas y Automática de la Universidad de León (España)[^UNILEON] entre los años 2012 a 2017. El objetivo central de aquella investigación[^TESIS] era demostrar, mediante ensayos reproducibles, técnicas para distribuir la _carga computacional_ generada por una aplicación (o sub-sistema) empleando la tecnología de los sistemas multi-agente.

La investigación se centró en las sobrecargas de cómputo originadas por un sub-sistema dedicado a la transformación del contenido de grandes archivos en formato (.OWL)[^PROTEGEE] de ontologías, al formato (Knowledge-Base/Working-Memory) de _reglas_ y _hechos_ empleado por los _sistemas expertos_. El software empleado en dichos sub-sistemas para realizar la transformación  es conocido como _Razonadores de ontologías_[^RAZON]. Se encuentran desarrollados principalmente en C++[^CPLUS], Java[^ORACLE] y en lenguajes Jess[^JESS] o CLIPS[^CLIPS] ambos específicos para el desarrollo de _sistemas expertos_. Estos dos últimos, Jess y CLIPS son herramientas de construcción de _sistemas expertos basados en reglas_ denominados _**sistemas de producción**_. El conocimiento en los sistemas expertos se almacena en formato de _Reglas_ y los acontecimientos o datos específicos del problema en formato de _Hechos_. 

Para tener la capacidad de reproducir los resultados de los análisis era necesario construir un instrumento de observación y desarrollar clases de Agentes con suficiente flexibilidad para analizar los resultados en tiempo de ejecución del propio agente. Esos agentes debían incorporar además, la  capacidad de acceso y de gestión a los _sistemas expertos basados en reglas_ desarrollados en JESS, CLIPS o Prolog[^PROLOG]. El resultado fue el _IDE-dpsFramework_, un Entorno Integrado de Desarrollo de muy bajo peso, incorporado en Agentes de la plataforma multi-agente JADE[^TILAB].


Los agentes de _dpsFramework_ permiten por defecto, conectarse, controlar, gestionar y extraer el conocimiento generado en los motores de inferencia de tipos CLIPS o Jess.  Como consecuencia de ello, esos agentes pueden ser empleados en un espectro amplio de investigaciones donde, o bien es necesario distribuir el _sistema experto_ para lograr el efecto de reparto de la carga computacional mediante la migración del Agente hacia otro servidor gestionado por la plataforma JADE[^TILAB], o bien son los propios agentes los que utilizan las conclusiones alcanzadas por el _sistema experto_ para modelar y alterar sus comportamientos y objetivos.


<br>


## 1.1 Tipos de Agente-DPS accesibles desde el Entorno _dpsFramework_

Se ha integrado en cuatro Agentes de JADE: <br>
-  (1) **Board**
-  (2) **Monitor**
-  (3) **Node** 
-  (4) **Stage-Node**.



  Los agentes creados a partir de esas clases fueron diseñados para cumplir con objetivos y funcionalidades distintas, sin embargo, cada instancia concreta de esos agentes puede ser además, adaptada a cada investigación y cada caso de estudio particular porque poseen la capacidad de compilar en tiempo de ejecución sus comportamientos y obtener de sus archivos de configuración la relación de servicios activados por defecto en el momento de inicialización. Se relacionan seguidamente cuáles son sus características principales:




- ![TicketBoard](/assets/images/logoPsBoard.gif){:height="86px" align="left" hspace="10px"  border="0px"} **Agentes-DPS-Board**. Activan el servicio de _páginas amarillas_[^YELLOW] de JADE y ofrecen un espacio de almacenamiento para objetos de tipo _Ticket_ a los agentes de la aplicación. Un objeto _Ticket_ contiene datos de las soluciones parciales de un problema en curso de resolución o las soluciones finales alcanzadas sobre un problema planteado. Los _Agentes-Board_ almacenan y exponen dichos _Tickets_ para que otros agentes de la aplicación puedan colaborar y avanzar en el proceso de resolución de problemas. Los _Agentes-Board_ almacenan los _Tickets_ en  registros en una base de datos HyperSQL[^HSQL].  De esa forma mantienen su servicio intacto cuando la plataforma multi-agente se detiene o cuando los propios _Agentes-Board_ abandonan la plataforma. Los _Agentes-Board_ son el instrumento clave para alcanzar la _colaboración_ entre agentes de la aplicación, sin necesidad de construir procesos más complejos de coordinación entre agentes, como el caso de la _cooperación_, que es empleada para compartir las tareas de cómputo. 

El gestor de bases de datos HyperSQL[^HSQL] está íntegramente desarrollado en Java y forma parte del _IDE-dpsFramework_, por lo que la alimentación y extracción de los registros almacenados en _Agentes-Board_ puede tener lugar mediante la transmisión de Mensajes ACL[^FIPAACL] desde otros agentes de la plataforma o, de manera masiva desde una consola de gestor de bases de datos HyperSQL externa a la propia plataforma multi-agente. _dpsFramework_ ofrece utilidades adicionales, entre las que se encuentra la apertura de la Shell del gestor de bases de datos HSQL desde la línea de órdenes. En concreto se obtiene la shell con: `$  java shell hsql`, o con la sentencia: `$  java shell hsql -gui` para abrir en modo gráfico el Esquema de base de datos utilizado por los _Agentes-Board_.




{:.caption-left}
**Fig. 1:** Ejemplo de Interfaz Gráfica de Usuario de un Agente-DPS clase _Monitor_ en modo _depuración_.<br>
![](/assets/images/psMonitorAgent00.png){:width="384px" align="center"  border="0px" }




- ![Monitor](/assets/images/logoPsMonitorAgent.gif){:width="48px" align="left" hspace="10px"  border="0px"} **Agentes-DPS-Monitor**. Están especializados en facilitar la programación en Lenguaje Java sobre una Shell[^BEANSHEL] desde la interfaz gráfica de los propios agentes. Aportan funcionalidades propias de un IDE, como por ejemplo: resaltado de sintaxis[^RSYNTAX]; completado de comandos;  creación de objetos, sus métodos y propiedades; incorporación y eliminación de comportamientos en el agente; etc. Desde la shell de los _Agentes-Monitor_ se puede interactuar  con cualquiera de los otros agentes de una misma aplicación. De esa forma, los _Agentes-Monitor aportan a _Ingenieros de Conocimiento_ y a _Expertos del Dominio_, un mecanismo de _acceso remoto_ a los motores de inferencia integrados en los _Agentes-DPS-Node_ (tratados a  continuación). Una vez concluido el desarrollo de la aplicación, la misión crítica de estos _Agentes-Monitor_ es ejecutar la migración de los _Agentes-DPS-Node_ entre contenedores remotos gestionados por la plataforma multi-agente JADE. (ver, Fig. 1)




- ![Node](/assets/images/logoPsNode.gif){:width="48px" align="left" hspace="10px"  border="0px"} **Agentes-DPS-Node**. Están especializados en ofrecer alto rendimiento para gestionar un _sistema experto_ desarrollado en CLIPS o Jess. Cada _Agente-DPS-Node_ (ver, Fig. 2) posee una instancia propia del motor de inferencia, con el que dialogan y con el que se coordinan mediante el paso de mensajes. El código ejecutable del _sistema experto_ de los _Agentes-DPS-Node_ se encuentra alojado en sub-directorios de trabajo de cada uno de estos agentes. Los  _Agentes-DPS-Node_ tiene 42 comportamientos que componen sus 11 servicios fundamentales. Esos servicios se pueden configurar, activar y desactivar a demanda para cada _Agente-DPS-Node_ particular. La misión de estos servicios es facilitar la auto-gestión y la auto-recuperación, tanto de los propios agentes como de los  _sistemas expertos_ que gobiernan. Los servicios son mecanismos por defecto en los _Agentes-DPS-Node_ creados para facilitar la depuración e incorporación de las competencias específicas del dominio de razonamiento en cada agente de la aplicación (ver, Tabla 1).


{:.caption-left}
**Tabla 1**. Nombres de los 11 _Servicios fundamentales_  de los _Agentes-DPS_.

{:.table-left   }
| Basal      | Depuración             | Autogestión  |
|:--------  |:--------------------- |:---------   |
| **Visibility**: ver u ocultar la interfaz gráfica del agente.         | **NodePlugged**: se gestionan y despachan los mensajes recibidos.   | **Cooperation**: coordinación con otro _Agente-DPS-Node_ según las instrucciones incorporadas en un _script_ para la ejecución conjunta de tareas.   | 
| **Capability**: relación de archivos del _sistema experto_ a cargar en las memorias (Working-Memroy / Knowledge-Base) durante el inicio del _Agente-DPS-Node_.  | **EnginePlugged**: activar diálogos y gestión del motor de inferencia del _Agente-DPS-Node_.  | **Auto-Pilot**: modo piloto-automático o auto-gestión integral llevada a cabo por el propio _Agente-DPS-Node_.     | 
| **SelfBackup**: cron del _Agente-DPS-Node_ para salvaguardar las memorias Working-Memory y Knowledge-Base de su _sistema experto_.          | **DomainExpert**: activar las Shell síncrona y asíncrona de comunicación interna del _Agente-DPS-Node_. Sólo aplicable a instancias abiertas con _Stage-Node_.  | **Collaboration**: participar en resolución de problemas con otros agentes mediante la Pizarra de Tickets. Requiere un _Agente-Board_ activo en la Plataforma. | 
| **Migration**: capacidad para emitir y/o atender demandas de _Agentes-DPS-Node_ y ejecutar la migración propia/de otros agentes, entre contenedores gestionados por la Plataforma.          |               | **SelfRestore**: recuperación del estado íntegro y coherente de la memorias Working-Memory y Knowledge-Base del _sistema experto_ después del proceso de inicio del _Agente-DPS-Node_.   | 

{:.table-left   }


{:.caption-left}
**Fig. 2:** Interfaz gráfica informativa de un Agentes-DPS-Node<br>
![](/assets/images/nodeAgent01.png){:width="464px" align="centre"  border="0px" }




- ![Stage-Node](/assets/images/logoPsStageBussy.gif){:width="48px" align="left" hspace="10px"  border="0px"} **Agentes-DPS-Stage-Node**. Fueron diseñados para lanzar a los _Agentes-DPS-Node_ recubiertos de una interfaz gráfica adicional. Esa segunda interfaz gráfica está enriquecida y orientada para facilitar la depuración y la adaptación de las capacidades de la instancia específica de  _Agente-DPS-Node_. Entre los componentes incorporados por la clase _Stage-Node_ a un _Agente-DPS-Node_ se encuentran: la Shell del Intérprete de Java[^ORACLE] y, dos Shell adicionales conectadas al _sistema experto_ gobernado por el _Agente-DPS-Node_. Esos intérpretes de línea de comandos permiten a los  _Ingenieros de conocimiento_ y   _Expertos de dominio_ depurar y comprobar el funcionamiento del _sistema experto_ en tiempo de ejecución del _Agente-DPS-Node_. Con la cubierta gráfica aportada por la clase _Stage-Node_ a los _Agentes-DPS-Node_ se alcanza una visión precisa de cuáles serán las características expuestas por el _sistema experto_ del agente y su interacción con otros _sistemas expertos_ en ejecución. Una vez concluida la depuración y adaptación de cada _Agente-DPS-Node_, estos se pueden lanzar de nuevo sobre la plataforma JADE, invocando a su clase original.


_**En síntesis:**_  Las clases de agente **Board**, **Monitor** y **Node** han sido diseñadas con los siguientes objetivos: 

- Crear agentes desplegables sobre la plataforma JADE.   
- Conectar con _sistemas expertos_ desarrollados en CLIPS o Jess.    
- Operar sobre arquitecturas de 32/64bits y con sistemas operativos: Microsoft Windows, MacOS X o Linux incluido Raspbian-Pi[^PI].
- Mantener los agentes operativos durante días o años sin perder el conocimiento inicial, ni los conocimientos adquiridos.     
- Detectar el hardware gráfico del servidor donde se ejecutan los agentes, de forma que los agentes pueden ser desplegados en, o migrados hacia, infraestructuras y granjas de servidores virtualizados que no poseen un entorno gráfico explícito.

Las clase de agente **Stage-Node** ha sido diseñada además, con los siguientes objetivos específicos:
- Adaptar cada instancia específica de _Agente-DPS-Node_.
- Permitir, a los _Ingenieros de conocimiento_ y a los _Expertos de dominio_, realizar con comodidad el ajuste y la comprobación del funcionamiento correcto del _sistema experto_ conectado a cada _Agente-DPS-Node_ en tiempo de ejecución del agente.
- Facilitar a los _Agentes-DPS-Node_ separar su interfaz gráfica destinada a la depuración del Agente, de la interfaz gráfica e informativa que es propia del _Agente-DPS-Node_ (ver, Fig. 2). 


<br>

## Referencias


[^TILAB]: **JADE Platform**. <http://jade.tilab.com/>. CSELT, S. & TILab, S. (2017). Jade - java agent development framework. is a framework to develop multi-agent systems in compliance with the fipa specifications. jade 4.5.0 - revision 6825 of 23-05-2017 10:06:04. Open Source, under LGPL restrictions.

[^SHOHAM]: **Agent Oriented Programming**. Shoham, Y. (2005). Agent oriented programming: An overview of the framework and summary of recent research. <https://link.springer.com/chapter/10.1007/3-540-58095-6_9>


[^FIPA]: **FIPA IP**. [FIPA00025] FIPA Interaction Protocol Library Specification. Foundation for Intelligent Physical Agents, 2002. <http://www.fipa.org/specs/fipa00025/> 





[^HSQL]: **HyperSQL**: HSQLDB - 100% Java Database. <http://hsqldb.org/>





[^WOOL]: **Multi-Agent Systems**. [**1**] Wooldridge, M. (2002). An Introduction to Multi-Agent Systems. John Wiley & Sons Ltd. [**2**] Ishida, T. (1994). Parallel, distributed and multiagent production systems. Springer-Verlag Berlin. [**3**] Ishida, T. (1995). Parallel, distributed and multi-agent production systems: a research foundation for distributed artificial intelligence. In ICMAS (pp. 416–422). [**4**] Mas, Ana. (2005). Agentes Software y Sistemas Multiagente. Conceptos, Arquitecturas y Aplicaciones. Prentice Hall.



[^PI]: **Raspbian-Pi Operating Systems**. [**1**] Molloy, Derek. <http://exploringrpi.com/>: Exploring Raspberry Pi. John Wiley Sons, Inc. (2016). [**2**] Raspbian OS for Raspberry-Pi (2018) <https://www.raspberrypi.org/downloads/raspbian/>


[^ORACLE]: **ORACLE Java**. Java(TM) Platform Standard and JDK, versions: 7. and 8. API Spec. <http://www.oracle.com/technetwork/java/javase/downloads/index.html> (2017).


[^PROTEGEE]: **Protégé software**. [**1**] Protégé Community, D. T. & Stanford University, S. o. M. (2014). Protégé,A free, open-source ontology editor and framework for building intelligent systems. Stanford Center for Biomedical Informatics Research (BMIR), Stanford University. Stanford, California 94305. [**2**] Eriksson, H. (2003). Using jesstab to integrate protégé and jess. IEEE Intelligent Systems, 18(2), 43–50. [**3**] Hoffman, O., Bellifemine, F., & Friedman-Hill, E. (2001). Software: Jadejessprotege, package example for closer integration of jade with jess, optionally also with protege. Available in: <http://jade.tilab.com/documentation/examples/jadejessprotege>


[^GITREPO]: **_dpsFramework_ GitHub Repositories**. <https://github.com/dpsframework>




[^CLIPS]: **CLIPS**. [**1**] Giarratano, J. C. P. (2014). CLIPS User’s Guide. Version 6.30. CLIPS.  [**2**] Riley, G. (2016). Clips rule based programming language expert system tool clips (6.31) and CLIPSJNI (0.5), clips rule based programming language web site. Available in: <https://sourceforge.net/projects/clipsrules/>.





[^JESS]: **JESS**.  [**1**]Friedman-Hill, E.: JESS, Expert System Software Tool (8.0a1 (alfa)). Sandia National Laboratories. <http://herzberg.ca.sandia.gov/> (2016). [**2**] Friedman-Hill, E. (2003). JESS in Action. Manning Greenwich, CT. [**3**] Cardoso, H. L. (2007). Integrating jade and jess. available in: http://jade.tilab.com/   documentation/tutorials-guides/integrating-jade-and-jess/.




[^PROLOG]: **Prolog Language**. [**1**] Merritt, D. (2012). Building expert systems in Prolog. Springer Science & Business Media. [**2**]  SWI-Prolog <http://www.swi-prolog.org/>. [**3**] Fred Dushin and J. Wielemaker. University of Amsterdam. JPL.pl Java Interface. A Java interface for SWI-Prolog.




[^UNILEON]: **Leon University** (SPAIN). <http://www.unileon.es>.




[^TESIS]: **PhD Thesis**. Aguayo, F.J., García I. (2017) Deploying production systems on distributed using the Multi-Agent paradigm: applied techniques. <https://dialnet.unirioja.es/servlet/tesis?codigo=124344> Department of Electrical and Systems Engineering and Automation. Leon University (SPAIN).




[^BEANSHEL]: **BeanShell**. [**1**] Niemeyer, P.: Lightweight Scripting for Java. <http://www.beanshell.org/> (2014). [**2**] Nick Lombard, BeanShell at GitHub <https://github.com/beanshell/beanshell>. 





[^RSYNTAX]: **RSyntaxTexArea**. A syntax highlighting, code folding text editor for Java Swing applications. . <https://github.com/bobbylight/RSyntaxTextArea/> (2017).
[^FIPAACL]: **FIPA ACL**. [FIPA00008] FIPA Agent Communication Language Specification. Foundation for Intelligent Physical Agents, 2000. <http://www.fipa.org/specs/fipa00008/>





[^RAZON]: **Ontologies Reasoner**. [**1**] Luger, G. & Chakrabarti, C. (2011). Knowledge-based probabilistic reasoning from expert systems to graphical models: Report. [**2**] Meditskos, G. & Bassiliades, N. (2011). Clips–owl: A framework for providing object-oriented extensional ontology queries in a production rule engine. Data & Knowledge Engineering, 70(7), 661–681. [**3**] Meditskos, G. & Bassiliades, N. (2008). A rule-based object-oriented owl reasoner. Knowledge and Data Engineering, IEEE Transactions on, 20(3), 397–410. 



[^CPLUS]: **C++ Language**.



[^YELLOW]: **Yellow pages JADE Service**. [**1**] Bellifemine, F.L., Caire, G., Greenwood, D.: Developing Multi-Agent Systems with JADE. Wiley Series in Agent Technology. (2007). [**2**] Cancedda, P. & Caire, G. (2010). JADE Tutorial Creating Ontologies by means of the Bean-Ontology Class, volume 15-April-2010 - JADE 4.0. Telecom Italia S.p.A. [**3**] Yellow Pages examples: <http://jade.tilab.com/documentation/examples/yellow-pages/>



