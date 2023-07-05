# Un poco mas alla de los Fundamentos

---

<br>

## Indice

---

- [ ] 1. [Introduccion a la Seccion](#1-introduccion-a-la-seccion)
- [ ] 2. [Cambios en los Archivos](#2-cambios-en-los-archivos)
- [ ] 3. [Actualizar mensaje del commit y revertir commits](#3-actualizar-mensaje-del-commit-y-revertir-commits)
- [ ] 4. [Preparando un Repositorio para viajes en el tiempo](#4-preparando-un-repositorio-para-viajes-en-el-tiempo)
- [ ] 5. [Viajes en el tiempo, resets y reflog](#5-viajes-en-el-tiempo-resets-y-reflog)
- [ ] 6. [Cambiar el Nombre y eliminar archivos mediante Git](#6-cambiar-el-nombre-y-eliminar-archivos-mediante-git)
- [ ] 7. [Ignorando archivos que no deseamos](#7-ignorando-archivos-que-no-deseamos)

<br>

## 1. Introduccion a la Seccion

---

Estamos entrando a la sección 3 del curso, la cual ya se pone bien interesante.
Eventualmente nosotros vamos a tener un repositorio y archivos en los cuales van a ir cambiando conforme ustedes van haciendo commits.

A mí me gusta ver que un comic es como una fotografía en el punto del tiempo, donde se dijeron Ok, estoy parado aquí, voy a tomar una fotografía.
Esa fotografía o cómic usualmente me gusta verlo con una fotografía, porque una fotografía es como un recuerdo del tiempo exactamente en el momento que ustedes la tomaron.
Es decir, ustedes pueden ver fotografías suyas de hace 10 años, 15 años, 20 años y van a ver que esa fotografía se mantiene literalmente igual.

Eso es la analogía que me gusta hacer con los comics.

Pero a diferencia de una fotografía real, ustedes pueden viajar en el tiempo, es decir, literalmente tomar su proyecto y moverse o moverlos físicamente en el file system de el sistema operativo, mover este punto del tiempo y llegar y posicionarse en ese instante donde ustedes crearon ese comic, o antes de ese comic o después de ese comic.

Ustedes van a poder hacer eso y no solo mover todo el repositorio, ustedes también, inclusive pueden seleccionar sólo un archivo que quieren que regrese en el tiempo.

Esto es súper útil, muy genial que nos permita hacer algo de este tipo.
Lo cual también vamos a hacer ejercicios en esta sección que van a ser destructivos.
Es decir, vamos a viajar en el tiempo y vamos a destruir todos los comics posteriores a ese punto del tiempo, aunque eso en teoría es imposible.
O sea, en teoría la única manera de destruir toda esa historia es que literalmente borramos la carpeta de nuestro proyecto.

Pero ustedes van a ver que vamos a movernos en el tiempo y vamos a viajar en el tiempo al pasado y vamos a ver que el repositorio cambió.

Y luego también les voy a enseñar a que ustedes puedan recuperar todos esos comics a pesar de que nosotros hicimos cambios a futuro.

Pero Git siempre mantiene todo un historial de los cambios que suceden en nuestro repositorio.

Esta sección es súper importante y muy interesante.

<br>

## 2. Cambios en los Archivos

---

En un proyecto lo inicializamos, y procedemos a crear o modificar el proyecto.
Algunos archivos pueden tener diferentes tipos de cambios:

- Añadir nuevos elementos al archivo (crear una función).
- Eliminar elementos existentes del archivo (eliminar una variable global).
- Modificar contenido dentro del mismo archivo (cambiar nombre de variables para mayor claridad).
  Cada uno de estos cambios generará un registro en el histórico
  de git. Estas acciones son importantes porque ayudan a entender cómo ha ido evolucionando el código desde su creación.

Git correspondiente al archivo modificado.

Para ver estas modificaciones podemos usar el siguiente comando :

```bash
git diff # Muestra las diferencias realizadas en el paso del tiempo
```

Este comando mostrará todas las líneas agregadas, eliminadas u actualizadas en cada commit desde su creación.

Tambien tenemos los siguientes comandos :

```bash
git diff <archivo_modificado> # Muestra las diferencias entre el estado actual del archivo y su versión guardada previamente.
git log --oneline FILENAME # donde "FILENAME" es el nombre del archivo que queremos consultar las modificaciones.
e.g git log --oneline index.html # Muestra todas las versiones del archivo 'index.html' desde su creación hasta sus ultimas actualizaciones.
```

<br>

## 3. Actualizar mensaje del commit y revertir commits

---

Digamos que nos equivocamos al escribir el mensaje del commit y queremos editarlo.
Para hacer esto existen diferente formas, pero la mas sencilla es la siguiente :

```bash
git commit --amend -m "mensaje a coregir"
```

Este comando corrige el mensaje del ultimo commit realizado.

En otro supuesto caso que quiera añadir algun cambio a algun commit anterior, lo puedo hacer de la siguiente manera :

```bash
git reset --soft HEAD^ # El HEAD se refiere al ultimo commit, si bien en lugar del este puede ir el hash de algun commit
```

Asi tambien el `^` se refiere al anterior del ultimo commit, si quisiese apuntar a versiones mas anteriores podria poner : `git reset --soft HEAD^2`.

<br>

## 4. Preparando un Repositorio para viajes en el tiempo

---

En un nuevo proyecto o repositorio, inicializo el repositorio `git init` y posteriormente creo el archivo `misiones.md`.
Guardo los cambios `git add misiones.md`.
Realizampos el respectivo commit : `git commit -m 'Agregamos Misiones'`

Esto mismo realizo con nuevos archivos llamados `heroes.md` y `ciudades.md`.

Acontinuacion, añado una carpeta llena de historias y procedo con la preparacion anterior.

Todo esto puedo hacerlo tambien dirigiendome a la carpeta `/code`, ahi se encuentra todo estos arechivos para practicar los **\*viajes en el tiempo**.\*

- **Acontinuacion los comando para este ejercicio/preparacion :**

Primero creamos el `README.md` con una pequeña descripcion y procedemos con los comandos :

```bash
git add README.md
git commit -m "Readme agregado"
```

```bash
git add misiones.md
git commit -m "Agregamos misiones"
```

```bash
git add heroes.md
git commit -m "Agregamos heroes"
```

```bash
git add ciudades.md
git commit -m "Agregamos ciudades"
```

```bash
git add historia/
git commit -m "Agregamos la historia de batman y superman"
```

Nos dirigimos al achivo `heroes.md` y añadimos a linterna verde en el listado.
Procedemos al `add` y `commit` :

```bash
git -am "Heroes.md : Agregamos a Linterna Verde"
```

Con esto estamos listo para movernos en el tiempo.

<br>

## 5. Viajes en el tiempo, resets y reflog

Imaginemos que 3 commit anterioes todo estaba bien y despues todo se frego.

volvemos a un punto anterior en el timepo con el siguiente comando :

```bash
git reset --mixed dfg233fc # En lugar de "dfg233fc" pudes poner el hash del commit al que deseas volver...
```

Este comando es parecido al anterior pero con la terminacion `--mixed` el cual tampoco es destructuvo, pero saca todo del stage y los cambios quedan listos para que lo pueda volver a añadir.

Si quieres eliminar todo lo posterior al punto en el que volviste es con el siguiente comando :

```bash
git reset --hard dfg233fc # En lugar de "dfg233fc" pudes poner el hash del commit desde el cual eliminaras todos los commits posteriores a este y sus cambios realizados en el proyecto (por eso se dice que este comando es "destructivo")...
```

Para volver a recuperar todo lo borrado es de la siguiente manera:

1. _`git reflog`_ -> Es la refernecia o un log de referencias de todo lo que ha sucedido en orden cronologico.
2. Si deseamos reatableser algun punto ya borrado, copiamos el hash del commit donde queremos volver, esto lo obtenemos del comando anterior, y luego lo ejecuamos con el siguiente comando :

```bash
git reset --hard 11fdfd31 # Donde "11fdfd31" es el hash al cual queremos volver...
```

Este comando lo que hace es, al referencial commits ya borrados, reconstruye el proyecto hasta el punto donde estaba en ese commit.

<br>

Ahora, esto no es algo que ustedes deben de hacer de manera normal.
O sea, no sería algo del día a día lo que yo acabo de hacer.

Usualmente, si ustedes no están seguros que van a implementar alguna funcionalidad nueva, lo mejor es que creamos una rama y nos vayamos por esa rama mientras estamos desarrollando.
Cuando ya terminamos de trabajar y ya todo eso está listo, vamos a unir esa rama con nuestro repositorio o nuestra o bueno, en teoría también eso tardará más con nuestra rama main o la master.
Usualmente sólo vamos a trabajar en ramas y luego fusionamos esas ramas con el main.

**¿Por qué?**

Porque de esa manera no tenemos que estar jugando con los cambios en el tiempo, porque si otras personas también estuviera trabajando con nuestro repositorio, ellos también pueden sufrir este tipo de movimientos que nosotros hicimos.

Ok, entonces esa es una de las razones por las cuales _se busca de que el main o el master sólo tenga los comics definitivos_. Aunque ustedes ya vieron, no necesariamente eso puede ser así.

Ustedes pueden revisar el master o el main a diferentes puntos del tiempo por si acaso no comete errores, porque inclusive no quiere decir que una rama unida al master o al main todo está correcto.

Puede ser que ustedes necesitan deshacer los cambios de una rama, que sería exactamente lo mismo que nosotros practicamos en esta seccion, que ustedes más adelante van a ver que aquí va a decir que se unió una rama.

Ustedes pueden regresarse al punto anterior de la unificación de esa rama, que eso es algo que vamos a ver un poco más adelante.

<br>

## 6. Cambiar el Nombre y eliminar archivos mediante Git

---

Para este ejercio, creamos el archivo `destruir-mundo.md`, y lo agregamos al repo con el siguiente mensaje : _"Destruir mundo añadido"_.

Ahora que tal si este archivo no es para destruir el mundo si no para salvarlo.

Podria corregit este nombre usando el siguiente comando :

```bash
git mv destruir-mundo.md salvar-mundo.md
```

Este comando ya lo añade al state asi que solo hay que hacer el `commit -m`.

Si deseo eliminar el archivo es con el siguiente comando :

```bash
git rm destruir-mundo.md
```

Este comando lo elimina pero sigue teniendolo en el stage, lo cual se puede recuperar con el comando `git reset --hard`.
Para confirmar la eliminacion debo de hacer el `commit -m`.

<br>

## 7. Ignorando archivos que no deseamos

---

Para ignorar archivos que no deseamos podemos crear un `.gitignore` en nuestro directorio raiz o proyecto, donde podremos especificar los patrones de nombres de archivos a excluir del control de versiones git.
Por ejemplo:

- Archivos temporales o cache generados por nuestro editor (como `.idea` en Jetbrains IDEs).
- Carpetas creadas automáticamente, como `__pycache__`, `.venv/` etc...
- Ficheros binarios descargados desde internet sin necesidad de tenerlos localmente (`*.zip`).

* Podemos ignorar estos ficheros creando un fichero `.gitignore`:

```text
# Ignore Node files an directories
node_modules/
*.log
.env
.env.local
.env.dev

# Ignore PyCharm files and directories
/.idea/*
/*.iml
*/out/
build/
dist/
*.egg-info/

# Ignore Python virtual environment directory
/__pycache__/
.venv/
```

Esta configuración indicará a Git los patrones de nombres de directorios y ficher
que se omiten del control de versiones.

- [ ] [indice](#indice)
