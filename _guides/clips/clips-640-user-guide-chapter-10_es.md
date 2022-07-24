---
layout: guide 
lang:   es
ref:    c640ug10

manualcode: c640ug

title:      'CLIPS 6.4 Guía de Usuario'
headtitle:  'Propiedades fascinantes'
shorttitle: 'Giarratano, J.C. (2021)'

toc:    true 
author: 'Dr. Giarratano, Joseph C.' 
date:   '2021-04-09 03:17:40:49:44 +0100' 

keywords: 
  - 'CLIPS' 
  - 'COOL' 

chapter: 10
--- 




![image](images/clips-user-guide-JC-Giarratano-Banner.jpg){:width="200px"  border="0px" } 
![image](images/clips_logo.jpg){:width="128px"  border="0px" } 



# Capítulo 10: Propiedades fascinantes



> Si quieres tener clase, actúa, vístete y habla como tus amigos.


En este capítulo aprenderá más sobre los `campos`  y cómo especificar sus características usando propiedades. Así como los `campos` describen instancias, las propiedades describen `campos`. El uso de propiedades es una buena práctica en Ingeniería de software porque hay una mayor posibilidad de que CLIPS marque un valor como ilegal, en lugar de correr el riesgo de obtener un error de tiempo de ejecución o incluso un bloqueo. Hay muchos tipos de propiedades que se pueden usar para especificar `campos`, como se resume en la siguiente tabla.



| Nombre de  propiedad o concepto | Descripción |
| ---  | ---  |
|  default and default-dynamic           | Establecer valores iniciales para los campos |
|  cardinality                           | Número de valores del multicampo |
|  access type                           | Acceso de lectura-escritura, solo lectura, solo inicialización |
|  storage                               | Slot (campo) local en instancia o slot compartido en clase |
|  propagation                           | Heredar o no heredar campos |
|  source                                | herencia compuesta o exclusiva |
|  documentation                         | Documentación de campos |
|  override message                      | Indicar mensaje a enviar para anulación de slot |
|  create accessor                       | Crear controladores put y get |
|  visibility                            | Público o privado solo para definir la clase |
|  reactive                              | Cambia el campo por un disparador de coincidencia de patrón |






Por razones de espacio, solo describiremos algunas de la propiedades de los `campos` con más detalle en el resto de este capítulo. Para obtener más detalles, consulte el Manual de referencia de CLIPS.





## 10.1. Un slot (campo) con nombre predeterminado



La propiedad predeterminada establece el valor predeterminado de un `campo` cuando se crea o inicializa una instancia, como se muestra en el siguiente ejemplo.

```lisp
CLIPS> (clear)
CLIPS> (defclass DUCK (is-a USER)
   (slot sound (default quack))
   (slot ID)
   (slot sex (default male)))
CLIPS> (make-instance Dorky_Duck of DUCK)
[Dorky_Duck]
CLIPS> (send [Dorky_Duck] print) 
[Dorky_Duck] of DUCK
(sound quack)
(ID nil)
(sex male)
CLIPS>
```




Como puede ver, los valores predeterminados para el `campo` sexo y el `campo` sonido fueron establecidos por los valores predeterminados de las propiedades. Después de la palabra clave predeterminada puede emplearse cualquier expresión CLIPS válida que no involucre una variable.

Por ejemplo, la expresión predeterminada del `campo` de sonido es el símbolo quack. Las funciones se pueden usar en la expresión con su propiedad, como se mostrará en el siguiente ejemplo.
Esta propiedad predeterminada es estática porque el valor de su expresión de propiedad se determina cuando se define la clase y nunca cambia a menos que se redefina la clase. Por ejemplo, establezcamos el valor predeterminado de ID de `campo` en la función (gensym\*) que devuelve un nuevo valor que no está en el sistema cada vez que la llame:

```lisp
CLIPS> (clear)
CLIPS> (defclass DUCK (is-a USER)
   (slot sound (default quack))
   (slot ID (default (gensym*)))
   (slot sex (default male)))
CLIPS> (make-instance [Dorky_Duck] of DUCK) ; Dorky_Duck #1
[Dorky_Duck]
CLIPS> (send [Dorky_Duck] print)
[Dorky_Duck] of DUCK
(sound quack)
(ID gen1)
(sex male)
CLIPS> (make-instance [Dorky_Duck] of DUCK) ; Dorky_Duck #2
[Dorky_Duck]
CLIPS> (send [Dorky_Duck] print)
[Dorky_Duck] of DUCK
(sound quack)
(ID gen1)
(sex male)
CLIPS>
```





Como puede ver, la ID siempre es gen1 ya que (gensym\*) solo se evalúa una vez y no nuevamente cuando se crea la segunda instancia. Tenga en cuenta que los valores de (gensym\*) pueden ser diferentes en su computadora si ya ha llamado a (gensym\*), ya que aumenta en uno cada vez que se llama y no se restablece con (clear). La función (gensym\*) se restablece a su valor inicial solo si reinicia CLIPS.

