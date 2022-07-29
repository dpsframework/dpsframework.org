---
layout: proposal 

shorttitle: 'P1-FIPA-CORBA'
githubrepo: 'p1-fipa-corba'


title:     'FIPA upgrade proposal to OpenJDK-18'
headtitle: 'Proposal to upgrade FIPA and CORBA implemented by JADE 4.5.4 to Java Platform OpenJDK-18 or higher'







toc: true 

author: 'Aguayo, FJ' 
date: '2022-05-16 11:07:56:49:44 +0100' 
modified_date: '2022-07-23 12:11:56:49:44 +0100'

keywords: 
  - 'FIPA' 
  - 'ACL' 
  - 'Multi-agent Systems' 


ref: fipa2022
lang: es
categories: jade


tags: FIPA protocols ACL
metadata: '' 

--- 


> **_Resumen:_** Acceso al escenario Inicio Fin Retirado el 25 de enero de 2011 Página de descarga de revisión pública 20 de marzo de 2002 19 de mayo de 2002 Votación preliminar comunitaria Ver resultados 20 de noviembre de 2001 26 de noviembre de 2001 Página de inicio de sesión de revisión de la comunidad 16 de octubre de 2001 26 de noviembre de 2001 Formación del grupo de expertos 17 de octubre de 2000 19 de enero de 2001 Boleta de revisión de JSR Ver resultados 3 de octubre de 2000 16 de octubre de 2000 Estado: Retirado Motivo: Retirado a petición del responsable de especificaciones. Versión de JCP en uso: 2.1 Versión del acuerdo de participación de especificación de Java en uso: 1.0


<br>**_Palabras clave:_** 
{% include keywords-list.html %}




# 1. Presentación


JSR: solicitudes de especificación de Java
JSR 87: Servicios de agente de JavaTM

Acceso al escenario Inicio Fin
Retirado el 25 de enero de 2011
Página de descarga de revisión pública 20 de marzo de 2002 19 de mayo de 2002
Votación preliminar comunitaria Ver resultados 20 de noviembre de 2001 26 de noviembre de 2001
Página de inicio de sesión de revisión de la comunidad 16 de octubre de 2001 26 de noviembre de 2001
Formación del grupo de expertos 17 de octubre de 2000 19 de enero de 2001
Boleta de revisión de JSR Ver resultados 3 de octubre de 2000 16 de octubre de 2000
Estado: Retirado
Motivo: Retirado a petición del responsable de especificaciones.
Versión de JCP en uso: 2.1
Versión del acuerdo de participación de especificación de Java en uso: 1.0


Descripción:
Esta especificación define un conjunto de objetos e interfaces de servicio para soportar el despliegue y operación de agentes comunicativos autónomos.

Dirija sus comentarios sobre este JSR a los líderes de especificaciones.
Equipo

Cables de especificación
  Francis G. McCabe Fujitsu Limited
Grupo de expertos
  Fujitsu limitada Hewlett-Packard IBM
  Spydell, Andy Suguri, Hiroki Sun Microsystems, Inc.
  Tolety, Instituto de Cognición Humano-Máquina de la Universidad Siva Perraju de West Florida

Este JSR ha sido retirado
Motivo: Retirado a petición del responsable de especificaciones.

Solicitud de especificación de Java original (JSR)

Identificación | Solicitud | Contribuciones | Información Adicional

# Sección 1: Identificación
Participante que envía: Fujitsu Ltd.
Nombre de la persona de contacto: Francis G. McCabe
Dirección de correo electrónico: fgm@fla.fujitsu.com
Número de teléfono: +1 408 530 4549
Número de fax: +1 408 530 4515

Membresía inicial del grupo de expertos:

Fujitsu, Hewlett-Packard, IBM, Sun Microsystems


# Sección 2: Solicitud
## 2.1 Describa la especificación propuesta:
Esta especificación define un conjunto de objetos e interfaces de servicio para soportar el despliegue y operación de agentes comunicativos autónomos.

Se basa en la Arquitectura Abstracta desarrollada por FIPA, la Fundación para Agentes Físicos Inteligentes (ver sección 3.1). Esta Arquitectura Abstracta define cómo los agentes pueden registrarse y descubrirse unos a otros, y cómo los agentes interactúan mediante el intercambio de mensajes intencionales que se basan en la teoría de los actos de habla y la lógica de predicados de primer orden.

La especificación define dos tipos de entidades:

>  Clases de Java para objetos correspondientes a los diversos elementos de ACL (lenguaje de comunicación de agentes) y SL (lenguaje de contenido), así como nombres y descripciones de agentes FIPA.
>  Interfaces Java correspondientes a los servicios de agente para registro, descubrimiento y comunicación de agentes.

