---
layout: guide
ref:  c640ug04
lang:  es
idiom:  es-ES
imagepath:  '../images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug

toc:  true

title:  "CLIPS 6.4 Guía de usuario"
subtitle:  "El tipo de reglas que has visto hasta ahora ilustra la simple coincidencia de patrones con hechos. En este capítulo, aprenderá formas muy poderosas de combinar y manipular hechos."
headtitle:  'Variables de interés'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Dr. Giarratano, Joseph C.'
department:  
authors:

departments:

chapter:  4
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'
date_published:  '2021-04-09'
date_modified:  '2022-08-17'

---




  
#  **Capítulo 4**
  

  

#  4. Variables de interés



   
>  Nada cambia más que el cambio




El tipo de reglas que ha visto hasta ahora ilustra la simple coincidencia de patrones con hechos. En este capítulo, aprenderá formas muy poderosas de combinar y manipular hechos.




##  4.1. Seamos Variables




Al igual que con otros lenguajes de programación, CLIPS tiene **variables** para almacenar valores. A diferencia de un hecho, que es **estático** o inmutable, el contenido de una variable es **dinámico** a medida que cambian los valores que se le asignan. Por el contrario, una vez que se afirma un hecho, sus campos solo pueden modificarse retractándose y afirmando un nuevo hecho con los campos modificados. Incluso la acción de modificar (descrita más adelante en el capítulo sobre deftemplate) actúa retractando y afirmando un hecho modificado, como se puede ver comprobando el índice de hechos.




El nombre de una variable, o **identificador de variable**, siempre se escribe con un signo de interrogación seguido de un símbolo que es el nombre de la variable.




<p class="code-label">El formato general es</p>
```scheme
  ?<variable-name>
``` 



Las variables globales, que se describirán con más detalle más adelante, tienen una sintaxis ligeramente diferente.




<p class="code-label">Al igual que en otros lenguajes de programación, los nombres de las variables deben ser significativos en un buen estilo de programación. A continuación se muestran algunos ejemplos de nombres de variables válidos.</p>
```scheme
?x
?noun
?color
?sensor
?valve
?ducks-eaten
``` 







<p class="code-label">Antes de poder utilizar una variable, se le debe asignar un valor. Como ejemplo de un caso en el que no se asigna un valor, intente ingresar lo siguiente y CLIPS responderá con el mensaje de error que se muestra.</p>
```scheme
CLIPS> (unwatch all)
CLIPS> (clear)
CLIPS>
(defrule test
=>
(printout t ?x crlf))

[PRCCODE3] Undefined variable x
referenced in RHS of defrule.

ERROR:
(defrule MAIN::test
=>
(printout t ?x crlf))
CLIPS>
``` 



**CLIPS** da un mensaje de error cuando no puede encontrar un valor **enlazado** a **?x**. El término **bound** significa la vinculación de un valor y su asignación a una variable. Solo las variables globales están vinculadas y accesibles desde todas las reglas. Todas las demás variables solo están vinculadas dentro de una regla. Antes y después de que se active una regla, las variables no globales, no están vinculadas por lo que CLIPS generará un mensaje de error si intenta consultar una variable no vinculada (_non-bound_).




##  4.2. Ser asertivo




Un uso común de las variables es hacer coincidir un valor en el LHS y luego afirmar esta variable vinculada en el RHS. Por ejemplo, ingrese:


<p class="code-label"></p>
```scheme
(defrule make-quack
(duck-sound ?sound)
=>
(assert (sound-is ?sound)))
``` 


Ahora confirme el hecho siguiente (duck-sound quack), luego (run) del programa. Verifique los hechos y verá que la regla ha producido el hecho (sound-is quack) porque la variable **?sound** sí estaba vinculada a valor _quack_ en la LHS de la regla.

<p class="code-label">Por supuesto, también puede usar una variable más de una vez. Por ejemplo, ingrese lo siguiente. Asegúrese de hacer un (reset) y luego un _assert_ para confirmar el hecho (duck-sound quack) nuevamente.</p>
```scheme
(defrule make-quack
(duck-sound ?sound)
=>
(assert (sound-is ?sound ?sound)))
```

Cuando la regla se dispara, producirá el hecho (sound-is quack) ya que, la variable **?sound** se usa dos veces.

##  4.3. Lo que el Pato diga

