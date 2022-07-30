---
layout: paper
ref:  cardoso2021
lang:  es
idiom:  es-ES
imagepath:  'images/'
images:
  -  'cardoso-banner.png'
  -  'cardoso-fig1.png'
  -  'cardoso-fig2.png'
  -  'cardoso-table1.png'



citation:  'Cardoso, R.C.; Ferrando, A. A Review of Agent-Based Programming for Multi-Agent Systems. Computers 2021, 10, 16. https://doi.org/10.3390/ computers10020016 Academic Editor: Paolo Bellavista'




toc:  true


title:  'FIPA: Especificación de protocolos para la interacción de sistemas de múltiples agentes'
headtitle:  'Cardoso, R.C.; Ferrando, A. A Review of Agent-Based Programming for Multi-Agent Systems. Computers 2021, 10, 16.'
shorttitle:  'Cardoso, Ferrando (2021)'
year:  '2021'
author:  'Cardos, R.C.'
department:  'Department of Computer Science, The University of Manchester, Manchester M13 9PL, UK '
authors:
  -  'Ferrando, A.'


departments:
  -  'Department of Computer Science, The University of Manchester, Manchester M13 9PL, UK '

updates:  'https://www.mdpi.com/2073-431X/10/2/16?type=check_update&version=2'

doi:  'https://doi.org/10.3390/computers10020016'
url:  
editor:  'Academic Editor: Paolo Bellavista. Publisher’s Note: MDPI stays neu tral with regard to jurisdictional claims in published maps and institutional affiliations. '
pubdate:  '2021/01/27'
license:  'Copyright: © 2021 by the authors. Li censee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (https://creativecommons.org/ licenses/by/4.0/).'




date:  '2021/01/27'
modified_date:  '2021/01/27'



---








Control de citas:  [^1],  [^2],  [^3],  [^4],  [^5],  [^6],  [^7],  [^8],  [^9],  [^10],  [^11],  [^12],  [^13],  [^14],  [^15],  [^16],  [^17],  [^18],  [^19],  [^20],  [^21],  [^22],  [^23],  [^24],  [^25],  [^26],  [^27],  [^28],  [^29],  [^30],  [^31],  [^32],  [^33],  [^34],  [^35],  [^36],  [^37],  [^38],  [^39],  [^40],  [^41],  [^42],  [^43],  [^44],  [^45],  [^46],  [^47],  [^48],  [^49],  [^50],  [^51],  [^52],  [^53],  [^54],  [^55],  [^56],  [^57],  [^58],  [^59],  [^60],  [^61],  [^62],  [^63],  [^64],  [^65],  [^66],  [^67],  [^68],  [^69],  [^70],  [^71],  [^72],  [^73],  [^74],  [^75],  [^76],  [^77],  [^78],  [^79],  [^80],  [^81],  [^82],  [^83],  [^84],  [^85],  [^86],  [^87],  [^88]. 


> **{{ site.data.i18n[page.lang].abstract }}:**  Los agentes inteligentes y autónomos son una subárea de la inteligencia artificial simbólica en la que estos agentes deciden, ya sea de forma reactiva o proactiva, sobre un curso de acción razonando sobre la información disponible sobre el mundo (incluido el entorno, el propio agente y otros agentes). . Abarca multitud de técnicas, como protocolos de negociación, simulación de agentes, argumentación multiagente, planificación multiagente y muchas otras. En este artículo, nos enfocamos en la programación de agentes y proporcionamos una revisión sistemática de la literatura sobre programación basada en agentes para sistemas multiagente. En particular, analizamos tanto los lenguajes de programación de agentes veteranos (aún mantenidos) como los novedosos, sus extensiones, el trabajo de comparación de algunos de estos lenguajes y las aplicaciones encontradas en la literatura que hacen uso de la programación de agentes. Palabras clave: programación basada en agentes; sistemas multiagente; lenguajes de programación de agentes

**{{ site.data.i18n[page.lang].keywords}}:**  programación basada en agentes; sistemas multiagente; lenguajes de programación de agentes

#  1. Introducción



Los sistemas multiagente (MAS) **[^1]** son ​​una rama bien establecida de la inteligencia artificial (IA). Aunque son relativamente jóvenes con respecto a áreas de investigación más arquetípicas, los MAS tienen una rica historia; en 1995 **[^2]** la tecnología de agentes fue reconocida como un área de investigación en rápido desarrollo y una de las áreas de tecnología de la información de más rápido crecimiento. Tal afirmación sigue siendo cierta hoy en día, donde se pueden encontrar muchos artículos de investigación, herramientas y conferencias cuyo objetivo es avanzar en la investigación en el área. A pesar de esto, los MAS no se usan tan ampliamente como podrían. Teniendo en cuenta el aspecto de programación de agentes de los MAS, según **[^3]**, la razón clave es que hay pocos incentivos para que los desarrolladores cambien a los lenguajes de programación de agentes (APL) actuales, ya que los comportamientos que se pueden programar fácilmente son lo suficientemente simples como para ser implementables. en los lenguajes principales con solo una pequeña sobrecarga en el tiempo de codificación. Esto, entre la presencia de demasiadas opciones desorganizadas disponibles, no ayuda a que los lenguajes y herramientas de programación basados ​​en agentes sean elegidos por usuarios no expertos.



Un agente inteligente **[^4]** puede generalizarse como una entidad informatizada que: es capaz de razonar (racional/cognitivo), de tomar sus propias decisiones de forma independiente (autónomo), de colaborar con otros agentes cuando es necesario (social), de percibir el contexto en el que opera y reacciona adecuadamente (reactivo), y finalmente, para tomar acción con el fin de lograr sus objetivos (proactivo). Un sistema basado en agentes (u orientado a agentes) es un sistema donde los agentes son las entidades principales, tratadas como abstracciones de primera clase. Desde una perspectiva de programación, se puede seguir el mismo razonamiento. En particular, al usar una comparación, podemos decir que los agentes son para los lenguajes de Programación Orientada a Agentes (AOP) lo que los objetos son para los lenguajes de Programación Orientada a Objetos (OOP). En un lenguaje de programación basado en agentes, los agentes son los bloques de construcción, y los programas se obtienen programando sus comportamientos (cómo razona un agente), sus objetivos (lo que pretende lograr un agente) y su interoperación (cómo colaboran los agentes para resolver una tarea). ).



Los agentes son adecuados para usarse en aplicaciones que involucran cómputo distribuido o concurrente o cuando se requiere comunicación entre diferentes componentes. Por esta razón, la tecnología de agentes es útil en aplicaciones que razonan sobre mensajes/objetos recibidos a través de una red. Al preservar su estado de procesamiento y el estado del mundo que los rodea, los agentes también son ideales para las aplicaciones de automatización. Además, los agentes autónomos pueden operar sin la intervención del usuario y pueden usarse en aplicaciones tales como automatización de plantas/procesos, gestión de flujos de trabajo, robótica y otras. Otra ventaja de la programación basada en agentes es que debido al ciclo de razonamiento presente en los agentes, también es posible proporcionar explicaciones sobre las decisiones que ha tomado un agente.




El objetivo de este artículo es revisar los últimos trabajos en programación basada en agentes, para ayudar a los usuarios expertos y no expertos a comprender mejor el estado actual de las tecnologías de programación basada en agentes, e identificar direcciones futuras de investigación en esta área. En particular, nos enfocamos en los últimos lenguajes de programación de agentes, plataformas y marcos para el desarrollo de MAS. Se tienen en cuenta tanto los artículos teóricos como los prácticos, y también analizamos brevemente las extensiones recientes, las comparaciones existentes y las aplicaciones de la programación basada en agentes.




Con respecto a otras revisiones y encuestas sobre APL en la literatura **[^3]**, **[^5]-[^10]**, nuestra revisión se enfoca en desarrollos recientes y considera trabajos que presentan nuevas APL, así como trabajos que se enfocan en extender o comparar APL existentes. Además, consideramos aspectos tanto teóricos como prácticos; esto ayuda a tener una mejor comprensión de la brecha de realidad entre los APL teóricos y prácticos. Finalmente, con respecto a revisiones anteriores, nos enfocamos en toda la clase de APL, y no en un área específica de APL como en **[^6]**, donde solo se consideran los aspectos de ingeniería, o en **[^7]**, donde solo se consideran las plataformas de APL, o en **[^8]**, donde solo se analiza la literatura de simulación basada en agentes, o en **[^3]**,**[^5]**, donde su enfoque está en un modelo específico de agencia (Creencia-Deseo-Intención—BDI).




Este documento está estructurado de la siguiente manera. En la Sección 2 se proporciona una breve historia de la programación basada en agentes. En la Sección 3, se presenta el proceso de revisión sistemática seguido en este documento. La Sección 4 contiene los hallazgos de la revisión con los artículos encontrados en nuestra búsqueda de la literatura. En la Sección 5, se discuten los resultados de la revisión y se sugieren direcciones futuras. Finalmente, en la Sección 6, se reportan las conclusiones del trabajo.




#  2. Historia de la programación basada en agentes