Ahora supongamos que queremos realizar un seguimiento de las diferentes instancias de Dorky_Duck que se han creado. En lugar de usar el valor predeterminado estático `static default`, podemos usar la propiedad de la llamada dinámica predeterminada `default-dynamic` que evaluará su expresión de propiedad cada vez que se cree una nueva instancia. Note la diferencia entre el siguiente ejemplo y el anterior.


```lisp
CLIPS> (clear)
CLIPS> (defclass DUCK (is-a USER)
   (slot sound (default quack))
   (slot ID (default-dynamic (gensym*)))
   (slot sex (default male)))
CLIPS> (make-instance [Dorky_Duck] of DUCK) ; Dorky_Duck #1
[Dorky_Duck]
CLIPS> (send [Dorky_Duck] print)
[Dorky_Duck] of DUCK
(sound quack)
(ID gen2)
(sex male)
CLIPS> (make-instance [Dorky_Duck] of DUCK) ; Dorky_Duck #2
[Dorky_Duck]
CLIPS> (send [Dorky_Duck] print)
[Dorky_Duck] of DUCK
(sound quack)
(ID gen3)         ; Note ID is different from Dorky_Duck #1
(sex male)
CLIPS> 
```


En este ejemplo, que usa el valor predeterminado dinámico, el ID de la segunda instancia, gen3, es diferente de la primera instancia, gen2. Por el contrario, para el ejemplo anterior de valor predeterminado estático, los valores de ID eran los mismos, gen1, ya que (gensym\*) solo se evaluó una vez cuando se definió la clase en lugar de cada nueva instancia en el caso de valor predeterminado dinámico.


## 10.2. Propiedades cardinales


La cardinalidad de un `slot` se refiere a uno de los dos tipos de campos que puede contener un `slot`: (1) de tipo campo-único o (2) de tipo campo-múltiple. El término cardinalidad se refiere a un conteo. Un `slot` de campo único enlazado contiene solo un valor de campo, mientras que un `slot` de campo-múltiple  puede contener cero o más valores de campo. El `slot` que posee un solo campo  y el que tienen varios campos enlazada contienen cada un un valor. Sin embargo, el valor de varios campos puede tener varios campos. Por ejemplo, (a b c) es un único valor multicampo con tres campos. La cadena vacía "" es un valor de un solo campo, al igual que "a b c". Por el contrario, un `slot`unbound (vacío) no tiene valor.


Como analogía con las variables de un solo campo y de varios campos, piense en un `slot` como su buzón de correo. A veces puede encontrar una sola pieza de correo no deseado que no tiene un sobre. En cambio, se acaba de pegar una etiqueta de dirección en una hoja de papel doblada dirigida a "Residente". Otras veces puede encontrar un sobre con múltiples anuncios. La única pieza de correo no deseado sin sobre es como un valor de un solo campo, mientras que el sobre con varios anuncios es como el valor de varios campos. Si el distribuidor de correo no deseado comete un desliz y le envía un sobre sin nada dentro, esto corresponde a la variable multicampo vacía. (Ahora que lo pienso, si el sobre de correo no deseado está vacío, ¿realmente ha recibido correo no deseado?)


Una propiedad múltiple con la palabra clave multislot se utiliza para almacenar un valor de varios campos, como se muestra en el siguiente ejemplo.









```lisp
CLIPS> (clear)
CLIPS> (defclass DUCK (is-a USER)
   (multislot sound	 (default quack quack)))
CLIPS> (make-instance [Dorky_Duck] of DUCK)
[Dorky_Duck]
CLIPS> (send [Dorky_Duck] print)
[Dorky_Duck] of DUCK
(sound quack quack)
CLIPS>
```



Se puede acceder a uno de los valores de un campo múltiple con `get-` y con `put-`, como se muestra en los siguientes ejemplos, que muestran cómo realizar un seguimiento de los patos charlatanes.

```lisp
CLIPS> (send [Dorky_Duck] put-sound quack1 quack2 quack3)
(quack1 quack2 quack3)
CLIPS> (send [Dorky_Duck] get-sound)
(quack1 quack2 quack3)
CLIPS>
```



Se pueden utilizar funciones CLIPS estándar como `nth$` para obtener el campo n-ésimo de un valor de campo múltiple. El siguiente ejemplo muestra cómo elegir un cierto pato en concreto.


```lisp
CLIPS> (nth$ 1 (send [Dorky_Duck] get-sound))
quack1
CLIPS> (nth$ 2 (send [Dorky_Duck] get-sound))
quack2
CLIPS> (nth$ 3 (send [Dorky_Duck] get-sound))
quack3
CLIPS> 
```




