---
layout:  project
toc:  true
author:  'Ernest J. Friedman-Hill'
license:  'Sandia National Laboratories'
ref:  p49-jess-80
lang:  es
date:  '2013-08-01'
modified:  '2022-08-31'
status:  'En curso: comprobaciones finales'
title:  'Propuesta: compilación y revisión de Jess 8.0a1'
subtitle:  'Propuesta de revisión de Jess 8.0a1 para su compilación con Java 1.8 a 32bit y con OpenJDK 11 o superior a 64bits.'
headtitle:  'Jess es un motor de reglas para la plataforma Java. Para usarlo, especifique la lógica en forma de reglas usando uno de dos formatos: el lenguaje de reglas Jess (preferido) o XML. También proporciona algunos de sus propios datos para que operen las reglas. Cuando ejecuta el motor de reglas, sus reglas se llevan a cabo. Las reglas pueden crear nuevos datos o pueden hacer cualquier cosa que pueda hacer el lenguaje de programación Java.'
imagepath:  'images/jess-8/'
images:
  -  'jess.gif'
  
---

##  Lista de Tareas:
- [x]  \(1) Preparar Jess-8.0a1 para ser compilado con Java SE-1.8 y con JDK-17
- [x]  \(2) Listar reconmendaciones del compilador Java sobre el código de Jess. Documentar y organizar.
- [x]  \(3) Iniciar versiones a medida que se introduzcan cambios para adaptar el código a Java-1.6 hasta Java-11
- 
- 
- 
- 
- 
- 








  

##   Sección 1: Identificación
-  Responsable de la propuesta: _FJ Aguayo_.
-  Fecha de la propuesta: Agosto, 2022.
-  Ubicación de resultados: GitHub repo.

##   Sección 2: Procesos
-  
-  

###  2.1. Descripción de la propuesta:

-  
-  

###  2.2. Plataforma de destino
-  Java JDK-11[^java] hasta JDK-18[^migra17]. OpenJDK-18[^openJDK]. 
  
-  Agentes-PS de JADE, version 1.9 o superior (2022)




###  2.3. ¿Qué necesita la propuesta de para su ejecución?
-  ECLIPSE IDE 2022-R3. 
-  
-  Agentes PS de JADE version 1.9 o superior.
-  

###  2.4. ¿Por qué esta propuesta?
-  
-  






###  2.5. Tecnología o tecnologías subyacentes:
-  
-  
-  
-  








###  2.6. ¿Nombre de la librería generada?
-    jess-8.0b1-x86.jar
-    jess-8.0b1-x64.jar
-    
-    
-    
-    









###  2.7. Dependencias en sistemas operativos específicos
-  












###  2.8. Cuestiones de seguridad por el modelo de seguridad actual
-  














###  2.9. ¿Problemas de internacionalización o localización?
-  















###  2.10. ¿Alguna necesidad de revisión como resultado de este trabajo?
-  
















###  2.11. Cronograma para el desarrollo de esta propuesta
-   Inicio: **Agosto de 2022**
-   Final: **--**
















##   Sección 3: Contribuciones
-    



###  3.1. Documentos, propuestas o implementaciones que describen la tecnología.















###  3.2. Punto de partida de la obra.
-   



















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
  
  








##  _Bibliografía_



[^java]: ORACLE Java 17 is the latest long-term support (LTS) release under Java's six-month release cadence and is the result of extensive collaboration between Oracle engineers and other members of the worldwide Java developer community via the OpenJDK Community and the Java Community Process (JCP). Verificada con la versioón jdk-17.0.3.1 (junio, 2022). https://www.oracle.com/news/announcement/oracle-releases-java-17-2021-09-14/.

[^jade]:    JADE Platform. jade - Revision 6867: /trunk. https://jade.tilab.com/svn/jade/trunk/  Login/passwod: jade/jade. Version 4.5.4 (abril, 2022).

[^migra17]: Significant Changes in JDK 17 Release. Notes for additional descriptions of the new features and enhancements, and API specification in JDK 17. Updates in Java SE 17 and JDK 17: https://docs.oracle.com/en/java/javase/17/migrate/significant-changes-jdk-release.html

[^openJDK]: OpenJDK 17 is the open-source reference implementation of version 17 of the Java SE Platform, as specified by by JSR 390 in the Java Community Process. JDK 17 reached General Availability on 14 September 2021. URL for OpenJDK-11 is: https://openjdk.java.net/projects/jdk/11/. URL for OpenJDK-17 is: https://openjdk.java.net/projects/jdk/17/.


