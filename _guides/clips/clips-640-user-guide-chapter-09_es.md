---
layout: guide
lang:   es
ref:    c640ug09

manualcode: c640ug

title:      'CLIPS 6.4 Guía de Usuario'
headtitle:  'Mensajes significativos'
shorttitle: 'Giarratano, J.C. (2021)'

toc:    true
author: 'Dr. Giarratano, Joseph C.'
date:   '2021-04-09 03:17:40:49:44 +0100'

keywords:
  - 'CLIPS'
  - 'COOL'

chapter: 9
---




![image](images/clips-user-guide-JC-Giarratano-Banner.jpg){:width="200px"  border="0px" } 
![image](images/clips_logo.jpg){:width="128px"  border="0px" } 


# Capítulo 9: Mensajes significativos



## 9.1. Los pájaros y las abejas





> Siempre es mejor complacer a tus superiores que a tus subordinados.<br>
  — Bowen

En este capítulo aprenderá más sobre clases y objetos llamados instancias. Verá cómo especificar los atributos de las clases usando campos y cómo enviar mensajes a los objetos.



En el Capítulo 1 aprendiste las ideas básicas de la herencia. La razón por la que la herencia es tan importante en OOP es que la herencia permite la fácil construcción de software personalizado. Por software personalizado, no queremos decir que el software se crea desde cero. Más bien, es como utilizar un artefacto producido en masa y adaptarlo para un cometido especial. El artefacto producido en masa puede considerarse un producto de una fábrica de software que produce de forma rápida, económica y confiable artefactos de un tipo general que están destinados a personalizarse fácilmente.


El corazón del paradigma OOP es la creación de una jerarquía de clases para producir software de manera rápida, fácil y confiable. Generalmente, este software es una modificación del software existente para que los programadores no estén siempre "reinventando la rueda".


Aunque en el pasado, la gente ha tratado de proporcionar código reutilizable a través de mecanismos tales como bibliotecas de subrutinas, el paradigma OOP puro en lenguajes como Smalltalk, lleva el concepto de código reutilizable a su conclusión lógica al intentar construir todo el software en un sistema como de código reutilizable. En Smalltalk, todo es un objeto, incluso las clases. En CLIPS, las instancias de los tipos primitivos como NUMBER, SYMBOL, STRING, etc., así como las instancias definidas por el usuario, son objetos. Las clases no son objetos en CLIPS. Por ejemplo, el NUMBER 1, el SYMBOL Pato, la STRING "Pato" y la instancia definida por el usuario Pato son todos objetos.


El paradigma OOP es bastante diferente del enfoque de la biblioteca de subrutinas en el que se pueden usar o no fragmentos de código de subrutina según el capricho del programador. El paradigma OOP fomenta y admite el código modular, los controladores de mensajes, que se pueden modificar y mantener fácilmente. Esta característica de la mantenibilidad del código está jugando un papel cada vez más importante a medida que aumentan el tamaño y el costo de los sistemas.


Una clase en OOP es como una fábrica de software que tiene la información de diseño de un objeto. En otras palabras, una clase es como una plantilla que se puede usar para producir objetos idénticos que son instancias de la clase. La analogía clásica es que una clase es como el modelo de una vaca y, se considera al objeto que produce la leche, llamado "la vaca Elsie", como la instancia.


La sintaxis general de un nombre de instancia es simplemente un símbolo entre corchetes, [ ], de la siguiente manera.


```
[<name>]
```



Los corchetes en realidad no forman parte del nombre de la instancia, que es un símbolo, como lo es Elsie. Los corchetes se usan para rodear el nombre de una instancia si existe peligro de ambigüedad al usar el nombre. Esto puede ocurrir en la función (send) y, por lo tanto, se utilizan corchetes en (send). En caso de duda, utilizar siempre los corchetes, ya que no duele.


Algunos de los diferentes tipos de objetos en CLIPS se indican en la siguiente tabla.


