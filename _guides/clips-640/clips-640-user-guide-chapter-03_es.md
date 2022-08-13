---
layout: guide
ref:  c640ug03
lang:  es
idiom:  es-ES
imagepath:  'images/'
images:
  -  'cug-640-banner.png'
  -  'clips_logo.png'

manualcode:  c640ug

toc:  true

title:  "CLIPS 6.4 Guía de usuario"
subtitle:  "En los primeros dos capítulos, aprendió los fundamentos de CLIPS. Ahora verá cómo construir sobre esa base para crear programas más potentes."
headtitle:  'Incorporando los detalles'
shorttitle:  'Giarratano, J.C. (2021)'
year:  '2021'
author:  'Dr. Giarratano, Joseph C.'
department:  
authors:

departments:

chapter:  3
doi:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/clips_documentation_640.zip/download'
url:  'https://sourceforge.net/projects/clipsrules/files/CLIPS/6.40/'
editor:  'Gary Riley'
pubdate:  '2021-04-09'
license:  'GNU Lesser General Public License v3.0'
date_published:  '2021-04-09'
date_modified:  '2022-08-14'

---




  
#  **Capítulo 3**
  

  

#  3. Agregar los detalles



   
>No es el panorama general el problema, son los detalles




En los primeros dos capítulos, aprendió los fundamentos de CLIPS. Ahora verá cómo construir sobre esa base para crear programas más potentes.




##  3.1. Parar y Continuar




Hasta ahora, solo ha visto el tipo de programa más simple que consta de una sola regla. Sin embargo, los sistemas expertos que consisten en una sola regla no son muy útiles. Los sistemas expertos prácticos pueden consistir en cientos o miles de reglas. Ahora echemos un vistazo a una aplicación que requiere varias reglas.




Suponga que desea escribir un sistema experto para determinar cómo debe responder un robot móvil a un semáforo. Es mejor escribir este tipo de problema usando varias reglas.




<p class="code-label">Por ejemplo, las reglas para las situaciones de luz roja y verde se pueden escribir de la siguiente manera.</p>
```scheme
  (defrule red-light
(light red)
=>
(printout t "Stop" crlf))

(defrule green-light
(light green)
=>
(printout t "Go" crlf))

``` 

Una vez que las reglas se hayan ingresado en CLIPS, confirme con _assert_ un hecho (luz roja) y ejecute. Verá "Stop" impreso. Ahora confirme el hecho (luz verde) y ejecute con (run). Debería ver "Adelante" impreso.




##  3.2. Dar un paseo




Si lo piensa, existen otras posibilidades además de los simples casos rojo, verde y amarillo. Algunos semáforos también tienen una flecha verde para giros a la izquierda protegidos. Algunos tienen una mano que se ilumina para indicar si una persona puede caminar o no. Algunos tienen letreros que dicen caminar o no caminar. Por lo que dependiendo de si nuestro robot camina o conduce, puede que tenga que prestar atención a diferentes señales.




La información sobre caminar o conducir debe confirmarse con _assert_ además de la información sobre el estado de la luz. Se pueden hacer reglas para cubrir estas condiciones pero, esas reglas deben tener más de un patrón.




<p class="code-label">Por ejemplo, supongamos que queremos que una regla se active si el robot está caminando y si el letrero de caminar dice caminar. Una regla podría escribirse de la siguiente manera:</p>
```scheme
(defrule take-a-walk
(status walking)
(walk-sign walk)
=>
(printout t "Go" crlf))

```


La regla anterior tiene dos patrones. Ambos patrones deben ser satisfechos por hechos en la lista de hechos para que la regla se active. Para ver cómo funciona esto, ingrese la regla y luego confirme con _assert_ los hechos (status walking) y (walk-sign walk). Cuando ejecuta con (run), el programa imprimirá "Go" ya que se cumplen ambos patrones y se activa la regla.