<p class="code-label">Las variables también se usan comúnmente en la salida de impresión, como en</p>
```scheme
(defrule make-quack
(duck-sound ?sound)
=>
(printout t "The duck said "
?sound crlf))
```


Haga un (reset), he ingrese esta regla y confirme el hecho y luego ejecute con (run) para averiguar qué dijo el pato. ¿Cómo modificaría la regla para poner comillas dobles alrededor de quack en la salida?



<p class="code-label">Se puede usar más de una variable en un patrón, como muestra el siguiente ejemplo.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule whodunit
(duckshoot ?hunter ?who)
=>
(printout t ?hunter " shot "
?who crlf))
CLIPS> (assert (duckshoot Brian duck))
<Fact-1>
; Duck dinner tonight!
CLIPS> (run)
Brian shot duck
CLIPS> (assert (duckshoot duck Brian))
<Fact-2>
; Brian dinner tonight!
CLIPS> (run)
duck shot Brian
; Missing third field
CLIPS> (assert (duckshoot duck))
<Fact-3>
; Rule doesn't fire,
; no output
CLIPS> (run)
CLIPS>
``` 



Observe la gran diferencia que se genera por el orden de los campos para determinar quién disparó a quién. También puede ver que la regla no se activó cuando se confirmó el hecho (uckshoot duck). La regla no se activó porque ningún campo del hecho coincidía con la restricción del segundo patrón, **?who**.




##  4.4. El soltero feliz




La retracción es muy útil en sistemas expertos y generalmente se realiza en el RHS en lugar de en el nivel superior. Antes de que se pueda retractar un hecho, este debe ser especificado en CLIPS. Para retractar un hecho desde el interior de una regla, la **dirección del hecho** o _fact-address_  primero debe vincularse a una variable en el LHS.




Hay una gran diferencia entre vincular una variable al contenido de un hecho y vincular una variable a la dirección del hecho. En los ejemplos que ha visto, como en el patrón de concordarcia creado por (duck-sound ?sound), una variable llamada **?sound** estaba vinculada al valor de un campo. Es decir, ?soun estaba vinculada al valor _quack_. Sin embargo, si desea eliminar el hecho cuyo contenido es (duck-soun quack), primero debe indicar a CLIPS la dirección del hecho que desea retirar.


La dirección del hecho se especifica usando la **flecha izquierda** seguida de un guión, `<-`. Para crear esto, simplemente escriba un símbolo "<" seguido de un "-". 

<p class="code-label">Como ejemplo de retractación de un hecho desde el interior de una regla,</p>
```scheme
CLIPS> (clear)
CLIPS> (assert (bachelor Dopey))
<Fact-1>
CLIPS> (facts)
f-1 (bachelor Dopey)
For a total of 1 fact.
CLIPS>
(defrule get-married
?duck <- (bachelor Dopey)
=>
(printout t "Dopey is now happily married "
?duck crlf)
(retract ?duck))
CLIPS> (run)
Dopey is now happily married <Fact-1>
CLIPS> (facts)
CLIPS>
``` 



Observe que la (impresión) imprime el índice de hechos de **?duck**, <Fact-1>, ya que la flecha izquierda asocia la dirección del hecho a la variable ?duck. Además, no hay ningún hecho (bachelor Dopey) porque se ha sido extraido o retractado.


Las variables se pueden usar para seleccionar el valor de un hecho al mismo tiempo que capturar y asociar la  dirección del índice del ese hecho, como se muestra en el siguiente ejemplo.

<p class="code-label">Por conveniencia, también se ha definido un **(deffacts)**.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule marriage
?duck <- (bachelor ?name)
=>
(printout t ?name
 is now happily married
crlf)
(retract ?duck))
CLIPS>
(deffacts good-prospects
(bachelor Dopey)
(bachelor Dorky)
(bachelor Dicky))
CLIPS> (reset)
CLIPS> (run)
Dicky is now happily married
Dorky is now happily married
Dopey is now happily married
CLIPS>
``` 



Observe cómo la regla activó todos los hechos que coincidían con el patrón (bachelor ?name). CLIPS también tiene una función llamada **índice de datos** o _fact-index_ que se puede utilizar para devolver el índice del hecho como una dirección del hecho (o puntero del hecho).




##  4.5. No es importante