{:.table-left}
| Objeto   |   Clase |
|  ---  |  ---  |
| Dorky_Duck   |   SYMBOL |
| "Dorky_Duck"   |   STRING |
| 1.0   |   FLOAT |
| 1   |   INTEGER |
| (1 1.0 Dorky_Duck "Dorky_Duck")   |   MULTIFIELD |
| <Pointer: 00AB12CD>   |   EXTERNAL-ADDRESS |
| [Dorky_Duck]   |   DUCK  |





Las clases de SYMBOL, STRING, FLOAT, INTEGER y MULTIFIELD tienen los mismos nombres que aquellos con los que está familiarizado por la programación basada en reglas en CLIPS. Estos se denominan tipos de objetos primitivos porque los proporciona CLIPS y se mantienen automáticamente según sea necesario. Estos tipos primitivos se proporcionan principalmente para su uso en funciones genéricas. Dos esas clases primitivas son además, compuestas. Son NUMBER, la cual puede ser FLOAT o INTEGER, y LEXEME que puede ser un SYMBOL o una STRING. Las clases compuestas se proporcionan por conveniencia si el tipo de número o el tipo de caracteres no resulta importante.


Por el contrario, los tipos de objetos definidos por el usuario son aquellos que usted define a través de clases definidas por la programación. Si vuelve a consultar las clases CLIPS predefinidas de la Fig. 1.7 en el capítulo 1, verá que las clases primitivas y las definidas por el usuario: son las clases que corresponden con el nivel superior en CLIPS.


Dos funciones convierten un símbolo en un nombre de instancia y viceversa. El `(symbol-to-instance-name)` convierte un símbolo en un nombre de instancia, como se muestra a continuación.

```lisp
CLIPS> (clear)      ; Get rid of any old classes
CLIPS> (symbol-to-instance-name Dorky_Duck)
[Dorky_Duck]
CLIPS> (symbol-to-instance-name (sym-cat Dorky "_" Duck))
[Dorky_Duck]
CLIPS>
```



Observe cómo las funciones estándar de CLIPS como por ejemplo (sym-cat), que concatena elementos, se pueden usar con el sistema de objetos de CLIPS.

La función opuesta, `instance-name-to-symbol`, convierte un nombre de instancia en un símbolo, como muestran los siguientes ejemplos.


```lisp
CLIPS> (instance-name-to-symbol [Dorky_Duck])
Dorky_Duck
CLIPS> (str-cat (instance-name-to-symbol [Dorky_Duck]) " is a DUCK")
"Dorky_Duck is a DUCK"
CLIPS>
```










## 9.2. Pato tonto


Hay una diferencia entre la Naturaleza y la OOP. En la Naturaleza, los objetos se reproducen solo a partir de objetos similares, como los pájaros y las abejas (la gallina y el huevo son las excepciones a esta regla). Sin embargo, en OOP, las instancias solo se crean utilizando la plantilla de clase. En un OOP puro como Smalltalk, se crea una instancia de una clase específica enviando un mensaje a la clase. De hecho, el corazón de OOP implica enviar diferentes tipos de mensajes de un objeto a otro, incluso de un objeto a sí mismo.


Para ver cómo funcionan los mensajes, comencemos ingresando los siguientes comandos para crear una clase DUCK definida por el usuario y verificar que se haya incorporado. Tenga en cuenta que no se especifica ningún descriptor de función para la clase DUCK. Si una clase tiene un rol concreto, se pueden crear instancias directas de la clase. Si no se especifica el rol, CLIPS determina el rol por herencia. Para determinar el rol por herencia, las clases del sistema se comportan como clases concretas. Por lo tanto, por defecto, cualquier clase que herede de USER es una clase concreta y no necesita declararse como tal para permitir la creación de instancias directas.


