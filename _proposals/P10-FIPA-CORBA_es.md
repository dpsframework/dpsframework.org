---
layout:  proposal
toc:  true
author:  'FJAC'
license:  'GNU Lesser General Public License v2.1'
ref:  p10-fipa-corba
lang:  es
date:  '2022-01-02'
modified:  '2022-06-18'
status:  'Cancelado'
title:  'Compilar FIPA con Java JDK-17'
subtitle:  'Integrar CORBA en FIPA y adaptar para compilar con OpenJDK-17'
headtitle:  'Propuesta de compilación del módulo FIPA perteneciente a JADE 4.5.4 con Java OpenJDK-17 y, su posterior adaptación al sistema de módulos de la plataforma Java, integrando las librerías de GlassFish CORBA ORB.'
imagepath:  'images/fipa-corba/'
images: 
  -  'fipa_logo__0075_.png'
  -  'logo-ieee-pes2x.png'
  -  'fipa.png'


---







  

##   Sección 1: Identificación
-  Responsable de la propuesta: FJAC
-  Fecha de la propuesta: Enero, 2022
-  Ubicación de resultados: GitHub

##   Sección 2: Actualización
-  Se utilizan compilador OpenJDK-11 a OpenJDK-18.
-  Se utiliza implementación de FIPA realizada por JADE en 2002.

###  2.1. Descripción de la propuesta:

-  Se propone extraer temporalmente el módulo FIPA del núcleo del desarrollo de la plataforma JADE. Ya que, con la versión actual de Java JDK-18 o superior, ya no es posible compilar JADE. Esto está provocado porque las librerías de CORBA han sido eliminadas del núcleo de las versiones Estándar de Java SE y de la versión de desarrollo Java JDK veriones 17 y superiores. 
-  Una vez realizada la separación FIPA del núcleo de JADE, se podrá conocer el alcance de los cambios necesarios en el módulo FIPA; conocer cuáles son las librerías necesarias de GlassFish de CORBA ORB para alcanzar una estabilidad óptima; y permitir la integración posterior del módulo FIPA con JADE compilado con OpenJDK-17 o superior.

###  2.2. Plataforma de destino
-  Java SE 17, OpenJDK-17 o superior, Java JDK-17 o superior. Esto implica que podrá ser utilizado en entornos de Escritorio o de Servidor, con arquitecturas y sistemas operativos distintos.
  
-  El objetivo final es su integración en JADE 4.5.4, y permanecer a las espera de una futura revisión de JADE.




###  2.3. ¿Qué necesita la propuesta de actualización?
-  Acceso al código del módulo FIPA de la Plataforma JADE. Se encuentra en: <https://jade.tilab.com/svn/jade/trunk/>
-  Un entorno de desarrollo. Se ha empleado Eclipse 2021-12.
-  Una recopilación pormenorizada de los errores que ofrece el compilador OpenJDK-17/ Java JDK-17; su corrección progresiva; la incorporación del Sistema de Módulos de la Plataforma Java para permitir la integración posterior de este módulo FIPA con la plataforma JADE.


###  2.4. ¿Por qué esta propuesta?
-  Porque la evolución del compilador Java, ha eliminado del núcleo de Java, las librerías de CORBA. 
-  Porque no es posible compilar la Plataforma JADE sobre Java OpenJDK-17. El único modo es incorporar las librerías GlassFish CORBA ORB al CLASSPATH. Exigiendo, a su vez, la distribución de JADE con estas librerías concretas.






###  2.5. Tecnología o tecnologías subyacentes:
-  OpenJDK-9 a OpenJDK18.
-  Oracle Java JDK-9 hasta Oracle Java JDK-18.
-  GlassFish CORBA ORB 2.4









###  2.6. ¿Nombre del paquete para la propuesta de API?
-  Archivo: **org-fipa-2002.jar**
-  Paquete: **FIPA**













###  2.7. Dependencias en sistemas operativos específicos
-  Las correspondientes a la versión y arquitectura del compilador de Java.












###  2.8. Cuestiones de seguridad por el modelo de seguridad actual
-  No se han analizado.














###  2.9. ¿Problemas de internacionalización o localización?
-  No se han implementado.















###  2.10. ¿Alguna necesidad de revisión como resultado de este trabajo?
-  No se ha previsto. A la espera de revisión.
















###  2.11. Cronograma para el desarrollo de esta propuesta
-   Inicio: **Enero de 2022**
-   Final: **Julio 2022**
















##   Sección 3: Contribuciones




###  3.1. Documentos, propuestas o implementaciones que describen la tecnología.















###  3.2. Punto de partida de la obra.
-   Módulo FIPA implementado por TILAB, dentro del desarrollo de JADE.



















##   Sección 4: Información Adicional (Opcional)












###  4.1. Información adicional a incluir en la Propuesta de Mejora
-  Otros documentos relevantes incluyen los siguientes documentos FIPA, que se pueden encontrar en http://www.fipa.org
  
1. [FIPA00003] FIPA Agent Communication Language Specification (http://www.fipa.org/fipa00003/),
1. [FIPA00007] FIPA Content Languages Specification (http://www.fipa.org/fipa00007/),
1. [FIPA00008] FIPA SL Content Language Specification (http://www.fipa.org/fipa00008/),
1. [FIPA00009] FIPA CCL Content Language Specification (http://www.fipa.org/fipa00009/),
1. [FIPA00010] FIPA KIF Content Language Specification (http://www.fipa.org/fipa00010/),
1. [FIPA00011] FIPA RDF Content Language Specification (http://www.fipa.org/fipa00011/),
1. [FIPA00067] FIPA Message Transport Service Specification (http://www.fipa.org/fipa00067/),
1. [FIPA00068] FIPA ACL Message Representation Library Specification (http://www.fipa.org/fipa00068/),
1. [FIPA00069] FIPA ACL Message Representation in Bit-efficient Encoding Specification (http://www.fipa.org/fipa00069/),
1. [FIPA00070] FIPA ACL Message Representation in String Specification (http://www.fipa.org/fipa00070 /),
1. [FIPA00071] FIPA ACL Message Representation in XML Specification (http://www.fipa.org/fipa00071/),
1. [FIPA00072] FIPA Agent Message Transport Envelope Representation Library Specification (http://www.fipa.org/fipa00072/),
1. [FIPA00073] FIPA Agent Message Transport Envelope Representation in String Specification (http://www.fipa.org/fipa00073/),
1. [FIPA00074] FIPA Agent Message Transport Protocol Library Specification (http://www.fipa.org/fipa00074/),
1. [FIPA00075] FIPA Agent Message Transport Protocol for IIOP Specification (http://www.fipa.org/fipa00075/),
1. [FIPA00076] FIPA Agent Message Transport Protocol for WAP Specification (http://www.fipa.org/fipa00076/).




 