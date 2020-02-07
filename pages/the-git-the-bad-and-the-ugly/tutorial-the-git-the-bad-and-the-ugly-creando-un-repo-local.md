---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-creando-un-repo-local.html
sidebar: tutorials
title: ' Creando un repo (local)'
toc: false
---


En este apartado veremos el primer paso trabajando con un gestor de versiones: crear un repositorio. 

> Comandos básicos: git init, git clone

## Crear un repositorio: git init

Para nuestro primer ejemplo, crearemos un repositorio local en el que empezar a trabajar. Para ello crearemos una carpeta nueva que contendrá el repositorio, y usaremos el comando 'git init':

```bash
$ mkdir test_repo
$ cd test_repo
$ git init
```

Tras introducir estos comandos, habremos creado un repositorio nuevo, que estará disponible de forma local.

![](img/tutorials/the-git-the-bad-and-the-ugly/git_init.png)

El repositorio está vacío, así que vamos a añadir nuestro primer archivo. Abriremos un editor de texto y crearemos un archivo que se llame 'README.md'. Dentro, escribiremos la frase 'Hola, mundo!'. Para aquellos que usen GNU/Linux, esto se puede realizar usando el siguiente comando:

```bash
$ echo "Hola, mundo!" > README.md
```

![](img/tutorials/the-git-the-bad-and-the-ugly/hola_mundo.png)

### Añadir archivos al repositorio: git add / git commit

Este achivo está creado, pero todavía no se ha marcado para añadir al repositorio.

![](img/tutorials/the-git-the-bad-and-the-ugly/git_pre_add.png)

El comando que nos permite marcar los archivos que se añadirán al repositorio es 'git add <archivo>'.

```bash
$ git add README.md
``` 

Ahora el archivo está marcado, pero todavía no se ha añadido al repositorio. Podemos comprobarlo ejecutando el comando 'git status'.

```bash
$ git status
```

![](img/tutorials/the-git-the-bad-and-the-ugly/git_add.png)

Una vez tengamos seleccionados todos los archivos que deseamos incluir en el repositorio, hacemos un commit con el comando 'git commit'. Un commit guardará en estado actual de los archivos que hemos marcado, y les asignará un mensaje que indica los cambios realizados, así como un autor y un identificador.

```bash
$ git commit -m "Commit inicial"
```
Usando el flag '-m' podremos especificar el mensaje que indica los cambios. Si no usamos el flag '-m', nos aparecerá una pantalla donde escribir el mensaje.

![](img/tutorials/the-git-the-bad-and-the-ugly/git_commit.png)

Todo los cambios que hemos hecho hasta ahora han sido únicamente en el repositorio de nuestro ordenador. En el próximo apartado aprenderemos a subir estos cambios a un repositorio online, y a descargar los posibles cambios que otros usuarios hayan hecho en nuestro repositorio.
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-instalar-git.html" next="tutorial-the-git-the-bad-and-the-ugly-crear-un-repositorio-remoto.html" %}