Si una clase tiene un rol abstracto, no se pueden crear instancias directas de ella. Las clases abstractas se definen solo con fines de herencia. Por ejemplo, se podría definir una clase abstracta llamada PERSON cuyas propiedades como nombre, dirección, edad, altura, peso, etc., sean heredadas por las clases concretas MAN y WOMAN. Una instancia directa de MAN podría ser una persona-hombre llamada Harold, y una instancia directa de WOMAN es una persona-mujer llamada Henrietta.

```lisp
CLIPS> (defclass DUCK (is-a USER))
CLIPS> (describe-class DUCK)
================================================================
****************************************************************
Concrete: direct instances of this class can be created.
Reactive: direct instances of this class can match defrule patterns.

Direct Superclasses: USER
Inheritance Precedence: DUCK USER OBJECT
Direct Subclasses:
----------------------------------------------------------------
Recognized message-handlers:
init primary in class USER
delete primary in class USER
create primary in class USER
print primary in class USER
direct-modify primary in class USER
message-modify primary in class USER
direct-duplicate primary in class USER
message-duplicate primary in class USER
****************************************************************
================================================================
CLIPS>
```


Dado que las clases no son objetos en CLIPS, no podemos enviar un mensaje para crear un objeto. En su lugar, la función `make-instance` se utiliza para crear una instancia de objeto. La sintaxis básica es la siguiente.


```lisp
(make-instance [<instance-name>] of <class> <slot-override>)
```



Normalmente, especifica un nombre de instancia. Sin embargo, si no lo hace, CLIPS generará uno utilizando la función gensym\*. También se pueden especificar valores de campos.


Ahora que tenemos una fábrica de patos, hagamos algunas instancias de la siguiente manera, donde el nombre de la instancia está entre paréntesis. Tenga en cuenta el uso de la palabra clave "of" para separar el nombre de la instancia del nombre de la clase. Debe incluir el "of" o se producirá un error de sintaxis. Además, tenga en cuenta que los corchetes en el código significan un nombre de instancia, mientras que los corchetes en la metasintaxis, como por ejemplo cuanodo se utiliza (make-instance) anterior, significan una opción.


```lisp
CLIPS> (make-instance [Dorky] of DUCK)
[Dorky]
CLIPS> (make-instance [Elsie] of COW)
[PRNTUTIL1] Unable to find class COW.
CLIPS> (make-instance Dorky_Duck of DUCK)
[Dorky_Duck]
CLIPS> (instances)
[initial-object] of INITIAL-OBJECT
[Dorky] of DUCK
[Dorky_Duck] of DUCK
For a total of 3 instances.
CLIPS>
```



---



Una vez que la instancia se crea correctamente, CLIPS responde con el nombre de la instancia. Si no es posible crear una instancia, CLIPS responde con un FALSO. Además, al igual que los comandos (rules) y (facts), CLIPS tiene la función `instances` para imprimir las instancias de una clase. El objeto `initial-object` enumerado es similar al hecho `initial-fact`.  Se proporcionó en versiones anteriores de CLIPS para activar inicialmente algunos tipos de reglas, pero ahora solo brinda compatibilidad con versiones anteriores para programas que hacen referencia directa a él.


Para el caso de (make-instance), los corchetes alrededor del nombre de la instancia son opcionales para una clase definida por el USUARIO. Como ejemplo, creemos el primo de Dorky, Dorky_Duck, sin corchetes de la siguiente manera.




```lisp
CLIPS> (make-instance Dorky_Duck of DUCK)
[Dorky_Duck]        ; Instance Dorky_Duck is made.
CLIPS>
```



Hay dos reglas importantes sobre las instancias a tener en cuenta.


- Solo se puede utilizar una instancia del mismo nombre en un módulo.
- Una clase no se puede redefinir si existen instancias de la clase.


Por ejemplo, hagamos un clon de Dorky_Duck de la siguiente manera (es este clon malvado el que siempre mete en problemas a Dorky_Duck porque nadie puede distinguirlos. Los niños a menudo también tienen clones como este, y algunos adultos).



