# Seccion 6 : Inicios en Github, Git Remote - Push & Pull

---

<br>

## Indice

---

- [ ] 1. [Introduccion Github Remote - Push & Pull](#1-introduccion-github-remote---push--pull)
- [ ] 2. [Creando una cuenta de Github](#2-creando-una-cuenta-de-github)
- [ ] 3. [Push a Github](#3-push-a-github)
- [ ] 4. [Push de los Tags de nuestro repositorio](#4-push-de-los-tags-de-nuestro-repositorio)
- [ ] 5. [Creando - release tags](#5-creando---release-tags)
- [ ] 6. [Actualizando el perfil de Github](#6-actualizando-el-perfil-de-github)
- [ ] 7. [Pull de los ultimos cambios en el repositorio de Github](#7-pull-de-los-ultimos-cambios-en-el-repositorio-de-github)
- [ ] 8. [Warning - Pulling without strategy](#8-warning---pulling-without-strategy)
- [ ] 9. [Clonar un Repositorio](#9-clonar-un-repositorio)
- [ ] 10. [Subir cambios locales al remoto](#10-subir-cambios-locales-al-remoto)
- [ ] 11. [Git Pull Rebase](#11-git-pull-rebase)

<br>

## 1. Introduccion Github Remote - Push & Pull

---

Git es un sistema de control de versiones que nos permite realizar el seguimiento y la organ
izacion del desarrollo de nuestro proyecto a traves de las diferentes etapas: desde
el diseño hasta su despliegue final.

En esta seccion aprenderemos como trabajar con git remote push pull para subir o borrar archivos al repositorio remoto (en este caso github).

Github es una plataforma online para alojar proyectos utilizando el servicio git como sistema principal de versionamiento. Es muy util cuando queremos tener acceso a los archivos o código fuente de nuestras aplicaciones sin necesidad de descargarlos localmente en cada computadora donde trabajamos con él.
En esta seccion vamos a aprender a utilizar GitHub como repositorio remoto (remoto = remote), asi poder subir cambios realizados en nuestros códigos al repositorio centralizado ofrecido por github.com

Git Remote es una caracteristica fundamental para trabajar con git ya sea local o remoto. Con esta funcionalidad podemos tener acceso al repositorio centralizado donde se almacenan todos los proyectos.

**_`git push -u origin main`_ :**

- `-u` -> Nos ayuda a que la proxima vez que queramos hacer `push`, no nesecitemos especificar la rama.
- `origin` -> Nombre del repositorio.
- `main` -> Rama que deseamos enviar.

<br>

## 2. Creando una cuenta de Github

---

Para crearte una cuenta en Github : [Registrate](https://www.github.com/)

Una vez creada tu cuenta, te pedira crear un nuevo perfil para poder empezar a usar GitHub como plataforma digital donde podras almacenar tus proyectos en linea con otros usuarios.

<br>

## 3. Push a Github

---

Realizar un `push` a nuestra cuenta de Github

```bash
$ git add . # Añadir todos los archivos al stage area (index)
$ git commit -m "Mensaje"   # Hacer el Commit con mensaje para describir lo realizado
$ git remote add origin https://github.com/usuario/nombre_repositorio.git
$ git branch -M main    # Setear upstream
$ git push -u origin main     # Realizo el push a mi nuevo repo creado en github
$ git pull     # Actualiza localmente tu repo con el remoto, si hubiesemodificaciones o conflictos
```

Si es la primera vez que haces esta conexion te va a pedir que te autentiques. Puedes hacerlo muy facilmente con la opcion del navegador o con tus creenciales (email and password).

<br>

## 4. Push de los Tags de nuestro repositorio

---

Para subir mis **tags** ejecuto el comando :

```bash
git push --tag         #Subir todos tus tags creados al servidor
```

Si solo quiero subir uno especifico:

```bash
git push origin tagName        #Sube esa única etiqueta al servidor
```

<br>

## 5. Creando - release tags

---

Un `release tag` es un punto específico donde se hace una versión estable y contiene todas las correcciones
y mejoras que fueron hechas desde la última versión estable publicada en ese momento.

En pocas palabras, es la personalizacion de un tag (descripcion, imagenes, etc...).

Podemos crear y publicar releases desde la página del proyecto en GitHub. Para hacerlo debemos ir a la pestaña Releases e iniciar sesión como administrador del repositorio para poder realizar esta acción. Una vez dentro pulsamos en 'New release'. En la siguiente ventana seleccionamos una versión y agregamos un nombre y comentario.

<br>

## 6. Actualizando el perfil de Github

---

Puedes actualizar tu perfil de GitHub editando su información básica como nombre completrado, foto de perfil, biografía, links sociales, entre otros.

1. Entra en Tu Perfil > Settings
2. Haz click en "Profile"
3. Edita la informacion del perfil segun desees
4. Guardar cambios

<br>

## 7. Pull de los ultimos cambios en el repositorio de Github

---

El pull o actualización de código consiste en descargar nuevos archivos/cambios en tu computadora local a partir de lo que hay actualmente en GitHub para poder trabajar con ellos sincronizados.
Ejecuta este comando en la terminal dentro de la carpeta raíz de nuestro proyecto git clonado:

```sh
$ git pull
```

Este comando descarga todas las actualizacones de mi repositorio remoto a mi local.

Tambien se puede ser mas especifico :

```sh
$ git pull <remote_name> <branch_name> # Ejemplo: $ git pull upstream master
```

Donde `<remote_name>` es el nombre del remoto definido previamente (`origin por defecto`) y `<branch_name>` es el nombre de la rama por default (`master`). Si no tienes configurados estos valores usa `$ git pull`.

<br>

## 8. Warning - Pulling without strategy

---

**Si recibes un warning** como `warning: no common commits` al ejecutar `$git pull` esta ocurriendo porque tu branch esta desactualizada con respecto a su remote counterpart, y por lo tanto es necesario hacer merge manualmente antes de poder subir tus archivos nuevos al repo.

Para solucionarlo ejecuta el siguiente comando :

```bash
git config --global pull.ff only
```

Esta linea te permite configurar Git para que solo tome fusión y fast forward cuando se realiza una operación de merge entre ramas locales y remotas, evitando posibles conflictos con rebases o cherry picks intermediarios.

Establecemos que cuando hagamos una fusión, solo permitiremos fast forward.

**_Ahora si podes hacer tu primer pull sin problema alguno!_**

<br>

## 9. Clonar un Repositorio

---

Si quieres copiar o bajar los archivos del código desde GitHub para trabajarlos local en tú computadora puedes usar `Git Clone` :

1. Entra al sitio web de Github y busca el repositorio donde que desees clonar.
2. Haz click en "Clone or download" > Copia la URL HTTPS
3. Abre Git Bash (Windows), Terminal (Mac/Linux). Usa cd (change directory) para entrar en la carpeta donde quieras clonar el proyecto
4. Escribe el comando `git clone`, luego pega la url https que acabavas de copiar e introduce `Enter`
5. Se creara una nueva carpeta con el nombre del proyecto dentro de la raiz de la carpeta
6. **_Ahora ya estás listo para comenzar a desarrollar_**

<br>

## 10. Subir cambios locales al remoto

---

Luego de hacer cambios en nuestro proyecto, procedemos a subir los cambios a nuestro repositorio :

1. Abre Git Bash o Terminal
2. Navega hasta la ruta local del proyecto
3. Guardo los cambios y creo el commit (en caso que haya cambios no guardados)
4. Ejecuto el comando `git push` para subir los commits creados a mi repositorio en Github.

<br>

## 11. Git Pull Rebase

---

En caso que haya un conflicto al _actualizar_ el proyecto en mi local y _ademas_ hayamos hecho la cofiguracion del punto **6 -> [Warning - Pulling without strategy](#8-warning---pulling-without-strategy)** me dara un `Warning` y no podre solucionar el conflicto.

Para solucionar este `Warning` procedo a ejecutar el siguiente comando :

```bash
git config --global pull.rebase true
```

Este comando permite realizar rebase antes de actualizar las ramas desde el servidor.

Ahora ya podemos ejecutar `git pull` y solucionar el conflicto como normalmente lo hacemos.

Si ya terminamos de hacer los cambios y como estamos en un `rebase`, ejecutamos el comando :

```bash
git rebase --continue
```

Esto nos permitira continuar con el flujo de trabajo habitual sin tener problemas.

Subimos los cambios con `git push` y listo, **_cambios subidos al repositorio de Github!!!_**

---

Para saber un poco mas del [flujo de Github](https://blog.mergify.com/understanding-the-github-pull-request-workflow/)

---

- [ ] [Indice](#indice)
