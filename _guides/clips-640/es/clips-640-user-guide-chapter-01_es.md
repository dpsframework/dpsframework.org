---
layout: guide
ref:  c640ug01
lang:  es
idiom:  es-ES
imagepath:  '../images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug








toc:  true


title:  "CLIPS 6.4 Guía del usuario"
headtitle:  'Solo los hechos'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Dr. Giarratano, Joseph C.'
department:  
authors:



departments:



chapter:  1
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'




ndtdate:  '2022-07-01 11:07:56:49:44 +0100'
date_published:  '2021-04-09'
date_modified:  '2022-07-16'
publisher:  'Gary Riley'

---




#  **Capítulo 1**

# 1.  Solo los hechos

>  Si ignoras los hechos, nunca te preocuparás por equivocarte


Este capítulo introduce los conceptos básicos de un sistema experto. Verá cómo insertar y eliminar datos en CLIPS.


## 1.1.   Introducción


CLIPS es un tipo de lenguaje informático diseñado para escribir aplicaciones llamadas **sistemas expertos**. Un sistema experto es un programa que está diseñado específicamente para modelar la experiencia o el conocimiento humano. Por el contrario, los programas comunes, como los programas de nómina, los procesadores de texto, las hojas de cálculo, los juegos de computadora, etc., no pretenden incorporar la experiencia o el conocimiento humanos. (Una definición de un experto, es alguien a más de 50 millas de su casa y que lleva un maletín).


CLIPS se denomina herramienta de sistema experto porque es un entorno completo para desarrollar sistemas expertos que incluye funciones como un editor integrado y una herramienta de depuración. La palabra shell está reservada para la parte de CLIPS que realiza inferencias o razonamientos. El shell de CLIPS proporciona los elementos básicos de un sistema experto:


1. **fact-list** (Lista de hechos) y la **instance-list** (lista de instancias): son la Memoria global de datos

2. **knowledge-base** (base de conocimientos): Contiene todas las reglas, la **rule-base** (base de datos de reglas)

3. **inference-engine** (motor de inferencia): Controla la ejecución general de las reglas


Un programa escrito en CLIPS puede constar de reglas, hechos y objetos. El motor de inferencia decide qué reglas deben ejecutarse y cuándo. Un sistema experto basado en reglas escrito en CLIPS es un programa basado en datos donde los hechos y los objetos, si se desea, son los datos que estimulan la ejecución a través del motor de inferencia.


Este es un ejemplo de cómo CLIPS difiere de los lenguajes de procedimiento como Java, Ada, BASIC, FORTRAN y C. En los lenguajes de procedimiento, la ejecución puede realizarse sin datos. Es decir, las sentencias son suficientes en esos lenguajes para provocar la ejecución. Por ejemplo, una declaración como PRINT 2 + 2 podría ejecutarse inmediatamente en BASIC. Esta es una declaración completa, que no requiere ningún dato adicional para provocar su ejecución. Sin embargo, en CLIPS, se requieren datos para provocar la ejecución de reglas.





Originalmente, CLIPS tenía capacidades para representar solo reglas y hechos. Sin embargo, las mejoras de la versión 6.0 permiten que las reglas coincidan tanto con objetos como con hechos. Además, los objetos se pueden usar sin reglas mediante el envío de mensajes, por lo que el motor de inferencia ya no es necesario si usa solo objetos. En los capítulos 1 a 7, discutiremos los hechos y las reglas de CLIPS. Las características de los objetos de CLIPS se tratan en los capítulos 8 a 12.


## 1.2.  El principio y el final


Para iniciar CLIPS, simplemente ingrese el comando de ejecución apropiado para su sistema.

<p class="code-label">Debería ver aparecer el indicador CLIPS de la siguiente manera:</p>
```scheme
CLIPS >
```


En este punto, puede comenzar a ingresar **comandos** directamente en CLIPS. El modo en el que ingresa comandos directos se denomina **top-level** **nivel superior**. Si tiene una versión de interfaz gráfica de usuario (GUI) de CLIPS, también puede **seleccionar** algunos comandos usando el mouse o las teclas de flecha en lugar de escribirlos. Consulte la Guía de interfaces de CLIPS para ver una discusión sobre los comandos admitidos. por las diversas GUI de CLIPS. Por simplicidad y uniformidad en este libro, supondremos que los comandos se escriben.


