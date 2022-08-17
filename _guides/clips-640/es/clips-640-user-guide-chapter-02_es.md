---
layout: guide
ref:  c640ug02
lang:  es
idiom:  es-ES
imagepath:  '../images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug
toc:  true
title:  "CLIPS 6.4 Guía del usuario"
headtitle:  'Siguiendo las reglas'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Dr. Giarratano, Joseph C.'
department:  
authors:



departments:



chapter:  2
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'




date_published:  '2021-04-09'
date_modified:  '2022-08-09'

---




  
#  **Capitulo 2**
  

>  

#  2. Siguiendo las reglas



   
>Si quieres llegar a algún lado en la vida, no rompas las reglas, ¡crea tú las reglas!




##  2.1. Creando las buenas reglas




Para realizar un trabajo útil, un sistema experto debe tener reglas además de hechos. Ya que ha visto cómo se afirman y retractan los hechos, es hora de ver cómo funcionan las reglas. Una regla es similar a una declaración IF THEN en un lenguaje de procedimiento como Java, C o Ada.




<p class="code-label">Una regla IF THEN se puede expresar en una combinación de lenguaje natural y lenguaje informático de la siguiente manera:</p>
```scheme
IF certain conditions are true
THEN execute the following actions

``` 


Otro término para la declaración anterior es **pseudocódigo**, que literalmente significa código falso. Si bien la computadora no puede ejecutar directamente el pseudocódigo, sirve como una guía muy útil para escribir código ejecutable. El pseudocódigo también es útil para documentar reglas. Una traducción de reglas del lenguaje natural a CLIPS no es muy difícil si se tiene en mente la analogía (IF, THEN) esto es: SI, ENTONCES. A medida que crezca su experiencia con CLIPS, descubrirá que escribir reglas en CLIPS se vuelve más fácil. Puede escribir reglas directamente en CLIPS o cargar reglas desde un archivo de reglas creado por un editor de texto.



  
<p class="code-label">El pseudocódigo para una regla sobre sonidos de patos podría ser</p>
```scheme
IF the animal is a duck
THEN the sound made is quack
``` 



Lo siguiente es un hecho y una regla llamada pato que es el pseudocódigo anterior expresado en sintaxis CLIPS. El nombre de la regla sigue inmediatamente después de la palabra clave defrule.




<p class="code-label">Aunque puede ingresar una regla en una sola línea, se acostumbra colocar diferentes partes en líneas separadas para facilitar la lectura y la edición.</p>
```scheme
CLIPS> (unwatch facts)
CLIPS> (clear)
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS>
(defrule duck
    (animal-is duck)
=>
    (assert (sound-is quack)))
CLIPS>

``` 


Si escribe la regla correctamente como se muestra, debería volver a aparecer el indicador CLIPS. De lo contrario, verá un mensaje de error. Si recibe un mensaje de error, es probable que haya escrito mal una palabra clave o haya olvidado un paréntesis. Recuerde, el número de paréntesis izquierdo y derecho siempre debe coincidir en una declaración.





La misma regla se muestra a continuación con comentarios agregados para que coincidan con las partes de la regla. También se muestra el comentario de **encabezado de regla** opcional entre comillas, "Aquí viene el pato charlatán". Solo puede haber un comentario de encabezado de regla y debe colocarse después del nombre de la regla y antes del **primer patrón**. Aunque ahora solo estamos discutiendo la coincidencia de patrones con los hechos, de forma genérical, un patrón se puede comparar con una **entidad de patrón**. Una entidad de patrón o _pattern entity_ es un hecho o una instancia de una clase definida por el usuario. La coincidencia de patrones en los objetos se discutirá más adelante.




CLIPS intenta hacer coincidir el patrón de la regla con una entidad de patrón. Por supuesto, los espacios en blanco que consisten en espacios, tabulaciones y retornos de carro pueden usarse para separar los elementos de una regla para mejorar la legibilidad. Otros comentarios comienzan con un punto y coma y continúan hasta que se presiona la tecla de retorno de carro para terminar una línea.




<p class="code-label">CLIPS ignora los comentarios:</p>
```scheme
; Rule header
(defrule duck
    ; Comment
    "Here comes the quack"
     ; Pattern
        (animal-is duck)
=> ; THEN arrow
     ; Action  
     (assert (sound-is quack)))

``` 



>    &clubs; _Solo puede existir un nombre de regla a la vez en CLIPS._





Ingresar el mismo nombre de regla, en este caso `duck`, reemplazará cualquier regla existente con ese nombre. Es decir, si bien puede haber muchas reglas en CLIPS, solo puede haber una regla que se llame `duck`. Esto es análogo a otros lenguajes de programación en los que solo se puede usar un nombre de procedimiento para identificar un procedimiento de forma única.