Puede tener cualquier número de patrones o acciones en una regla. El punto importante a tener en cuenta es que la regla se coloca en la agenda solo si todos los patrones se satisfacen con hechos. Este tipo de restricción se denomina **elemento condicional AND lógico (CE)** en referencia a la relación AND de la lógica booleana. Se dice que una relación AND es verdadera solo si todas sus condiciones son verdaderas.




   Dado que los patrones son del tipo AND lógico, la regla no se activará si solo se cumple uno de los patrones. Todos los hechos deben estar presentes antes de que se cumpla el LHS de una regla y la regla se coloque en la agenda.




##  3.3. Una cuestión de estrategia




La palabra **estrategia** fue originalmente un término militar para la planificación y operaciones de la guerra. Hoy en día, el término estrategia se usa comúnmente en los negocios (porque los negocios son la guerra) para referirse a los planes de alto nivel de una organización para lograr sus objetivos, por ejemplo, “¡Hacer mucho dinero vendiendo más hamburguesas grasosas que nadie en el mundo!"




En los sistemas expertos, un uso del término estrategia es en la resolución de conflictos de activaciones. Ahora podría decir: “Bueno, solo diseñaré mi sistema experto para que solo se pueda activar una regla a la vez. Entonces no hay necesidad de resolución de conflictos”. La buena noticia es que, si tiene éxito, la resolución de conflictos es realmente innecesaria. La mala noticia es que este éxito prueba que su aplicación puede ser bien representada por un programa secuencial. Por lo tanto, debería haberlo codificado en C, Java o Ada en primer lugar y no haberse molestado en escribirlo como un sistema experto.




CLIPS ofrece siete modos diferentes de resolución de conflictos: profundidad, amplitud, LEX, MEA, complejidad, simplicidad y aleatorio. Es difícil decir que uno es claramente mejor que otro sin considerar la aplicación específica. Incluso entonces, puede ser difícil juzgar cuál es "mejor". Para obtener más información sobre los detalles de estas estrategias, consulte el _Manual de referencia de CLIPS_.




La **estrategia de profundidad** es la **estrategia predeterminada** estándar de CLIPS. La configuración predeterminada se establece automáticamente cuando CLIPS se inicia por primera vez. Posteriormente, puede cambiar la configuración predeterminada. En la estrategia de profundidad, las nuevas activaciones se colocan en la agenda después de las activaciones con mayor prominencia, pero antes de las activaciones con igual o menor prominencia. Todo esto simplemente significa que la agenda está ordenada de mayor a menor prominencia.




>   &clubs;   _En este libro, todas las discusiones y ejemplos asumirán la estrategia de profundidad._




Ahora que todas estas configuraciones opcionales diferentes están disponibles, asegúrese de que antes de ejecutar un sistema experto desarrollado por otra persona, sus configuraciones sean las mismas que las de ellos. De lo contrario, puede encontrar que la operación es ineficiente o incluso incorrecta. De hecho, es una buena idea codificar explícitamente todas las configuraciones en cualquier sistema que desarrolle para que se configure correctamente.




##  3.4. Dame los hechos con `Deffacts`




Mientras trabaja con CLIPS, es posible que se canse de escribir las mismas afirmaciones desde el nivel superior. Si va a utilizar las mismas aserciones cada vez que se ejecuta un programa, primero puede cargar las aserciones desde un disco utilizando un archivo por lotes. Una forma alternativa de ingresar hechos es usando la palabra clave definir hechos, **deffacts**.




<p class="code-label">Por ejemplo:</p>
```scheme
CLIPS> (unwatch facts)
CLIPS> (unwatch activations)
CLIPS> (clear)
CLIPS>
(deffacts walk "Some facts about walking"
; status fact to be asserted
(status walking)
; walk-sign fact to be asserted
(walk-sign walk))
CLIPS> (reset)
; reset causes facts from
; deffacts to be asserted
CLIPS> (facts)
f-1 (status walking)
f-2 (walk-sign walk)
For a total of 2 facts.
CLIPS>
```



