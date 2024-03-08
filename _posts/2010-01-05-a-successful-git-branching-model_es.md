---
layout: post

title:  "Método para aplicar Git-Branching con éxito"
headtitle:  'Un método para aplicar Git-Branching con éxito (2010)'
shorttitle:  'Driessen, Vincent (2010)'


ref: gitBranching2010

lang:  es
idiom:  es_ES

author: "Vincent Driessen"


department: '<br>Website: https://nvie.com/ <br>Thoughts and writings by Vincent Driessen.'
date: 2010-01-05 09:48:44 +0100


categories: posts
menu:  false
toc: true


imagepath:  '/assets/imgs/'
images:
  -  'git-model2x.png'


license: CC-BY

---





**_Vincent Driessen_** (2010)

>  En esta publicación expongo el modelo de desarrollo que presenté hace un año, aproximadamente, para algunos de mis proyectos (tanto en el trabajo como en privado) y que ha resultado ser un gran éxito. 

* Post original localizado en el Blog de: **_Vincent Driessen_**[^VINCENT].



>  ... He tenido la intención de escribir sobre esto desde hace un tiempo pero, nunca he encontrado el tiempo para hacerlo hasta ahora. No hablaré sobre los detalles de ningún proyecto, simplemente hablaré sobre la estrategia de creación de Ramas y la gestión del proceso de paso a producción de proyectos de desarrollo de software.


![Modelo Driessen para la gestión de versiones con Git]({{  post.url | prepend: site.baseurl  }}/assets/imgs/git-model2x.png){:width="450px"}



## 1. ¿Por qué Git?

En la Web se pueden consultar discusiones exhaustivas sobre los pros y contras de Git en comparativas con otros sistemas centralizados de control de versiones de código. Hay muchas guerras abiertas que están en llamas por allí. Como desarrollador, prefiero Git por encima de todas las demás herramientas de hoy en día. Git realmente cambió la forma en que los desarrolladores piensan al fusionar y crear ramas en los proyectos de código. Desde el clásico mundo de CVS y Subversión del que provengo, la fusión y creación de ramas siempre ha sido considerada un tanto aterradora ("Cuidado con los conflictos de fusión, que te muerden!") Y eso es algo que sólo haces de vez en cuando.

Pero con Git, realizar esas acciones es extremadamente simple y, en realidad, se consideran una de las partes centrales de tu flujo de trabajo habitual. Por ejemplo, en los libros de los CVS y Subversion, la bifurcación y la fusión se comentan por primera vez en los capítulos posteriores (para usuarios avanzados), mientras que en cada libro de Git, ya está cubierto en el capítulo 3 (conceptos básicos).

Como consecuencia de su simplicidad y naturaleza repetitiva, la creación de ramas y la fusión ya no son algo a lo que temer. Se supone que las herramientas de control de versiones ayudan a la bifurcación / fusión más que cualquier otra cosa.

Ya basta de herramientas, veamos el modelo de desarrollo. El modelo que voy a presentar aquí no es más que un conjunto de procedimientos que cada miembro del Equipo de Desarrollo debe seguir para llegar a un proceso  administrado del desarrollo de software.




## 2. Centralizado pero, descentralizado

La configuración del Repositorio que vamos a utilizar y que funciona correctamente con este modelo de Ramas es aquel que posee un Repositorio Central `real`. Tenga en cuenta que decir que ese repositorio es central es sólo una consideración. (Puesto que que Git es un Distributed VCS y no existe, a nivel técnico, un repositorio central). Nos referiremos a este Repositorio Central como `origin`. Ese nombre, ya debería ser familiar para todos los usuarios de Git.

![Descentralizado pero centralizado (Vincent Driessen)]({{  post.url | prepend: site.baseurl  }}/assets/imgs/centr-decentr2x.png ){:width="450px"}


Cada desarrollador, "tira de" (`git pull`) y "empuja hacia" (`git push`)  el Repositorio Central denominado  `origin`. Pero además de esas actuaciones pull-push de carácter centralizado, cada desarrollador también puede obtener los cambios realizados por otros compañeros,  formando Equipos-Secundarios (Sub-Equipos). Eso podría ser útil por ejemplo, para trabajar dos o más desarrolladores juntos en una nueva característica grande, antes de llevar el trabajo en progreso al Repositorio `origin` de manera prematura. En la figura anterior, hay Sub-Equipos formados por: Alice y Bob, por Alice y David, y por Clair y David. 


