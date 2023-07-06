# Seccion 5 : Git Stash y Git Rebase - Para realizar cambios de emergencia

---

<br>

## Indice

---

- [ ] 1. [Introduccion a la seccion - Stash / Rebase](#1-introduccion-a-la-seccion---stash--rebase)
- [ ] 2. [Git Stash](#2-git-stash)
- [ ] 3. [](#)
- [ ] 4. [](#)
- [ ] 5. [](#)
- [ ] 6. [](#)

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

- [ ] 6. [Indice](#indice)