<p class="code-label">El modo normal de salir de CLIPS es con el comando de salida. Teclear solamente:</p>
```scheme
(exit)
```


en respuesta a la indicación CLIPS y luego presione la tecla de retorno de carro.


## 1.3.   Haciendo una lista


Al igual que con otros lenguajes de programación, CLIPS reconoce ciertas palabras clave. Por ejemplo, si desea incorpoar datos en la lista de hechos, puede usar el comando **assert** (confirmar).


<p class="code-label">Como ejemplo de confirmación, ingrese lo siguiente justo después de la solicitud de CLIPS como se muestra a continuación:</p>
```scheme

CLIPS> (assert (duck))
```


Aquí el comando de confirmación **assert** toma (pato) como argumento. Asegúrese de presionar siempre la tecla de retorno de carro para enviar la línea de sentencias a CLIPS.


<p class="code-label">Podrá ver la respuesta</p>
```scheme
<Fact-1>
```




lo que indica que CLIPS ha almacenado el hecho del pato en la lista de hechos y le ha asignado el identificador 1. Los **angle-brackets** o **corchetes angulares** se utilizan como delimitadores en CLIPS para rodear el nombre de un elemento. CLIPS nombrará automáticamente los hechos utilizando un número que aumenta secuencialmente y enumerará el índice de hechos más alto cuando se afirma uno o más hechos.


Observe que el comando (assert) y su argumento (pato) están entre paréntesis. Como muchos otros lenguajes de sistemas expertos, CLIPS tiene una sintaxis similar a LISP que usa paréntesis como delimitadores. Aunque CLIPS no está escrito en LISP, el estilo de LISP ha influido en el desarrollo de CLIPS.


## 1.4.   Y comprobar todo esto, dos veces


Suponga que desea ver lo que hay en la lista de hechos. Si su versión de CLIPS es compatible con una GUI, puede seleccionar el comando apropiado del menú. Alternativamente, puede ingresar comandos desde el teclado. A continuación, describiremos los comandos del teclado ya que las selecciones de la ventana se explican por sí mismas.


El comando de teclado para ver hechos es con el comando hechos **facts command**. Teclee  (facts) en respuesta al prompt de CLIPS y CLIPS responderá con una lista de hechos en la **fact-list**. Asegúrese de poner paréntesis alrededor del comando o CLIPS no lo aceptará.

<p class="code-label">El resultado del comando (facts) en este ejemplo debería ser:</p>
```scheme
CLIPS> (facts)
f-1 (duck)
For a total of 1 fact.

CLIPS>
```

El término _f-1_ es el **fact-identifier** (identificador de hecho) asignado al hecho (pato) por CLIPS. A cada hecho insertado en la **fact-list** se le asigna un identificador de hecho único que comienza con la letra "f" y le sigue un número entero llamado **fact-index** (índice de hechos). Al iniciar CLIPS, y después de ciertos comandos como **clear** y **reset** (que se analizarán con más detalle más adelante), el índice de datos se establecerá en uno y luego se incrementará en uno a medida que se realicen nuevos cambios cada vez que un hecho es insertado con **assert**.

<p class="code-label">¿Qué pasa si intenta poner un segundo pato en la lista de hechos? </p>
Intentémoslo y veamos. _Assert_ un nuevo (pato), luego emita un comando (facts) de la siguiente manera
```scheme
CLIPS> (assert (duck))
<Fact-1>
CLIPS> (facts)
f-1 (duck)
For a total of 1 fact.
CLIPS>
```

CLIPS devuelve el mensaje <Fact-1> para indicar que el hecho ya existe. Verá solo el "f-1 (duck)" original. Esto muestra que CLIPS no aceptará una entrada duplicada de un hecho. Sin embargo, hay un comando de anulación, **set-fact-duplication**, que permitirá la entrada de datos duplicados.

<p class="code-label">Por supuesto, puede incluir otros hechos diferentes. Por ejemplo, confirmar (assert) un hecho  (quack) y luego consultar la lista con el comando (facts). Verá los siguiente:</p>
```scheme
CLIPS> (assert (quack))
<Fact-2>
CLIPS> (facts)
f-1 (duck)
f-2 (quack)
For a total of 2 facts.
CLIPS>
```