El nombre obligatorio de esta instrucción deffacts, **walk**, sigue a la palabra clave _deffacts_. Después del nombre hay un comentario opcional entre comillas dobles. Al igual que el comentario opcional de una regla, el comentario (deffacts) se conservará con (deffacts) después de que CLIPS lo cargue. Después del nombre o comentario están los hechos que se afirmarán en la lista de hechos. Los hechos en una declaración de deffacts se vuelven a confirmar en la memoria usando el comando CLIPS (reset).




El (reset) tiene una ventaja en comparación con un comando (clear) en que (reset) no elimina todas las reglas. El (reset) deja tus reglas intactas. Me gusta (clear), porque elimina todas las reglas activadas de la agenda y también elimina todos los hechos antiguos de la lista de hechos. Dar un comando (reset) es una forma recomendada de comenzar la ejecución del programa, especialmente si el programa se ha ejecutado antes y la lista de hechos está repleta de datos antiguos.




En resumen, el (reset) hace dos cosas por los hechos.


  

1. Elimina hechos existentes de la lista de hechos (fact-list), lo que puede eliminar reglas activadas de la agenda.


2. Realiza una confirmación y re-entrada de los hechos a partir de declaraciones existentes (deffacts).




En realidad, el (reset) también realiza las operaciones correspondientes en los objetos. Elimina instancias y confirma y añade de nuevo las instancias declaradas con  **definstances**.




##  3.5. Eliminación selectiva




El comando **undeffacts** elimina a (deffacts) del proceso de recarga de los hechos con assert, eliminando además los deffacts de la memoria.



<p class="code-label">Por ejemplo:</p>
```scheme
CLIPS> (undeffacts walk)
CLIPS> (reset)
CLIPS> (facts)
CLIPS>

``` 


Este ejemplo demuestra cómo se ha suprimido la declaración de **walk** (con deffacts). Para restaurar una declaración de deffacts después de un comando (undeffacts), debe ingresar la declaración de los deffacts nuevamente. Además de los propios hechos, CLIPS también le permite eliminar reglas de forma selectiva utilizando **undefrule**.




##  3.6. ¡Míralo!




Puedes **ver reglas**  (watch rules) disparándose y **ver activaciones** (watch activations) en la agenda. Las **estadísticas de vigilancia** (watch statistics) que imprimen información sobre el número de reglas activadas, el tiempo de ejecución, las reglas por segundo, el número medio de hechos, el número máximo de hechos, el número medio de activaciones y el número máximo de activaciones. La información estadística puede ser útil para **afinar** un sistema experto y para optimizar su velocidad. Otro comando, llamado **ver compilaciones** (watch compilations), muestra información cuando se cargan las reglas. El comando (watch all) vigilará todo.




La impresión de la información de **watch** en la pantalla o en el disco con el comando **dribble** ralentizará un poco su programa porque CLIPS usa más tiempo para imprimir o guardar en el disco. El comando **dribble-on** almacenará todas las entradas y salidas ingresadas en el símbolo del sistema en un archivo de disco hasta que se ingrese el comando **dribble-off**. Esto es conveniente para proporcionar un registro permanente de todo lo que sucede.




Estos comandos son los siguientes.



```scheme
(dribble-on <filename>)
(dribble-off <filename>)
```


Otro comando de depuración útil es (run), que toma un argumento opcional del número de activaciones de reglas. Por ejemplo, un comando (run 21) le diría a CLIPS que ejecute el programa y luego se detenga después de que se activa la regla 21 (_N.d.T_ hasta la veintiunava regla, que estaba activada en la agenda). Un comando (run 1) le permite recorrer un programa ejecutando una a una las reglas activadas.




Al igual que muchos otros lenguajes de programación, CLIPS también le brinda la capacidad de establecer puntos de interrupción. Un punto de interrupción es simplemente un indicador para que CLIPS detenga la ejecución justo antes de ejecutar una regla específica. El comando **set-break* establece un punto de interrupción. El comando **remove-break** eliminará un punto de interrupción que se haya establecido. El comando **show-breaks** enumerará todas las reglas que tienen puntos de interrupción establecidos.




La sintaxis de estos comandos para el argumento `<rulename>` se muestra a continuación.



```scheme
(set-break <rulename>)
(remove-break <rulename>)
(show-breaks)
```