En 1993, la Programación Orientada a Agentes se introdujo por primera vez **[^11]** como una especialización de la Programación Orientada a Objetos. En particular, analiza la noción del estado mental de un agente, que consiste en su información, decisiones y capacidades. Este trabajo también describe los programas de agentes en el intérprete AGENT-0 (implementado en el lenguaje Lisp) y su comunicación usando la teoría de los actos de habla, esta última todavía se usa para definir la comunicación de agentes en varios lenguajes de programación de agentes contemporáneos. A lo largo de los años, se han desarrollado muchos modelos cognitivos y de razonamiento para la programación basada en agentes. En esta sección, analizamos tres modelos particulares que han sido fundamentales en el diseño de muchos lenguajes de programación de agentes en el pasado y que todavía se utilizan en nuevos lenguajes en la actualidad: Sistema de razonamiento procedimental (PRS), BDI y Cálculo de situación.




El Sistema de Razonamiento Procedural (PRS) **[^12]** (implementado en Lisp) define un sistema capaz de razonar sobre procesos, es decir, formas procedimentales de conocimiento. Un agente en este sistema puede usar estos procedimientos para seleccionar intenciones para lograr objetivos particulares. A diferencia de los lenguajes de programación convencionales, estos procedimientos no se invocan a priori, sino que se activan cuando son capaces de contribuir a algún objetivo o reaccionar ante alguna situación. Si bien comparte algunas similitudes con los planificadores de IA de la época, su principal diferencia es que realiza una planificación jerárquica parcial en el sentido de que interactúa con un entorno dinámico durante el proceso de razonamiento, en lugar de generar un plan para un entorno estático.




El modelo Creencia-Deseo-Intención (BDI) **[^13]**,**[^14]** consiste en un proceso de razonamiento que ayuda a la toma de decisiones de seleccionar una acción apropiada para el logro de algún objetivo. Sus tres actitudes mentales son: creencia: conocimiento que el agente cree acerca de su entorno, de sí mismo y de otros agentes; deseo: los estados deseados que el agente quiere lograr; e intención: una secuencia de pasos hacia el logro de un deseo. Estas actitudes mentales representan respectivamente los estados de información, motivación y deliberación del agente. El flujo de trabajo en un sistema BDI genérico se muestra en la Figura 1 y funciona como tal: una función de revisión de creencias recibe información de entrada del entorno (por ejemplo, sensores) y es responsable de actualizar la base de creencias. Esta actualización puede generar más opciones que pueden convertirse en deseos actuales basados ​​en la base de creencias y la base de intenciones. Un filtro se encarga de actualizar la base de intenciones, teniendo en cuenta su estado anterior y la base de creencias y la base de deseos actuales. Finalmente, se elige una intención para ser realizada como una acción por parte del agente. BDI es el modelo de agencia más popular, ha sido y sigue siendo utilizado en muchos lenguajes de programación de agentes. AgentSpeak(L) **[^15]** es un lenguaje que sirve como una abstracción de los sistemas BDI implementados que se pueden utilizar para interpretar los programas de agente como programas lógicos de cláusula de bocina. La teoría detrás de este lenguaje se ha implementado como base para muchas APL.








**{{ site.data.i18n[page.lang].figure  }}  1**.  El modelo BDI.<br>
![]( {{ page.imagepath }}{{  page.images[1]  }} )







El Cálculo de Situación **[^16]** es un lenguaje de primer orden diseñado para representar cambios en entornos dinámicos. Una situación es un término de primer orden que representa una secuencia de acciones. Una situación inicial es cuando aún no se han producido acciones. La función do(a, s) da como resultado una situación sucesora de s después de ejecutar la acción a, similar a los sistemas de transición de estado. Los entornos dinámicos juegan un papel importante en la programación basada en agentes y, como tal, Situation Calculus se ha utilizado para modelar cómo cambia el mundo como resultado de la ejecución de acciones.








Como veremos en la Sección 4, hay muchos otros modelos que han inspirado los lenguajes de programación basados ​​en agentes, sin embargo, estos tres fueron los más influyentes en la historia pasada de la programación basada en agentes. Algunos lenguajes de agentes comparten similitudes o incluso mezclan conceptos de otros paradigmas de programación, como procedimental, imperativo, orientado a objetos, funcional, actor, concurrente, etc. Comparar las diferencias o entrar en detalles sobre estos otros paradigmas está fuera del alcance de esta revisión.o en un área específica de APL como en **[^6]**, donde solo se consideran los aspectos de ingeniería, o en **[^7]**, donde solo se consideran las plataformas de APL, o en **[^8]**, donde solo se analiza la literatura de simulación basada en agentes, o en **[^3]**,**[^5]**, donde su enfoque está en un modelo específico de agencia (Creencia-Deseo-Intención—BDI).




Este documento está estructurado de la siguiente manera. En la Sección 2 se proporciona una breve historia de la programación basada en agentes. En la Sección 3, se presenta el proceso de revisión sistemática seguido en este documento. La Sección 4 contiene los hallazgos de la revisión con los artículos encontrados en nuestra búsqueda de la literatura. En la Sección 5, se discuten los resultados de la revisión y se sugieren direcciones futuras. Finalmente, en la Sección 6, se reportan las conclusiones del trabajo.






#  3. Metodología de revisión







Realizamos una revisión sistemática de la literatura sobre lenguajes de programación de agentes durante los últimos 5 años (2015-2020). En la Figura 2 se muestra un diagrama que ilustra nuestra metodología de revisión. Para cada término buscado, consideramos las primeras 10 páginas (100 entradas) recuperadas por Google Scholar (ordenadas por relevancia), para un total de 400 entradas (incluidos los duplicados).




Los términos utilizados en nuestra búsqueda fueron:




- Lenguajes de programación basados ​​en agentes
- Extensiones de programación basadas en agentes
- Comparación de programación basada en agentes
- Aplicaciones de programación basadas en agentes








**{{ site.data.i18n[page.lang].figure  }}  2**.  Diagrama de flujo de revisión sistemática.<br>
![]( {{ page.imagepath }}{{  page.images[2]  }} )






Después de eliminar los duplicados, teníamos 250 documentos restantes. A estos, agregamos 16 entradas de fuentes externas; en su mayoría referencias antiguas que no aparecerían en la búsqueda, además de algunas otras que se encuentran en citas en papel y otras fuentes. De las 16 entradas externas, ocho fueron APL influyentes que se desarrollaron antes de 2015 y se actualizaron recientemente (es decir, 2017-2020).



#  4. Revisar los hallazgos sobre la programación basada en agentes para Mas





En esta sección, cubrimos toda la investigación encontrada en nuestra revisión sistemática de la literatura. Comenzamos con los lenguajes de programación de agentes y sus extensiones, luego continuamos discutiendo las comparaciones existentes en la programación basada en agentes y cerramos la sección con una breve revisión de las aplicaciones en el área.




##  4.1. Lenguajes de programación de agentes




Reportamos los lenguajes de programación de agentes encontrados en la revisión sistemática en la Tabla 1. Como mencionamos en la Sección 2, podemos ver que BDI es claramente el modelo de agencia más popular, siendo utilizado en 7 de los 15 lenguajes. La mayoría de los lenguajes implementados se han implementado en Java, probablemente para aprovechar la multiplataforma de Java a través de su máquina virtual Java. La tabla contiene solo los lenguajes de propósito general de alto nivel que se pueden usar para desarrollar MAS independientes del dominio. Si bien otros enfoques, como el modelado y la simulación basados ​​en agentes (ABMS) y los agentes cognitivos en robótica, no se incluyen en la tabla, informamos brevemente algunas de las investigaciones novedosas que se han realizado en esas áreas más adelante.





**{{ site.data.i18n[page.lang].table  }}  1**.  Tabla 1. Una colección de lenguajes de programación de agentes recientes (o actualizados recientemente). Los idiomas que no tienen una implementación disponible públicamente se representan con una X. En caso de que haya varias ramas de implementación, la columna Última actualización hace referencia a la última actualización en la rama maestra.<br>
![]( {{ page.imagepath }}{{  page.images[3]  }} )



###  4.1.1. APL de propósito general





En **[^6]** se puede encontrar una encuesta sobre la programación orientada a agentes desde la perspectiva de la ingeniería de software. Uno de los principales desafíos informados en la encuesta para los desarrolladores de APL es la necesidad de cerrar la brecha cognitiva que existe entre los conceptos que sustentan los lenguajes convencionales y los que sustentan AOP. En **[^21]** los autores intentan llenar este vacío centrándose en comprender la relación entre AgentSpeak(L) **[^15]** y OOP con el objetivo de tratar de reducir la brecha cognitiva percibida. Tal trabajo propone un nuevo lenguaje de programación de agentes tipificados estáticamente denominado ASTRA.





En **[^22]** los autores presentan Chromar, una notación basada en reglas con semántica estocástica que produce una cadena de Markov de tiempo continuo. Chromar está integrado en Haskell, lo que le otorga un mayor poder expresivo y se adapta a la disponibilidad de tipos enriquecidos. En Chromar, las reglas son abstracciones de primer orden que pueden describir un comportamiento (posiblemente parcial) de un agente individual y una acción sincronizada de dos o más agentes.




