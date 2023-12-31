# Seccion 4 : Ramas, Uniones, Conflictos y Tags

---

<br>

## Indice

---

- [ ] 1. [Introduccion a la Seccion de Ramas](#1-introduccion-a-la-seccion-de-ramas)
- [ ] 2. [Introduccion : Ramas, Uniones y Conflictos](#2-introduccion--ramas-uniones-y-conflictos)
- [ ] 3. [Merge : Fast-Forward](#3-merge--fast-forward)
- [ ] 4. [Merge : Union Automatica](#4-merge--union-automatica)
- [ ] 5. [Uniones con Conflictos](#5-uniones-con-conflictos)
- [ ] 6. [Tags - Etiquetas](#6-tags---etiquetas)
- [ ] 7. [Creando Etiquetas - Tags](#7-creando-etiquetas---tags)
- [ ] 7. [](#)
- [ ] 7. [](#)
- [ ] 7. [](#)

<br>

## 1. Introduccion a la Seccion de Ramas

---

Yo le recomiendo por favor, por favor, por favor, acostúmbrese a trabajar con ramas. Es decir, yo como desarrollador digo saben qué?, voy a empezar a crearme una implementación nueva, algún sistema de usuarios o alguna pantalla nueva de administración de productos, algo de carrito de compras. Qué se yo. Entonces, en el momento que ustedes dicen OK, voy a empezar a trabajar en esa característica inmediatamente piensen `necesito una rama`.

**¿Por qué?**

Primero las ramas es como una versión diferente de proyecto, como ustedes lo tengan, por ejemplo al master por acá.
Una rama es un desprendimiento, exactamente una copia literal de como se encuentra ese repositorio en ese momento y ustedes pueden experimentar con esa rama.

**¿Por qué es útil esto?**

Porque puede ser que ustedes accidentalmente o de manera intencional, por código que ya no haga que funcione la aplicación o añadieron características que rompen el funcionamiento de la aplicación. O puede que ustedes simplemente digan Saben qué?, esa funcionalidad no creo que la vayamos a implementar todavía, pero sí debemos de seguir trabajando en otras características que yo tengo en la aplicación.

_Entonces, con una rama muy fácilmente._

Bueno, haciendo paréntesis, si no estuviéramos trabajando en Git y no estuviéramos trabajando en ramas, posiblemente ustedes tendrían que ser un control Z Control Z control Z de todos los archivos o tener una copia física del sisten del mismo repositorio para tratar de llegar al punto en el tiempo como nosotros teníamos originalmente nuestro proyecto, cosa que es casi imposible porque va a quedar basura y va a quedar cosas o remanentes, cosa que no pasa si ustedes están trabajando con las ramas.

La idea de la rama es que ustedes fácilmente puedan cambiar entre la rama main o la master, o pasar a otra rama, o crear una nueva rama o unir ramas. Todo eso lo que vamos a ver en esta sección, así de fácil, es literalmente con un pequeño comando.

Ustedes se mueven entre ramas y me gusta verlo porque ahorita está de moda todo lo que es el multiverso de Marvel.

Me gusta verlo como una versión alternativa o un multiverso de su repositorio. En pocas palabras, ustedes pueden experimentar ahí cuando ya tienen una característica lista en una rama, ustedes pueden decir Saben qué?, esto está listo para unirlo a la rama Master o usualmente ustedes van a ver que también vamos a renombrar a la rama a main.

Entonces, cuando mi característica está lista, ustedes la van a poder unir a la rama principal o a otra rama que ustedes quieran. Esto va a ser varios panoramas o les va a plantear varios panoramas. Está el panorama de fast forward, que es más, digamos que sería lo ideal.

Que nosotros trabajáramos con fast forward es, en pocas palabras, significaría de que nuestro repositorio.
Bueno, obviamente cuando hacemos la separación y a hacer commits en esta rama, la rama original o de donde se desprendió, digamos que todavía no ha tenido ningún avance o no ha tenido ningún cambio significativo que cuando yo una rama al master o al main, entonces lo que va a seguir es que va a actualizar mi rama principal hasta el punto de traer todos los comités que estuvieron en la rama que yo creé.

_Eso hace un fast forward_, es decir, no hubo ningún problema y adelanta mi repositorio y mi git lo pone exactamente al punto de unión de la rama.

Luego vamos a tener otros casos que son un poco más caóticos, donde vamos a tener que hacer un Rebase.

Ya vamos a ver que es un Rebase, a ver otros casos donde va a haber conflictos y va a decir no sé que hacer aquí.

Dos personas tocaron el mismo código, no sé a que las líneas me chocan, no sé qué hacer. Por favor, dime que tenemos. Bueno, cómo vamos a proceder acá?, eso es lo que les va a plantear y vamos a caer en un modo de conflicto o un estado de conflicto, el cual hay que asegurarse de resolverlo antes de hacer cualquier otra característica en nuestro repositorio.

En fin, eso es lo que vamos a hacer en esta sección.

Vamos a trabajar con ramas y resolución de conflictos.

<br>

## 2. Introduccion : Ramas, Uniones y Conflictos

---

**¿Que es una Rama?**
Una Rama es una linea independiente del resto de las ramas dentro de la historia de un proyecto git. Cada vez que crees una nueva característica u otra pieza funcional para tu aplicación, te recomiendo crear una rama separada para el desarrollo. Esto ayuda a mantener limpio el código principal y permite realizar cambios sin problemas al mismo tiempo que evita los efectos secundarios en el trabajo realizado por otras personas.

Una **Rama**, también llamada _Branch_, es la herramienta fundamental para desarrollo ágil e integración continua (CI). Es como si tuvieres dos cuerpos diferentes dentro del mismo cerebro: uno personalizado y seguro, el otro que está lleno de ideas innovadoras pero no funcionales ni completamente probadas en tu laboratorio experimental.
Con las ramas, podemos experimentar sin preocuparnos por los cambios.

**¿Que es una Union?**
Una Union es la combinación de dos ramas para crear una nueva historia linealizada del proyecto.
Estas son los tipos de uniones que existen :

1. Fusión: Se realiza cuando queremos integrar varias ramas en uno
2. División: Es utilizada cuando tenemos diferentes ideas sobre algún aspecto del proyecto e intentamos desarrollarlas en ramas separadas. Consiste en separar una rama en dos ramas diferentes.
3. Transplante: Este tipo de union consiste en tomar parte de una rama y pegársela dentro de otra ya creada.
4. Mezcla: Esta opción permite fusionar ramas desde distintos puntos.
5. Squash and Merge: Es similar al mezclado pero reduce todos los commits.
6. Fast Forward: Este método no crea una nueva rama sino que actualiza directamente la última confirmada (HEAD). Esto quiere decir que si tenemos algún commit pendiente después de realizar la fusión/transplante/mezcla, este será ignorado.

**¿Que es el problema de la union?**
El problema es que si hay conflictos entre archivos no solucionables mediante merge directamente, debemos resolverlos manualmente antes de realizar la union.

<br>

## 3. Merge : Fast-Forward

---

Primero que nada creamos un nuevo archivo, en este caso el archivo `villanos.md`. Añadimos un titulo y algunos villanos.

Ahora yo quiero mantener el proyecto original como esta asi que creare otra rama.
Para hacerlo debo de ejecutar el siguiente comano :

```bash
git branch rama-villanos # en lugar de "rama-villanos" poner el nombre de su preferencia a esta nueva rama
```

Este comando creará una nueva rama llamada `rama-villanos`. Luego de tener la rama creada puedo irme a mi archivo local donde estoy desarrollando e iniciar a realizar algunos cambios.

Con el comando `git branch` puedo ver en que rama me encuentro. En este caso sigo en la rama de origen (main / master).

Si yo me quiero mover a la rama que cree es con el siguiente comando :

```bash
git checkout rama-villanos
```

En este momento tengo mi nuevo directorio donde voy a trabajar. Aqui vamos a realizar algunos cambios en nuestro código fuente. Después de esto si quieres volver atras a tu rama principal puedes usar el comando `checkout master`.

Ahora que ya cree mi nueva rama de trabajo, procedo a añadir al repositorio los nuevos cambios, esto lo puedo hacer con el comando `git -am "Agregamos Villanos.md"`.

Ahora puedo practicar añadiendo nuevos cambios al proyecto y por consecuente a esta rama.

Si me muevo a la rama principal, puedo observar que los cambios que realice anteriormente no se encuentran en el proyecto.

Yo quiero que lo que se encuentra en mi nueva rama de trabajo (`rama-villanos`) este en el proyecto de la rama principal. Esto lo puedo hacer de la siquiente manera :

1. Primero nos situamos en la rama principal.

```bash
git checkout master
```

2. Ahora hacemos un merge entre las dos ramas, para esto usamos :

```bash
git merge rama-villanos
```

Esto hará una fusión lineal del contenido de ambas ramas, lo que significa que solo se tomarán los archivos que no existen ya en la rama principal (Fast Forward).

3. Si hay conflictos los resuelvemos manualmente y luego lo subimos:

```bash
# si no hay ningún error podemos continuar... ó ...
# git mergetool
```

4. Una vez terminado todo se puede borrar la `rama-villana` usando :

```bash
git branch -d rama-villanos
```

<br>

## 4. Merge : Union Automatica

---

Primeramente, si yo quiero crear una rama y al mismo tiempo moverme a esa rama puedo utilizar el siguiente comando :

```bash
git checkout -b rama-trabajo # Donde en "rama-trabajo" va el nombre a la nueva rama que quieres crear y moverte
```

En el caso de que tengamos varias ramas diferentes trabajando sobre distintos archivos o carpetas del mismo repositorio Git es posible utilizar una técnica llamada "merge automatic" (también llamada auto-merging). Esta tecnica permite hacer merges sin tener que preocuparnos por resolver conflictos manuales y evita tener que realizar muchas veces el comando `git merge <branch_name>`.
Para habilitar este modo automático debemos ejecutar el siguiente comando desde la terminal:

```bash
git config --global pull.rebase true # Habilitación global
```

Esto hará que todos nuestras futuras fusiones locales realizadas con `pull` o `fetch` se realicen mediante rebase en lugar de merge tradicional.
Con esta configuración ya podremos usar el comando `git pull origin main` para actualizar localmente nuestro proyecto al último commit disponible en la rama principal remota.

<br>

## 5. Uniones con Conflictos

---

Un conflicto es cuando dos ramas _modifican un mismo archivo en diferentes partes_, Git no sabe cual es la mejor versión del código para fusionar las diferencias entre ambas ramas y por tanto nos pide que decidamos qué hacer.

Al momento de hacer `git merge rama-conflicto` git detecta el conflicto.

Al momento de detectar el conflicto, Git aumenta lineas de texto en tu archivo conflicto y literalmente te escribe donde se realizo el conflicto y te indica tus opciones.
Para resolverlo puedes elegir y eliminar el codigo que creas conveniente.

En caso de tener conflictos al realizar una merge o rebase automaticamente aparecerá esta ventana donde podremos elegir cualquier opción disponible (eligiendo uno de los archivos y luego presionando "M" para marcarlo como solucionado en ese archivo). Siempre tendremos la posibilidad de resolver manualmente estos conflictos editando directamente el fichero generado por Git.

<br>

## 6. Tags - Etiquetas

---

Los tags son referencias a puntos específicos en el historial del proyecto, se utiliza para marcar versiones importantes o para realizar rollbacks cuando algo sale mal.

Generalmente los tags son usados para :

- Marcar una versión estable del proyecto (v1, v2...)
- Identificar un release en particular
- Enviar versiones al repositorio oficial o a nuestros clientes

<br>

## 7. Creando Etiquetas - Tags

---

Para crear un Tag hay varias formas :

- **`git tag nombre_del_tag` ->** Crea la etiqueta localmente sin subirla al servidor remoto.
- **`git push origin nombre_del_tag`**-> Sube la etiqueta al servidor remoto.
  Ejemplo:

```bash
$ git tag nueva_version
$ git push --tags #Sube las etiquetas locales al servidor remoto
```

También se pueden usar comandos más avanzados como por ejemplo:

```bash
#Creación de etiqueta con mensaje personalizado
$ git tag -m "Mensaje" nuevo_tag
#Eliminar etiqueta existente
$ git tag -d old_tag
#Listado de todas las etiquetas disponibles
$ git tag
#Listado de todas las etiquetas disponibles
$ git show-ref --tags | cut -d / -f3-40
```

Los nombre de las etiquetas deben cumplir con algunos estándares y convenciones que dependen mucho de cada equipo/organización pero generalmente siguen el siguiente patrón:

`<nombre_versión>-<número>`

Por lo tanto si tenemos dos releases `v1.5.0` y `v2.0.0` podemos nombrarlas así:

- `v1.5.0`: primer lanzamiento de la aplicación
- `v2.0.0`: segundo lanzamiento de la aplicación

Estos 3 numeros tiene el siguiente significado :

- Primer número : Cada vez que incrementamos este numero, significa un gran cambio en nuestro proyecto o librería. Es decir, algo muy importante ha sido agregado o quitado del código fuente principal. Por ejemplo : si vamos a pasar de PHP 8.x a PHP 9.y debemos realizar muchas modificaciones para adaptarnos al nuevo entorno. En ese caso podra ser buena idea actualizar los nombres de las tags para incluirlo dentro del mismo rango semántico.

- Segundo número : Se refiere a características adicionales que han sido agregadas al producto. Puede ser un parche, mejoras menores, corrección de errores, etcétera. No debe considerarse grandes cambios.

- Tercer número : Se refiere a algunos bugs encontrado y parchados. No se consideran cambios grandes.

Otra forma es seguir el estándar semver que define cómo numerar versiones software (https://semver.org/)

- [ ] [Indice](#indice)