Observe que el hecho (quack) ahora está en la lista de hechos.


Los hechos pueden ser eliminados o **retracted**. Cuando se retracta de un hecho, no se modifican los índices de los otros hechos, por lo que puede haber índices de hechos "faltantes". Como analogía, cuando un jugador de fútbol deja un equipo y no es reemplazado, los números de camiseta de los otros jugadores no se ajustan debido al número que falta (a menos que realmente odien al tipo y quieran olvidar que alguna vez jugó para ellos) .



## 1.5.   Eliminando las pruebas (o, los hechos)



<p class="code-label">El comando borrar **clear** elimina todos los hechos de la memoria, como se muestra a continuación.</p>
```scheme
CLIPS> (facts)
f-1 (duck)
f-2 (quack)
For a total of 2 facts.
CLIPS> (clear)
CLIPS> (facts)
CLIPS>
```



El comando (clear) esencialmente restaura CLIPS a su estado de inicio original. Borra la memoria de CLIPS y restablece el identificador de hechos a uno. 
<p class="code-label">Para ver esto, confirme con assert (animal-is duck), luego verifique la lista de hechos.</p>
```scheme
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (facts)
f-1 (animal-is duck)
For a total of 1 fact.
CLIPS>
```



Tenga en cuenta que (animal-is duck) tiene un identificador de hechos de f-1 porque el comando (clear) restablece los identificadores de hechos. El comando (clear) en realidad hace más que simplemente eliminar hechos. Además de eliminar todos los hechos, (clear) también elimina todas las reglas, como verás en el siguiente capítulo.


## 1.6.   Delicadeza al consumir Campos



