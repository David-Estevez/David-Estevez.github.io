---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-y-si-uso-windows.html
sidebar: tutorials
title: ' ¿Y si uso Windows?'
toc: false
---


Aunque esta guía se centra principalmente en el uso de Git desde la consola de comandos en un sistema GNU/Linux, también existen otras alternativas para usar Git desde Windows.

## GitHub Desktop
GitHub posee una aplicación llamada [GitHub Desktop](https://desktop.github.com/) que nos permite gestionar repositorios de Git de forma gráfica desde Windows.

![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-desktop.png)

## Configurando GitHub Desktop
Tras instalar GitHub Desktop en nuestro sistema, el programa nos pedirá nuestros datos de GitHub para su configuración.

![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-login.png)

Tras la configuración se nos mostrará la pantalla principal del programa con un repositorio de prueba con el que aprender a usar GitHub Desktop.
![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-main-screen.png)

Si la configuración no ha sido correcta, o si deseamos cambiarla, podemos usar la pantalla de opciones de GitHub Desktop.
![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-options.png)

## Clonar repositorios de GitHub
Para clonar un repositorio de GitHub, pulsaremos en el símbolo "+" que aparece en la esquina superior izquierda. 

![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-clone.png)

En el menú desplegable podremos ver los repositorios que tenemos en nuestra cuenta de GitHub. Seleccionaremos el que deseemos clonar y el programa nos preguntará en qué carpeta local queremos que se almacenen los archivos del repositorio.

![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-clone02.png)

Una vez seleccionada la carpeta, nos mostrará una pantalla de carga mientras GitHub Desktop descarga nuestro repositorio.

![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-clone03.png)

## Añadir archivos al repositorio (git add & git commit)
Si creamos archivos o editamos archivos existentes en el directorio del repositorio, GitHub Desktop lo reconocerá y nos oferecerá la posibilidad de añadirlos al commit actual. Esto sería equivalente a ejecutar un comando `git add` en la terminal.
![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-add.png)

Una vez están seleccionados los archivos, podremos escribir un mensaje de commit y una descripción, igual que haríamos con un comando `git commit` desde la terminal. Pulsando el botón "Commit to master" crearía el commit en la rama master.
![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-commit.png)

## Eliminar archivos del repositorio (git rm & git commit)
Para eliminar archivos del repositorio, primero debemos borrarlos de la carpeta local del repositorio. Una vez borrados, la pantalla principal de GitHub Desktop nos ofrecerá un diálogo similar al de añadir archivos, que podremos usar para hacer un commit en el que se borren dichos archivos del repositorio.
![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-remove.png)

## Subir y bajar cambios desde el repositorio remoto (git push & git pull)
Para subir y bajar cambios desde el repositorio remoto, GitHub Desktop dispone de un botón "sync" en la parte superior derecha.
![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-main-screen02.png)

Al hacer click veremos como el botón para a poner "syncing", lo cual nos indica que está sincronizando datos con el repositorio remoto.
![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-push-pull.png)

## Explora y experimenta
En esta sección hemos cubierto los comandos básicos de Git realizados desde GitHub Desktop, pero la aplicación permite llevar a cabo muchas más acciones. Explora y experimenta con la interfaz para descubrilas, o usa [la guía online de GitHub Desktop](https://help.github.com/desktop/).

![](img/tutorials/the-git-the-bad-and-the-ugly/win-gh-main-screen03.png)
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-usando-etiquetas.html" next="tutorial-the-git-the-bad-and-the-ugly-colaborando-con-proyectos-en-github.html" %}