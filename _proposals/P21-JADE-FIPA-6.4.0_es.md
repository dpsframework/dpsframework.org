---
layout:  proposal
toc:  true
author:  'TILAB Telecom'
license:  'GNU Lesser General Public License v2.1'
ref:  p21-jade-fipa-4.6.0
lang:  es
date:  '2022-12-19'
modified:  '2023-01-14'
status:  'Finalizado'
title:  'Compilación de JADE-6.4.0 (revisión de Diciembre de 2022) con JDK-17LTS'
subtitle:  'Propuesta de compilación de JADE-4.6.0-r6871 con JDK-17LTS o versiones posteriores de Java.'
headtitle:  'Unificación de las librerías usadas por el núcleo de JADE 4.6.0: Esta es una propuesta para actualizar el mecanismo de compilación con OpenJDK-11 a 18 o superior. '
imagepath:  'images/jade-fipa/'
images:  
  -  'jade-rotated.png'
  -  'jade.png'
  -  'fipa.png'


---







  

##   Sección 1: Identificación
-  Responsable de la propuesta: _FJ Aguayo_.
-  Fecha de la propuesta: Enero 2023.
-  Ubicación de resultados: GitHub repo.

##   Sección 2: Descripción de la propuesta
-  Compilador OpenJDK-11 a OpenJDK-18.
-  Se utiliza Revision 6871 de JADE versión 4.6.0 de, 19 de Diciembre de 2022

###  2.1. Resumen

-  
-  

###  2.2. Plataforma de destino
-  Java SE 17, OpenJDK-17 o superior, Java JDK-17 o superior. Esto implica que podrá ser utilizado en entornos de Escritorio o de Servidor, con arquitecturas y sistemas operativos distintos.
  
-  El objetivo final es su integración en JADE 4.6.0, y permanecer a las espera de una futura revisión de JADE para JAVA 11 o superior.




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
-  Archivo: **jade-4.6.0.jar**
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
-   Inicio: **Diciembre de 2022**
-   Final: **Enero de 2023**
















##   Sección 3: Contribuciones




###  3.1. Documentos, propuestas o implementaciones que describen la tecnología.















###  3.2. Punto de partida de la obra.
-   JADE-4.6.0 Revisión 6871.



















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
  