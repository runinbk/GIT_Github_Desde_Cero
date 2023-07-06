# Seccion 5 : Git Stash y Git Rebase - Para realizar cambios de emergencia

---

<br>

## Indice

---

- [ ] 1. [Introduccion a la seccion - Stash / Rebase](#1-introduccion-a-la-seccion---stash--rebase)
- [ ] 2. [Git Stash](#2-git-stash)
- [ ] 3. [Conflictos con el Stash](#3-conflictos-con-el-stash)
- [ ] 4. [Stash Avanzado](#4-stash-avanzado)
- [ ] 5. [Git Rebase](#5-git-rebase)
- [ ] 6. [Rebase - Actualizando una Rama](#6-rebase---actualizando-una-rama)
- [ ] 7. [Rebase - Squash](#7-rebase---squash)
- [ ] 8. [Rebase - Reword](#8-rebase---reword)
- [ ] 9. [Rebase - Edit](#9-rebase---edit)

<br>

## 1. Introduccion a la seccion - Stash / Rebase

---

Git stash es una herramienta que nos permite guardar temporalmente los archivos modificados sin commitearlos en el repositorio local, para luego recuperar o aplicar dichos archivos al estado actual del proyecto. Esto puede ser útil cuando queremos trabajar con proyectos grandes donde no deseamos perder ninguna version anterior del código en caso de tener un error inesperado durante las fases de desarrollo.

**¿Qué es el Stash?**

Imagínense que ustedes estén trabajando en una característica, ya sea en su rama o en la rama main es una rama, pero ya sé que están trabajando en el main, cosa que no le recomendaría o están trabajando en su rama y de repente llega alguien y le dice Hey, por favor, por favor desplega los cambios que ustedes tienen actualmente en la rama.

Pero pero digamos que el jefe no sabe que ustedes están trabajando características o características nuevas que todavía no han sido unidas a la rama, O es trabajo que ustedes todavía no quieren que impacte algún commit.

Entonces el `Stash` es un lugar o una bóveda segura en el cual ustedes pueden mover todos los cambios, inclusive cambios de archivos que GUI todavía no le da seguimiento. Puede tomar todos esos cambios y ponerlo en esta bóveda. Esa bóveda lo que va a ser es que va a tenerlo de manera segura.

Todos mis cambios, todos los cambios en los que yo estuve trabajando desde el último commit. Entonces al hacer un `Stash` regresamos al punto inicial, o mejor dicho al último punto donde se encuentra nuestro GET en la rama en la cual estamos trabajando.

Eventualmente hacemos modificaciones y cualquier otra cosa que necesitemos y luego le podemos decir a Git, sabes qué Git, necesito regresar mi trabajo así como lo grabe en la bóveda.

Entonces Git va a ir, va a tomar sus cambios y literalmente lo va a colocar todo, esto va a causar varios tipos de panoramas, al igual que como hacíamos o vimos en la sección pasada de los merch.

Ustedes pueden tener un fast-forward para poder tener una rama de conflicto o estar en un estado de conflicto porque pudiera ser que hiciera modificaciones en el mismo archivo. Entonces, Git les va a pedir, hey, hay que resolver esto antes de extraer todo mi `Stash`.

Normalmente el estallas básicamente una bóveda en la cual ustedes pueden ir colocando ahí todas las todos sus cambios que no han hecho o no han sido impactados en la rama en la cual ustedes están trabajando, es decir, todavía no son commits, no son fotografías.

La parte del stash puede ser un poco confusa, especialmente cuando ustedes empiezan a meter mucho `Stash`. Yo no lo recomendaría, bueno, no es que no lo puede hacer, pero en mi experiencia yo no le recomendaría que ustedes trabajen con mucho en el `Stash`.

Es decir, están trabajando en una característica o estén alistas perfecto y tan pronto puedan ustedes regresen la información de Stash y sigan trabajando con esos cambios.

No agreguen al `Stash` una y otra y otra y otra vez. Es decir, ustedes no van a tener eso, pueden tener un montón de `Stash`, es decir, un montón de registros en la bóveda, pero no se acostumbren a hacer eso porque es muy difícil después acordarse de que era cada uno de los `Stash`. A pesar de que se les puede poner nombre y decir que esto era una característica que estaba implementando, es muy fácil, demasiado fácil, se lo digo por experiencia. Es muy fácil olvidarse cuando ustedes tienen dos o tres estas guardados, es muy difícil saber ok, voy a recuperar este trabajo o el otro. En mi experiencia yo les digo una vez ustedes ya resuelven la necesidad, apaguen el incendio, necesitan recuperar la información que tienen en el `Stash` ahí, hasta ahí está todo perfecto y sigan haciéndolo de esa manera.

No digan ok, voy a meter esto al `Stash` sigue trabajando, eso también lo voy a meter al `Stash` siguen trabajando, saben que eso no va a meter al `Stash` no hagan eso.

Se puede hacer, sí, y Git les va a mantener todo sus `Stashes`, pero no lo hagan porque es muy fácil confundirse al día de mañana.

El otro tema que vamos a ver aquí, que es sumamente importante, es el `Rebase` y especialmente una cosa que me gusta muchísimo, que se conoce como el `Rebase interactivo`.

El `Rebase` es muy poderoso y ustedes tienen que tener mucho cuidado con él, no por el hecho de que sea difícil de usar. No, nada de eso, es relativamente sencillo y tiene una opción interactiva en el cual ustedes pueden decirle cada uno de los pasos que esto es importante, especialmente en las últimas versiones de Git para ser lo que son `merge` y trabajar con Github también es sumamente útil, pero un `Rebase` básicamente les va a permitir a ustedes unir commits, separar commits, hacer lo que se conoce como un `Scuash` que a mí me gusta verlo como que dos bolas de nieve choquen y se fusionan, eso es un `Scuash`.
También se puede volver a separar, pueden renombrar los nombres de los commits. Pero nuevamente otra recomendación personal, yo les diría que los cambios que pueden hacer ustedes como el `Rebase`, sólo háganlo si esos cambios no han impactado el repositorio o un repositorio externo o no han subido sus cambios a otro repositorio. ¿Por qué?, porque recordemos que muchas personas pueden estar trabajando con nuestro mismo proyecto o inclusive nosotros mismos en otra computadora, por lo cual puede que no seamos los únicos trabajando en el mismo.

Si ustedes se van al pasado y empiecen a hacer cambios ahí, eventualmente esto va a causar conflictos que tienden a ser un poco más difíciles de resolver. No es que no se puede hacer, pero nuevamente yo les digo creo que ya les he dicho más de una vez, o si no es la primera vez que se lo digo porque sé que lo menciona varias veces en el curso.

**_Por favor, traten de no cambiar la historia._**

Si ustedes se van a la historia, empiezan a hacer modificaciones ahí, luego en el presente, entonces eso puede causar conflictos que nosotros tenemos que evitar, especialmente si esos cambios ya han sido impactados en algún repositorio remoto nuevamente.

Git no tiene un límite de commits, no tiene un límite de transacciones que ustedes pueden hacer, entonces no hace falta, no hace falta que ustedes vayan al pasado, digan ok, este comida estaba mal y ya tengo como 50 commits adelante, dice no hace falta, especialmente cuando ya hicieron los cambios en un repositorio externo.

<br>

## 2. Git Stash

---

Para este punto utilizaremos la carpeta `05-demo-stash` para realizar ejercios de practica.

_Algo que aclarar :_

> "El Stash no deberia de ser nesesario si yo trabajo con ramas.."

Primero que nada, realizamos cualquier tipo de modificaciones, y por alguna razon no queremos o podemos hacer un nuevo commit, entonces usamos el git Stash para guardar los cambios temporalmente fuera de los commit y volver el proyecto al estado del ultimo commit.

Esto se hace con el siguinete comando :

```bash
git stash # Guarda los archivos modificados en un estado temporal
```

o tambien :

```bash
git stash save -m "<mensaje>" # Guarda los archivos modificados en un estado temporal con un mensaje recordatorio
```

Este comando guardará todos los archivos modificados y listos para commit pero sin hacer ningún commit realmente. Esto es útil cuando estás trabajando en varias tareas y quieres mantener algunas cosas paralelas por separado antes de pasar al siguiente proyecto o etapa del desarrollo.

Con los cambios guardados puedo reguir haciendo cambios en el proyecto y crear nuevos commits mientras los cambios del `Stash` siguen guardados. Al hacer esto debo de tener cuidado de no hacer cambios en el mismo archivo de los cambios del `Stash`.

En cualquier momento puedo recuperar los cambios guardados por en el `Stash` con el comando :

```bash
git stash pop  # Restaurara los cambios guardados en el Stash
```

Con los cambios recuperados podemos proceder a crear un commit con los mismos.

<br>

## 3. Conflictos con el Stash

---

En casos de conflictos al querer recuperar los cambios guardados en el stash, esto por que al extraes los cambios guardados en el `Stash` el archivo fue modificado y al recuperar los cambios hay un **conflicto**.

- Si el conflicto es en diferentes lineas del archivo, git lo soluciona de forma automatica con un `Auto-merge`, recupera los cambios guardados y ya estan listos para crear un nuevo commit.

- Si el conflicto es en la misma linea se solucionan de manera manual como en el `git merge`. Ahora lo unico que se debe hacer es crear el commit respectivo.

<br>

## 4. Stash Avanzado

---

Si tengo algun residuo de los `Stash` o simplemente quiero borar todos los `Stash`, lo puedo hacer con el comando :

```bash
git stash clear # Borra todos los estados temporales de git
```

Al guardar muchos `Stash`, estos tienen comportamiento de pila (El ultimo en ingresar es el primero en salir), al tener muchos guardados estos adquieren una posicion por asi decirlo el cual es su `hash` con el que nos podemos referir para recuperar us `Stash` especifico.
Ejemplo:

```console
$ git stash list
stash@{0}: WIP on main : c658b1 Conflictos en Stash resueltos
stash@{1}: WIP on main : c658b1 Conflictos en Stash resueltos
stash@{2}: WIP on main : c658b1 Conflictos en Stash resueltos
stash@{3}: WIP on main : c658b1 Conflictos en Stash resueltos
```

Si quisiera recuperar un `Stash` especifico, en este caso el nro 2, podria hacerlo de la siguente manera :

```bash
git stash apply stash@{2}
```

Esta accion no elimina el estado temporal del `Git`, solo lo restaura al estado actual del proyecto y se puede volver a aplicar si es necesario con otro comando como por ejemplo `git stash pop`.

Si es que vuelvo a guardar este cambio en un `Stash`, como anteriormente no lo eliminamos y solo lo restauramos, al guardarlo tendriamos este **cambio duplicado** en la pila de `Stash`.

Si yo quiero borra un `Stash` especifico, lo puedo hacer con el comando :

```bash
git stash drop <número_del_stach>
```

En mi ejemplo si quieres eliminar el nuevo estado temporal que se encuentre guardo puesto que es duplicado,
podes usar el siguiente comando :

```bash
git stash drop stash@{0}
```

Este ultimo comando solo eliminara ese particular `Stash`, pero no afectara al estado del proyecto actual.

Si yo quiero la informacion en particular de un `Stash` lo puedo hacer con el comando :

```bash
git show show stash@{"numero"}
```

o tambien :

```bash
git show --stat stash@{"numero"}
```

Por ejemplo para ver toda la información sobre el primer `Stash`:

```bash
git show show stash@{0}
```

Si yo quiero ver mas informacion de todos los `Stash` :

```bash
git stash list --stat
```

Mas informacion sobre los `Stash` : https://git-scm.com/docs/git-stash

<br>

## 5. Git Rebase

---

El rebase o fusión de ramas consiste en combinar las diferencias entre dos ramas y genera una nueva rama resultante desde el punto de vista histórico. El objetivo principal del rebasing es tener un historial lineal limpio sin bifurcaciones ni merges intermedios.

Para realizar un rebase hay varias formas:

1. Usando git pull -r (Rebases and updates the current branch from its remote counter part). Este metodo se usa cuando ya estamos trabajando localmente, nos permite traer todas las modificaciones que existen en el remoto y fusionarlas automaticamente con nuestro codigo local. Es decir, si hubieran conflictos durante este proceso tendriamos que resolverlos manualmente antes de poder continuar desarrollando.

2. Usando git fetch origin master && git rebase FETCH_HEAD. Este método realiza primero un "fetch" del contenido del repo original, luego aplica el cambios recientes al código actual usando el comando "rebase". Esto significa que no creamos una nueva rama a partir de esta etapa sino que aplicamos directamente los cambios al mismo tiempo que descargamos datos adicionales. Por tanto, debemos estar seguros de que todo está bien con lo que hemos obtenido del servidor en caso contrario podremos revertirlo fácilmente.

3. Desde Visual Studio Code podemos usar el plugin Git Graph. Con él podemos visualizar gráficamente como quedará nuestro proyecto tras hacerle un rebase. También ofrece opciones para ejecutar comandos de rebase automáticos y también puede mostrar por separado cada uno de los commits incluidos en el nuevo historico. Además tiene integración con GitHub Desktop.

4. Mediante línea de comandos mediante el uso de diferentes flags disponibles en git. Algunos ejemplos son "-i", "--interactive", "-m", "--merge (combina la última confirmación de la rama actual con su base)" "-p", "--preserve-merges (preserva los merges dentro del commit)", etc

En resumen, cualquier forma de rebase te permitira mantener tu trabajo organizado

El `rebase` nos sirve para :

1. Ordenar commits
2. Mover nuestros commits desde otra rama a nuestra actual rama activa
3. Combinar multiples cambios en una sola linea de tiempo
4. Separar commits
5. Resolver conflictos entre ramas
6. Eliminar y reescribir historia

<br>

## 6. Rebase - Actualizando una Rama

---

Para actualizar una rama con el `rabase`
Primero debemos irnos a la rama que queramos actualizar `git checkout feature_branch`.

Luego ejecutaremos el comando `git rebase master`, esto hará que todos los commit del branch base (master), se apliquen al branch local(feature_branch).

Si tenemos algún conflicto durante este proceso tendremos que resolverlo manualmente y luego volver a aplicar el rebase usando `git add.` y `git rebase --continue`.

Una vez finalizada esta operación nos dirigimos a la rama al cual queremos traer todos los cambios con el comando `git checkout master`.

Para termianr esta operacion ejecutamos el comando `git merge feature_branch`.

Podremos subir las modificaciones a la rama usando el siguiente comando `git push origin <nombreRama>`.

<br>

## 7. Rebase - Squash

---

Tratar de seguir la siguiente regla :

> "El `rebase` es para los cambios que no han sido subidos a un repositorio, esto por que alguien mas podria tener estos cambios y modificar los mismos traeria muchos conflictos al equio."

Si yo quiero unir dos commits, sea cual sea el mitivo de esto, lo puedo hacer con el comando :

```bash
$ git rebase -i HEAD~4 # Al poner el '4' hago referencia a los 4 commits antes del ultimo
```

Esto me abrirá mi editor de texto donde aparecerán todos mis commit
Luego busco por ejemplo al primer commit "commit c" e indico:

```console
.
.
pick c Commit C (mensaje original)
pick b Commit B (mensaje nuevo)
.
.
```

Presiono la `tecla a` para hacer una insercion (editar) y escribo lo siguiente :

```console
.
.
pick c Commit C (mensaje original)
squash b Commit B (mensaje nuevo)
.
.
```

s (squash) para aplicar esos comandos sobre este commit y guardo el archivo.

Para salir y guardar primero presiono la `tecla Esc` seguido escribo `:wq!` y luego `tecla Enter`.

Este procedimiento hará que se combine todo en uno solo, quedandome así con el mensaje de "Commit A + Commit B".

<br>

## 8. Rebase - Reword

La opcion `reword` permite modificar el mensaje de un commit existente sin tener que crear uno nuevo.
Para usarlo solo tienes que seleccionar el commit en tu lista de cambios usando las flechas arriba/abajo y despues presionar la tecla `r`, se abrirá el editor de texto con el contenido actualizado del commit, simplemente editalo como quieras y guadalos (`Esc + wq!`).

<br>

## 9. Rebase - Edit

---

La opcion `edit` permite editar el contenido de archivos en cada commit despues de ser reordenados durante el proceso de rebase.
Este comando nos sirve cuando queremos editar directamente nuestro último commit
Ejemplo:

```bash
git rebase -i HEAD~3
# Modificamos el tercer commit, en caso de no haberlo hecho ya podemos hacerlo usando git commit --amend
```

Se abrira un editor con las opciones del rebase, seleccionando el ultimo commit (`reword`)
Modifique los campos deseados como si fuera a realizar un nuevo commit normalmente. Guarda y cierra el editor. El resultado sera un nuevo commit con sus cambios realizados y modificando su descripción. Guardado y cerrado se ejecutara el rebase automaticamente con los cambios realizados.

Esto se puede utilizar para separar commits, con la ayuda de otros comando.
Si es asi al finalizar los cambios ejecute el comando `git rebase --continue`.

- [ ] 6. [Indice](#indice)