Técnicamente, esto no significa otra cosa que: Alice, ha definido un Repositorio Remoto mediante la sentencia  `git remote` denominado como `bob` que apunta hacia el repositorio del propio Bob, y viceversa.



## 3. Las ramas principales


![Ramas principales (Vincent Driessen)]({{  post.url | prepend: site.baseurl  }}/assets/imgs/main-branches2x.png){:width="350px" align="left" hspace="20px"  border="1px"}



En esencia, este método (o modelo) de desarrollo está inspirado en gran medida por los modelos pre-existentes. El repositorio central (`origin`) posee dos ramas principales, ambas con una vida infinita:

* Rama `master`   (producción)
* Rama `develop`  (desarrollo)

La rama `master` sobre el Repositorio Central `origin`, ya debería ser familiar para los usuarios de Git. Paralelamente a esa rama `master`, existirá otra rama llamada `develop`.


Consideramos que `origin/master` es la rama principal en el repositorio central donde el código fuente del commit denominado HEAD, reflejará siempre el estado del código que está preparado para pasar al entorno de producción.


Y establecemos que `origin/develop` es la rama principal en el repositorio central donde el código fuente de HEAD, reflejará siempre un estado del código con los últimos cambios desarrollados que se incorporarán a la próxima versión. Algunos llaman a esta rama, la "rama de integración". Ahí, es donde se crean las compilaciones nocturnas automatizadas.

Cuando el código fuente en la rama de `develop` alcanza un punto estable y está listo para ser liberado, todos los cambios deben fusionarse nuevamente en la rama `master` de alguna manera y luego, etiquetarse con un número de versión. Se analizará en detalle cómo se hará esto más adelante.

Por lo tanto, cada vez que los cambios se fusionan nuevamente en el `master`, esa será por definición, una nueva versión de producción. Y debemos ser muy estrictos con esto, por lo que teóricamente, podríamos usar un script que llame a Git para construir y desplegar automáticamente nuestro software en nuestros servidores del entorno de producción, cada vez que se realice un `git commit` sobre la rama principal `master` del repositorio central `origin`.


## 4. Las Ramas de apoyo


Junto a las dos ramas principales `master` y `develop`, nuestro modelo de desarrollo utiliza una variedad de ramas de apoyo para facilitar el desarrollo paralelo entre los miembros del equipo, para facilitar el seguimiento de características, para preparar lanzamientos de producción y para ayudar a solucionar rápidamente los problemas en producción que aparecen en la vida real. A diferencia de las ramas principales, estas ramas de apoyo siempre tienen un tiempo de vida limitado ya que, eventualmente, son eliminadas.

Los diferentes tipos de ramas que podemos usar son:

* Ramas tipo `Requisitos funcionales` (Feature branches)
* Ramas tipo `Número de Release`      (Release branches)
* Ramas tipo `Parches de reparación`  (Hotfix branches)


Cada una de estas ramas tiene un propósito específico y están sujetas a reglas estrictas en cuanto a cuáles deben ser las ramas que las generan y cuáles deben ser las ramas objetivo donde se deben fusionar cada uno de sus cambios. Esto lo revisaremos en un minuto.


Desde un punto de vista técnico, estas ramas no deben ser consideradas "especiales". Los tipos de las ramas se clasifican en función de cómo las usemos. Por supuesto, las ramas de apoyo son las viejas y conocidas ramas de `git`.




### 4.1. Ramas de tipo: Requisito-Funcional


Deberían separarse a partir de:

     `develop`

Deben fusionarse nuevamente contra:
     
     `develop`
     
Por convenio, su nomenclatura será:
   
     Cualquier nombre excepto: `master`, `develop`, `release-*`, o `hotfix-*`

Las ramas de __Requisitos-Funcionales__ (a veces llamadas ramas temáticas) se utilizan para desarrollar nuevas funcionalidades que se incorporarán en la próxima versión o, para una versión futura. Cuando se comienza a desarrollar una nueva funcionalidad, la versión del producto donde se incorporará esa característica es desconocida en ese momento. El objetivo de las ramas dedicadas a crear nuevas Funcionalidades es que dichas ramas existirán mientras esa nueva característica o funcionalidad esté en desarrollo y que; sólo serán fusionadas hacia la rama principal `develop` (para que queden agregadas definitivamente las nuevas funcionalidades a la próxima versión) o bien serán simplemente eliminadas (en caso de que el experimento haya sido un fracaso).


> Las ramas de Requisitos-Funcionales normalmente existirán sólo en los Repositorios Locales de los desarrolladores, nunca en el Repositorio `origin`.