<p class="code-label">La sintaxis general de una regla se muestra a continuación.</p>
```scheme
(defrule rule_name "optional_comment"
(pattern_1) ; Left-Hand Side (LHS)
(pattern_2) ; of the rule consisting
.           ; of elements before
.           ; the "=>"
.
(pattern_N)
=>
(action_1)  ; Right-Hand Side (RHS)
(action_2)  ; of the rule consisting
.           ; of elements after
.           ; the "=>". The last ")"
.           ; balances the opening
(action_M)) ; "(" to the left of
; "defrule". Be sure all
; your parentheses
; balance or you will
; get error messages

``` 


Toda la regla debe estar entre paréntesis. Cada uno de los **patrones de reglas** y **acciones** debe estar entre paréntesis. Una acción es en realidad una función que normalmente **no tiene valor de retorno**, pero realiza alguna acción útil, como (assert) o (retract). Por ejemplo, una acción podría ser (assert  (ducke)). Aquí el nombre de la función es `assert` y su argumento es `duck`. Tenga en cuenta que no queremos ningún valor de retorno, como un número. En cambio, queremos que se confirme el hecho (pato). Una **función** en CLIPS es una pieza de código ejecutable identificada por un nombre específico, que devuelve un valor útil o realiza un efecto secundario útil, como (printout) para volcar e imprimir un resultado.




   Una regla a menudo tiene múltiples patrones y acciones. El número de patrones y acciones no tiene por qué ser igual, por lo que se eligieron diferentes índices, N y M, para los patrones y acciones de la regla.




Se pueden escribir cero o más patrones después del encabezado de la regla. Cada patrón consta de uno o más campos. En la regla del pato, el patrón es (animal-es pato), donde los campos son `animal-is` y `pato`. CLIPS intenta comprobar la coincidencia de los patrones de reglas con los hechos en la lista de hechos. Si todos los patrones de una regla coinciden con los hechos, la regla se **activa** y se incluye en la **agenda**. La agenda es una colección de **activaciones** que son aquellas reglas que coinciden con entidades patrón. Cero o más activaciones pueden estar en la agenda.




El símbolo `=>` que sigue los patrones de una regla se llama flecha. La flecha representa el comienzo de la parte ENTONCES de una regla SI-ENTONCES (y puede leerse como `implica`).




La última parte de una regla es la lista de cero o más acciones que se ejecutarán cuando se active la regla. En nuestro ejemplo, la única acción es confirmar el hecho (sound-is quack) (el-sonido-es graznido). El término **fires** o disparos significa que CLIPS ha seleccionado una regla determinada para la ejecución de la agenda.




>    &clubs; _Un programa dejará de ejecutarse cuando no haya activaciones en la agenda._




Cuando hay múltiples activaciones en la agenda, CLIPS determina automáticamente qué activación es apropiada para ser dispararada. CLIPS ordena las activaciones en la agenda en términos de prioridad creciente o **prominencia** (_salience_).





La parte de la regla antes de la flecha se llama lado izquierdo **(LHS)** y la parte de la regla después de la flecha se llama lado derecho **(RHS)**. Si no se especifican patrones, CLIPS activa automáticamente la regla cuando se ingresa un comando **(reset)**.




##  2.2. Vamos a graznar




CLIPS siempre ejecuta las acciones en el RHS de la regla de mayor prioridad en la agenda. Luego, esta regla se elimina de la agenda y se ejecutan las acciones de la nueva regla de mayor prominencia. Este proceso continúa hasta que no hay más activaciones o se encuentra un comando para detener.




<p class="code-label">Puede comprobar lo que hay en la **agenda** con el comando agenda. Por ejemplo:</p>
```scheme
CLIPS> (agenda)
0 duck: f-1
For a total of 1 activation.
CLIPS>

``` 


El primer número '0' es la prominencia de la activación 'pato', y 'f-1' es el identificador de hecho del hecho (el-animal-es pato) (animal-is duck), que coincide con la activación. Si la prominencia de una regla no se declara explícitamente, CLIPS le asigna el valor predeterminado de cero, donde los posibles valores de prominencia oscilan entre -10 000 y 10 000. En este libro, usaremos la definición del término **default** o **predeterminado** en el sentido de la forma estándar.





<p class="code-label">Si solo hay una regla en la agenda, esa regla se activará. Dado que el patrón LHS de la regla del sonido del pato es</p>
```scheme
(animal-is duck)

``` 

este patrón se cumplirá con el hecho (animal-is duck) y, por lo tanto, la regla del sonido del pato debería activarse.




Se dice que cada campo del patrón es una **restricción literal**. El término **literal** significa que tiene un valor constante, a diferencia de una variable cuyo valor se espera que cambie. En este caso, los literales son `animal-is` y también, `duck`.




