---
layout:  proposal
toc:  true
author:  'Gary Riley'
license:  'GNU Lesser General Public License v2.1'
ref:  p41-clipsjni-640
lang:  es
date:  '2021-05-14'
modified:  '2022-08-24'
status:  'En curso: comprobaciones finales'
title:  'Propuesta: auto-localización de librería nativa para CLIPSJNI-6.40'
subtitle:  'Propuesta de actualización de CLIPS-JNI-6.40 para facilitar la detección de la arquitectura de máquina y ubicación de librería nativa en tiempo de ejecución'
headtitle:  'El componente desarrollado en Java CLIPSJNI-6.40 permite conectar Java al núcleo de CLIPS desarrollado en C++. Esta propuesta de actulización aporta una solución para detectar la arquitectura de la máquina en tiempo de ejecución, además de incorporar otras mejoras de seguridad adicionales, ajuste de declaración de variables y errores en el borrado del Router del motor CLIPS. Está evolución menor de CLIPSJNI-6.40 está orientada a los Agentes-PS de JADE. Esos agentes gestionan y ejecutan sistemas expertos, e intercambián sus hechos, reglas y conclusiones. Sin embargo, esta evolución de CLIPSJNI-6.40 puede ser útil en cualquier aplicación que requiera conectividada CLIPS 6.40 desde Java.'
imagepath:  'images/clipsjni-640/'
images:
  -  'clips.gif'
  
---

##  Lista de Tareas:
- [x]  \(1) Preparar CLIPSJNI-6.40 para ser compilado con Java SE-1.8 y con el sistemas de módulos JPMS[^migra17] de Java.
- [x]  \(2) Comprobar que después de las modificaciones, puede ser compilado con versiones de Oracle Java[^java] JDK-11 hasta JDK-17 LTS (2022-2029) y superiores. Y además, permitir compilación con versiones de OpenJDK[^openJDK] desde la openJDK-11 hasta la OpenJDK-18.
- [x]  \(3) Comprobar los 90 métodos nuevos que aporta la nueva versión de CLIPSJNI-6.40. Y su comportamiento sobre agentes de la plataforma JADE. En concreto, las modificaciones profundas realizadas en el Router.
- [x]  \(4) Incorporar archivos de secuencia de pasos de compilación para las diferentes arquitecturas.
- [x]  \(5) Realizar los Test de CLIPS 6.40 sobre una consola de Agentes tipo Nodo.
- [x]  \(6) Preparar como Repositorio GitHub para permitir su análisis y evaluación de la propuesta.
- [x]  \(7) Afinar el método deleteRouter()
- [x]  \(8) Crear y ajustar el mecanismo de selección de Librería Nativa mediante Path del JAR o mediante PATH del sistema operativo.
- [x]  \(9) Eliminación de declaraciones estáticas. Cambios en los objetos: ExternalAddressValue, InstanceAddresValue, Router, y creación del objeto Shell.








  

##   Sección 1: Identificación
-  Responsable de la propuesta: _FJ Aguayo_.
-  Fecha de la propuesta: Abril, 2022.
-  Ubicación de resultados: GitHub repo.

##   Sección 2: Procesos
-  La interfaz nativa de Java CLIPS-JNI version 6.40 para CLIPS 6.40[^1] ha sido revisada por _Gary Riley_ el pasado 2021-04-29. El código fuente está disponible en Source forge, en <https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/>.
-  Los agentes JADE[^jade] con capacidades de integrar y ejecutar Sistemas Expertos autónomos sobre la plataforma Multi-Agente, requieren conocer de antemano cuál es la arquitectura de la máquina Java y del hardware donde se ejecutan. 

###  2.1. Descripción de la propuesta:

-  Incorporar en CLIPS-JNI-6.40 un método para detectar cuál es la máquina de Java y la arquitectura hardware del nodo donde se ejecuta el sistema Multi-Agente, y de esa forma, la propia Librería CLIPSJNI de pueda asociar y enlazar con su librería nativa en C++.
-  El desarrollo de los elementos de seguridad adicionales, se realizó mediante el ajuste de la visibilidad de los Objetos fundamentales que componen la librería CLIPS-JNI-6.40

###  2.2. Plataforma de destino
-  Java JDK-11[^java] hasta JDK-18[^migra17]. OpenJDK-18[^openJDK]. CLIPS 6.40
  
-  Agentes-PS de JADE, version 2.1 o superior (2022)