#### 4.1.1. Crear una rama de Requisito Funcional

Cuando se comienza a trabajar sobre una nueva Funcionalidad, se creará una imagen de la rama `develop`. 

````shell
    $ git checkout -b myfeature develop
    Creación y desplazamiento (de forma simultánea) a la rama: "myfeature"
````      
      
  
#### 4.1.2. Incorporación de una Funcionalidad finalizada

Los Requisitos Funcionales finalizados deberían ser fusionados contra la rama `develop` para que estos sean definitivamente incorporados a la nueva versión.



````shell
    $ git checkout develop
      Cambiarse a la rama 'develop' (Local)
      
    $ git merge --no-ff myfeature
      Fusionar sin rebasar la rama `develop` ea1b82a..05e9557
      (Sumario de modificaciones)
      
    $ git branch -d myfeature
      Eliminar la rama myfeature (fue la número: 05e9557).
      
    $ git push origin develop
      Sincronizar contra el Repositorio Central `origin`, la rama `develop`.
````




El parámetro `--no-ff` provoca que la fusión genere un nuevo objeto `commit` sobre la rama `develop`, incluso si esa fusión se pudiese realizar con una incorporación inmediata (fast-forward) de los cambios incorporados por la nueva funcionalidad en el código de la rama `develop`. Esto evita perder información sobre la existencia histórica de la rama que permitió crear aquel Requisito-Funcional y agregar todos los `commit` que  conformaron la nueva funcionalidad. En la figura, a continuación, se muestran las diferencias de ambas formas de fusionar (con y sin `--no-ff`):



![Incorporación de Funcionalidades (Vincent Driessen)]({{  post.url | prepend: site.baseurl  }}/assets/imgs/merge-without-ff2x.png){:width="450px" hspace="20px"  border="1px"}



En el segundo caso, es imposible analizar, a partir del histórico de `commits` de Git, cuál de los `commit` ha implementado la funcionalidad en todo su conjunto: tendrías que leer manualmente todos los mensajes de registro. Revertir entonces, una funcionalidad completa  (es decir, un grupo de `commits`) sería un verdadero dolor de cabeza en el segundo caso, mientras que, se hace fácilmente, si se utiliza el parámetro `--no-ff`.

Sí, esta forma de actuar creará algunos `comits` más (vacíos) pero, la ganancia será mucho mayor que el coste.


### 4.2. Ramas de tipo: Número de Release


Deberían separarse a partir de:

     `develop`

Deben fusionarse nuevamente contra:
     
     `develop` y `master`
     
Por convenio, su nomenclatura será:
   
     `release-*`



     
Las ramas de apoyo de tipo Número de Release (`release-*`), permiten preparar una nueva versión del proyecto para su lanzamiento. Estas ramas permiten realizar ajustes de última hora y también realizar modificaciones cruzadas sobre los archivos. Además, permiten correcciones de errores menores y la preparación de los Meta-Datos para la nueva versión (número de versión, las fechas de compilación, etc.). Al hacer todo este trabajo en una rama Número de Release (`release-*`), la rama `develop` quedará limpia, de manera que podrá recibir nuevas funcionalidades pertenecientes a la próxima versión.

El momento clave para crear una nueva Rama Número de Release (`release-*`) y realizar su extracción de la rama principal `develop`, se produce cuando la rama `develop` refleja (casi por entero) el estado deseado para la nueva versión del producto. Al menos, con todas las funcionalidades que estaban destinadas a esa versión deberían ya estar fusionadas sobre `develop` en este momento. Y, todas las funcionalidades destinadas a futuras versiones deberían esperar a ser creadas, hasta que esta Rama Número de Release (`release-*`) se haya vuelto a fusionar sobre `develop`.

Es exactamente durante la creación de la rama tipo Número de Release (`release-*`) cuando se le asigna un número de versión y, no antes. Hasta ese momento, la rama de desarrollo (`develop`) reflejaba los cambios para la "próxima versión" pero, no estaba claro si esa "próxima versión" se convertirá en 0.3 ó en 1.0, hasta que se inicie la Rama Número de Release (`release-*`). Esa decisión se toma, en el momento de inicio de creación de la Rama Número de Release (`release-*`) y se emplearán las reglas establecidas por el proyecto para el establecimiento del número de versión.


####  4.2.1. Crear una Rama de Versión