Se dice que un hecho como (duck) o (quack) constan en un solo **field** (campo). Un campo es un espacio protegido (ya sea con o sin nombre propio) que puede tener almacenado un valor concreto. Como una analogía simple, puede pensar en un campo como un el marco de una fotografía. El marco puede contener una imagen, tal vez una foto de su pato mascota (para aquellos de ustedes que tienen curiosidad sobre cómo se ve una imagen de un "graznido de pato", podría ser (**1**) una foto del rastro dejado por osciloscopio de un pato cuando dice "cuac”, donde la señal de entrada proviene de un micrófono, o (**2**) para aquellos de ustedes que tienen una inclinación más científica, una transformada rápida de Fourier de la señal “cuac”, o (**3**) un locutor charlatan de la televisión que vende una cura milagrosa para arrugas, pérdida de peso, etc.). Los _placeholders_ o espacios de almacenamiento que poseen un nombre, solo se usan con **plantillas predefinidas** (**deftemplates**), que se describen con más detalle en el capítulo 5.



El hecho (pato) tiene un único espacio de almacenamiento sin nombre alguno que permita  referirse al valor "pato". Este es un ejemplo de un hecho de **single-field**, **campo único**. Un campo es un espacio de almacenamiento para un valor. Como analogía, piense en platos (campos) para contener a los alimentos (valores).


El **orden** de un campo sin nombre es muy importante. Por ejemplo, si un hecho fue definido:

```scheme
(Brian duck)
```

e interpretado por una regla como el cazador Brian le disparó a un pato, entonces el hecho:

```scheme
(duck Brian)
```

significaría que el pato cazador le disparó a Brian el humano. Por el contrario, el orden de los campos con nombre no es significativo, como verá más adelante con **deftemplate**.


En realidad, es una buena ingeniería de software comenzar el hecho con una relación que describa los campos. Un hecho mejor definido sería: 

```scheme
(hunter-game duck Brian)
```

para destacar de forma implícita que el primer campo es el cazador y el segundo campo es la pieza de caza en juego.


Ahora son necesarias algunas definiciones. Una **list** lista es un grupo de elementos sin orden implícito. Decir que una lista está **ordered** ordenada significa que la posición en la lista es significativa. Un **multifield** multicampo es una secuencia de campos, cada uno de los cuales puede tener un valor. Los ejemplos de (pato Brian) y (pato Brian) son hechos multicampo. Si un campo no tiene valor, el símbolo especial **nil**, que significa "nada", se puede usar para un campo vacío como marcador de la posición de ese campo. Por ejemplo:


```scheme
(duck nil)
```


significaría que el pato asesino no consiguió ningún trofeo de caza hoy.


Tenga en cuenta que el **nil** es necesario para indicar un marcador de posición, incluso si no tiene valor. Por ejemplo, piense en un campo como análogo a un buzón. Hay una gran diferencia entre un buzón vacío y ningún buzón. Sin el **nil**, el hecho se convierte en un hecho de un solo campo (pato). Si una regla depende de dos campos, no funcionará con un solo campo, como se verá más adelante.


Hay varios _types_ **tipos** diferentes de campos disponibles: _float, integer, symbol, string, external-address, fact-address, instance-name e instance-address_: **de coma flotante**, de tipo **entero**, de tipo **símbolo**, de **cadena-de-caracteres**, campos de tipo **puntero-externo**, campos de **puntero-de-hecho**, campos para albergar **nombre-de-instancia** y campos de **puntero-de-instancia**. El tipo de cada campo está determinado por el tipo de **valor** almacenado en el campo. En un campo sin nombre, el tipo está determinado implícitamente por el tipo que coloca dentro en el campo. En **deftemplates**, puede declarar explícitamente el tipo de valor que puede contener un campo. El uso de tipos explícitos refuerza los conceptos de **ingeniería de software**, que es una disciplina de programación para producir software de calidad.


Un **symbol**, **símbolo** es un tipo de campo que comienza con un carácter ASCII imprimible y va seguido opcionalmente de cero o más caracteres imprimibles. Los campos suelen estar delimitados o acotados por uno o más espacios o paréntesis. Por ejemplo:

```scheme
(duck-shot Brian Gary Rey)
```


Sin embargo, esto podría ser un **deftemplate** correcto y legal si "duck-shot" se define como el nombre de un campo, mientras que "Brian Gary Rey" son los valores asociados con ese campo que posee un nombre.


CLIPS distingue entre mayúsculas y minúsculas. Además, ciertos caracteres tienen un significado especial para CLIPS.

```scheme
"  ""   (    )   &   |   <   ~   ;   ?   $  

```


Los caracteres `""&"", ""|"", and ""~""` no podrán ser empleados para nombres aislados de símbolos ni tampoco como partes del nombre de un símbolo. 


 Algunos de esos caracteres actúan como delimitadores para indicar el final del nombre de un símbolo. Los siguientes actúan como delimitadores de símbolos.  
 
- Cualquier carácter ASCII que no sea imprimible, inclyendo espacios, retornos de línea, tabuladores, así como los finales de línea (LF en archivos UNIX).
- comillas dobles, `  `"
- la apertua y cierre de paréntesis, `() `
- ampersand, `&`
- barra vertical, `| `
- menor que,` <`. Obsérvese que este podría ser el primero de los caracteres de un símbolo.
- tilde, `~ `
- punto y coma, `;` indica el inicio de un comentario, y el retorno de línea lo finaliza.
- ?   y   `$?`  no pueden iniciar el nombre de un símbolo pero, pueden estar en el parte media de su definición como nombre de símbolo.


El punto y coma actúa como el comienzo de un comentario en CLIPS. Si intenta confirmar **assert** un punto y coma, CLIPS pensará que está ingresando un comentario y esperará a que termine. Si accidentalmente ingresa un punto y coma en el nivel superior, simplemente escriba un paréntesis de cierre y un retorno de carro. CLIPS responderá con un mensaje de error y volverá a aparecer el prompt de CLIPS (Esa es, una de las pocas ocasiones probadas en la vida en las que es necesario hacer algo mal para hacer algo bien).


A medida que lea este manual, aprenderá los significados especiales de los caracteres anteriores. Con la excepción de `“&”, “|”` y ` “~” `, puede usar los demás como se describe. Sin embargo, puede ser confuso para alguien que lea su programa y trate de entender lo que está haciendo el programa. En general, es mejor evitar el uso de estos caracteres en símbolos a menos que tenga una buena razón para usarlos.



<p class="code-label">Los siguientes son ejemplos de símbolos:</p>
```racket
duck
duck1
duck_soup
duck-soup
duck1-1_soup-soup
d!?#%^
```





El tipo **string** es el segundo tipo de campo. Una campo tipo cadena de caracteres debe comenzar y terminar con comillas dobles. Las comillas dobles son parte del campo. Cero o más caracteres de cualquier tipo pueden aparecer entre comillas dobles. A continuación se muestran algunos ejemplos de campo tipo cadena de caracteres.


```racket
  "duck"
  "duck1"
  "duck/soup"
  "duck soup"
  "duck soup is good!!!"
```




El tercer y cuarto tipos, son los **campos numéricos**. Un campo que representa un número puede ser un campo de tipo entero **integer** o de punto flotante **floating-point**. Un tipo de punto flotante se conoce comúnmente como un **float**.


Todos los números en CLIPS se tratan como enteros "largos" o flotantes de doble precisión **double-precision**. Los números sin punto decimal se tratan como enteros a menos que estén fuera del rango de enteros. Ese rango depende de la arquitectura de la expresada en número de bits, N, utilizados para representar el número entero de la siguiente manera:




- Desde   -2 <sup>N-1</sup>
- 
- 
- 
- Hasta      2<sup>N-1</sup> - 1

Para enteros "extra largos" de 64 bits, esto corresponde a un rango de números:
- Desde - 9,223,372,036,854,775,808
-    
-  
-  
- Hasta  9,223,372,036,854,775,807



Como ejemplos de números, confirme (assert) los siguientes datos donde, el último número, está en notación exponencial y usa la "e" o "E" para la potencia de diez.



```racket
CLIPS> (clear)
CLIPS> (facts)
CLIPS> (assert (number 1))
<Fact-1>
CLIPS> (assert (x 1.5))
<Fact-2>
CLIPS> (assert (y -1))
<Fact-3>
CLIPS> (assert (z 65))
<Fact-4>
CLIPS> (assert (distance 3.5e5))
<Fact-5>
CLIPS> (assert (coordinates 1 2 3))
<Fact-6>
CLIPS> (assert (coordinates 1 3 2))
<Fact-7>
CLIPS> (facts)
f-1 (number 1)
f-2 (x 1.5)
f-3 (y -1)
f-4 (z 65)
f-5 (distance 350000.0)
f-6 (coordinates 1 2 3)
f-7 (coordinates 1 3 2)
For a total of 7 facts.
CLIPS>
```



Como puede ver, CLIPS imprime el número ingresado en notación exponencial como 350000.0 porque convierte el formato de potencia de diez a punto flotante si el número es lo suficientemente pequeño.


Observe que cada hecho, (fact) debe comenzar con un símbolo como "número", "x", "y", etc. Antes de la versión 6.0 de CLIPS, era posible ingresar solo un número como un hecho. Sin embargo, ahora se requiere un símbolo como primer campo. Además, ciertas palabras reservadas utilizadas por CLIPS no se pueden usar como primer campo, pero se pueden usar para otros campos. Por ejemplo, la palabra reservada **not** se usa para indicar un patrón de negación y no se puede usar como el primer campo de un hecho.


Un hecho, **fact**, consta de uno o más campos encerrados entre paréntesis izquierdo y derecho uno asociado al otro. Para simplificar, solo discutiremos hechos en los primeros siete capítulos, pero la mayor parte de la discusión sobre la coincidencia de patrones también se aplica a los objetos. Las excepciones son ciertas funciones, como _assert_ _retract_ , que solo se aplican a hechos, no a loa objetos. Las formas correspondientes de manipular objetos se analizan en los capítulos 8 a 12.


Un hecho puede estar ordenado **ordered** o desordenado **unordered**. Todos los ejemplos que ha visto hasta ahora son hechos ordenados porque el orden de los campos marca la diferencia. Por ejemplo, observe que CLIPS los considera como hechos separados, aunque se utilizan los mismos valores "1", "2" y "3" en cada uno.


```racket
f-6 (coordinates 1 2 3)
f-7 (coordinates 1 3 2)
```


Los hechos ordenados deben usar la posición del campo para definir los datos. Como ejemplo, el hecho ordenado (duck Brian) tiene dos campos y también los tiene (Brian pato). Sin embargo, CLIPS los considera como dos hechos separados porque el orden de los valores de campo es diferente. Por el contrario, el hecho (duck-Brian) tiene un solo campo debido a que el guión "-" concatena los dos valores.


Los hechos basados en platillas **deftemplate facts**, que se describen con más detalle más adelante, están desordenados porque utilizan campos con nombre para definir los datos. Esto es análogo al uso de estructuras en C y otros lenguajes.
Los campos de tipo **Multicampo** normalmente están separados por **espacios en blanco** que consisten en uno o más espacios, tabulaciones, retornos de carro o saltos de línea. Por ejemplo, ingrese los siguientes ejemplos como se muestra y verá que cada hecho almacenado es el mismo.

```racket
CLIPS> (clear)
CLIPS> (assert (The duck says "Quack"))
<Fact-1>
CLIPS> (facts)
f-1 (The duck says "Quack")
For a total of 1 fact.
CLIPS> (clear)
CLIPS> (assert (The duck says "Quack" ))  <Fact-1>
CLIPS> (facts)
f-1 (The duck says "Quack")
For a total of 1 fact.
CLIPS>
```



Los retornos de carro también se pueden utilizar para mejorar la legibilidad. En el siguiente ejemplo, se escribe un retorno de carro después de cada campo y el hecho confirmado (assert) es el mismo que antes cuando el hecho se ingresó en una línea.


```racket
CLIPS> (clear)
CLIPS> (assert (The
duck
says
Quack))
<Fact-1>
CLIPS> (facts)
f-1 (The duck says "Quack")
For a total of 1 fact.
CLIPS>
```



Sin embargo, tenga cuidado si inserta un retorno de carro dentro de una cadena, como muestra el siguiente ejemplo.


```racket
CLIPS> (assert (The
duck
says
"Quack  
))"
<Fact-2>
CLIPS> (facts)
f-1 (The duck says "Quack")
f-2 (The duck says "Quack")
For a total of 2 facts.
CLIPS>
```



Como puede ver, el retorno de carro incrustado en las comillas dobles se generó con la cadena para colocar la comilla doble de cierre en la siguiente línea. Esto es importante porque CLIPS considera el hecho f-1 distinto del hecho f-2.



Observe también que CLIPS conservó las letras mayúsculas y minúsculas en los campos del hecho. Es decir, la “T” de “The” y la “Q” de “Quack” están en mayúsculas. Se dice que CLIPS distingue entre mayúsculas y minúsculas porque distingue entre letras mayúsculas y minúsculas. Por ejemplo, confirme los hechos (duck) y (Duck) y luego emita un comando (facts). Verá que CLIPS le permite ingresar a (duck) y a (Duck) como hechos diferentes porque CLIPS distingue entre mayúsculas y minúsculas.



El siguiente ejemplo es un caso más realista en el que se utilizan retornos de carro para mejorar la legibilidad de una lista. Para ver esto, confirme el siguiente hecho donde se usan retornos de carro y espacios para colocar campos en lugares apropiados en diferentes líneas. Los guiones o signos menos se usan intencionalmente para crear campos únicos, por lo que CLIPS tratará elementos como "fudge sauce" (salsa de chocolate) como un solo campo.


```racket
CLIPS> (clear)
CLIPS>
(assert (grocery-list
ice-cream
cookies
candy
fudge-sauce))
<Fact-1>
CLIPS> (facts)
"f-1 (grocery-list ice-cream cookies candy fudge-sauce)  
For a total of 1 fact."
CLIPS>
```



Como puede ver, CLIPS reemplazó los retornos de carro y las pestañas con espacios simples. Si bien el uso de espacios en blanco para separar los hechos es conveniente para una persona que lee un programa, CLIPS los convierte en espacios simples.


## 1.7.   Una cuestión de estilo


Es un buen estilo de programación basada-en-reglas, usar el primer campo de un hecho para describir la relación de los siguientes campos. Cuando se usa de esta manera, el primer campo se llama _relación_. Los campos restantes del hecho se utilizan para valores específicos. Un ejemplo es (lista de comestibles, helado, galletas, dulces, salsa de chocolate) o (grocery-list ice-cream cookies candy fudge-sauce). Los guiones se utilizan para hacer que varias palabras quepan, y se asocien, a un solo campo.


Una buena documentación es incluso más importante, en un sistema experto, que en lenguajes como Java, C, Ada, etc., porque las reglas de un sistema experto generalmente no se ejecutan de forma secuencial. CLIPS ayuda al programador a escribir hechos descriptivos como este por medio de deftemplates.


Otro ejemplo de hechos relacionados es  (duck), (horse), and (cow) o ... (pato), (caballo) y (vaca). Es un estilo mucho mejor, referirse a ellos de la siguiente forma:


```racket
(animal-is duck)
(animal-is horse)
(animal-is cow)
          or as the single fact
(animals duck horse cow)
```



ya que la relación animal-es o animales describe su relación y proporciona cierta documentación a la persona que lee el código.



Las relaciones explícitas, _animal-is_ y _animals_, tienen más sentido para una persona que el significado implícito de (duck), (horse) y (cow). Si bien este ejemplo es lo suficientemente simple como para que cualquiera pueda descifrar las relaciones implícitas, es fácil caer en la trampa de escribir hechos en los que la relación no es tan obvia (De hecho, es mucho más fácil hacer algo más complicado que fácil, ya que la gente está más impresionada por la complejidad que por la simplicidad.)



## 1.8.   Obteniendo el suficiente espacio


Dado que los espacios en blanco se utilizan para separar varios campos, se deduce que los espacios no se pueden incluir simplemente en los hechos. Por ejemplo:

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is walrus))
<Fact-1>
CLIPS> (assert ( animal-is walrus ))
<Fact-1>
CLIPS> (assert ( animal-is walrus ))
<Fact-1>
CLIPS> (facts)
f-1 (animal-is walrus)
For a total of 1 fact.
CLIPS>
```



Solo se afirma un hecho _ (animal-is walrus)_ (es-animal morsa), ya que CLIPS ignora los espacios en blanco y considera todos estos hechos equivalentes. Por lo tanto, CLIPS responde con `<Fact-1>` cuando intenta ingresar los dos últimos datos duplicados. CLIPS normalmente no permite que se ingresen hechos duplicados a menos que cambie la configuración de **set-fact-duplication** para permitir la duplicación de hechos.


Si desea incluir espacios en un hecho, debe usar comillas dobles. Por ejemplo,

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is "duck"))
<Fact-1>
CLIPS> (assert (animal-is "duck "))
<Fact-2>
CLIPS> (assert (animal-is " duck"))
<Fact-3>
CLIPS> (assert (animal-is " duck "))
<Fact-4>
CLIPS> (facts)
f-1 (animal-is "duck")
f-2 (animal-is "duck ")
f-3 (animal-is " duck")
f-4 (animal-is " duck ")
For a total of 4 facts.
CLIPS>
```