```lisp
CLIPS> (make-instance Dorky_Duck of DUCK)
[Dorky_Duck]
CLIPS> (instances)
[initial-object] of INITIAL-OBJECT
[Dorky] of DUCK
[Dorky_Duck] of DUCK                    ; Still only one Dorky_Duck
For a total of 3 instances.
CLIPS>
```






## 9.3. Mucho ruido y pocas nueces sobre las instancias


Si se emite un comando (reset), se eliminan todas las instancias en la memoria y se crea una instancia [initial-instance], análoga al hecho denominado: `initial-fact`.




```lisp
CLIPS> (reset)
CLIPS> (instances)
[initial-object] of INITIAL-OBJECT
For a total of 1 instance.
CLIPS>
```



Así como `(deffacts)` define plantillas de hechos, también hay `definstances` para definir instancias cuando se emite un `(reset)`. Lo siguiente `(definstances)` también ilustra el comentario opcional entre comillas dobles después del nombre de la instancia, DORKY_OBJECTS.


```lisp
CLIPS> (definstances DORKY_OBJECTS "The Dorky Cousins"
   (Dorky of DUCK)
   (Dorky_Duck of DUCK))

CLIPS> (instances)
[initial-object] of INITIAL-OBJECT
For a total of 1 instance.

CLIPS> (reset)

CLIPS> (instances)

[initial-object] of INITIAL-OBJECT
[Dorky] of DUCK
[Dorky_Duck] of DUCK
For a total of 3 instances.

CLIPS>
```




## 9.4. El pato que desaparece



Aunque un `(reset)` eliminará todas las instancias excepto [initial-instance], también creará nuevas instancias desde `(definstances)`. Si desea eliminar una instancia de forma permanente, la función `unmake instance` eliminará una o todas las instancias, según su argumento.

Para eliminar todas las instancias, utilice "\*".


Los siguientes ejemplos ilustran el comando `(unmake instance)`.

```lisp
CLIPS> (unmake-instance *)       ; Delete all instances
TRUE
CLIPS> (instances)               ; Check that all are gone
CLIPS> (reset)                   ; Create new instances again
CLIPS> (instances)               ; Check new instances created
[initial-object] of INITIAL-OBJECT
[Dorky] of DUCK
[Dorky_Duck] of DUCK
For a total of 3 instances.

CLIPS> (unmake-instance [Dorky]) ; Delete a specific instance
TRUE

CLIPS> (instances)
[initial-object] of INITIAL-OBJECT
[Dorky_Duck] of DUCK
For a total of 2 instances.

CLIPS>
```





Otra forma de eliminar una instancia específica es enviar un mensaje de eliminación. La sintaxis general de la función (send) es la siguiente.


```
   (send [<instance-name>] <message>)
```



• Solo se puede especificar un nombre de instancia en un comando y debe estar entre corchetes si es un nombre definido por el usuario.

Por ejemplo, lo siguiente hará desaparecer a Dorky_Duck.



```lisp
CLIPS> (reset)        ; Create new instances again

CLIPS> (instances)    ; Check new instances created
[initial-object] of INITIAL-OBJECT
[Dorky] of DUCK
[Dorky_Duck] of DUCK
For a total of 3 instances.

CLIPS> (send [Dorky_Duck] delete)
TRUE

CLIPS> (instances)
[initial-object] of INITIAL-OBJECT
[Dorky] of DUCK
For a total of 2 instances.

CLIPS>
```




El "\*" en un `(send)` no funcionará para eliminar todas las instancias. El "\*" solo funciona con la función (unmake). Otra alternativa es definir su propio controlador para eliminar que aceptará "\*" y, por lo tanto, le permitirá emitir mensajes con `(send [nombre de instancia] my_delete \*)`.