En lugar de vincular un valor de campo a una variable, la presencia de un campo no vacío se puede detectar solo usando un **comodín** o _wildcard_ `*`. Por ejemplo, suponga que está ejecutando un servicio de citas para patos y, una patita afirma mediante un hecho, que solo sale con patos cuyo primer nombre es Dupey. En realidad, hay dos criterios en esta especificación, ya que implica que el pato debe tener más de un nombre. Entonces, un simple (bachellor Dopey) no es adecuado porque solo posee un nombre ese hecho.




Este tipo de situaciones, en las que solo se especifica una parte del hecho, es muy común y muy importante. Para resolver este problema, se puede usar un comodín para hacer coincidir los Dopeys.




La forma más simple de comodín se llama _single-field wildcard_ o **comodín de un solo campo** y se muestra con un signo de interrogación, "?". Los "?" también se les denomina _single-field constraint_ o  **restricción de un solo campo**.




<p class="code-label">Un comodín de un solo campo representa exactamente un campo, como se muestra a continuación.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule dating-ducks
(bachelor Dopey ?)
=>
(printout t "Date Dopey"
crlf))
CLIPS>
(deffacts duck
(bachelor Dicky)
(bachelor Dopey)
(bachelor Dopey Mallard)
(bachelor Dinky Dopey)
(bachelor Dopey Dinky Mallard))
CLIPS> (reset)
CLIPS> (run)
Date Dopey
CLIPS>
``` 



El patrón incluye un comodín para indicar que el apellido de Dopey no es importante. Siempre que el primer nombre sea Dopey y que haya algún apellido (pero, no segundo nombre), la regla se cumplirá y se disparará. Debido a que el patrón tiene tres campos de los cuales uno es un comodín de un solo campo, solo los hechos de exactamente tres campos pueden satisfacerlo. En otras palabras, solo los Dopeys con exactamente dos nombres pueden satisfacer a esta patita.




<p class="code-label">Suponga que desea especificar Dopeys con exactamente tres nombres. Todo lo que tendrías que hacer es escribir un patrón como</p>
```scheme
(bachelor Dopey ? ?)
or, if only persons with three names whose middle name was Dopey,
(bachelor ? Dopey ?)
or, if only the last name was Dopey, as in the following:
(bachelor ? ? Dopey)
``` 



Otra posibilidad interesante ocurre si Dopey debe ser el primer nombre, pero solo se aceptan aquellos Dopeys con dos o tres nombres. Una forma de resolver este problema es escribir dos reglas.



<p class="code-label">Por ejemplo</p>
```scheme
(defrule eligible
(bachelor Dopey ?)
=>
(printout t "Date Dopey" crlf))
(defrule eligible-three-names
(bachelor Dopey ? ?)
=>
(printout t "Date Dopey" crlf))
``` 



Ingrese y ejecute esto y verá que se imprimen Dopeys con dos y tres nombres. Por supuesto, si no desea fechas anónimas, debe vincular los nombres de Dopey con una variable e imprimirlos.




##  4.6. Volverse loco




En lugar de escribir reglas separadas para manejar cada campo, es mucho más fácil usar el _multifield wildcard_ o **comodín multicampo**. Este es un signo de dólar seguido de un signo de interrogación, **“$?”**, y representa cero o más campos. Observe cómo esto contrasta con el comodín de un solo campo que debe coincidir exactamente con un campo.




<p class="code-label">Las dos reglas para las fechas ahora se pueden escribir en una sola regla de la siguiente manera.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule dating-ducks
(bachelor Dopey $?)
=>
(printout t "Date Dopey" crlf))
CLIPS>
(deffacts duck
(bachelor Dicky)
(bachelor Dopey)
(bachelor Dopey Mallard)
(bachelor Dinky Dopey)
(bachelor Dopey Dinky Mallard))
CLIPS> (reset)
CLIPS> (run)
Date Dopey
Date Dopey
Date Dopey
CLIPS>
``` 



Los comodines tienen otro uso importante porque se pueden adjuntar a un campo simbólico para crear una variable como **?x**, **$?x**, **?name** o **$?name**. La variable puede ser una **variable de un solo campo** o una **variable de varios campos** dependiendo de si un "?" o “$?” se utiliza en el LHS. Tenga en cuenta que en el RHS solo se usa un ?x, donde la "x" puede ser cualquier nombre de variable. Puede pensar en el "$" como una función cuyo argumento es un comodín de un solo campo o una variable de un solo campo y devuelve un comodín de varios campos o una variable de varios campos, respectivamente.





