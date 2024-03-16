---  
layout:           project
toc:              true
author:           'JADE Team (TILAB Telecom)'
license:          'GNU Lesser General Public License v2.1'
ref:              jade-platform
lang:             es
date:             '2022-12-19'
modified:         '2024-03-10'
status:           'Finalizado'
title:            'JADE-4.6.1 con imágenes Maven de Docker'
subtitle:         'Archivos `pom.xml` específicos para compilar `jade-platform-4.6.1.jar` con las últimas imágenes de Maven'
headtitle:        'Compilación y unificación de librerías utilizadas por JADE 4.6.1 (11/07/2023), reorganización de la estructura de directorios en el modelo MAVEN y preparación de archivos `pom.xml` y `pom8.xml` para obtener la versión funcional de JADE Platform con contenedores Docker..'
imagepath:        'images/jade-fipa/'
images:  
  -  'jade-rotated.png'
  -  'jade.png'
  -  'fipa.png'



---



Control de citas: [^1], [^2], [^3], [^4].



  

##   Sección 1: Identificación
-  Propone: _FJ Aguayo_.
-  Fecha de propuesta: Enero 2023.
-  Ubicación de resultados: GitHub Repo.

##   Sección 2: Descripción de la propuesta
-  Incorporar el modelo Maven al código fuente más reciente disponible de la Plataforma JADE.
-  Preparar archivos POM.XML de Maven y Scripts necesarios para realizar la compilación de JADE sobre contenedores oficiales de Maven en Docker Hub.

###  2.1. Resumen

  Para mejorar la seguridad y restringir al mínimo las vulnerabilidades generadas por el proceso de compilación, se propone este proyecto de mantenimiento de generación de la librería jade.jar. Actualmente esa librería se construye con Apache Ant, tal y como propone el Equipo JADE. Esta propuesta, entregará archivos POM.xml de Maven, para obtener las veriones de la misma librería pero, compilados con última versión oficial de las imágenes en Docker Hub aportadas por Apache Maven. Y de esa manera, obtener un mecanismo fiable de generación de imágenes para contenedores con las librerías: dpsAgents, dpsFramework, CLIPSJNI, Prolog JPL y Jess en versiones Java 8 ó JDK17.  
  

###  2.2. Plataforma de destino
-  Inicialmente esta propuesta se realizó para utilizar Java JDK 17 ó  OpenJDK-17 o superior. 
  
-  Se amplía ese objetivo inicial. En esta revisión, se utilizan las imágenes necesarias de Maven en Docker Hub, para obtener la librería de la Plataforma JADE adecuada a cada Arquitectura y versión de JDK exigidas por cada aplicación y despliegue concreto.




###  2.3. ¿Qué necesita la propuesta de actualización?
-  Acceso al código de la Plataforma JADE. Se encuentra en: <https://jade.tilab.com/svn/jade/trunk/>
-  Un entorno de desarrollo. Se ha empleado Eclipse 2021-12. En esta revisión se ha utilizado Eclipse 2023-12.
-  Una recopilación pormenorizada de los errores que ofrece el compilador OpenJDK-17/ Java JDK-17; su corrección progresiva; la incorporación del Sistema de Módulos de la Plataforma Java para permitir la integración posterior de JADE con su módulo FIPA bajo el sistema de módulos de Java.


###  2.4. ¿Por qué esta propuesta?
-  Porque la evolución del compilador Java, ha eliminado del núcleo de Java, las librerías de CORBA. 
-  Porque es necesario contar con un proceso fiable y repetible de la generación de JADE.jar sobre un primer contenedor dedicado a su compilacón, que permitirá que se integre en la imagen Docker para la arquitectura específica donde se ejecute frente a CLIPS-JNI, Prolog JPL y Jess, BeanShell, etc. Utilizadas por dpsAgents y dpsFramework






###  2.5. Tecnología o tecnologías subyacentes:
-  OpenJDK-9 a OpenJDK18.
-  Oracle Java 8 hasta Oracle Java JDK-18.
-  GlassFish CORBA ORB 2.4
-  Apache-Commoms 1.3
-Docker
-Maven
-Imágenes: maven:3.8.3-openjdk-17;  maven:3.3-jdk-8; maven:3.9.6-amazoncorretto-17-al2023; y maven:3.9.6-ibmjava-8





###  2.6. ¿Nombre del paquete para la propuesta de API?
-  Archivo: **jade-platform-4.6.1.jar**
-  Paquete: **jade**













###  2.7. Dependencias en sistemas operativos específicos
-  Las correspondientes a la versión y arquitectura del compilador de Java.












###  2.8. Cuestiones de seguridad por el modelo de seguridad actual
-  Delegadas en el ánalisis de vulnerabilidad ofrecido por la imagen oficial de Maven en Docker Hub.














###  2.9. ¿Problemas de internacionalización o localización?
-  No se han implementado.















###  2.10. ¿Alguna necesidad de revisión como resultado de este trabajo?
-  No se ha previsto. A la espera de revisión.
















###  2.11. Cronograma para el desarrollo de esta propuesta
-   Inicio: **Diciembre de 2022**
-   Final: **Enero de 2023**
- Revisado: **Marzo de 2024**















##   Sección 3: Contribuciones




###  3.1. Documentos, propuestas o implementaciones que describen la tecnología.















###  3.2. Punto de partida de la obra.
-   JADE-4.6.0 Revisión 6871.
- JADE-4.6.1 Revisión 6874.


















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
  
#   Bibliografía

[^1]:  **[1]**. Project results in: _JADE Platform compiled with Maven in Docker images_. 2024. Site: [https://github.com/dpsframework/jade-platform](https://github.com/dpsframework/jade-platform). 

[^2]:  **[2]**. Apache Maven Project: UTF-8 and other POM file specifications. Site: [https://maven.apache.org/plugins/maven-resources-plugin/examples/encoding.html](https://maven.apache.org/plugins/maven-resources-plugin/examples/encoding.html).


[^3]:  **[3]**. Maven images in Docker Hub. 2024. Site: <code>https://hub.docker.com/_/maven</code>.

[^4]:  **[4]**. Apache Maven Compiler Plugin. 2024. Site: [https://maven.apache.org/plugins/maven-compiler-plugin/](https://maven.apache.org/plugins/maven-compiler-plugin/).