Para hacer que un programa **se ejecute** simplemente ingrese el comando de ejecución. Escriba (**run**) y presione la tecla de retorno de carro.


<p class="code-label">Luego escriba un (facts) para verificar que el hecho fue confirmado e introducido en CLIPS por la regla.</p>
```scheme
CLIPS> (run)
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (sound-is quack)
For a total of 2 facts.
CLIPS>

``` 


Antes de continuar, guardemos (**save**) la regla del sonido del pato con el comando (save) para que no tenga que escribirla nuevamente (si aún no la ha guardado en un editor).



<p class="code-label">Simplemente ingrese un comando como:</p>
```scheme
(save "duck.clp")

``` 



para guardar las reglas presentes en la memoria de CLIPS hacia el disco y nombrar el archivo `duck.clp` donde `.clp` es simplemente una extensión conveniente para recordarnos que este es un archivo de código fuente de CLIPS. Tenga en cuenta que guardar el código de la memoria CLIPS de esta manera solo conservará el comentario de encabezado de regla opcional entre comillas y no los comentarios de punto y coma.




##  2.3. Patea a tu pato




Una pregunta interesante se le puede ocurrir en este momento. ¿Qué pasa si haces un (run) de nuevo? Hay una regla y un hecho que satisface la regla, por lo que la regla debe activarse. Sin embargo, si intenta esto y (ejecuta) nuevamente, verá que la regla no se activará. Esto puede ser algo frustrante. Sin embargo, antes de hacer algo drástico para aliviar su frustración, como patear a su pato mascota, necesita saber un poco más sobre algunos principios básicos de los sistemas expertos.



Una regla se activa si sus patrones coinciden con:

1. una nueva entidad de patrón que no existía antes o,
2. una entidad de patrón que existía antes pero que se retractó y reafirmó, es decir, un "clon" de la entidad de patrón anterior y, por lo tanto, ahora es una nueva entidad de patrón.




La regla, y los índices de los patrones coincidentes, conforman la activación. Si la regla o la entidad del patrón, o ambas, cambian, se elimina la activación. Una activación también puede eliminarse mediante un comando o una acción de otra regla que se disparó antes y eliminó las condiciones necesarias para la activación.




El motor de inferencia ordena las activaciones según su prominencia. Este proceso de clasificación se denomina **resolución de conflictos** porque elimina el conflicto de decidir qué regla debe activarse a continuación. CLIPS ejecuta el RHS de la regla con mayor prominencia en la agenda y elimina la activación. Esta ejecución se llama disparo de la regla en analogía con el disparo de una neurona. Una neurona emite un pulso de voltaje cuando se aplica un estímulo apropiado. Después de que una neurona se dispara, se somete a refracción y no puede volver a dispararse durante un cierto período de tiempo. Sin **refracción**, las neuronas seguirían disparando una y otra vez con exactamente el mismo estímulo.




Sin refracción, los sistemas expertos siempre estarían atrapados en bucles triviales. Es decir, tan pronto como se active una regla, seguirá activando el mismo hecho una y otra vez. En el mundo real, el estímulo que provocó el disparo eventualmente desaparecería. Por ejemplo, un pato de verdad, podría alejarse nadando o conseguir un trabajo en el cine. Sin embargo, en el mundo de la informática, una vez que se almacenan los datos, permanecen allí hasta que se eliminan explícitamente o se apaga la alimentación.




El siguiente ejemplo muestra las activaciones y el disparo de una regla. Tenga en cuenta que los comandos de observación  (watch) se utilizan para mostrar más cuidadosamente cada hecho y activación. La flecha que va hacia la derecha significa un hecho o activación de entrada, mientras que una flecha hacia la izquierda significa un hecho o activación de salida.



<p class="code-label">Se han agregado comentarios en azul/cursiva para explicación. No verá estos en la salida real:</p>
```scheme
CLIPS> (clear)
CLIPS>
(defrule duck
   (animal-is duck)   
=>
    (assert (sound-is quack)))
CLIPS> (watch facts)
CLIPS> (watch activations)
CLIPS> (assert (animal-is duck))
==> f-1 (animal-is duck)
; Activation salience is 0 by default,
; then rule name:pattern entity index
==> Activation 0 duck: f-1
<Fact-1>
; Notice that duplicate fact
; cannot be entered
CLIPS> (assert (animal-is duck))
<Fact-1>
CLIPS> (agenda)
0 duck: f-1
For a total of 1 activation.
CLIPS> (run)
==> f-2 (sound-is quack)
; Nothing on agenda after rule fires
; Even though fact matches rule,
; refraction will not allow this
; activation because the rule already
; fired on this fact
CLIPS> (agenda)
CLIPS> (facts)
f-1 (animal-is duck)
f-2 (sound-is quack)
For a total of 2 facts.
CLIPS> (run)
CLIPS>

``` 