GOAL **[^23]** es un lenguaje de programación de agentes declarativos que utiliza creencias y objetivos basados ​​en conocimientos para respaldar la toma de decisiones de sus agentes cognitivos. A pesar de compartir conceptos similares con el modelo BDI (creencias, deseos/metas), el lenguaje GOAL está más centrado en la toma de decisiones basada en reglas. Los programas de los agentes están escritos en la sintaxis específica de GOAL, pero el conocimiento del agente (por ejemplo, las reglas) generalmente se representa en Prolog.




Jason **[^24]** es una extensión del lenguaje AgentSpeak(L), basado en el modelo de agente BDI. Los agentes de Jason reaccionan a los eventos del sistema ejecutando acciones en el entorno, de acuerdo con los planes disponibles en la biblioteca de planes de cada agente. Una de las extensiones de Jason es la adición de reglas similares a Prolog que se pueden agregar y usar en la base de creencias de los agentes.



La plataforma JaCaMo **[^25]**,**[^26]** está compuesta por tres tecnologías, Jason, CArtAgO **[^27]** y Moise **[^28]**, cada una de las cuales representa un nivel de abstracción diferente. Jasón se usa paraprogramando el nivel de agente, CARtAgO es responsable del nivel de ambiente y Moise del nivel de organización. JaCaMo integra estas tres tecnologías definiendo un vínculo semántico entre conceptos en diferentes niveles de abstracción (agente, entorno y organización). El resultado final es la plataforma de desarrollo JaCaMo MAS. Proporciona soporte de primera clase y alto nivel para el desarrollo de agentes, entornos y organizaciones, lo que permite el desarrollo de sistemas multiagente más complejos.




Gwendolen **[^29]** inicialmente comenzó como un pequeño subconjunto de Jason con la esperanza de desarrollar programas de agentes verificables, pero desde entonces ha crecido hasta convertirse en su propia sintaxis y semántica. Debido a que es un lenguaje que se ha creado para admitir la verificación de agentes desde cero, está limitado en cuanto a las funciones que puede admitir; sin embargo, los conceptos básicos de AgentSpeak (L) y BDI están todos presentes. Existe una vasta literatura sobre verificación de programas de agentes y MAS, pero los consideramos fuera del alcance de esta revisión. Gwendolen, además de ser verificable, sigue siendo un lenguaje viable para desarrollar MAS de propósito general.



JADE **[^30]** es una plataforma de código abierto para el desarrollo de aplicaciones basadas en agentes peer-to-peer. Además de la abstracción del agente, también proporciona: modelo de composición y ejecución de tareas, comunicación de agente entre pares basada en el paso de mensajes asincrónicos y un servicio de páginas amarillas que admite el mecanismo de descubrimiento de publicación y suscripción. Los sistemas basados ​​en JADE se pueden distribuir entre máquinas con diferentes sistemas operativos y se han utilizado en muchos lenguajes (p. ej., Jason y JaCaMo) como infraestructura de distribución.



En **[^31]** los autores presentan JADEL (Lenguaje JADE), una extensión de JADE que brinda soporte para la construcción de agentes y MAS sobre JADE sin tener que usar Java directamente; posteriormente, en **[^32]**, los autores presentan Jadescript, una extensión de JADEL. Jadescript se caracteriza por una fuerte sintaxis expresiva inspirada en gran medida en los lenguajes de secuencias de comandos modernos para promover la legibilidad y hacer que los programas de agentes sean más similares al pseudocódigo.




Jadex **[^33]** permite la programación de agentes de software inteligente en XML y Java. La abstracción de agentes se basa en el modelo BDI y proporciona varias funciones, como: una infraestructura de tiempo de ejecución para agentes, múltiples estilos de interacción, soporte de simulación, formación automática de redes superpuestas y un amplio conjunto de herramientas de tiempo de ejecución.




LightJason, una plataforma basada en Java altamente escalable para programación y simulación orientada a agentes BDI, se presenta en **[^34]**. LightJason se basa en un lenguaje lógico que amplía AgentSpeak(L) con expresiones lambda, definición de reglas y planes múltiples, acciones de reparación explícitas, asignaciones de múltiples variables, ejecución paralela y variables seguras para subprocesos. Aunque el lenguaje está inspirado en AgentSpeak(L) y Jason, LightJason se implementa desde cero.



En **[^35]**, un lenguaje AOP llamado Lenguaje basado en la planificación para agentes y entornos computacionales (PLACE) agrega capacidad de planificación de IA a los agentes. PLACE tiene una estructura sintáctica cercana a BDI, mientras que la planificación se realiza en un planificador Hierarchical Task Network (HTN). A diferencia de otros lenguajes AOP, las acciones en PLACE tienen duraciones asociadas, por lo que requieren que el planificador sea capaz de manejar información temporal. Los agentes en PLACE tienen la capacidad de recuperarse de fallas adaptando sus actividades a las nuevas situaciones. Para este propósito, se agrega un mecanismo de reparación del plan que repara un plan si los eventos no anticipados en el entorno hacen que el plan se vuelva inviable.



En **[^36]** se propone el Lenguaje de Programación para Agentes Síncronos (PLASA). PLASA es independiente de la plataforma y facilita una implementación rápida de aplicaciones cooperativas en múltiples robots físicos y en entornos dinámicos. Esencialmente, PLASA implementa una variante del modelo Wait-Look-Compute-Move propuesto en **[^37]**, donde los robots se mueven sincrónicamente. Está diseñado como un lenguaje de programación de alto nivel, que permite a los usuarios especificar las instrucciones que deben realizar los robots en un lenguaje legible por humanos.


El sistema multiagente de modelo relacional (RMAS) **[^38]** es un enfoque centrado en la base de datos para sistemas multiagente adecuado para la incorporación del razonamiento y el control en sistemas ciberfísicos (CPS). La implementación inicial de RMAS se propone mediante el acoplamiento del entorno Matlab y el lenguaje de base de datos SQLite.




El enfoque de SARL **[^39]** es proporcionar un lenguaje extensible que esté equipado con la cantidad mínima de conceptos (es decir, conceptos clave) necesarios para admitir AOP. El lenguaje tiene como objetivo proporcionar abstracciones para concurrencia, distribución, interacción, descentralización, reactividad, autonomía y reconfiguración dinámica. Para ello no se basa en ningún modelo, sino que crea su propio Lenguaje Específico de Dominio (DSL) con el fin de proporcionar un núcleo reducido y más ligero.




###  4.1.2. ABMS, robótica y otros





Como se reconoce en **[^40]**, existe una brecha entre el software orientado a agentese Ingeniería (AOSE) metodologías y el desarrollo de ABMS. Para superar este problema, en **[^41]** se propone un proceso AOSE denominado Proceso para el desarrollo de simuladores basados ​​en agentes eficientes (PEABS). Utiliza la metodología INGENIAS **[^42]** para modelar la especificación y diseñar su estructura. Aplica un marco de adaptación que permite a los desarrolladores de ABMS obtener simulaciones con una alta eficiencia para grandes cantidades de datos. Otro enfoque para desarrollar ABMS se presenta en **[^43]**,**[^44]**, donde los autores proponen una nueva arquitectura de agente cognitivo basada en el modelo BDI e integrada en el lenguaje de modelado GAMA **[^45]**. Con respecto a trabajos previos de integración entre BDI y ABMS, en **[^43]** la arquitectura propuesta pretende ser flexible y fácil de usar para usuarios no expertos. Otro trabajo que tiene como objetivo integrar BDI y ABMS se presenta en **[^46]**, donde los autores presentan un marco que permite que los agentes cognitivos BDI se incrusten en un sistema ABMS. En comparación con **[^43]**, la referencia **[^46]** es más general ya que su objetivo es integrar cualquier sistema basado en BDI con ABMS. El único requisito es que se puedan identificar a priori los perceptos (u observaciones/eventos ambientales) de interés para cada agente y las acciones que el agente puede ejecutar en el entorno de simulación.




ALLEGRO (=ALGOL en PREGO **[^47]**,**[^48]**) es un formalismo de programación basado en una arquitectura de creencias para dominios estocásticos que pretende ser una alternativa a GOLOG **[^49]** para el control de alto nivel en aplicaciones robóticas. Otro lenguaje que se basa en GOLOG y el cálculo de situación se presenta en **[^50]**, donde se presenta una implementación prototipo de Yet Another GOLOG Interpreter (YAGI), un lenguaje de programación de agentes y robots basado en acciones. YAGI ofrece enlaces para marcos de robótica populares como Robot Operating System (ROS) **[^51]** y Fawkes.




En **[^52]** los autores presentan un marco de programación de agentes cognitivos afectivos (CAAF), un marco basado en la teoría de las emociones de creencias y deseos que permite el cálculo de las emociones para los agentes cognitivos (es decir, convertirlos en agentes cognitivos afectivos). Los autores presentan una semántica que muestra las construcciones de programación de estos agentes. Con estas construcciones, un programador puede crear un programa de agente con agentes cognitivos que calculan automáticamente las emociones durante las ejecuciones.