Se pretende que las interfaces de servicio puedan implementarse en términos de varias tecnologías diferentes, incluidos los estándares Java existentes y los sistemas propietarios. (A este respecto, la especificación es similar a las especificaciones anteriores, como JMS, el servicio de mensajes de Java).
## 2.2 ¿Cuál es la plataforma Java de destino? (es decir, escritorio, servidor, personal, integrado, tarjeta, etc.)
Es muy deseable que esta especificación se pueda utilizar para sistemas de agentes para una amplia gama de aplicaciones y plataformas de destino. Por lo tanto, se pretende que las especificaciones básicas se puedan utilizar en todas las plataformas Java, desde J2ME hasta J2EE. Sin embargo, es probable que algunas instancias de la especificación se basen en tecnologías Java que están restringidas a plataformas Java particulares.
## 2.3 ¿Qué necesidad de la comunidad Java abordará la especificación propuesta?
El modelo de agente comunicativo autónomo ha sido adoptado por muchos investigadores y desarrolladores de software, en áreas de aplicación tan diversas como el comercio electrónico, el control de procesos, el control del tráfico aéreo, la gestión de sistemas y el flujo de trabajo. La tasa de adopción se ha ralentizado por la falta de estándares y la falta concomitante de herramientas y sistemas de plataforma optimizados. La gran mayoría del trabajo relacionado con los agentes se realiza en Java y existe una demanda significativa de especificaciones estándar en esta área.
## 2.4 ¿Por qué las especificaciones existentes no satisfacen esta necesidad?
El lenguaje de programación Java se adapta bien al desarrollo de sistemas de agentes. Sin embargo, el rico conjunto de representaciones de datos y servicios de plataforma en Java significa que es poco probable que los sistemas de agentes desarrollados de forma independiente interoperen. Además, la falta de estándares ha inhibido el desarrollo de herramientas y componentes específicos de agentes.
## 2.5 Proporcione una breve descripción de la tecnología o tecnologías subyacentes:
La Arquitectura Abstracta de FIPA cubre dos áreas estrechamente relacionadas:

El registro y la ubicación de los agentes.


Comunicación entre agentes mediante mensajes asíncronos expresados ​​en ACL, el lenguaje de comunicación de agentes FIPA

En cada una de estas áreas, hay dos tipos de especificaciones:

- Servicios proporcionados por una plataforma de agentes: un contenedor en el que se ejecuta un agente. Estos servicios pueden implementarse usando una variedad de tecnologías subyacentes. Por ejemplo, el transporte de mensajes del agente se puede realizar mediante HTTP, IIOP o un mecanismo patentado; también puede ser proporcionado por un proveedor de Java Message Service, como IBM MQ-Series o Sun JMQ. Los diversos servicios se definen como interfaces Java, que pueden implementarsented por una variedad de diferentes plataformas de agentes.
- Objetos Java que definen descripciones de agentes, mensajes de agentes y los componentes de cada uno. Estos objetos se utilizan en todas las implementaciones de la API. Diferentes plataformas de agentes e implementaciones de servicios pueden requerir diferentes tipos de serialización. La compatibilidad con versiones anteriores de los sistemas FIPA97 requerirá el uso de IIOP como transporte de mensajes y mensajes codificados mediante una sintaxis de cadenas similar a LISP.

Al igual que en especificaciones como JMS, la API de agentes de Java no requerirá ni definirá mecanismos para la interoperabilidad entre diferentes tipos de plataforma de agentes.

En este punto, se anticipa que la especificación puede incluir los siguientes elementos:

- Clases Java para ACL (lenguaje de comunicación de agentes) basadas en FIPA-ACL
- Clases de Java para nombres de agentes
- Clases de Java para descripciones de agentes
- Interfaces Java para servicios de directorio de agentes
- Interfaces Java para acciones de Agent Messaging
- Especificación para la serialización de objetos relacionados con agentes (ACL, nombres, descripciones) de acuerdo con las especificaciones FIPA actuales
- Especificación para la serialización de objetos relacionados con agentes (ACL, nombres, descripciones) en XML
- Especificación para un esquema JNDI para descripciones de agentes
- Especificación para el mapeo del servicio Agent Messaging en términos de la especificación Java Message Service (JMS)
- Especificación para el mapeo del servicio Agent Messaging en términos de otros servicios de transporte, como IIOP y HTTP, usando servicios Java ORB