##  3.7. Un buen partido (una coincidencia correcta)




Puede encontrarse con una situación en la que está seguro de que una regla debe activarse pero, la regla no se activa. Si bien es posible que esto se deba a un error en CLIPS, no es muy probable debido a la gran habilidad de las personas que programaron CLIPS (NOTA: ANUNCIO COMERCIAL PAGADO PARA LOS DESARROLLADORES).




En la mayoría de los casos, el problema ocurre debido a la forma en que escribió la regla. Como ayuda para la depuración, CLIPS tiene un comando llamado **matches** que puede decirle qué patrones en una regla coinciden con los hechos. Los patrones que no coinciden impiden que la regla se active. Una razón común por la que un patrón no coincide con un hecho es el resultado de escribir mal un elemento en el patrón o en la previa confirmación con del hecho con _assert_.




<p class="code-label">El argumento de (matches) es el nombre de la regla que se comprobará en busca de coincidencias. Para ver cómo funciona (matches), primero (clear), luego ingrese la siguiente regla.</p>
```scheme
(defrule take-a-vacation
; Conditional element 1
(work done)
; Conditional element 2
(money plenty)
; Conditional element 3
(reservations made)
=>
(printout t "Let's go!!!" crlf))

```


A continuación se muestra cómo se utiliza (matches). Introduzca los comandos como se muestra. Observe que (watch facts) está activado.




<p class="code-label">Esta es una buena idea cuando confirma e introduce hechos manualmente, ya que le brinda la oportunidad de verificar la ortografía de los hechos.</p>
```scheme
CLIPS> (watch facts)
CLIPS> (assert (work done))
 ==> f-1 (work done)
<Fact-1>
CLIPS> (matches take-a-vacation)
Matches for Pattern 1
f-1
Matches for Pattern 2
None
Matches for Pattern 3
None
; CE is conditional element
Partial matches for CEs 1 - 2
None
Partial matches for CEs 1 - 3
None
Activations
None
; The return value indicates
; the total patterns
; matched, the total partial
; matches, and the
; total activations
(1 0 0)
CLIPS>
``` 


El hecho con el identificador de hecho f-1 coincide con el primer patrón o elemento condicional de la regla y lo informa (matches). Dado que una regla tiene N patrones, el término coincidencias parciales se refiere a cualquier conjunto de coincidencias de los primeros N-1 patrones con hechos. Es decir, las coincidencias parciales comienzan con el primer patrón de una regla y terminan con cualquier patrón hasta el último (N-ésimo) patrón, pero sin incluirlo. En cuanto no se puede hacer una coincidencia parcial, CLIPS no realiza más comprobaciones. Por ejemplo, una regla con cuatro patrones tendría coincidencias parciales del primer y segundo patrón y también del primero, segundo y tercer patrón. Si todos los N patrones coinciden, la regla se activará.




##  3.8. Otras características




Algunos comandos adicionales son útiles con valores predeterminados. Por ejemplo, el comando **list-deffacts** enumerará los nombres de los valores predeterminados actualmente cargados en CLIPS. Otro comando útil es **ppdeffacts** que imprime los hechos almacenados en un archivo deffacts.




Otras funciones le permiten manipular cadenas fácilmente:


- **assert-string**: realiza una aserción de un hecho empleando una cadena como argumento y confirmando e introducciendo el hecho en la memoria, y sin que ese hecho tenga que contener solo campos tipo cadena.


- **str-cat**: construye una cadena entre comillas simples a partir de elementos individuales mediante la concatenación de cadenas. str-index: Devuelve un índice de cadena de la primera aparición de una subcadena.


- **sub-string**: Devuelve una subcadena de una cadena.


- **str-compare**: Realiza una comparación de cadenas.


- **str-length**: Devuelve la longitud de la cadena, que es la longitud de una cadena.


- **sym-cat**: Devuelve un símbolo concatenado.




Si desea imprimir una variable multicampo sin paréntesis, la forma más sencilla es utilizar la función de implosión de cadenas, **implode$**.