##  4.2. Extensiones de lenguajes de programación de agentes




En la sección anterior, informamos trabajos que presentan APL novedosas (2015–2020), junto con trabajos que presentan las APL más influyentes (≤2015) que aún se mantienen. Ahora, consideramos los trabajos más influyentes que han ampliado las APL existentes. Nos referimos a las extensiones de APL como trabajos que han cambiado las APL existentes internamente, ya sea agregando nuevas características o construyendo sobre las APL existentes, por ejemplo, al personalizar la APL para un escenario nuevo y específico.



En **[^54]** se presenta una versión mejorada del Sistema de Agentes Múltiples para Mercados Eléctricos Competitivos (MASCEM) **[^53]**. Esta versión extendida del simulador MASCEM tiene como objetivo apoyar la integración de modelos nuevos y complementarios. Las importantes decisiones de implementación estructural brindan la facilidad para acomodar diferentes herramientas y mecanismos, lo que hace que MASCEM pueda lidiar con el entorno en constante cambio y altamente exigente de los mercados de electricidad. En particular, la nueva extensión de MASCEM trae el uso de ontologías para apoyar las comunicaciones de los jugadores.



En **[^55]**, los autores presentan TABSAOND, una extensión de PEABS **[^41]**. La principal diferencia entre TABSAOND y PEABS es que el primero se centra en el diseño e implementación de los procesos de toma de decisiones en escenarios no deterministas. Además, los simuladores ahora se implementan como aplicaciones móviles y herramientas en línea.



En **[^56]** se propone un modelo de sincronización conservador para el lenguaje SARL y su plataforma de tiempo de ejecución Janus. Dado que Janus no hace ninguna suposición sobre el orden de los eventos que intercambian los agentes, no es posible utilizar la plataforma Janus para la simulación basada en agentes que involucre tiempo sin proporcionar a la plataforma un mecanismo de sincronización específico. Un modelo para tal mecanismo se describe en su extensión.






Los autores de **[^57]** proponen nuevas construcciones de programación para integrar un modelo de emoción avanzado pero basado en reglas, EMIA **[^58]**, en línea con el lenguaje de agente 2APL **[^59]**. La combinación de ambos se ha llevado a cabo redefiniendo la sintaxis, la semántica y el ciclo de deliberación de 2APL. Esta combinación se enfoca principalmente en la generación de emociones basadas en eventos, y la simulación resultante muestra una gran credibilidad en las emociones expresadas por el agente al responder a los escenarios de la vida real.




ARGO **[^60]** es una arquitectura Jason personalizada para programar agentes robóticos integrados utilizando el middleware Javino y los filtros de percepción.




En **[^61]**, los autores muestran cómo la reflexión procedimental en el lenguaje de programación de agentes meta-APL **[^62]** puede usarse para permitir una implementación directa de algunosde los pasos en el ciclo de deliberación de un agente BDI, al permitir que tanto los programas del agente como la estrategia de deliberación del agente se codifiquen en el mismo lenguaje de programación.




Una extensión **[^63]** de Jason y Gwendolen permite que los agentes en estos lenguajes se comuniquen con ROS, apoyando así la programación de agentes autónomos que pueden controlar y tomar decisiones de alto nivel en aplicaciones robóticas desarrolladas en ROS. La extensión se realiza a través de una interfaz que se utiliza como entorno entre el agente y ROS, y la comunicación entre el entorno y los nodos ROS se realiza mediante la biblioteca rosbridge. La principal diferencia entre su trabajo y los intentos anteriores de extender las APL tradicionales para admitir ROS es que su enfoque no requiere modificaciones adicionales en ninguna de las dos APL o ROS, lo que lo hace utilizable y portátil para diferentes versiones de estas herramientas. De manera similar, en **[^64]** se presenta un marco para usar Jason con ROS en sistemas integrados y se introduce una nueva arquitectura para admitir interacciones de bajo nivel entre ROS y el agente.




Finalmente, en **[^65]** se presenta un modelo para un marco de programación de agentes BDI que integra el aprendizaje por refuerzo y una implementación basada en el lenguaje de programación Jason. El enfoque admite el diseño de agentes BDI donde algunos planes pueden programarse explícitamente y otros pueden ser aprendidos por el agente durante la etapa de desarrollo/ingeniería.









##  4.3. Comparación de lenguajes de programación de agentes



A partir de la investigación descrita en las dos secciones anteriores, podemos observar que hay muchas APL para desarrollar MAS disponibles en la comunidad de programación basada en agentes. Desafortunadamente, muy a menudo la evaluación de un idioma se pierde parcial o incluso por completo. En el pasado se han realizado algunos estudios como **[^66]** para comparar lenguajes de agentes con otros paradigmas, en ese caso la comparación fue con lenguajes basados ​​en actores. En sus resultados, los autores han demostrado que los lenguajes de agentes (específicamente Jason en ese trabajo) pueden competir con lenguajes más livianos como los actores.



En **[^67]**, los autores presentan un marco de evaluación para evaluar lenguajes de modelado específicos de dominio existentes o recientemente definidos para MAS. La evaluación se centra tanto en el lenguaje como en las herramientas correspondientes y proporciona resultados tanto cualitativos como cuantitativos.





En **[^68]** se muestra una comparación entre el pseudocódigo de un conocido algoritmo para resolver problemas de satisfacción de restricciones distribuidas y la implementación de tal algoritmo en JADEL.



El trabajo en **[^69]** se enfoca en comparar plataformas paralelas que soportan simulaciones de múltiples agentes y su ejecución en recursos de alto rendimiento como clústeres paralelos.



Los autores de **[^70]** realizan una evaluación sistemática de los enfoques ABMS diferenciando los conceptos de qué tan complejo es el comportamiento del modelo y qué tan complicada es la estructura del modelo, e ilustran la relación no lineal entre ellos. Luego, evalúan las compensaciones entre modelos simples (a menudo teóricos) y modelos complicados (a menudo basados ​​empíricamente).





##  4.4. Aplicaciones basadas en agentes




En esta sección enumeramos algunas de las aplicaciones más recientes que utilizan programación basada en agentes. Nuestro objetivo aquí es mostrar la amplia variedad de dominios de aplicaciones en los que los agentes pueden ser útiles, por lo tanto, esta lista no es exhaustiva y no es el enfoque principal de nuestra revisión.



El Concurso de Programación Multiagente (https://multiagentcontest.org/) (MAPC) es una competencia internacional anual que ocurre desde 2005. Su propósito es estimular la investigación en programación multiagente mediante la introducción de escenarios de referencia complejos que requieren una acción coordinada y se puede usar para probar y comparar lenguajes de programación, plataformas y herramientas de múltiples agentes. En los últimos años se han utilizado implementaciones que utilizan diferentes plataformas y lenguajes basados ​​en agentes; como JaCaMo **[^71]**–**[^73]**, Jason **[^74]**,**[^75]**, GOAL **[^76]**.




En **[^77]**,**[^78]** se propusieron modelos basados ​​en agentes para simular y evaluar la transmisión de la enfermedad por coronavirus (COVID-19). Existe toda una área de investigación centrada en el uso de tecnologías basadas en agentes en la industria energética. Por ejemplo, en **[^79]**, las tecnologías MAS se utilizan para el control de Microgrid, su optimización y distribución en el mercado. Para lecturas adicionales, hay una encuesta **[^80]** sobre las aplicaciones de MAS en el control y operación de Microrredes, y una revisión **[^81]** del estado del arte en la aplicación de MAS a problemas de optimización de energía.



En **[^82]**, se presenta una aplicación de ABMS para estudiar las relaciones entre las actividades humanas y los cambios en el uso y la cobertura del suelo para respaldar las decisiones científicas con respecto a la planificación y el uso razonables del suelo. El modelo se implementa en base a la plataforma de modelado Repast **[^83]**.



En **[^84]**, los autores presentan e ilustran FlowLogo, un entorno de modelado interactivo para desarrollar modelos de aguas subterráneas basados ​​en agentes acoplados. FlowLogo está implementado en NetLogo y es thEl primer software integrado que ofrece una forma sencilla de representar los comportamientos de los agentes que evolucionan con las condiciones del agua subterránea. En **[^8]** se puede encontrar una encuesta sistemática sobre las herramientas y aplicaciones de ABMS.




En **[^10]** se proporciona una guía metodológica para el uso de agentes BDI en simulaciones sociales y una descripción general de las metodologías y herramientas existentes para usarlos.






Los agentes se pueden usar para desarrollar sistemas de Internet de las cosas (IoT) autogestionados debido a su naturaleza distribuida, conciencia del contexto y autoadaptación (para obtener más información sobre el uso de microservicios como agentes en IoT **[^85]**,**[^86]**). En **[^87]**, los autores tienen como objetivo mejorar el desarrollo de aplicaciones IoT utilizando agentes y líneas de productos de software en sistemas de autogestión.




En **[^88]** se presentan experimentos para validar la programación de robots autónomos utilizando Jadescript. Presenta el novedoso soporte para manejadores de percepción que se ha introducido recientemente en el lenguaje para hacer frente a la alta tasa de datos de los sensores en aplicaciones robóticas.




#   5. Discusión y Direcciones Futuras




Como hemos mostrado, existe una amplia variedad de opciones para la programación basada en agentes, desde los enfoques más tradicionales (por ejemplo, BDI) hasta la simulación o la planificación. Algunos lenguajes también han intentado combinar conceptos de la programación basada en agentes con otros paradigmas de programación, sobre todo de la programación orientada a objetos. Uno de los principales inconvenientes de tratar de lograr una comunidad más amplia de programadores en programación basada en agentes es la falta de conocimiento y familiaridad con sus conceptos, que son significativamente diferentes de otros paradigmas más comunes. Los lenguajes de programación basados ​​en agentes que usan algunos de los conceptos de estos otros paradigmas pueden ayudar a traer nuevos programadores que de otro modo se sentirían demasiado intimidados. Estos lenguajes híbridos tienen su propio nicho de aplicaciones según los conceptos que utilizan, que a veces pueden superponerse con los lenguajes de programación de agentes más "puros", pero los enfoques "puros" aún son necesarios para abordar completamente todas las abstracciones de programación de agentes (agente, entorno). , organización, interacción, etc.).