Puede hacer que la regla se active nuevamente si retracta el hecho y luego lo vuelve a confirmar como un hecho nuevo.


##  2.4. Muéstrame las reglas

A veces, es posible que desee ver una regla mientras está en CLIPS. Hay un comando llamado **ppdefrule**, o imprimir elegantemente la regla, que imprime las  reglas.




<p class="code-label">Para ver una regla, especifique el nombre de la regla como argumento para _ppdefrule_. Por ejemplo;</p>
```scheme
CLIPS> (ppdefrule duck)
(defrule MAIN::duck
(animal-is duck)
=>
(assert (sound-is quack)))
CLIPS>

``` 



CLIPS pone diferentes partes de la regla en diferentes líneas por el bien de la legibilidad. Los patrones antes de la flecha todavía se consideran el LHS y las acciones después de la flecha todavía se consideran el RHS de la regla. El término MAIN hace referencia al módulo MAIN o PRINCIPAL en el que se encuentra esta regla de forma predeterminada. Puede definir módulos para poner reglas, de una forma análoga a la empleada para poner las declaraciones y funciones en diferentes paquetes, módulos, procedimientos o funciones que es habitual en otros lenguajes de programación. El uso de módulos facilita la escritura de sistemas expertos que tengan muchas reglas, ya que estos pueden agruparse con sus propias agendas para cada módulo. Para obtener más información, consulte el _Manual de referencia de CLIPS_.




¿Qué sucede si desea imprimir una regla pero no puede recordar el nombre de la regla? No hay problema. Simplemente use el comando de reglas en respuesta a un aviso de CLIPS y CLIPS imprimirá los nombres de todas las reglas.



<p class="code-label">Por ejemplo, ingrese:</p>
```scheme
CLIPS> (rules)
duck
For a total of 1 defrule.
CLIPS>

``` 


##  2.5. Escríbeme




Además de afirmar hechos en el RHS de las reglas, también puede imprimir información utilizando la función de impresión **printout**. CLIPS también tiene una palabra clave de retorno de carro/salto de línea llamada **crlf** que es muy útil para mejorar la apariencia de la salida al formatearla en diferentes líneas.



<p class="code-label">Para variar, el crlf no se incluye entre paréntesis. Como ejemplo:</p>
```scheme
CLIPS>
  (defrule duck
    (animal-is duck)
=>
     ;; Be sure to type in the "t"
     (printout t "quack" crlf))
==> Activation 0 duck: f-1
CLIPS> (run)
quack
CLIPS>

``` 



La salida es el texto entre comillas dobles. Asegúrese de escribir la letra "**t**" después del comando de impresión. Esto le dice a CLIPS que envíe la salida al dispositivo de **salida estándar de su computadora**. Generalmente, el dispositivo de salida estándar es su terminal (de ahí la letra `t` después de la impresión). Sin embargo, esto se puede redefinir para que el dispositivo de salida estándar sea algún otro dispositivo, como un módem o un disco.




##  2.6. Otras características




El comando **declare prominencia** (declare salicece) proporciona un control explícito sobre qué reglas se incluirán en la agenda. Debe tener cuidado al usar esta función con demasiada libertad para que su programa no se vuelva demasiado controlado. Una forma de hacer que una regla se active nuevamente es forzar la reactivación de la regla mediante el comando de regla de actualización **refresh**.




El comando **load** de carga la regla que había guardado previamente en el disco en el archivo `duck.clp` o cualquier nombre y directorio en el que lo haya guardado. Puede cargar un archivo de reglas hechas en un editor de texto en CLIPS usando el comando de carga.




Una forma más rápida de cargar archivos es guardarlos primero en un formato binario legible por máquina con el comando guardar binario llamado **bsave**. El comando de carga binaria, **bload**, se puede usar para leer estas reglas binarias en la memoria CLIPS mucho más rápido, ya que CLIPS no tiene que volver a interpretar los archivos.




Otros dos comandos útiles le permiten guardar y cargar hechos usando un archivo. Estos son **save-facts** que literamente es guardar-hechos y **load-facts** o cargar-hechos. (_save-facts_) guardará todos los hechos en la lista de hechos en un archivo mientras que (_load-facts_) cargará los hechos de un archivo en la lista de hechos.




El comando **batch** realiza una lectura y ejecución paso a paso de los comandos redactados sobre un  archivo como si estuvieran escritos en el top-level (en la propia shell, en el nivel superior). Otro comando útil proporciona una interfaz para su sistema operativo. El comando **system** permite la ejecución de comandos del sistema operativo o ejecutables dentro de CLIPS. Para obtener más información sobre todos estos temas, consulte el _Manual de referencia de CLIPS_.


