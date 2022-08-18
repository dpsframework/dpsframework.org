---
layout:  proposal
toc:  true
author:  'Aguayo, FJ'
license:  'GNU Lesser General Public License v2.1'
ref:  p40-clipsjni-051
lang:  es
date:  '2022-04-27'
modified:  '2022-08-17'
status:  'En curso'
title:  'Solicitud de especificación de CLIPS JNI v0.51 (Interfaz nativa de Java)'
subtitle:  'Una modificación de CLIPS-JNI-0.51 para detectar la arquitectura de la máquina en tiempo de ejecución y opciones de seguridad adicionales.'
headtitle:  'CLIPS JNI (interfaz nativa de Java) Propuesta de especificación para la versión 0.51. Esta propuesta proporciona una modificación de CLIPS-JNI-0.51 para detectar la arquitectura de la máquina en tiempo de ejecución y otras opciones de seguridad adicionales. Esta versión proporciona una integración más estable entre los Agentes-PS de JADE con capacidad de resolución de problemas y los sistemas expertos desarrollados para la versión CLIPS 6.31 que ejecutan estos agentes.'
imagepath:  'images/clipsjni-051/'
images:
  -  'clips_logo.png'
  
---







  

##   Sección 1: Identificación
-  Responsable de la propuesta: _FJ Aguayo_.
-  Fecha de la propuesta: Abril, 2022.
-  Ubicación de resultados: GitHub repo.

##   Sección 2: Actualización propuesta
-  La interfaz nativa de Java CLIPS-JNI version 0.51 para CLIPS 6.31 ha sido revisada por _Gary Riley_ el pasado 2019-08-06, comp puede comprobarse en Source forge, en <https://sourceforge.net/projects/clipsrules/files/CLIPS/6.31/>.
-  Los agentes JADE con capacidades de integrar y ejecutar Sistemas Expertos autónomos sobre la plataforma Multi-Agente, requieren conocer de antemano cuál es la arquitectura de la máquina Java y del hardware donde se ejecutan. 

###  2.1. Descripción de la propuesta:

-  Realizar un desarrollo sobre CLIPS-JNI-0.51 para que esa interfaz detecte cuál es la máquina de Java y la arquitectura hardware de nodo donde se ejecuta el sistema Multi-Agente, y de esa forma, la propia Librería CLIPSJNI asocie y enlace con su librería nativa en C++.
-  El desarrollo de los elementos de seguridad adicionales, se realizó mediante el ajuste de la visibilidad de los Objetos fundamentales que componen la librería CLIPS-JNI-0.51

###  2.2. Plataforma de destino
-  Java JDK-11 hasta JDK-18. OpenJDK-18. CLIPS 6.31
  
-  Agentes de Resolución de Problemas de JADE, version 1.9 o superior.




###  2.3. ¿Qué necesita la propuesta de para su ejecución?
-  ECLIPSE IDE 2022. 
-  CLIPS 6.31 código-fuente. CLIPS-JNI-0.51 código-fuente.
-  Agentes PS de JADE version 1.9 o superior.


###  2.4. ¿Por qué esta propuesta?
-  Porque la librería dpsAgents-1.8-full.jar, desarrollada para JAVA 1.8, no es capaz de enlazar los sistemas expertos autónomos de los agentes JADE, con el núcleo de CLIPS 6.31, ni tampoco con CLIPS 6.40.
-  Porque el mecanismo de detección y enlace entre el Agente y CLIPS o Prolog, debe realizarse por parte de la librería nativa, en un enlace temprano, eliminando del agente la necesidad de localizar la ubicación de la Librería Nativa para OS-X, Gnu-Linux, Windows 32bits o Windows 64bits.






###  2.5. Tecnología o tecnologías subyacentes:
-  CLIPS
-  COOL
-  Java
-  Lisp








###  2.6. ¿Nombre de la librería generada?
-    clipsjni-051ps-i586.jar
-    clipsjni-051ps-amd64.jar
etc.












###  2.7. Dependencias en sistemas operativos específicos
-  Ninguna.












###  2.8. Cuestiones de seguridad por el modelo de seguridad actual
-  No se aplica en este proyecto














###  2.9. ¿Problemas de internacionalización o localización?
-  No se han implementado.















###  2.10. ¿Alguna necesidad de revisión como resultado de este trabajo?
-  No se ha previsto. A la espera de revisión.
















###  2.11. Cronograma para el desarrollo de esta propuesta
-   Inicio: **Abril de 2022**
-   Final: **Agosto 2022**
















##   Sección 3: Contribuciones




###  3.1. Documentos, propuestas o implementaciones que describen la tecnología.















###  3.2. Punto de partida de la obra.
-   CLIPSJNI-051 en Source Forge en: https://sourceforge.net/projects/clipsrules/files/CLIPS/6.31/clips_jni_051.tar.gz/download



















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
  