De los 15 lenguajes de programación de agentes enumerados en la Tabla 1, cinco no tienen una implementación disponible públicamente (es decir, el código no está alojado en un dominio público/accesible). Esto representa un problema importante, ya que limita la usabilidad práctica del lenguaje propuesto y dificulta la comparación cuantitativa con otros lenguajes. No todas las extensiones a idiomas existentes requieren una implementación para ser útiles, sin embargo, tener una disponible siempre es positivo para la comunidad.




Aunque hay varias comparaciones cualitativas (por ejemplo, conceptos, características) en la literatura, el uso de diferentes modelos de agencia dificulta proporcionar una comparación justa entre las características presentes en estos idiomas. Se debe realizar un estudio más profundo para identificar las características fundamentales de la programación orientada a agentes y, lo que es más importante, cómo encajan estas características en los diferentes modelos de agencia que utilizan los lenguajes de programación existentes.




Las comparaciones cuantitativas (p. ej., rendimiento) de los lenguajes de programación son más complicadas debido al ciclo de desarrollo de tener actualizaciones constantes, lo que es aún más común en los lenguajes de programación desarrollados en la academia (como lo son la mayoría de los lenguajes de programación de agentes). Sin embargo, es importante desarrollar puntos de referencia específicos de agentes que la comunidad pueda usar fácilmente para evaluar nuevos lenguajes de programación o extensiones de lenguajes existentes.




La mayoría de los idiomas ofrecen una variedad de ejemplos diferentes que muestran sus características y fortalezas. Si bien estos ejemplos son ciertamente útiles para comprender y aprender mejor el lenguaje, por lo general no son suficientes para convencer a los nuevos usuarios de la aplicabilidad del lenguaje en aplicaciones del mundo real. Es difícil desarrollar estudios de casos complejos y realistas, pero la comunidad de agentes tiene disponible un conjunto de escenarios complejos como parte del MAPC anual que podría aprovecharse mejor para probar y comparar lenguajes de programación de agentes.




Dos encuestas recientes **[^3]**,**[^5]** centradas en la programación de agentes BDI describen las limitaciones y desafíos en el área. En un manifiesto **[^3]**, el autor argumenta que es necesario ampliar el conjunto de funciones de las APL actuales para permitir una adopción más amplia de la tecnología de agentes. El autor tampoco está de acuerdo con encuestas anteriores en que la falta de metodologías y herramientas más pulidas no es el factor principal (aunque contribuye) en la adopción limitada de APL; en cambio, el autor sugiere que hay poco o ningún incentivo para que los desarrolladores realicen el cambio a AOP, ya que los comportamientos que se muestran actualmente en las aplicaciones de la literatura se pueden implementar en lenguajes más convencionales con un esfuerzo limitado. La encuesta en **[^5]** resume la historia hasta el momento y el estado del arte en la programación de agentes con un enfoque en los enfoques basados ​​en BDI. Identifican como un gran desafío para futuras investigaciones la integración de técnicas de IA en agentes lenguajes de programación como un paso importante y necesario para la amplia aceptación y adopción de AOP.




_Recomendación para futuras investigaciones_




Teniendo en cuenta los últimos 5 años de investigación sobre APL, se han propuesto muchos marcos, plataformas y modelos novedosos. Cada uno de estos, junto con nuevas extensiones, enriqueció la literatura basada en agentes y amplió el espectro de posibles aplicaciones. Sin embargo, como se observa correctamente en **[^3]**,**[^5]**, el principal problema de las APL actuales no está en su conjunto de características, sino en su usabilidad. Generalmente, no hay deseo de aprender nuevos idiomas cuando las ventajas no son sencillas. En nuestra revisión, analizamos APL que eran a la vez expresivos y potentes, pero con importantes problemas de usabilidad; como la ausencia de una herramienta (mantenida), documentación y comparaciones cualitativas y cuantitativas con otros idiomas. En nuestra opinión, la investigación adicional sobre APL tendrá que abordar estos problemas de usabilidad para tratar de difundir el uso de APL fuera de la comunidad de agentes.







#   6. Conclusiones




La programación basada en agentes es un área de investigación próspera de la inteligencia artificial. En este artículo de revisión, hemos clasificado tanto las contribuciones veteranas como las recientes según cuatro categorías diferentes: lenguajes de programación basados ​​en agentes, sus extensiones, las comparaciones entre lenguajes y, por último, algunas de las aplicaciones que utilizan estos lenguajes. Para cada contribución, revisamos brevemente el contenido y esbozamos los resultados clave. Para comprender mejor el estado actual del arte, no solo nos enfocamos en los últimos enfoques, sino que también revisamos brevemente los lenguajes de programación basados ​​en agentes más destacados que aún se mantienen.




Cada año hay muchas extensiones a los lenguajes existentes e incluso se proponen lenguajes completamente nuevos, sin embargo, la mayoría de ellos se limitan a descripciones formales sin ninguna implementación para respaldar la teoría formal. El pequeño subconjunto de enfoques con implementación carece de una evaluación efectiva. La comparación de nuevos enfoques con el estado del arte es uno de los principales pasos necesarios para avanzar en el área de la programación basada en agentes. Las comparaciones cualitativas y cuantitativas pueden ayudar a identificar brechas en los lenguajes existentes, lo que puede conducir a mejoras o nuevos enfoques que puedan hacer frente a los desafíos planteados. Además, en nuestra revisión también hemos identificado una falta de aplicaciones del mundo real. Para ampliar el uso de estos lenguajes, es importante que su usabilidad en el mundo real esté bien documentada, por lo tanto, alentamos y recomendamos más artículos basados ​​en aplicaciones que puedan demostrar las características de la programación basada en agentes en el mundo real. .



>   **Financiación**: Esta investigación fue financiada por el Industrial Strategy Challenge Fund (ISCF) del Reino Unido, proporcionada por UK Research and Innovation (UKRI) y administrada por el Engineering and Physical Sciences Research Council (EPSRC) en el marco de Robotics and AI for Extreme. Programa de entornos con subvenciones Robotics and AI in Nuclear (RAIN) Hub (EP/R026084/1), Future AI and Robotics for Space (FAIR-SPACE) Hub (EP/R026092/1) y Offshore Robotics for Certification of Assets (ORCA ) Buje (EP/R026173/1).




>  **Conflictos de interés**: Los autores declaran no tener ningún conflicto de interés. Los financiadores no tuvieron ningún papel en el diseño del estudio; en la recopilación, análisis o interpretación de datos; en la redacción del manuscrito, o en la decisión de publicar los resultados.


















































































































#  Abreviaturas



Se han utilizado las siguientes abreviaturas en el manuscrito:

| Acron.  | Concept    |     Concepto  | 
|  :---:     |  :---    |   :---  |  
|  AI  |  Artificial Intelligence  |  Inteligencia artificial  | 
|  AOP  |  Agent-Oriented Programming  |  Programación Orientada al Agente
|  AOSE  |  Agent-Oriented Software Engineering  |  Ingeniería de Software Orientada al Agente
|  APL  |  Agent Programming Language  |  Lenguaje de programación del agente
|  BDI  |  Belief-Desire-Intention  |  Creencia-Deseo-Intención
|  CPS  |  Cyber-Physical Systems  |  Sistemas ciberfísicos
|  DSL  |  Domain Specific Language  |  Lenguaje específico de dominio
|  HTN  |  Hierarchical Task Network  |  Red jerárquica de tareas
|  Iot  |  Internet of Things  |  Internet de las Cosas
|  MAPC  |  Multi-Agent Programming Contest  |  Concurso Programación Multiagente
|  MAS  |  Multi-Agent System  |  Sistema Multi-Agente
|  OOP  |  Object-Oriented Programming  |  Programación orientada a objetos
|  PRS  |  Procedural Reasoning System  |  Sistema de razonamiento procedimental  