## 2.6 ¿Hay un nombre de paquete propuesto para la especificación API? (es decir, org.algo, etc.)
javax.agente
## 2.7 ¿Tiene la especificación propuesta alguna dependencia de sistemas operativos, CPU o dispositivos de E/S específicos que usted conozca?
No
## 2.8 ¿Hay algún problema de seguridad que no pueda ser abordado por el modelo de seguridad actual?
Como es probable que el modelo de seguridad JMS evolucione con J2EE Ver.2, es probable que se requiera una revisión del modelo de agente.
## 2.9 ¿Existen problemas de internacionalización o localización?
No
## 2.10 ¿Existen especificaciones que puedan quedar obsoletas, en desuso o que necesiten revisión como resultado de este trabajo?
No

## 2.11 Describa el calendario previsto para el desarrollo de esta especificación.

Inicio Septiembre 2000
Borrador comunitario julio de 2001

Los borradores públicos y finales dependerán del proceso de revisión.



# Sección 3: Contribuciones
## 3.1 Enumere los documentos, especificaciones o implementaciones existentes que describen la tecnología. Incluya enlaces a los documentos si están disponibles públicamente.
1. [FIPA00001] Arquitectura abstracta de FIPA (http://www.fipa.org/fipa00001/),
1. [FIPA00061] Especificación de parámetros FIPA ACL (http://www.fipa.org/fipa00061/),
1. Plataforma Java2, edición estándar (http://java.sun.com/j2se/1.3/index.html)
1. Plataforma Java2, Micro Edición (http://java.sun.com/j2me/index.html)
1. Java2 SDK, edición empresarial (http://java.sun.com/j2ee/overview.html)
1. Servicio de mensajes de Java (JMS) (http://java.sun.com/products/jms/index.html)
1. Servicio de nombres y directorios de Java (JNDI) (http://java.sun.com/products/jndi/index.html)
1. Lenguaje de marcado extensible (XML) (http://www.w3c.org/XML/)
## 3.2 Explicación de cómo se pueden utilizar estos elementos como punto de partida para el trabajo.
La Arquitectura Abstracta FIPA describe los servicios básicos que debe proporcionar una plataforma de agentes, así como las relaciones entre ellos. También describe el idioma de comunicación del agente y el idioma del contenido. Como su nombre lo indica, presenta estos elementos arquitectónicos como abstracciones, independientes de tecnologías particulares, codificaciones, etc. Como tal, tiene la intención explícita de ser un punto de partida para especificaciones concretas como la propuesta por este JSR.

# Sección 4: Información Adicional (Opcional)
## 4.1 Esta sección contiene cualquier información adicional que el Participante remitente desee incluir en el JSR.
Otros documentos relevantes incluyen los siguientes documentos FIPA, que se pueden encontrar en http://www.fipa.org
1. [FIPA00003] Especificación del idioma de comunicación del agente FIPA (http://www.fipa.org/fipa00003/),
1. [FIPA00007] Especificación de idiomas de contenido FIPA (http://www.fipa.org/fipa00007/),
1. [FIPA00008] Especificación de lenguaje de contenido FIPA SL (http://www.fipa.org/fipa00008/),
1. [FIPA00009] Especificación de lenguaje de contenido de FIPA CCL (http://www.fipa.org/fipa00009/),
1. [FIPA00010] Especificación de lenguaje de contenido FIPA KIF (http://www.fipa.org/fipa00010/),
1. [FIPA00011] Especificación de lenguaje de contenido FIPA RDF (http://www.fipa.org/fipa00011/),
1. [FIPA00067] Especificación del servicio de transporte de mensajes FIPA (http://www.fipa.org/fipa00067/),
1. [FIPA00068] Especificación de biblioteca de representación de mensajes FIPA ACL (http://www.fipa.org/fipa00068/),
1. [FIPA00069] Representación de mensajes FIPA ACL en especificación de codificación eficiente en bits (http://www.fipa.org/fipa00069/),
1. [FIPA00070] Representación de mensaje FIPA ACL en especificación de cadena (http://www.fipa.org/fipa00070/),
1. [FIPA00071] Representación de mensajes FIPA ACL en la especificación XML (http://www.fipa.org/fipa00071/),
1. [FIPA00072] Especificación de la biblioteca de representación de sobres de transporte de mensajes del agente FIPA (http://www.fipa.org/fipa00072/),
1. [FIPA00073] Representación de sobre de transporte de mensajes de agente FIPA en especificación de cadena (http://www.fipa.org/fipa00073/),
1. [FIPA00074] Especificación de la biblioteca del protocolo de transporte de mensajes del agente FIPA (http://www.fipa.org/fipa00074/),
1. [FIPA00075] Protocolo de transporte de mensajes del agente FIPA para la especificación IIOP (http://www.fipa.org/fipa00075/),
1. [FIPA00076] Protocolo de transporte de mensajes del agente FIPA para la especificación WAP (http://www.fipa.org/fipa00076/).