###  2.3. ¿Qué necesita la propuesta de para su ejecución?
-  ECLIPSE IDE 2022-R3. 
-  CLIPS 6.40 código-fuente. CLIPS-JNI-6.40 código-fuente.
-  Agentes PS de JADE version 1.9 o superior.
-  CLIPS 6.40 test[^cool]

###  2.4. ¿Por qué esta propuesta?
-  Porque Gary D. Riley, autor de la librería, ha realizado una profunda transformación de este componente de software. Se ha multiplicado por 5 el total de métodos en el Objeto principal (Environment()). Esta modificación, ha alterado Interfaces y declaraciones, lo que hace imposible su integración con versiones, iguales o previas, de Agentes-PS 1.8.
-  Porque las mejoras en la versión CLIPS 6.40 de la Herramienta de construcción de Sistemas Expertos son muy relevantes, al igual que en la llibrería CLIPSJNI.JAR. Por ello, esta propuesta es además, un mecanismo de documentación interna y de investigación.






###  2.5. Tecnología o tecnologías subyacentes:
-  CLIPS
-  COOL
-  Java
-  Lisp








###  2.6. ¿Nombre de la librería generada?
-    clipsjni-6.40-amd32.jar --> libclipsjni-6.40-amd32.so
-    clipsjni-6.40-amd64.jar --> libclipsjni-6.40-amd64.so
-    clipsjni-6.40-x86.jar   --> clipsjni-6.40-x86.dll
-    clipsjni-6.40-x64.jar   --> clipsjni-6.40-x64.dll
-    clipsjni-6.40-osx64.jar --> libclipsjni-6.40-osx64.jnilib
-    clipsjni-6.40-arm64.jar --> libclipsjni-6.40-arm64.so









###  2.7. Dependencias en sistemas operativos específicos
-  Ninguna. Es la propia librería la que se adapta y se compila para cada sistema, JVM y arquitectura de hardware.












###  2.8. Cuestiones de seguridad por el modelo de seguridad actual
-  No se aplica en este proyecto














###  2.9. ¿Problemas de internacionalización o localización?
-  No se han implementado. Se documenta siguiendo el proceso de investigación de cada nuevo método incorporado a CLIPSJNI-6.40















###  2.10. ¿Alguna necesidad de revisión como resultado de este trabajo?
-  No se ha previsto. La propuesta y el resultado aportado, quedan en un Repositoroi de GitHub para su estudio y valoración.
















###  2.11. Cronograma para el desarrollo de esta propuesta
-   Inicio: **Abril de 2022**
-   Final: **Agosto 2022**
















##   Sección 3: Contribuciones
-    F.J. Aguayo (2022).



###  3.1. Documentos, propuestas o implementaciones que describen la tecnología.















###  3.2. Punto de partida de la obra.
-   CLIPSJNI-6.40 en Source Forge en: https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40



















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
  
  








##  _Bibliografía_

[^1]: CLIPS Rule Based Programming Language Files. Expert System Tool. Gary, Riley D. (Ed. 2022). URL: https://sourceforge.net/projects/clipsrules/.

[^java]: ORACLE Java 17 is the latest long-term support (LTS) release under Java's six-month release cadence and is the result of extensive collaboration between Oracle engineers and other members of the worldwide Java developer community via the OpenJDK Community and the Java Community Process (JCP). Verificada con la versioón jdk-17.0.3.1 (junio, 2022). https://www.oracle.com/news/announcement/oracle-releases-java-17-2021-09-14/.

[^jade]:    JADE Platform. jade - Revision 6867: /trunk. https://jade.tilab.com/svn/jade/trunk/  Login/passwod: jade/jade. Version 4.5.4 (abril, 2022).

[^migra17]: Significant Changes in JDK 17 Release. Notes for additional descriptions of the new features and enhancements, and API specification in JDK 17. Updates in Java SE 17 and JDK 17: https://docs.oracle.com/en/java/javase/17/migrate/significant-changes-jdk-release.html

[^openJDK]: OpenJDK 17 is the open-source reference implementation of version 17 of the Java SE Platform, as specified by by JSR 390 in the Java Community Process. JDK 17 reached General Availability on 14 September 2021. URL for OpenJDK-11 is: https://openjdk.java.net/projects/jdk/11/. URL for OpenJDK-17 is: https://openjdk.java.net/projects/jdk/17/.

[^cool]: COOL is the acronym for CLIPS Object Oriented Language.
