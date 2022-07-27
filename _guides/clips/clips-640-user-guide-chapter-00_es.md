---
layout: guide
ref:  c640ug00
lang:  es
idiom:  es-ES
imagepath:  'images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug








toc:  true


title:  "CLIPS 6.4 Guía del usuario"
headtitle:  'Léame'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Dr. Giarratano, Joseph C.'
department:  
authors:



departments:



chapter:  0
doi:  
url:  
editor:  'Gary Riley'
pubdate:  '2021'
license:  ''




ndtdate:  '2022-07-01 11:07:56:49:44 +0100'
date_published:  '2022-07-16'
date_modified:  '2022-07-16'
publisher:  'Gary Riley'

---


<h1 class="no_toc">CLIPS 6.40 Guía del usuario (2021)</h1>

>  Autor: Dr. **Joseph C. Giarratano**<br>
>  Editor: **Gary Riley**

-  CLIPS 6.40 User's Guide está disponible en _SourceForge_[^1].
-  _Traducción: Dr. **Francisco J. Aguayo**_ (Junio, 2022)



#   Tabla de contenidos
Léame<br>
1. Solo los hechos<br>
2. Siguiendo las reglas<br>
3. Agregar los detalles<br>
4. Variables con intereses<br>
5. Hacerlo con estilo<br>
6. Ser funcional<br>
7. Cómo tener el control<br>
8. Cuestiones de herencia<br>
9. Mensajes significativos<br>
10. Facetas fascinantes<br>
11. Gestionando a los Manipuladores<br>
12. Preguntas y respuestas<br>
Información de soporte<br>




#  _Léame_



>  El primer paso en el camino a la sabiduría es admitir la ignorancia. <br>El segundo paso es darse cuenta de que no tienes que contarlo al mundo.



Esta sección se llamaba anteriormente el Prefacio, pero como nadie se lo leía, le cambié el nombre por un título más convencional que los usuarios de computadoras están condicionados a obedecer. Otra sugerencia fue llamar a esto la sección No Léame, pero dado que la gente de hoy cree todo lo que lee, tenía miedo de que realmente no lo leyeran.

El propósito de un Prefacio, perdón, un Léame, es proporcionar metaconocimiento sobre el conocimiento contenido en un libro. El término **metaconocimiento** significa conocimiento sobre el conocimiento. Entonces, esta descripción del Léame es en realidad un metametaconocimiento. Si está confundido o intrigado en este punto, siga adelante y lea este libro de todos modos porque necesito todos los lectores que pueda conseguir.


##  _¿Qué es CLIPS?_

CLIPS es una herramienta de sistema experto desarrollada originalmente por Software Technology Branch (STB), NASA/Lyndon B. Johnson Space Center. Desde su primer lanzamiento en 1986, CLIPS se ha perfeccionado y mejorado continuamente. Ahora es utilizado por miles de personas en todo el mundo.

CLIPS está diseñado para facilitar el desarrollo de software para modelar el conocimiento o la experiencia humana.

Hay tres formas de representar el conocimiento en CLIPS:

-- _**Reglas**_, que están destinadas principalmente al conocimiento heurístico basado en la experiencia.

-- _**Deffunctions**_ y las  _**generic functions**_, que se destinan principalmente al conocimiento procedimental.

--  _**Programación orientada a objetos**_, también destinada principalmente al conocimiento procedimental. Se admiten las cinco características generalmente aceptadas de la programación orientada a objetos: clases, manejadores de mensajes, abstracción, encapsulación, herencia y polimorfismo. Las reglas pueden coincidir con los patrones en los objetos y frente a los hechos.
  
Puede desarrollar software usando solo reglas, solo objetos o una combinación de objetos y reglas.

  CLIPS también ha sido diseñado para la integración con otros lenguajes como C y Java. De hecho, CLIPS es un acrónimo de C Language Integrated Production System. Las reglas y los objetos también forman un sistema integrado, ya que las reglas pueden coincidir con patrones en hechos y objetos. Además de usarse como una herramienta independiente, CLIPS se puede llamar desde un lenguaje de procedimiento, realizar su función y luego devolver el control al programa que lo llamó. Asimismo, el código de procedimiento puede definirse como funciones externas y llamarse desde CLIPS. Cuando el código externo completa la ejecución, el control vuelve a CLIPS.