Las ramas de Número de Release  (`release-*`) se crean a partir de la rama (`develop`). Por ejemplo, supongamos que la versión 1.1.5 es la versión de producción actual y tenemos una versión próxima muy importante para liberar. El estado de la rama de desarrollo (`develop`) estará listo para realizar ese "próximo lanzamiento" y hemos decidido que se convertirá en la versión 1.2 (en lugar de 1.1.6 o 2.0). Así que, dejamos de crear nuevas ramas y establecemos sobre la rama de Número de Release, un nombre que refleja el nuevo número de versión:


````shell
    $ git checkout -b release-1.2 develop
    Creada y cambiado a nueva rama "release-1.2"
    
    $ ./bump-version.sh 1.2
    Archivos modificados correctamente, version bumped to 1.2.
    
    $ git commit -a -m "Bumped version number to 1.2"
    [release-1.2 74d9424] Bumped version number to 1.2
    1 files changed, 1 insertions(+), 1 deletions(-)
    
````


Después de crear la nueva rama (`release-1.2`) y cambiarse a ella, estampamos el número de versión en los archivos afectados. Aquí, `bump-version.sh` es un script del sistema operativo ficticio que cambia algunos archivos sobre la copia de trabajo local (working-copy) para que se refleje sobre los mismos la nueva versión. (Esto, por supuesto, puede ser un cambio manual; el hecho es que algunos archivos cambian). Luego, se hace un `commit` y el número de la versión queda embutido sobre dichos archivos de la rama de Número de Release `release-1.2`.

Esta nueva rama de Número de Release puede existir durante un tiempo, y sólo hasta que la versión se pueda lanzar definitivamente. Durante ese tiempo, las correcciones de errores finales que surjan en esos momentos (y localizados e incorporados desde ramas puntuales `hotfix-*`) se deberían aplicar sobre esa rama de Número de Release (en lugar de en la rama de `develop`). Agregar nuevas funcionalidades está estrictamente prohibido en esta rama de Número de Release. Esas Funcionalidades, debenrán ser fusionadas sobre `develop` y, por lo tanto, deben esperar el próximo lanzamiento del proyecto.


#### 4.2.1. Finalizando la Rama de versión

Cuando el estado de la rama de Número de Release (`release-1.2`) es el correcto y está lista para convertirse en una versión real, deben llevarse a cabo algunas acciones finales. En primer lugar, la rama de Número de Release (`release-1.2`) se fusionará en `master` (ya que, cada `commit` en `master` es una nueva versión por definición, recuerda). A continuación, esa fusión sobre la rama `master` debe etiquetarse (`git tag`) para tener una futura referencia clara y simple, a esa versión histórica. Finalmente, los cambios que se hayan incorporado a la rama de Número de Release (`release-1.2`) deben fusionarse de nuevo en `develop`, de modo que las versiones futuras también contengan estas correcciones de errores.

Los primeros dos pasos en Git serían:

````shell
    $ git checkout master
    Switched to branch 'master'
    
    $ git merge --no-ff release-1.2
    Merge made by recursive.
    (Summary of changes)
    
    $ git tag -a 1.2
````


Para mantener los cambios realizados sobre la Rama de Número de Release, necesitamos fusionar aquellos de nuevo sobre la rama `develop`. Esto se realiza en Git con:

````shell
    $ git checkout develop
    Switched to branch 'develop'
    
    $ git merge --no-ff release-1.2
    Merge made by recursive.
    (Summary of changes)
````

Este paso, bien podría llevar a un conflicto de fusión (e incluso es muy probable, ya que hemos cambiado el número de versión). Si es así, se corrige el mismo sobre el archivo adecuado y se aplica un `commit`.

Ahora hemos terminado y la rama de Número de Release puede ser eliminada, ya que, no la necesitamos más.

````shell
    $ git branch -d release-1.2
    Deleted branch release-1.2 (was ff452fe).
````



### 4.3. Ramas de tipo: Parches de reparación



Deberían separarse a partir de:

     `master`

Deben fusionarse nuevamente contra:
     
     `develop` y `master`
     
Por convenio, su nomenclatura será:
   
     `hotfix-*`

     
Las ramas de tipo Parche de reparación (hotfix-*) se parecen mucho a las ramas de Número de Release (release-*), ya que están destinadas también a preparar una versión nueva de producción, aunque no estén planificadas. Surgen de la necesidad de actuar inmediatamente sobre un error no deseado descubierto en una versión de producción activa. Cuando un error crítico en una versión de producción se debe resolver inmediatamente, una rama de tipo Parche de reparación se extrae de la Etiqueta (tag) correspondiente de la rama `master`.