<p class="code-label">Como ejemplo de una variable multicampo, la siguiente versión de la regla también imprime los campos de nombre del hecho coincidente porque una variable se equipara a los campos de nombre que coinciden:</p>
```scheme
CLIPS>
(defrule dating-ducks
(bachelor Dopey $?name)
=>
(printout t "Date Dopey " ?name crlf))
CLIPS> (reset)
CLIPS> (run)
Date Dopey (Dinky Mallard)
Date Dopey (Mallard)
Date Dopey ()
CLIPS>
``` 



Como puede ver, en el LHS, el patrón multicampo es **$?name** pero es **?name** cuando se usa como una variable en el RHS. Cuando ingrese y ejecute el programa, verá los nombres de todos los Dopeys elegibles. El comodín multicampo se ocupa de cualquier número de campos. Además, tenga en cuenta que los valores de varios campos se devuelven entre paréntesis.




Supongamos que desea una coincidencia de todos los patos que tienen un Dopey en alguna parte de su nombre, no necesariamente como su primer nombre.




<p class="code-label">La siguiente versión de la regla haría coincidir todos los hechos con un Dopey en ellos y luego imprimiría los nombres:</p>
```scheme
CLIPS>
(defrule dating-ducks
(bachelor $?first Dopey $?last)
=>
(printout t "Date "
?first
 Dopey 
?last crlf))
CLIPS> (reset)
CLIPS> (run)
Date () Dopey (Dinky Mallard)
Date (Dinky) Dopey ()
Date () Dopey (Mallard)
Date () Dopey ()
CLIPS>
``` 



El patrón coincide con cualquier nombre que tenga un Dopey en alguna parte.




Se pueden combinar comodines de uno o varios campos.




<p class="code-label">Por ejemplo, el patrón</p>
```scheme
(bachelor ? $? Dopey ?)
``` 



significa que el nombre y el apellido pueden ser cualquier cosa y que el nombre justo antes del último debe ser Dopey. Este patrón también requiere que el hecho coincidente tenga al menos cuatro campos, ya que el “$?” coincide con cero o más campos y todos los demás deben coincidir exactamente con cuatro.




Aunque las variables multicampo pueden ser esenciales para la **coincidencia de patrones** en muchos casos, su uso excesivo puede causar mucha ineficiencia debido al aumento de los requisitos de memoria y una ejecución más lenta.





>    &clubs; _Como regla general de estilo, debe usar $? solo cuando no conoce la longitud de los campos. No use $? simplemente como una comodidad de escritura._




##  4.7. El soltero ideal




Las variables utilizadas en los patrones tienen una propiedad importante y útil, que se puede enunciar de la siguiente manera.





>    &clubs; _La primera vez que se vincula una variable, retiene ese valor solo dentro de la regla, tanto en el LHS como en el RHS, a menos que se cambie en el RHS._




<p class="code-label">Por ejemplo, en la siguiente regla</p>
```scheme
(defrule bound
(number-1 ?num)
(number-2 ?num)
=>)
If there are some facts
f-1 (number-1 0)
f-2 (number-2 0)
f-3 (number-1 1)
f-4 (number-2 1)
``` 



entonces la regla solo puede ser activada por el par f-1, f-2 y el otro par f-3, f-4. Es decir, el hecho de que f-1 no puede coincidir con f-4 porque cuando **?num** está vinculado a 0 en el primer patrón, el valor de **?num** en el segundo patrón también debe ser 0. Asimismo, cuando **?num* está vinculado a 1 en el primer patrón, el valor de **?num** en el segundo patrón debe ser 1. Observe que la regla se activará dos veces por estos cuatro hechos: una activación para el par f-1, f-2 y la otra activación para el par f-3, f-4.




Como un ejemplo más práctico, ingrese la siguiente regla. Observe que la misma variable, ?name, se usa en ambos patrones.