Si ya estás familiarizado con la programación orientada a objetos en otros lenguajes como Smalltalk, C++, Objective C o Java, conoces las ventajas de los objetos en el desarrollo de software. Si no está familiarizado con la programación orientada a objetos, encontrará que CLIPS es una excelente herramienta para aprender este nuevo concepto en el desarrollo de software.

##  _Sobre qué trata este libro_

La _Guía del usuario de CLIPS_ es un tutorial introductorio sobre las funciones básicas de CLIPS. No pretende ser una discusión exhaustiva de toda la herramienta. El volumen complementario de este libro es el _Manual de referencia de CLIPS_, que proporciona una discusión completa y exhaustiva de todos los temas de este libro y mucho más.

##  _Quién debería leer este libro_

El propósito de la _Guía del usuario de CLIPS_ es proporcionar una introducción elemental y fácil de leer a los sistemas expertos para personas con poca o ninguna experiencia con sistemas expertos.

La _Guía del usuario de CLIPS_ se puede utilizar en el aula o para el autoaprendizaje. El único requisito previo es que tenga un conocimiento básico de programación en un lenguaje de alto nivel como Java, Ada, FORTRAN, C (OK, BÁSICO si nada más, pero no lo admitiremos en público y rechazaremos esta declaración si se pregunta sobre ello).

##  _Como utilizar este libro_

La _Guía del usuario de CLIPS_ está diseñada para personas que desean una introducción rápida a la programación de sistemas expertos de manera práctica. Los ejemplos son de carácter muy general. Además, dado que aprender un nuevo idioma puede ser una experiencia frustrante, la escritura tiene un estilo ligero y humorístico (espero) en comparación con los libros de texto universitarios serios, masivos e intimidantes. Con suerte, el humor no ofenderá a nadie con sentido del humor.

Para obtener el máximo beneficio, debe escribir los programas de ejemplo en el texto a medida que lee el libro. Al escribir los ejemplos, verá cómo deberían funcionar los programas y qué mensajes de error aparecen si comete un error. El resultado de los ejemplos se muestra o describe después de cada ejemplo. Finalmente, debe leer el material correspondiente en el Manual de referencia de CLIPS a medida que cubre cada capítulo en la _Guía del usuario de CLIPS_.

Como cualquier otro lenguaje de programación, solo aprenderá a programar en CLIPS escribiendo programas en él. Para aprender realmente a programar sistemas expertos, debe elegir un problema interesante y escribirlo en CLIPS.

##  _Expresiones de gratitud_

Agradezco mucho los consejos y reseñas de este libro por parte de muchas personas. Gracias a Gary Riley, Chris Culbert, Brian Dantes, Bryan Dulock, Steven Lewis, Ann Baker, Steve Mueller, Stephen Baudendistel, Yen Huynh, Ted Leibfried, Robert Allen, Jim Wescott, Marsha Renals, Pratibha Boloor, Terry Feagin y Jack Aldridge. Un agradecimiento especial a Bob Savely por apoyar el desarrollo de CLIPS.
    
    

##  _Nota del editor_

Se han realizado cambios menores en el documento original del Dr. Giarratano para reflejar los cambios en las versiones más recientes de CLIPS --- Gary Riley.









##  _Bibliografía_

[^1]: CLIPS Rule Based Programming Language Files. Expert System Tool. Gary, Riley D. (Ed. 2022). URL: https://sourceforge.net/projects/clipsrules/. Available at: [https://altushost-swe.dl.sourceforge.net/project/clipsrules/CLIPS/6.40/clips_documentation_640.zip](https://altushost-swe.dl.sourceforge.net/project/clipsrules/CLIPS/6.40/clips_documentation_640.zip)