Tenga en cuenta que los espacios hacen que cada uno de estos hechos sea diferente a CLIPS, aunque el significado es el mismo para una persona.


¿Qué sucede si desea incluir las comillas dobles en un campo? La forma correcta de poner comillas dobles en un hecho es con la barra invertida, "\\", como muestra el siguiente ejemplo.

```racket
CLIPS> (clear)
CLIPS> (assert (single-quote "duck"))
<Fact-1>
CLIPS> (assert (double-quote "\"duck\""))
<Fact-2>
CLIPS> (facts)
f-1 (single-quote "duck")
f-2 (double-quote ""duck"")
For a total of 2 facts.
CLIPS>
```


## 1.9.   Retractarse de ese hecho



Ahora que sabe cómo poner hechos en la lista de hechos, es hora de aprender a eliminarlos. La eliminación de hechos de la lista de hechos se denomina retractación y se realiza con el comando de retractación  _retract_. Para retractarse de un hecho, debe especificar el índice del hecho, correspondiente al hecho como argumento de _retract_. Por ejemplo, configure su lista de hechos de la siguiente manera.


```racket
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (assert (animal-sound quack))
<Fact-2>
CLIPS> (assert (The duck says "Quack."))
<Fact-3>
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (animal-sound quack)
f-3 (The duck says "Quack.")
For a total of 3 facts.
CLIPS>
```