Un mensaje `(send)`  solo actúa sobre un objeto de destino que tiene un controlador apropiado. CLIPS proporciona automáticamente controladores para imprimir, iniciar, eliminar, etc. para cada clase definida por el usuario. Es importante darse cuenta de que el mensaje `(send [Dorky_Duck] delete)` solo funciona porque esta instancia es una clase `definida por el usuario`. Si define clases que no heredan de USER, como una subclase de INTEGER, también debe crear controladores apropiados para realizar todas las tareas deseadas, como imprimir, crear y eliminar instancias. Es mucho más fácil definir subclases de USER y aprovechar los controladores proporcionados por el sistema.












## 9.5. Que comiste en el desayuno


La función `(send)` es el corazón en la sala de operaciones de la OOP, ya que es la única forma adecuada para que los objetos se comuniquen unos con otros. De acuerdo con el principio de encapsulación de objetos, solo se debe permitir que un objeto acceda a los datos de otro objeto mediante el envío de un mensaje.


Por ejemplo, si alguien quiere saber qué desayunaste, generalmente te preguntará, es decir, te enviará un mensaje. Una alternativa descortés sería te abran la boca de un tirón y te miren por debajo de la garganta. Si no se sigue el principio de encapsulación de objetos, cualquier objeto puede jugar con las partes privadas de otros objetos, con resultados potencialmente desastrosos.


Una aplicación útil de `(send)`  es imprimir información sobre un objeto. Hasta ahora todos los ejemplos de objetos que has visto no tienen estructura. Sin embargo, así como `deftemplate` le da estructura a los hechos para obtener activaciones de las Rón de Reglas, los campos le dan estructura a un objeto. Al igual que `deftemplate`, en el caso de objetos un campo es una ubicación con nombre en el que se pueden almacenar datos. Sin embargo, a diferencia de los elementos o campos definidos por `deftemplate` para los hechos, los objetos obtienen sus campos de las clases y las clases usan la herencia. Por lo tanto, la información en los campos de objetos puede ser efectivamente heredada por objetos de subclases. Un campo no enlazado es aquel que no tiene valores asignados. Todos los campos deben estar enlazadas.


Como ejemplo simple, hagamos un objeto con campos para guardar información personal y luego enviarle mensajes. Los siguientes comandos configurarán primero el entorno CLIPS con las construcciones adecuadas. Los campos denominados `sound` y `age` inicialmente no contienen datos, es decir, valores nulos.



```lisp
CLIPS> (clear)
CLIPS> (defclass DUCK (is-a USER)
   (slot sound)
   (slot age))

CLIPS> (definstances DORK_OBJECTS
   (Dorky_Duck of DUCK))

CLIPS> (reset)

CLIPS> (send [Dorky_Duck] print)
[Dorky_Duck] of DUCK
(sound nil)
(age nil)

CLIPS> (send [Dorky_Duck] put-sound quack)
quack

CLIPS> (send [Dorky_Duck] print)
[Dorky_Duck] of DUCK
(sound quack)
(age nil)

CLIPS>
```




Observe que los campos se imprimen en el orden definido en la clase. Sin embargo, si la instancia hereda campos de más de una clase, los campos de las clases más generales se imprimirán primero.


El valor de un campo se cambia usando el mensaje `put`. De forma predeterminada, CLIPS crea un `put-handler` controlador de entrada para cada campo de una clase para manejar los mensajes de entrada. Observe el guión, "-", al final de "put-". El guión es una parte esencial de la sintaxis del mensaje, ya que separa el "put-" del nombre del campo. Solo se permite un "put-" en un (send). Por lo tanto, para cambiar varios campos o el mismo camapo en muchas instancias, debe enviar varios mensajes. En lugar de hacer esto manualmente, es posible escribir una función para hacer envíos múltiples o usar la función de modificación de instancia `modify-instance`.


El valor de un campo se puede establecer mediante una sobre-escritura de un campo `slot-override` dentro de un `make-instance` durante la creación de una instancia. Como por ejemplo:


```lisp
CLIPS> (make-instance Dixie_Duck of DUCK (sound quack) (age 2))
[Dixie_Duck]
CLIPS> (send [Dixie_Duck] print)
[Dixie_Duck] of DUCK
(sound quack)
(age 2)
CLIPS>
```






El mensaje complementario a "put-" es "get-", que obtiene los datos de un campo, como se muestra en el siguiente ejemplo. Si "put-" tiene éxito, devuelve el nuevo valor, mientras que si "get-" tiene éxito, devuelve los datos apropiados. Si "put-" o "get-" no tienen éxito, se devolverá un mensaje de error. Los siguientes ejemplos muestran cómo funciona esto.

```lisp
CLIPS> (send [Dorky_Duck] put-color white)                  ; No slot color
[MSGFUN1] No applicable primary message-handlers found for put-color.
FALSE
CLIPS> (send [Dorky_Duck] get-age)
nil
CLIPS> (send [Dorky_Duck] put-age 1) ; Value put in age
1
CLIPS> (send [Dorky_Duck] get-age) ; Check value is correct
1
CLIPS>
```








A diferencia del mensaje `put-`, el mensaje `get-` devuelve el valor de un campo. Dado que se devuelve un valor con `get-`, ese valor puede ser utilizado por otra función, asignado a una variable, y así sucesivamente. Por el contrario, un valor que se imprime no puede ser utilizado por otra función, asignado a una variable, etc., porque el valor va al dispositivo de salida estándar. Una forma de evitar este problema es imprimir en un archivo y luego leer los datos del archivo. Si bien esta no es una solución elegante, funciona. Otra forma es escribir su propio controlador de mensajes de impresión que también devuelva valores.


Un punto muy importante sobre los campos es que no pueden modificar los campos de una clase agregando campos, eliminando campos o cambiando las características de los campos. La única forma de cambiar una clase es (1) eliminar todas las instancias de la clase y (2) usar una (defclass) con el mismo nombre de clase y con los campos deseados. Esta situación es análoga a modificar una regla cargando una nueva regla con el mismo nombre.
















## 9.6. Etiqueta de clase


Ahora que ha aprendido acerca de los campos y las instancias, es hora de discutir sobre normas de Etiqueta de clases. El término etiqueta se refiere a un conjunto de pautas para hacer algo.


A diferencia de la programación de procedimientos estándar, el paradigma OOP está orientado a clases. Cada objeto está intrínsecamente relacionado con una clase, y esa clase es parte de una jerarquía de clases. En lugar de concentrarse en las acciones ante todo, el programador OOP considera la jerarquía de clases general o la arquitectura de clases, y cómo se enviarán los mensajes entre los objetos. Así, las acciones en los programas procedimentales habituales se realizan explícitamente, mientras que las acciones se realizan implícitamente en OOP. En cualquier caso, el resultado final es el mismo. Sin embargo, el sistema OOP se puede verificar, validar y mantener más fácilmente.


El uso adecuado de las clases se resume en las siguientes tres reglas.



> Reglas de Etiqueta de clases:

1. La jerarquía de clases debe estar en incrementos lógicos especializados utilizando enlaces is-a.
2. Una clase es innecesaria si solo tiene una instancia.
3. Una clase no debe tener el nombre de una instancia y viceversa.

La primera regla desaconseja la creación de una sola clase para su aplicación. Si una sola clase es adecuada, probablemente no necesite programación orientada a objetos. Al crear clases en incrementos, puede verificar, validar y mantener su código más fácilmente. Además, las jerarquías de clases incrementales se pueden colocar fácilmente en bibliotecas de clases para facilitar en gran medida la creación de código nuevo. Este concepto de bibliotecas de clases es análogo a las bibliotecas de subrutinas para acciones. Solo se pueden usar enlaces is-a, ya que esta es la única relación que admite la versión 6.31 de CLIPS.