<p class="code-label">Antes de hacer (reset) y (run), ingrese también un comando (watch all) para que pueda ver todo lo que sucede durante la ejecución.</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule ideal-duck-bachelor
(bill big ?name)
(feet wide ?name)
=>
(printout t "The ideal duck is "
?name crlf))
CLIPS>
(deffacts duck-assets
(bill big Dopey)
(bill big Dorky)
(bill little Dicky)
(feet wide Dopey)
(feet narrow Dorky)
(feet narrow Dicky))
CLIPS> (watch facts)
CLIPS> (watch activations)
CLIPS> (reset)
==> f-1 (bill big Dopey)
==> f-2 (bill big Dorky)
==> f-3 (bill little Dicky)
==> f-4 (feet wide Dopey)
==> Activation 0 ideal-duck-bachelor: f-1,f-4  '==> f-5 (feet narrow Dorky)
==> f-6 (feet narrow Dicky)
CLIPS> (run)
The ideal duck is Dopey
CLIPS>
``` 



Cuando se ejecuta el programa, el primer patrón coincide con Dopey y Dorky, ya que ambos tienen sobrenombre del tipo Bill el Grande (bill big). La variable **?name** está ligada a cada nombre. Cuando CLIPS intenta hacer coincidir el segundo patrón de la regla, solo la variable **?name** que está vinculada a Dopey también satisface el segundo patrón del que posee el sobrenombre de pies anchos (feet wide).




##  4.8. El pato de la suerte




Muchas situaciones ocurren en la vida en las que es aconsejable hacer las cosas de manera sistemática. De esa manera, si sus expectativas no funcionan, puede volver a intentarlo sistemáticamente (como el algoritmo común para encontrar al cónyuge perfecto casándose una y otra vez).




Una forma de organizarse es mantener una lista. (Nota: si realmente quiere impresionar a la gente, muéstreles una lista de sus listas). En nuestro caso, mantendremos una lista de solteros de pato, con la perspectiva más probable de matrimonio al frente. Una vez que se haya identificado a un soltero de pato ideal, lo colocaremos al principio de la lista como el pato de la suerte.




<p class="code-label">El siguiente programa muestra cómo se puede hacer esto agregando un par de reglas a la regla ideal del pato-soltero.</p>
```scheme
(defrule ideal-duck-bachelor
(bill big ?name)
(feet wide ?name)
=>
(printout t "The ideal duck is "
?name crlf)
(assert (move-to-front ?name)))
(defrule move-to-front
?move-to-front <- (move-to-front ?who)
?old-list <-
(list $?front ?who $?rear)
=>
(retract ?move-to-front ?old-list)
(assert (list ?who ?front ?rear))
(assert (change-list yes)))
(defrule print-list
?change-list <- (change-list yes)
(list $?list)
=>
(retract ?change-list)
(printout t "List is : " ?list crlf))
(deffacts duck-bachelor-list
(list Dorky Dinky Dicky))
(deffacts duck-assets
(bill big Dicky)
(bill big Dorky)
(bill little Dinky)
(feet wide Dicky)
(feet narrow Dorky)
(feet narrow Dinky))
``` 



<p class="code-label">La lista original se proporciona en los **deffacts** de la lista de solteros de pato. Cuando se ejecuta el programa, proporcionará una nueva lista de posibles candidatos.</p>
```scheme
CLIPS> (unwatch all)
CLIPS> (reset)
CLIPS> (run)
The ideal duck is Dicky
List is : (Dicky Dorky Dinky)
CLIPS>
``` 



Observe la afirmación (change-list yest) en la regla de mover al primero de la lista. Sin esta afirmación, la regla de la lista de impresión siempre se activaría en la lista original. Esta confirmación con _assert_ es un ejemplo de un **hecho de control** _control fact_ realizado para controlar la activación de otra regla. Los hechos de control son muy importantes para controlar la activación de ciertas reglas, y debe estudiar este ejemplo detenidamente para comprender por qué se usa. Otro método de control son los módulos, como se explica en el _Manual de referencia de CLIPS_.




La regla de mover al frente elimina la lista anterior y confirma la lista nueva. Si la lista anterior no se extrajo ni retractó, por lo que habría dos activaciones en la agenda para la regla de lista de impresión, pero solo se dispararía una. Solo uno se activará porque la regla de lista de impresión elimina el hecho de control requerido para la otra activación de la misma regla. No sabría de antemano cuál se dispararía, por lo que la lista anterior podría imprimirse en lugar de la lista nueva.