#  Bibliografía


[^1]:  **[1]**. Wooldridge, M. An Introduction to MultiAgent Systems, 2nd ed.; John Wiley and Sons: Hoboken, NJ, USA, 2009; ISBN 047149691X.


[^2]:  **[2]**. Wooldridge, M.J.; Jennings, N.R. Intelligent agents: theory and practice. Knowl. Eng. Rev. 1995, 10, 115–152. [CrossRef]


[^3]:  **[3]**. Logan, B. An agent programming manifesto. Int. J. Agent-Oriented Softw. Eng. 2018, 6, 187–210. [CrossRef]


[^4]:  **[4]**. Russell, S.J.; Norvig, P. Artificial Intelligence: A Modern Approach, 3rd ed.; Prentice Hall: Upper Saddle River, NJ, USA, 2010.


[^5]:  **[5]**. Bordini, R.H.; Seghrouchni, A.E.F.; Hindriks, K.V.; Logan, B.; Ricci, A. Agent programming in the cognitive era. Auton. Agents Multi Agent Syst. 2020, 34, 37. [CrossRef]


[^6]:  **[6]**. Mao, X.; Wang, Q.; Yang, S. A survey of agent-oriented programming from software engineering perspective. Web Intell. 2017, 15, 143–163. [CrossRef]


[^7]:  **[7]**. Kravari, K.; Bassiliades, N. A Survey of Agent Platforms. J. Artif. Soc. Soc. Simul. 2015, 18. [CrossRef]


[^8]:  **[8]**. Abar, S.; Theodoropoulos, G.K.; Lemarinier, P.; O’Hare, G.M.P. Agent Based Modelling and Simulation tools: A review of the state-of-art software. Comput. Sci. Rev. 2017, 24, 13–33. [CrossRef]


[^9]:  **[9]**. Isern, D.; Moreno, A. A systematic literature review of agents applied in healthcare. J. Med Syst. 2016, 40, 43. [CrossRef]


[^10]:  **[10]**. Adam, C.; Gaudou, B. BDI agents in social simulations: a survey. Knowl. Eng. Rev. 2016, 31, 207–238. [CrossRef]


[^11]:  **[11]**. Shoham, Y. Agent-oriented Programming. Artif. Intell. 1993, 60, 51–92. [CrossRef]


[^12]:  **[12]**. Georgeff, M.; Lansky, A. Procedural Knowledge. Proc. IEEE (Spec. Issue Knowl. Represent.) 1986, 74, 1383–1398. [CrossRef]


[^13]:  **[13]**. Bratman, M.E. Intentions, Plans, and Practical Reason; Center for the Study of Language and Information: Stanford, CA, USA, 1999.


[^14]:  **[14]**. Rao, A.S.; Georgeff, M. BDI Agents: From Theory to Practice. In Proceedings of the First International Conference on Multiagent Systems (ICMAS), San Francisco, CA, USA, 12–14 June 1995; pp. 312–319.


[^15]:  **[15]**. Rao, A.S. AgentSpeak(L): BDI Agents Speak Out in a Logical Computable Language. In Agents Breaking Away, Proceedings of the 7th European Workshop on Modelling Autonomous Agents in a Multi-Agent World, Eindhoven, The Netherlands, 22–25 January 1996; Lecture Notes in Computer Science; de Velde, W.V., Perram, J.W., Eds.; Springer: Berlin/Heidelberg, Germany, 1996; Volume 1038, pp. 42–55. [CrossRef]


[^16]:  **[16]**. McCarthy, J.; Hayes, P.J. Some Philosophical Problems from the Standpoint of Artificial Intelligence. In Machine Intelligence 4; Meltzer, B., Michie, D., Eds.; Edinburgh University Press: Edinburgh, UK, 1969; pp. 463–502. reprinted in McC90.


[^17]:  **[17]**. Issicaba, D.; Rosa, M.A.; Prostejovsky, A.M.; Bindner, H.W. Experimental validation of BDI agents for distributed control of electric power grids. In Proceedings of the 2017 IEEE PES Innovative Smart Grid Technologies Conference Europe (ISGT-Europe), Torino, Italy, 26–29 September 2017; pp. 1–6. [CrossRef]


[^18]:  **[18]**. Sorici, A.; Boissier, O.; Picard, G.; Santi, A. Exploiting the JaCaMo Framework for Realising an Adaptive Room Governance Application. In Proceedings of the Compilation of the Co-Located Workshops on DSM’11, TMC’11, AGERE! 2011, AOOPES’11, NEAT’11, and VMIL’11; New York, NY, USA, 1–31 October 2011; pp. 239–242. [CrossRef]


[^19]:  **[19]**. Persson, C.; Picard, G.; Ramparany, F.; Boissier, O. A JaCaMo-Based Governance of Machine-to-Machine Systems. In Advances on Practical Applications of Agents and Multi-Agent Systems; Demazeau, Y., Müller, J.P., Rodríguez, J.M.C., Pérez, J.B., Eds.; Springer: Berlin/Heidelberg, Germany, 2012; pp. 161–168.


[^20]:  **[20]**. Krupa, Y.; Vercouter, L. Handling Privacy as Contextual Integrity in Decentralized Virtual Communities: The PrivaCIAS Framework. Web Intelli. Agent Syst. 2012, 10, 105–116. [CrossRef]


[^21]:  **[21]**. Collier, R.W.; Russell, S.E.; Lillis, D. Reflecting on Agent Programming with AgentSpeak(L). In Proceedings of the PRIMA 2015: Principles and Practice of Multi-Agent Systems—18th International Conference, Bertinoro, Italy, 26–30 October 2015; Lecture Notes in Computer Science; Chen, Q., Torroni, P., Villata, S., Hsu, J.Y., Omicini, A., Eds.; Springer: Cham, Switzerland, 2015; Volume 9387, pp. 351–366. [CrossRef]


[^22]:  **[22]**. Honorato-Zimmer, R.; Millar, A.J.; Plotkin, G.D.; Zardilis, A. Chromar, a language of parameterised agents. Theor. Comput. Sci. 2019, 765, 97–119. [CrossRef]


[^23]:  **[23]**. Hindriks, K.V.; de Boer, F.S.; van der Hoek, W.; Meyer, J.J.C. Agent Programming with Declarative Goals. In Proceedings of the 7th International Workshop on Agent Theories, Architectures, Boston, MA, USA, 7–9 July 2020; pp. 228–243.


[^24]:  **[24]**. Bordini, R.H.; Wooldridge, M.; Hübner, J.F. Programming Multi-Agent Systems in AgentSpeak Using Jason; John Wiley & Sons: Hoboken, NJ, USA, 2007.


[^25]:  **[25]**. Boissier, O.; Bordini, R.H.; Hübner, J.F.; Ricci, A.; Santi, A. Multi-agent oriented programming with JaCaMo. Sci. Comput. Program. 2013, 78, 747–761. [CrossRef]


[^26]:  **[26]**. Boissier, O.; Bordini, R.; Hubner, J.; Ricci, A. Multi-Agent Oriented Programming: Programming Multi-Agent Systems Using JaCaMo; Intelligent Robotics and Autonomous Agents Series; MIT Press: Cambridge, MA, USA, 2020.


[^27]:  **[27]**. Ricci, A.; Piunti, M.; Viroli, M.; Omicini, A. Environment Programming in CArtAgO. In Multi-Agent Programming: Languages, Tools and Applications; Multiagent Systems, Artificial Societies, and Simulated Organizations; Springer: Boston, MA, USA, 2009; Chapter 8, pp. 259–288. [CrossRef]


[^28]:  **[28]**. Hübner, J.F.; Sichman, J.S.; Boissier, O. Developing organised multiagent systems using the MOISE+ model: programming issues at the system and agent levels. Int. J. Agent-Oriented Softw. Eng. 2007, 1, 370–395. [CrossRef]


[^29]:  **[29]**. Dennis, L.A. Gwendolen Semantics: 2017; Technical Report ULCS-17-001; University of Liverpool, Department of Computer Science: Liverpool, UK, 2017.


[^30]:  **[30]**. Bellifemine, F.L.; Caire, G.; Greenwood, D. Developing Multi-Agent Systems with JADE (Wiley Series in Agent Technology); John Wiley & Sons: Hoboken, NJ, USA, 2007.


[^31]:  **[31]**. Bergenti, F.; Iotti, E.; Monica, S.; Poggi, A. Agent-oriented model-driven development for JADE with the JADEL programming language. Comput. Lang. Syst. Struct. 2017, 50, 142–158. [CrossRef]


[^32]:  **[32]**. Bergenti, F.; Monica, S.; Petrosino, G. A scripting language for practical agent-oriented programming. In Proceedings of the 8th ACM SIGPLAN International Workshop on Programming Based on Actors, Agents, and Decentralized Control, AGERE!@SPLASH 2018, Boston, MA, USA, 5 November 2018; pp. 62–71. [CrossRef]