La segunda regla fomenta la idea de que las clases están pensadas como una plantilla para producir múltiples objetos del mismo tipo. Por supuesto, puede comenzar con cero o una instancia. Sin embargo, si nunca va a necesitar más de una instancia de una clase, debería considerar modificar su superclase para acomodar la instancia en lugar de definir una nueva subclase. Si todas sus clases solo tienen una instancia, es probable que su aplicación simplemente no se adapte bien a OOP y que la codificación en un lenguaje de procedimientos sea lo mejor.


La tercera regla significa que las clases no deben tener el nombre de instancias y viceversa, para eliminar la confusión.










## 9.7. Otras características

Hay una serie de funciones de predicado útiles para los campos `(slots)`. Si usa estas funciones de predicado para probar los valores apropiados para las funciones, su programa será más robusto contra los fallos. En general, si una función no devuelve VERDADERO, devuelve FALSO.




{:.table-left}
|  Función |  Funcionalidad / Significado |
| --- | --- |
| class slot existp  | Devuelve VERDADERO si existe el campo de clase.                                            |
| slot-existp        | Devuelve VERDADERO si existe el campo de la instancia.                                      |
| slot-boundp        | Devuelve VERDADERO si el campo especificada tiene un valor.                                 |
| instance-address   | Devuelve la dirección de la máquina en la que se almacena la instancia especificada.        |
| instance-name      | Devuelve el nombre dado una dirección y viceversa.                                           |
| instancep          | Devuelve VERDADERO si su argumento es una instancia.                                         |
| instance addressp  | Devuelve VERDADERO si su argumento es una dirección de instancia.                            |
| instance-namep     | Devuelve VERDADERO si su argumento es un nombre de instancia.                                |
| instance-existp    | Devuelve VERDADERO si existe la instancia.                                                   |
| list-definstances  | Lista todas las definiciones.                                               |
| ppdefinstances     | Imprime de forma elegante la definición.                         |
| watch instances    | Le permite ver las instancias que se crean y eliminan.                                      |
| unwatch instances  | Desactiva la observación (el eco constante) de las instancias.                               |
| save-instances     | Guardar instancias en un archivo.                                          |
| load-instances     | Cargar instancias de un archivo.                                  |
| undefinstances     | Elimina la definición nombrada de una instancia.        |









Accesos [^1], [^java], [^jade], [^migra17], [^openJDK], [^cool].





## Bibliografía

[^1]: CLIPS Rule Based Programming Language Files. Expert System Tool. Gary, Riley D. (Ed. 2022). URL: https://sourceforge.net/projects/clipsrules/.

[^java]: ORACLE Java 17 is the latest long-term support (LTS) release under Java's six-month release cadence and is the result of extensive collaboration between Oracle engineers and other members of the worldwide Java developer community via the OpenJDK Community and the Java Community Process (JCP). Verificada con la versioón jdk-17.0.3.1 (junio, 2022). https://www.oracle.com/news/announcement/oracle-releases-java-17-2021-09-14/.

[^jade]:    JADE Platform. jade - Revision 6867: /trunk. https://jade.tilab.com/svn/jade/trunk/  Login/passwod: jade/jade. Version 4.5.4 (abril, 2022).

[^migra17]: Significant Changes in JDK 17 Release. Notes for additional descriptions of the new features and enhancements, and API specification in JDK 17. Updates in Java SE 17 and JDK 17: https://docs.oracle.com/en/java/javase/17/migrate/significant-changes-jdk-release.html

[^openJDK]: OpenJDK 17 is the open-source reference implementation of version 17 of the Java SE Platform, as specified by by JSR 390 in the Java Community Process. JDK 17 reached General Availability on 14 September 2021. URL for OpenJDK-11 is: https://openjdk.java.net/projects/jdk/11/. URL for OpenJDK-17 is: https://openjdk.java.net/projects/jdk/17/.

[^cool]: COOL is the acronym for CLIPS Object Oriented Language.