El objetivo de este tipo de ramas es que, el trabajo de los miembros del equipo (en la rama de desarrollo) pueda continuar mientras que, otra persona, prepara una solución rápida para esa Etiqueta del `master` que está en producción.



![Ramas de Parches de reparación (Vincent Driessen)]({{  post.url | prepend: site.baseurl  }}/assets/imgs/hotfix-branches2x.png){:width="350px"  hspace="20px"  border="1px"}


#### 4.3.1. Crear una rama: Parche de reparación


Las ramas de Parche de reparación se crean a partir de la rama principal `master`. Por ejemplo, supongamos que la versión 1.2 (tag 1.2) es la versión de producción actual que está en ejecución y que está causando problemas debido a un error grave. Pero, los cambios en la rama de desarrollo `develop` aún son inestables. Deberíamos entonces crear una rama de tipo Parche de reparación y comenzar, de inmediato, a solventar el problema:

````shell
    $ git checkout -b hotfix-1.2.1 master
    Switched to a new branch "hotfix-1.2.1"
    
    $ ./bump-version.sh 1.2.1
    Files modified successfully, version bumped to 1.2.1.
    
    $ git commit -a -m "Bumped version number to 1.2.1"
    [hotfix-1.2.1 41e61bb] Bumped version number to 1.2.1
    1 files changed, 1 insertions(+), 1 deletions(-)
    
````


¡No te olvides de cambiar el número de versión después de crear la Rama hotfix! (Observar tag 1.2.1 en imagen).

Luego, corrige el error y aplica la corrección con uno o más `commits` separados.

````shell
    $ git commit -m "Fixed severe production problem"
    
    [hotfix-1.2.1 abbe5d6] Fixed severe production problem
    5 files changed, 32 insertions(+), 17 deletions(-)
````

#### Terminar una rama tipo: Parche de reparación

Cuando termines la rama de corrección de errores, ésta debe fusionarse de nuevo sobre el `master` y también, debe ser fusionada de nuevo sobre la rama de desarrollo `develop` a fin de garantizar que la corrección de errores también se incluya en la próxima versión. 


Este procedimiento, es muy similar a cómo se finalizan las ramas de tipo Número de Release. Primero, actualiza la rama `master` y etiqueta la nueva release.

````shell
    $ git checkout master
    Switched to branch 'master'
    
    $ git merge --no-ff hotfix-1.2.1
    Merge made by recursive.
    (Summary of changes)
    
    $ git tag -a 1.2.1
````


NOTA: también podrías querer emplear los parámetros  `-s` o `-u` <clave-de-encriptación> para firmar digitalmente esa versión.

Luego, incluye  también esa corrección de errores en la rama de desarrollo:

````shell
    $ git checkout develop
    Switched to branch 'develop'
    
    $ git merge --no-ff hotfix-1.2.1
    Merge made by recursive.
    (Summary of changes)
````

La única excepción a la regla se produce cuando actualmente ya existe una rama de Número de Release en curso y, los cambios de la rama Parche de reparación, se deberán aplicar entonces en esa rama de Número de Release, en lugar de sobre la rama de desarrollo `develop`. 

Fusionar así, el Parche de reparación de errores en la rama de Número de Release, dará como resultado que los cambios creados en el Parche de Reparación acaben dentro de la rama de desarrollo `develop` cuando la rama de Número de Release se cierre. (Si el trabajo en desarrollo requiere de inmediato esta corrección de error y no puede esperar a que se complete la rama de Número de Release, puede fusionar también, y de forma segura, el Parche de reparación del error en desarrollo `develop`).

Finalmente, elimine la rama temporal:

````shell
    $ git branch -d hotfix-1.2.1
    Deleted branch hotfix-1.2.1 (was abbe5d6).
````



## Sumario


Mientras que es cierto que no hay nada nuevo realmente sorprendente en este modelo de utilización de Git (mostrado en la figura "inicial" con la que comenzó esta publicación), sí que ha demostrado ser tremendamente útil en nuestros proyectos. Forma un modelo mental elegante que es fácil de comprender y permite a los miembros del equipo: desarrollar, compartir una visión y una compresión global del proceso de generación de ramas y del proceso de cierre de versiones.


## Referencias


[^VINCENT]: **Vincent Driessen**. A successful Git branching model. Tuesday, January 05, 2010. Availabled at <https://nvie.com/posts/a-successful-git-branching-model/>.