[^33]:  **[33]**. Pokahr, A.; Braubach, L.; Lamersdorf, W., Jadex: A BDI Reasoning Engine. In Multi-Agent Programming: Languages, Platforms and Applications; Springer: Boston, MA, USA, 2005; pp. 149–174. [CrossRef]


[^34]:  **[34]**. Aschermann, M.; Dennisen, S.; Kraus, P.; Müller, J.P. LightJason, a Highly Scalable and Concurrent Agent Framework: Overview and Application. In Proceedings of the 17th International Conference on Autonomous Agents and MultiAgent Systems, AAMAS   2018, Stockholm, Sweden, 10–15 July 2018; pp. 1794–1796.


[^35]:  **[35]**. Hashmi, M.A.; Seghrouchni, A.E.F.; Akram, M.U. A Planning Based Agent Programming Language Supporting Environment Modeling. In Proceedings of the IEEE/WIC/ACM International Conference on Web Intelligence and Intelligent Agent Technology, WI-IAT 2015, Singapore, 6–9 December 2015; pp. 76–83. [CrossRef]


[^36]:  **[36]**. Kilaru, J. PLASA: Programming Language for Synchronous Agents. Master’s Thesis, California State University, Long Beach, CA, USA, 2018.


[^37]:  **[37]**. Flocchini, P.; Prencipe, G.; Santoro, N.; Widmayer, P. Gathering of asynchronous robots with limited visibility. Theor. Comput. Sci.   2005, 337, 147–168. [CrossRef]


[^38]:  **[38]**. Bonci, A.; Pirani, M.; Bianconi, C.; Longhi, S. RMAS: Relational Multiagent System for CPS Prototyping and Programming. In Proceedings of the 14th IEEE/ASME International Conference on Mechatronic and Embedded Systems and Applications, MESA 2018, Oulu, Finland, 2–4 July 2018; pp. 1–6. [CrossRef]


[^39]:  **[39]**. Rodriguez, S.; Gaud, N.; Galland, S. SARL: A General-Purpose Agent-Oriented Programming Language. In Proceedings of the 2014 IEEE/WIC/ACM International Joint Conferences on Web Intelligence (WI) and Intelligent Agent Technologies (IAT), Warsaw, Poland, 11–14 August 2014; Volume III, pp. 103–110; [CrossRef]


[^40]:  **[40]**. Molesini, A.; Casadei, M.; Omicini, A.; Viroli, M. Simulation in agent-oriented software engineering: The SODA case study. Sci. Comput. Program. 2013, 78, 705–714. [CrossRef]


[^41]:  **[41]**. García-Magariño, I.; Gómez-Rodríguez, A.; Moreno, J.C.G.; Navarro, G.P. PEABS: A Process for developing Efficient Agent-Based Simulators. Eng. Appl. Artif. Intell. 2015, 46, 104–112. [CrossRef]


[^42]:  **[42]**. Pavón, J.; Gómez-Sanz, J.; Fuentes-Fernández, R., The INGENIAS methodology and tools. In Agent-Oriented Methodol; IGI Global: Hershey, PA, USA, 2005; pp. 236–276. [CrossRef]


[^43]:  **[43]**. Caillou, P.; Gaudou, B.; Grignard, A.; Truong, Q.C.; Taillandier, P. A Simple-to-Use BDI Architecture for Agent-Based Mod- eling and Simulation. In Proceedings of the European Social Simulation Association 2015, Groningen, The Netherlands,   14–18 September 2015; Volume 528, pp. 15–28. [CrossRef]


[^44]:  **[44]**. Taillandier, P.; Bourgais, M.; Caillou, P.; Adam, C.; Gaudou, B. A BDI Agent Architecture for the GAMA Modeling and Simulation Platform. In Proceedings of the Multi-Agent Based Simulation XVII—International Workshop, MABS 2016, Singapore, 10 May   2016; Volume 10399, pp. 3–23. [CrossRef]


[^45]:  **[45]**. Grignard, A.; Taillandier, P.; Gaudou, B.; Vo, D.; Huynh, N.Q.; Drogoul, A. GAMA 1.6: Advancing the Art of Complex Agent- Based Modeling and Simulation. In Proceedings of the PRIMA 2013: Principles and Practice of Multi-Agent Systems—16th International Conference, Dunedin, New Zealand, 1–6 December 2013; Volume 8291, pp. 117–131. [CrossRef]


[^46]:  **[46]**. Singh, D.; Padgham, L.; Logan, B. Integrating BDI Agents with Agent-Based Simulation Platforms. Auton. Agents Multi Agent Syst. 2016, 30, 1050–1071. [CrossRef]


[^47]:  **[47]**. Belle, V.; Levesque, H.J. PREGO: An Action Language for Belief-Based Cognitive Robotics in Continuous Domains. In Proceedings of the Twenty-Eighth AAAI Conference on Artificial Intelligence, Québec City, QC, Canada, 27–31 July 2014; pp. 989–995.


[^48]:  **[48]**. Belle, V.; Levesque, H.J. ALLEGRO: Belief-Based Programming in Stochastic Dynamical Domains. In Proceedings of the Twenty-Fourth International Joint Conference on Artificial Intelligence, IJCAI 2015, Buenos Aires, Argentina, 25–31 July 2015; pp. 2762–2769.


[^49]:  **[49]**. Levesque, H.J.; Reiter, R.; Lespérance, Y.; Lin, F.; Scherl, R.B. GOLOG: A Logic Programming Language for Dynamic Domains. J. Log. Program. 1997, 31, 59–83. [CrossRef]


[^50]:  **[50]**. Ferrein, A.; Maier, C.; Mühlbacher, C.; Niemueller, T.; Steinbauer, G.; Vassos, S. Controlling Logistics Robots with the Action-Based Language YAGI. In Proceedings of the Intelligent Robotics and Applications—9th International Conference, ICIRA 2016, Tokyo, Japan, 22–24 August 2016; Volume 9834, pp. 525–537. [CrossRef]


[^51]:  **[51]**. Quigley, M.; Conley, K.; Gerkey, B.; Faust, J.; Foote, T.; Leibs, J.; Wheeler, R.; Ng, A. ROS: An open-source Robot Operating System. In Proceedings of the Workshop on Open Source Software at the International Conference on Robotics and Automation, Kobe, Japan, 12–13 May 2009; p. 5.


[^52]:  **[52]**. Kaptein, F.; Broekens, J.; Hindriks, K.V.; Neerincx, M.A. CAAF: A Cognitive Affective Agent Programming Framework. In Proceedings of the Intelligent Virtual Agents—16th International Conference, IVA 2016, Los Angeles, CA, USA, 20–23 September   2016; Volume 10011, pp. 317–330. [CrossRef]


[^53]:  **[53]**. Praça, I.; Ramos, C.; Vale, Z.; Cordeiro, M. MASCEM: A multiagent system that simulates competitive electricity markets. IEEE Intell. Syst. 2003, 18, 54–60. [CrossRef]


[^54]:  **[54]**. Santos, G.; Pinto, T.; Praça, I.; Vale, Z. MASCEM: Optimizing the performance of a multi-agent system. Energy 2016, 111, 513–524. [CrossRef]


[^55]:  **[55]**. García-Magariño, I.; Navarro, G.P.; Lacuesta, R. TABSAOND: A technique for developing agent-based simulation apps and online tools with nondeterministic decisions. Simul. Model. Pract. Theory 2017, 77, 84–107. [CrossRef]


[^56]:  **[56]**. Cich, G.; Galland, S.; Knapen, L.; Yasar, A.; Bellemans, T.; Janssens, D. Addressing the Challenges of Conservative Event Synchronization for the SARL Agent-Programming Language. In Proceedings of the Advances in Practical Applications of Cyber-Physical Multi-Agent Systems, PAAMS Collection—15th International Conference, PAAMS 2017, Porto, Portugal, 21–23 June 2017; Volume 10349, pp. 31–42. [CrossRef]


[^57]:  **[57]**. Jain, S.; Asawa, K. Programming an expressive autonomous agent. Expert Syst. Appl. 2016, 43, 131–141. [CrossRef]


[^58]:  **[58]**. Jain, S.; Asawa, K. EMIA: emotion model for intelligent agent. J. Intell. Syst. 2015, 24, 449–465. [CrossRef]


[^59]:  **[59]**. Dastani, M. 2APL: A practical agent programming language. Auton. Agents Multi-Agent Syst. 2008, 16, 214–248. [CrossRef]


[^60]:  **[60]**. Pantoja, C.E.; Stabile, M.F.; Lazarin, N.M.; Sichman, J.S. ARGO: An Extended Jason Architecture that Facilitates Embedded Robotic Agents Programming. In Proceedings of the Engineering Multi-Agent Systems—4th International Workshop, EMAS   2016, Singapore, 9–10 May 2016; Volume 10093, pp. 136–155. [CrossRef]


[^61]:  **[61]**. Leask, S.; Logan, B. Programming deliberation strategies in meta-APL. In Proceedings of the International Conference on Principles and Practice of Multi-Agent Systems, Bertinoro, Italy, 26–30 October 2015; pp. 433–448.