## 10.3. Otras características


CLIPS posee algunas funciones aplicables a cada `slot` del tipo multi-campo. Se detallan en la siguiente tabla: 


| Function	| Meaning                        |
| --- | --- | 
| `slot-replace$`	| Reemplaza el rango especificado    |
| `slot-insert$`	| Inserta  el rango especificado     |
| `slot-delete$`	| Borra el rango especificado     |

A multifield slot with no values, e.g., the empty multifield value (), may be assigned to a slot with a (multiple) facet. Note that there is a difference between a slot with an empty multifield value () and an unbound slot. If you think of an empty multifield value as analogous to an empty bus, you can see there is a difference between no people (unbound slot) and a bus with no people (empty multifield value,  () ).


A create accessor facet tells CLIPS whether to create put- and get- handlers for a slot. By default, all slots have a read-write create-accessor so you don’t actually have to specify this facet to create handlers. If you define your own handlers, then you need to use ?NONE with the create-accessor facet. The other facet types for create accessor are read and write.


A storage facet defines one of two places that a slot value is stored: (1) in an instance, or (2) in the class. A slot value stored in the instance is called local because the value is only known to the instance. Thus, different instances may exist that have different local slot values. In contrast, a slot value stored in a class is called shared because it is the same for all instances of the class.


A local value is specified by the local facet, which is the default for a slot. A shared value is specified by the shared facet and all instances with this slot type will have their slot value automatically changed if one changes. An access facet defines one of three types of access for a slot, whether you use the handlers created by CLIPS or else define your own. The default type, read-write, allows you to both read and write the value of the slot. The other types are read-only and initialize-only.


Another way to set the instance values is with the initialize-instance function. An (initialize-instance) can be called at any time to reset the default values and retain values in non-(default) slots.


A (reset) can be thought of as a cold initialization since all values in non (default) slots are cleared, while a (initialize instance) can be considered a warm initialization since non-(default) values are retained. Of course, only (definstances) can be cold initialized since non-(definstances) will simply be deleted. Also, slot overrides may be used in (initialize-instance) as the last example shows.


Two predicate functions are designed for use with the access facets. Both these predicate functions return an error message if the specified slot or instance does not exist. The slot-writablep is a predicate function which returns TRUE if a slot is writable and FALSE if it is not. The slot-initablep predicate function returns TRUE if the slot is initializable and FALSE if it is not. The term initializable means that it is not read-only.

The inherit facet, which is the default, specifies that indirect instances of a class may inherit this slot from the class. As you recall, the indirect instances of a class are the instances of its subclasses, while the direct instances are those defined specifically for the class. The indirect instances of a class are direct instances of the subclasses in which they are defined. For example, [Dorky_Duck] is a direct instance of DUCK and an indirect instance of USER which is the superclass of DUCK. The no-inherit facet specifies that only a direct instance has the class slot.


It's important to realize that the (no-inherit) facet only prohibits inheritance from the class and not from its superclasses. This means that an instance may still inherit from superclasses of the (no-inherit) class.


The composite facet. facet states that facets which are not explicitly defined in the highest precedence class take their facets from the next higher precedence class. If the facet is not explicitly set in the next higher precedence class and it is composite too, CLIPS tries the next higher and so on until the facet is defined or there are no more classes. If the next higher class is not composite, CLIPS does not check further. The opposite to the composite facet is the exclusive facet, which is the default. For more information, see the CLIPS Reference Manual.


Un `slot` multicampo sin valores, por ejemplo, el valor multicampo vacío (), se puede asignar a un `slot` con una (múltiple) propiedad. Tenga en cuenta que existe una diferencia entre un `slot` con un valor de varios campos vacío () y un `slot` libre. Si piensa en un multicampo vacío como algo análogo a un autobús vacío, puede ver que hay una diferencia entre un campo vacío, o sea ninguna persona (campo vacío) y un autobús sin personas (valor de multicampo vacío, ()).


Una propiedad de acceso  en el momento de la creación del objeto, le dice a CLIPS si debe crear controladores de colocación y obtención para un campo. De forma predeterminada, todas los campos tienen un acceso de creación de lectura y escritura, por lo que en realidad no tiene que especificar esta propiedad para crear controladores. Si define sus propios controladores, entonces necesita usar ?NONE con la propiedad create-accessor. Los otros tipos de propiedads para crear un descriptor de acceso son de lectura y escritura.


Una propiedad de almacenamiento define uno de los dos lugares en los que se almacena un valor de campo: (1) en una instancia o (2) en la clase. Un valor de campo almacenado en la instancia se denomina local porque el valor solo lo conoce la instancia. Por lo tanto, pueden existir diferentes instancias que tengan diferentes valores de campos locales. Por el contrario, un valor de campo almacenado en una clase se denomina compartido porque es el mismo para todas las instancias de la clase.


