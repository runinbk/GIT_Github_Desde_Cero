# Seccion 2 : Git - Fundamentos

---

> "Lo mas sercano que tenemos a los viajes en el tiempo en git jejeje"

<br>

## Indice

---

- [ ] 1. [¿Por que nos interesa saber Git o un Sistema de Control de Versiones?](#1-¿por-que-nos-interesa-saber-git-o-un-sistema-de-control-de-versiones)
- [ ] 2. [Primeros comandos de Git](#2-primeros-comandos-de-git)
- [ ] 2.1. [Configuracion inicial de de Git](#21-configuracion-inicial-de-de-git)
- [ ] 3. [Nuestro primer repositorio](#3-nuestro-primer-repositorio)
- [ ] 4. [Nota - CRLF](#4-nota---crlf)
- [ ] 5. [¿Que hace Git por nosotros en estos momentos?](#5-¿que-hace-git-por-nosotros-en-estos-momentos)
- [ ] 6. [Exposicion sobre los comandos usados hasta el momento](#6-exposicion-sobre-los-comandos-usados-hasta-el-momento)
- [ ] 7. [Cambiar nombre de la rama principal (master -> main)](#7-cambiar-nombre-de-la-rama-principal-master---main)
- [ ] 8. [Demostracion de la creacion, puesta en escena y commits](#8-demostracion-de-la-creacion-puesta-en-escena-y-commits)
- [ ] 9. [Diferentes formas de agregar archivos al escenario(git add)](#9-diferentes-formas-de-agregar-archivos-al-escenariogit-add)
- [ ] 10. [Creando Alias para nuestros comandos](#10-creando-alias-para-nuestros-comandos)

<br>

## 1. ¿Por que nos interesa saber Git o un Sistema de Control de Versiones?

---

Utilizar un sistema de control de versiones como Git puede mejorar la eficiencia y la calidad del desarrollo de software, permitir una colaboración más efectiva y proporcionar una mayor flexibilidad y seguridad en el manejo de los proyectos.

Conocer Git o cualquier sistema de control de versiones, como Subversion o Mercurial, puede ser beneficioso para varias razones:

- Historial de cambios y versionado
- Colaboración en equipo
- Respaldo y recuperación
- Experimentación y ramificación
- Trabajo remoto y distribuido
- Control de calidad y revisión de código
- Mantenimiento del software con herramientas integradas para gestionar proyectos complejos

<br>

## 2. Primeros comandos de Git

---

Estos comandos se ejecutan en la consola de git `gitbash`.

A continuacion, mostraremos algunos comandos basicos :

- **git --version :** Nos dice la version que tenemos de git.

```console
$ git --version
git version x.x.xx
```

- **git help :** Al ejecutar este comando les aparece las ayudas de git. Una descripcion basica de la mayoria de los comandos de git y su uso. Basicamente es la documentacion que pueden encotrar en la web pero en la consola. Esta opcion te da bastante contenido, en caso de querer salir de esa bista _preciona la tecla U_ `tecla U`.

- **git init:** Inicializa una carpeta local como repositorio GIT. Se creara una nueva carpeta `.git` donde almacenará toda la información sobre nuestro proyecto.

<br>

### 2.1. Configuracion inicial de de Git

---

- Lo primero que se hace es configurar el nombre del usuario, esto se logra con el siguiente comando :

```bash
git config --global user.name "AQUI VA TU NOMBRE DE USUARIO..."
```

- Escribe este comando y preciona `Enter`, y si no le retorno nada significa que lo hizo bien.

- A continuacion configuramos el correo para enlazar nuestro git del computador a nuestra cuenta en Github. Utiliza el correo que tu cuenta de Github

```bash
git config --global user.email "CORREO DE GITHUB"
```

Este comando sirve para especificar tu correo electronico asociado a tus commits

- Ahora podemos ver las configuraciones actuales usando:

```bash
git config --list
```

Que nos mostrará todas las opciones establecidas actualmente.

- Tambien podemos utilizar el siguiente comando :

```bash
git config --global -e
```

Para editar directamente los archivos de configuración global (esto abrirá un editor predeterminado para modificarlos).
Para poder editar el archivo, precione la `tecla a` y podra hacer la edicion que quiera.
Para guardar los cambios y salir precione la `tecla Esc`, y seguidamente escriba :

```bash
:wq!
```

Esto significa: `w` = write(escribir), `q` = quick(salir) y `!` = para que lo haga inmediatamente.

> Una regla no escrita de Git : Si no les da ningun mensaje de retroalimentacion significa que lo hizo correctamente...

<br>

## 3. Nuestro primer repositorio

---

En git los proyectos son conocidos como `Repositorios` sea cual sea el proyecto en el que estemos trabajando.

En un proyecto cualquiera, dentro de la carpeta del proyecto, abre la consola de comando y ejecuta el siguiente comando:

```bash
git init
```

Con esta instrucción inicializamos un nuevo Repositorio local en nuestra computadora o servidor remoto (en caso de tenerlo).
Con esta instrucción se creara un nuevo directorio local `/.git` donde tendremos nuestra base de datos del proyecto. Este directorio contendrá todos los archivos y carpetas necesarios para controlar versiones mediante Git.
Este directorio nunca lo deben de tocar. Si ustedes borran o mueven algo de ese directorio Git ya no podra darle seguimiento a su proyecto. Literalmente borrarias tu repositorio.

Para revisar en que estado esta tu repositorio, en la consola escriba el siguiente comando :

```bash
git status
```

Este comando te muestra todos los archivos del directorio de trabajo (la carpeta donde tu estás ahora mismo). Si no hay nada nuevo todavía, se imprime el mensaje "nothing to commit".

Ahora si querés agregar un archivo al control de versiones usamos el comando :

```bash
touch index.html #  creaste un archivo nuevo desde una terminal
```

Y luego ejecutás este otro comando para verificarlo :

```bash
git add./index.html   # agregado del archivo al stage area (preparacion antes de ser commited).
```

Si quieres verificar todos los cambios realizados al repositorio utiliza el siguiente comando :

```bash
git add . # agregado de todos los cambios
```

Si quieres remover un rachivo del stage utiliza el siguiente comando :

```bash
git reset index.html # escribe el nombre del archivo
```

Una vez hecho todo esto podemos realizar el commit usando el siguente comando :

```bash
git commit -m "mensaje"    # mensaje describe las modificaciones realizadas.
```

Los commit son registrados permanentemente y se pueden revertir a cualquier momento para volver atrás hasta ese punto.
Un commit es un conjunto de archivos que han sido actualizados junto con sus respectivos mensajes, descripcionando lo que ha sucedido en cada uno de ellos. Los commits permiten tener una trazabilidad completa sobre la linea de tiempo de nuestro proyecto.

Con ésto ya tendríamos nuestro primero repositorio y archivos listos para subir a GitHub u otra plataforma similar.

<br>

## 4. Nota - CRLF

### Nota de actualización:

Algunos en la próxima clase han presentado este problema con el CRLF, no es nada serio, es básicamente una interpretación de un carácter.

Simplemente ejecuten este comando si presentan el error:

```bash
git config core.autocrlf true
```

## 5. ¿Que hace Git por nosotros en estos momentos?

Pongamonos en la situacion que el gato se sento en el teclado o algo le paso al proyecto sin que nosotros pudieramos intervenir, en ese momento y gracias a Git podemos recuperar el proyecto a la ultima version guardada en el repositorio.
Para esto podemos ejecutar el siguiente comando :

```bash
git checkout -- .
```

Esto restaura todos los archivo que el repositorio toma en cuenta.
<br>

## 6. Exposicion sobre los comandos usados hasta el momento

---

Los comandos que vimos hasta el momento son :

1. `git init` -> Inicia una nueva carpeta para trabajar con git
2. `git status`-> Muestra la situación del proyecto, archivos no versionados
3. `git add.` -> Añade a staging area (area temporal donde se guardo los cambios antes de ser confirmado), todos los archivos y directorios al repo (para hacer commits).
4. `git commit -m "message"` -> Guarda los cambios hechos al código. Agrega mensajes significativos

Además tenemos `otros comandos` como ser :

- `git diff` -> Compara lo nuevo con lo ya existente en el área
- `git log` -> Muestra un registro de todas las acciones realizadas
- `git reset HEAD file_name` -> Descartar cambios locales sin subir
- `git rm filename` -> Eliminar un archivo localmente y remoto
- `git branch name` crea una rama llamada 'name' a partir de master
- `git merge otherbranch` fusiona dos ramas diferentes

<br>

## 7. Cambiar nombre de la rama principal (master -> main)

---

Para ver en que rama estamos escribimos el siquiente comando en la consola :

```bash
git branch
```

Si ves algo así :

```
* main
```

Entonces te encuentras en la rama'main'. Para cambiarle su nombre
deberías hacerlo desde tu terminal usando este comando:

```bash
git branch -M main
```

Este comando se usa cuando quieres actualizar el nombre de una rama que tienes ya creada pero que está apuntando ahora mismo a otra rama diferentre sí.
Este comando sustituye la rama actual por una nueva denominada'main', perdiendo todo el historial anterior.

<br>

## 8. Demostracion de la creacion, puesta en escena y commits

---

Aqui hacer una prueba de todo lo anterios avanzado...

Volver al punto 6 :
[Exposicion sobre los comandos usados hasta el momento](#6-exposicion-sobre-los-comandos-usados-hasta-el-momento)
Practicar con los `otros comandos`

<br>

## 9. Diferentes formas de agregar archivos al escenario(git add)

---

Si en caso quieras agregar al repo no todos los archivos si no un tipo espesifico de archivos, por ejemplo en este caso los de tipo `html`, lo puedes hacer de la siguiente manera :

```bash
git add *.hatml
```

Esto de agrega todos los archivos `.hatml` del directorio raiz a git para ser incluido en un commit posteriormente.

Ahora, si quiero agregar algun archivo que este en una carpete tengo que especificar la o las carpetas

```bash
git add vistas/*.html
```

Esto agrega todos los archivos tipo `html` que esten dentro de la carpeta `/vistas`

Algo mas a comprender, es que, cuando se crea un directorio y este esta vacio, git no les da seguimiento hasta que este tenga algo dentro de la carpeta.

Si deseas agregar todo el contenido de una carpeta esto lo puedes realizar apuntando a la carpeta a agregar :

```bash
git add /carpeta/a/agregar/*.*   # Agregara todas las carpetas que quieras
```

<br>

## 10. Creando Alias para nuestros comandos

Existe una forma de abreviar los comandos de Git, esto es con los alias.
Un alias es un nombre alternativo que se le da a un comando completo de git.
Con esta característica podemos crear nuevas palabras clave para ejecutar comandos de manera más rápida e intuitiva.
Para definir un nuevo alias usamos:

```bash
git config --global alias.<alias_name> "<comando>"
```

Por ejemplo crearemos un alias llamado "st" (status), y asignaremos su función como mostrar el estado del repositorio actual:

```bash
git config --global alias.st "status --short"
```

Después podremos usar el alias "st", en lugar del comando largo `git status`. Por ejemplo:

```bash
git st    # Equivalente a 'git status'
```

Tambien se puede modificar los alias creados desde la configuracion global :

```bash
git config --global -e
# Modifica el fichero ~/.gitconfig y busca la linea '[alias]' donde
# podemos editar o añadir nuevos aliases
```

Existen muchas modificaciones o bandera que se les pueden agregar a los comando de Git, para mas informacion vease la documentacion de Git.
Ejemplo :

```bash
git log --online --decorate --all --graph
```

Se podría crear un alias como este: Este es un `Bonus ++`

```bash
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
```

- [ ] [indice](#indice)