[^62]:  **[62]**. Doan, T.T.; Yao, Y.; Alechina, N.; Logan, B. Verifying heterogeneous multi-agent programs. In Proceedings of the International conference on Autonomous Agents and Multi-Agent Systems, AAMAS ’14, Paris, France, 5–9 May 2014; pp. 149–156.


[^63]:  **[63]**. Cardoso, R.C.; Ferrando, A.; Dennis, L.A.; Fisher, M. An Interface for Programming Verifiable Autonomous Agents in ROS. In Proceedings of the European Conference on Multi-Agent Systems (EUMAS), Thessaloniki, Greece, 14–15 September 2020.


[^64]:  **[64]**. Onyedinma, C.; Gavigan, P.; Esfandiari, B. Toward Campus Mail Delivery Using BDI. J. Sens. Actuator Netw. 2020, 9, 56. [CrossRef]


[^65]:  **[65]**. Bosello, M.; Ricci, A. From Programming Agents to Educating Agents - A Jason-Based Framework for Integrating Learning in the Development of Cognitive Agents. In Proceedings of the Engineering Multi-Agent Systems—7th International Workshop, EMAS   2019, Montreal, QC, Canada, 13–14 May 2019; Volume 12058, pp. 175–194. [CrossRef]


[^66]:  **[66]**. Cardoso, R.C.; Zatelli, M.R.; Hübner, J.F.; Bordini, R.H. Towards Benchmarking Actor- and Agent-Based Programming Languages. In Proceedings of the Workshop on Programming Based on Actors, Agents, and Decentralized Control, Indianapolis, IN, USA,   27 October 2013; pp. 115–126.


[^67]:  **[67]**. Challenger, M.; Kardas, G.; Tekinerdogan, B. A systematic approach to evaluating domain-specific modeling language environ- ments for multi-agent systems. Softw. Qual. J. 2016, 24, 755–795. [CrossRef]


[^68]:  **[68]**. Bergenti, F.; Iotti, E.; Monica, S.; Poggi, A. A Comparison between Asynchronous Backtracking Pseudocode and its JADEL Implementation. In Proceedings of the 9th International Conference on Agents and Artificial Intelligence, ICAART, Porto, Portugal, 24–26 February 2017; Volume 2, pp. 250–258. [CrossRef]


[^69]:  **[69]**. Rousset, A.; Herrmann, B.; Lang, C.; Philippe, L. A survey on parallel and distributed multi-agent systems for high performance computing simulations. Comput. Sci. Rev. 2016, 22, 27–46. [CrossRef]


[^70]:  **[70]**. Sun, Z.; Lorscheid, I.; Millington, J.D.A.; Lauf, S.; Magliocca, N.R.; Groeneveld, J.; Balbi, S.; Nolzen, H.; Müller, B.; Schulze, J.; et al. Simple or complicated agent-based models? A complicated issue. Environ. Model. Softw. 2016, 86, 56–67. [CrossRef]


[^71]:  **[71]**. Cardoso, R.C.; Krausburg, T.; Baségio, T.L.; Engelmann, D.C.; Hübner, J.F.; Bordini, R.H. SMART-JaCaMo: An organization-based team for the multi-agent programming contest. Ann. Math. Artif. Intell. 2018, 84, 75–93. [CrossRef]


[^72]:  **[72]**. Krausburg, T.; Cardoso, R.C.; Damasio, J.; Peres, V.; Farias, G.P.; Engelmann, D.C.; Hübner, J.F.; Bordini, R.H. SMART–JaCaMo: An Organisation-Based Team for the Multi-Agent Programming Contest. In The Multi-Agent Programming Contest 2018; Ahlbrecht, T., Dix, J., Fiekas, N., Eds.; Springer International Publishing: Cham, Switzerland, 2019; pp. 72–100.


[^73]:  **[73]**. Cardoso, R.C.; Ferrando, A.; Papacchini, F. LFC: Combining Autonomous Agents and Automated Planning in the Multi-Agent Programming Contest. In Multi-Agent Progamming Contest; Springer: Cham, Switzerland, 2019; pp. 31–58.


[^74]:  **[74]**. Vezina, M.; Esfandiari, B. The Requirement Gatherers’ Approach to the 2019 Multi-Agent Programming Contest Scenario. In The Multi-Agent Programming Contest 2019; Ahlbrecht, T., Dix, J., Fiekas, N., Krausburg, T., Eds.; Springer International Publishing: Cham, Switzerland, 2020; pp. 106–150.


[^75]:  **[75]**. Villadsen, J.; Bjørn, M.O.; From, A.H.; Henney, T.S.; Larsen, J.B. Multi-Agent Programming Contest 2018—The Jason-DTU Team. In The Multi-Agent Programming Contest 2018; Ahlbrecht, T., Dix, J., Fiekas, N., Eds.; Springer International Publishing: Cham, Switzerland, 2019; pp. 41–71.


[^76]:  **[76]**. Jensen, A.B.; Villadsen, J. GOAL-DTU: Development of Distributed Intelligence for the Multi-Agent Programming Contest. In The Multi-Agent Programming Contest 2019; Ahlbrecht, T., Dix, J., Fiekas, N., Krausburg, T., Eds.; Springer International Publishing: Cham, Switzerland, 2020; pp. 79–105.


[^77]:  **[77]**. Wolfram, C. An Agent-Based Model of COVID-19. Complex Syst. 2020, 29. [CrossRef]


[^78]:  **[78]**. Prudhomme, C.; Cruz, C.; Cherifi, H. An Agent based model for the transmission and control of the COVID-19 in Dijon (extended abstract). In Proceedings of MARAMI 2020—Modèles & Analyse des Réseaux: Approches Mathématiques & Informatiques—The   11th Conference on Network Modeling and Analysis, Virtual Conference, Montpellier, France, 14–15 October 2020; Volume 2750.


[^79]:  **[79]**. Khan, M.W.; Wang, J. The research on multi-agent system for microgrid control and optimization. Renew. Sustain. Energy Rev.   2017, 80, 1399–1411. [CrossRef]


[^80]:  **[80]**. Kantamneni, A.; Brown, L.E.; Parker, G.G.; Weaver, W.W. Survey of multi-agent systems for microgrid control. Eng. Appl. Artif. Intell. 2015, 45, 192–203. [CrossRef]


[^81]:  **[81]**. González-Briones, A.; De La Prieta, F.; Mohamad, M.S.; Omatu, S.; Corchado, J.M. Multi-agent systems applications in energy optimization problems: A state-of-the-art review. Energies 2018, 11, 1928. [CrossRef]


[^82]:  **[82]**. QuanLi, X.; Kun, Y.; GuiLin, W.; YuLian, Y. Agent-based modeling and simulations of land-use and land-cover change according to ant colony optimization: A case study of the Erhai Lake Basin, China. Nat. Hazards 2015, 75, 95–118. [CrossRef]


[^83]:  **[83]**. North, M.; Collier, N.; Ozik, J.; Tatara, E.; Macal, C.; Bragen, M.; Sydelko, P. Complex Adaptive Systems Modeling with Repast Simphony. Complex Adapt. Syst. Model. 2013, 1, 1–26. [CrossRef]


[^84]:  **[84]**. Castilla-Rho, J.C.; Mariethoz, G.; Rojas-Mujica, R.; Andersen, M.S.; Kelly, B.F.J. An agent-based platform for simulating complex human-aquifer interactions in managed groundwater systems. Environ. Model. Softw. 2015, 73, 305–323. [CrossRef]


[^85]:  **[85]**. Savaglio, C.; Fortino, G.; Ganzha, M.; Paprzycki, M.; Badica, C.; Ivanovic, M. Agent-Based Computing in the Internet of Things: A Survey. In Proceedings of the Intelligent Distributed Computing XI—11th International Symposium on Intelligent Distributed Computing—IDC 2017, Belgrade, Serbia, 11–13 October 2017; Volume 737, pp. 307–320. [CrossRef]


[^86]:  **[86]**. Krivic, P.; Skocir, P.; Kusek, M.; Jezic, G. Microservices as Agents in IoT Systems. In Proceedings of the Agent and Multi-Agent Systems: Technology and Applications, 11th KES International Conference, KES-AMSTA 2017, Vilamoura, Algarve, Portugal, 21–23 June 2017; Volume 74, pp. 22–31. [CrossRef]


[^87]:  **[87]**. Ayala, I.; Amor, M.; Fuentes, L.; Troya, J.M. A Software Product Line Process to Develop Agents for the IoT. Sensors 2015, 15, 15640–15660. [CrossRef]


[^88]:  **[88]**. Iotti, E.; Petrosino, G.; Monica, S.; Bergenti, F. Exploratory Experiments on Programming Autonomous Robots in Jadescript. In Proceedings of the First Workshop on Agents and Robots for reliable Engineered Autonomy, AREA@ECAI 2020, Virtual Event, Santiago de Compostela, Spain, 4 September 2020; Volume 319, pp. 55–67. [CrossRef]
