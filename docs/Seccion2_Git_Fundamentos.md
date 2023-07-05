# Seccion 2 : Git - Fundamentos

---

> "Lo mas sercano que tenemos a los viajes en el tiempo en git jejeje"

## Indice

---

- [ ] 1. [¿Por que nos interesa saber Git o un Sistema de Control de Versiones?](#1-¿por-que-nos-interesa-saber-git-o-un-sistema-de-control-de-versiones)
- [ ] 2. [Primeros comandos de Git](#2-primeros-comandos-de-git)
- [ ] 2.1. [Configuracion inicial de de Git](#21-configuracion-inicial-de-de-git)
- [ ] 3. [Nuestro primer repositorio](#3-nuestro-primer-repositorio)
- [ ] 4. [](#)

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

### 2.1. Configuracion inicial de de Git

---

Lo primero que se hace es configurar el nombre del usuario, esto se logra con el siguiente comando :

```bash
git config --global user.name "AQUI VA TU NOMBRE DE USUARIO..."
```

Escribe este comando y preciona `Enter`, y si no le retorno nada significa que lo hizo bien.

A continuacion configuramos el correo para enlazar nuestro git del computador a nuestra cuenta en Github. Utiliza el correo que tu cuenta de Github

```bash
git config --global user.email "CORREO DE GITHUB"
```

Este comando sirve para especificar tu correo electronico asociado a tus commits

Ahora podemos ver las configuraciones actuales usando:

```bash
git config --list
```

Que nos mostrará todas las opciones establecidas actualmente.

Tambien podemos utilizar el siguiente comando :

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

## 3. Nuestro primer repositorio

---