Para eliminar el último hecho con el índice f-3, ingrese el comando de retracción y luego verifique sus hechos de la siguiente manera.


```racket
CLIPS> (retract 3)
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (animal-sound quack)
For a total of 2 facts.
CLIPS>
```



¿Qué sucede si intenta retractarse de un hecho que ya se retractó o de un hecho inexistente? Intentémoslo y veamos.


```racket
CLIPS> (retract 3)
[PRNTUTIL1] Unable to find fact f-3.
CLIPS>
```



Tenga en cuenta que CLIPS emite un mensaje de error si intenta retractarse de un hecho inexistente. La moraleja de esto es que no puedes recuperar lo que no has dado.
Ahora retractemos los otros hechos de la siguiente manera.


```racket
CLIPS> (retract 2)
CLIPS> (facts)
f-1 (animal-is duck)
For a total of 1 fact.
CLIPS> (retract 1)
CLIPS> (facts)
CLIPS>
```


También puede retractarse de varios hechos a la vez, como se muestra a continuación.

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (assert (animal-sound quack))
<Fact-2>
CLIPS> (assert (The duck says "Quack."))
<Fact-3>
CLIPS> (retract 1 3)
CLIPS> (facts)
f-2 (animal-sound quack)
For a total of 1 fact.
CLIPS>
```


Para retractarse de varios hechos, simplemente enumere los números de identificación de hechos en el comando (retractar). Simplemente puede usar **(retract *)** para retractarse de todos los hechos, donde el `*` indica todos.

```racket
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (assert (animal-sound quack))
<Fact-2>
CLIPS> (assert (The duck says "Quack."))
<Fact-3>
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (animal-sound quack)
f-3 (The duck says "Quack.")
For a total of 3 facts.
CLIPS> (retract *)
CLIPS> (facts)
CLIPS>
```


## 1.10.   Mira ese hecho


CLIPS proporciona varios comandos para ayudarle a depurar programas. Un comando le permite observar continuamente cómo se afirman y se retractan los hechos. Esto es más conveniente que tener que escribiren un comando *(watch facts)** una y otra vez y tratando de averiguar qué ha cambiado en la lista de hechos.




<p class="code-label">Para comenzar a ver hechos, ingrese el comando (ver hechos) como se muestra en el siguiente ejemplo.</p>
```racket
CLIPS> (clear)
CLIPS> (watch facts)
CLIPS> (assert (animal-is duck))
==> f-1 (animal-is duck)
<Fact-1>
CLIPS>
```


El **símbolo de doble flecha derecha**, `==>`, significa que un hecho está ingresando en la memoria, mientras que la **doble flecha izquierda** indica que un hecho está saliendo de la memoria, como se muestra a continuación.


```racket
CLIPS> (reset)
<== f-1 (animal-is duck)
CLIPS> (assert (animal-is duck))
==> f-1 (animal-is duck)
<Fact-1>
CLIPS> (retract 1)
<== f-1 (animal-is duck)
CLIPS> (facts)
CLIPS>
```



El comando (ver hechos), **(watch facts)**, proporciona un registro que muestra la dinámica; o estado de cambios sufridos por la lista de hechos. Por el contrario, el comando (facts) muestra el estado **estático** de la lista de hechos, ya que muestra el contenido actual de la lista de hechos. Para desactivar la visualización de hechos, ingrese **(unwatch facts)**.



Hay varias cosas que puedes ver. Estos incluyen los siguientes, que se describen con más detalle en el _Manual de referencia de CLIPS_. El **comentario** en CLIPS comienza con un **punto y coma**. CLIPS ignora todo lo que sigue al punto y coma.



<p class="code-label">The (watch facts) command provides a record that shows the dynamic; or changing state of the  fact-list</p>
```racket
(watch facts)
; instances used with objects
(watch instances)
; slots used with objects
(watch slots)
(watch rules)
(watch activations)
; messages used with objects
(watch messages)
; message-handlers used with objects
(watch message-handlers)
(watch generic-functions)
(watch methods)
(watch deffunctions)
; compilations are watched by default
(watch compilations)
(watch statistics)
(watch globals)
(watch focus)
; all watches everything
(watch all)
```


A medida que utilice más funciones de CLIPS, estos comandos como (watch), le resultarán muy útiles para la depuración. Para desactivar un comando (watch), ingrese un comando **unwatch** para no ver más cambios. Por ejemplo, para desactivar la visualización de compilaciones, ingrese **(unwatch compilations)**.