La propiedad local especifica un valor local, que es el valor predeterminado para un campo. La propiedad compartida especifica un valor compartido y todas las instancias con este tipo de `slot` tendrán su valor de `slot` cambiado automáticamente si uno cambia. Una propiedad de acceso define uno de los tres tipos de acceso para un campo, ya sea que use los controladores creados por CLIPS o defina los suyos propios. El tipo predeterminado, lectura-escritura, le permite leer y escribir el valor de el campo. Los otros tipos son de solo lectura y de solo inicialización.


Otra forma de establecer los valores de instancia es con la función initialize-instance. Se puede llamar a una (instancia de inicialización) en cualquier momento para restablecer los valores predeterminados y conservar los valores en ranuras no (predeterminadas).


Un (reset) o restablecimiento, se puede considerar como una inicialización en frío, ya que se borran todos los valores en los campos que no son (predeterminadas), mientras que una (instancia de inicialización) se puede considerar una inicialización en caliente, ya que se conservan los valores que no son (predeterminados). Por supuesto, solo (definstances) se pueden inicializar en frío ya que no (definstances) simplemente se eliminarán. Además, las anulaciones de campos se pueden usar en (inicializar instancia) como muestra el último ejemplo.


Dos funciones de predicado están diseñadas para usarse con las propiedads de acceso. Ambas funciones de predicado devuelven un mensaje de error si el campo o instancia especificada no existe. slot-writablep es una función de predicado que devuelve VERDADERO si se puede escribir en un campo y FALSO si no lo es. La función de predicado slot-initablep devuelve VERDADERO si el campo es inicializable y FALSO si no lo es. El término inicializable significa que no es de solo lectura.

La propiedad de herencia, que es la predeterminada, especifica que las instancias indirectas de una clase pueden heredar este `slot` de la clase. Como recordará, las instancias indirectas de una clase son las instancias de sus subclases, mientras que las instancias directas son aquellas definidas específicamente para la clase. Las instancias indirectas de una clase son instancias directas de las subclases en las que están definidas. Por ejemplo, [Dorky_Duck] es una instancia directa de DUCK y una instancia indirecta de USER, que es la superclase de DUCK. La propiedad sin herencia especifica que solo una instancia directa tiene el `slot` de clase.


Es importante darse cuenta de que la propiedad (sin herencia) solo prohíbe la herencia de la clase y no de sus superclases. Esto significa que una instancia aún puede heredar de las superclases de la clase (sin heredar).


La propiedad compuesta. facet establece que las propiedads que no están explícitamente definidas en la clase de precedencia más alta toman sus propiedads de la siguiente clase de precedencia más alta. Si la propiedad no se establece explícitamente en la siguiente clase de precedencia superior y también es compuesta, CLIPS intenta con la siguiente clase superior y así sucesivamente hasta que se define la propiedad o no hay más clases. Si la siguiente clase superior no es compuesta, CLIPS no realiza más comprobaciones. Lo opuesto a la propiedad compuesta es la propiedad exclusiva, que es la predeterminada. Para obtener más información, consulte el Manual de referencia de CLIPS.




Accesos [^1], [^java], [^jade], [^migra17], [^openJDK], [^cool]. 





## Bibliografía

[^1]: CLIPS Rule Based Programming Language Files. Expert System Tool. Gary, Riley D. (Ed. 2022). URL: https://sourceforge.net/projects/clipsrules/.

[^java]: ORACLE Java 17 is the latest long-term support (LTS) release under Java's six-month release cadence and is the result of extensive collaboration between Oracle engineers and other members of the worldwide Java developer community via the OpenJDK Community and the Java Community Process (JCP). Verificada con la versioón jdk-17.0.3.1 (junio, 2022). https://www.oracle.com/news/announcement/oracle-releases-java-17-2021-09-14/.

[^jade]:    JADE Platform. jade - Revision 6867: /trunk. https://jade.tilab.com/svn/jade/trunk/  Login/passwod: jade/jade. Version 4.5.4 (abril, 2022).

[^migra17]: Significant Changes in JDK 17 Release. Notes for additional descriptions of the new features and enhancements, and API specification in JDK 17. Updates in Java SE 17 and JDK 17: https://docs.oracle.com/en/java/javase/17/migrate/significant-changes-jdk-release.html

[^openJDK]: OpenJDK 17 is the open-source reference implementation of version 17 of the Java SE Platform, as specified by by JSR 390 in the Java Community Process. JDK 17 reached General Availability on 14 September 2021. URL for OpenJDK-11 is: https://openjdk.java.net/projects/jdk/11/. URL for OpenJDK-17 is: https://openjdk.java.net/projects/jdk/17/.

[^cool]: COOL is the acronym for CLIPS Object Oriented Language.



