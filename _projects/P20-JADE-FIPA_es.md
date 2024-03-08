---
layout:  project
toc:  true
author:  'TILAB Telecom'
license:  'GNU Lesser General Public License v2.1'
ref:  p20-jade-fipa
lang:  es
date:  '2022-07-24'
modified:  '2022-08-28'
status:  'Finalizado'
title:  'Compilación de JADE-FIPA con OpenJDK-18'
subtitle:  'Solicitud de mejora de JADE-FIPA para permitir su compilación con OpenJDK-18, JDK-17 LTS y versiones anteriores de Java.'
headtitle:  'Unificar las librerías utilizadas por el núcleo de JADE 4.5.4: esta es una propuesta para actualización del mecanismo de compilación de manera que pueda realizarse con OpenJDK-11 a 18 o superior. Y permitr la futura adopción del Java Platform Module System en el núcleo de JADE.'
imagepath:  'images/jade-fipa/'
images:  
  -  'jade-rotated.png'
  -  'jade.png'
  -  'fipa.png'



---







  

##   Sección 1: Identificación
-  Responsable de la propuesta: _FJ Aguayo_.
-  Fecha de la propuesta: Agosto 2022.
-  Ubicación de resultados: GitHub repo.

##   Sección 2: Actualización
-  Se utilizan compilador OpenJDK-11 a OpenJDK-18.
-  Se utiliza Revision 6868 de JADE versión 4.5.4 de, 17 de Julio de 2002 (por, G. Caire).

###  2.1. Descripción de la propuesta:

-  Se propone utilizar el Sistema de Módulos de Java sobre el núcleo de la plataforma JADE 4.5.4 (2022). Y conectar JADE al módulo FIPA de manera interna a través de la declaración del archivo org.tilab.jade hacia org.fipa. 
-  Una vez realizada la unificación con el módulo de FIPA con el núcleo de JADE 4.5.4 (2022), se podrá conocer el alcance de los cambios necesarios en el núcleo de JADE; conocer cuáles son las librerías necesarias adicionales requeridas por JADE 4.5.4 y permitir que JADE sea compilado con OpenJDK-17 o superior.

###  2.2. Plataforma de destino
-  Java SE 17, OpenJDK-17 o superior, Java JDK-17 o superior. Esto implica que podrá ser utilizado en entornos de Escritorio o de Servidor, con arquitecturas y sistemas operativos distintos.
  
-  El objetivo final es su integración en JADE 4.5.4, y permanecer a las espera de una futura revisión de JADE.




###  2.3. ¿Qué necesita la propuesta de actualización?
-  Acceso al código de la Plataforma JADE. Se encuentra en: <https://jade.tilab.com/svn/jade/trunk/>
-  Un entorno de desarrollo. Se ha empleado Eclipse 2021-12.
-  Una recopilación pormenorizada de los errores que ofrece el compilador OpenJDK-17/ Java JDK-17; su corrección progresiva; la incorporación del Sistema de Módulos de la Plataforma Java para permitir la integración posterior de JADE con su módulo FIPA bajo el sistema de módulos de Java.


###  2.4. ¿Por qué esta propuesta?
-  Porque la evolución del compilador Java, ha eliminado del núcleo de Java, las librerías de CORBA. 
-  Porque no es posible compilar la Plataforma JADE sobre Java OpenJDK-17. El único modo es incorporar las librerías GlassFish CORBA ORB al CLASSPATH. Exigiendo, a su vez, la distribución de JADE con estas librerías concretas.






###  2.5. Tecnología o tecnologías subyacentes:
-  OpenJDK-9 a OpenJDK18.
-  Oracle Java JDK-9 hasta Oracle Java JDK-18.
-  GlassFish CORBA ORB 2.4
-  Apache-Commoms








###  2.6. ¿Nombre del paquete para la propuesta de API?
-  Archivo: **com.tilab.jade-2002.jar**
-  Paquete: **jade**













###  2.7. Dependencias en sistemas operativos específicos
-  Las correspondientes a la versión y arquitectura del compilador de Java.












###  2.8. Cuestiones de seguridad por el modelo de seguridad actual
-  No se han analizado.














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
-   JADE Revisión 6868.



















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
  
  