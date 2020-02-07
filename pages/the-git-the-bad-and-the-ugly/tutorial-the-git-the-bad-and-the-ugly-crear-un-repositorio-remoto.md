---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-crear-un-repositorio-remoto.html
sidebar: tutorials
title: ' Crear un repositorio remoto'
toc: false
---

Para subir nuestro repositorio local a un repositorio online, primero deberemos crear un repositorio en un sitio online como GitHub o bitbucket. En este apartado aprenderemos a crear un repositorio online al que subir nuestro código para poder distribuir nuestro código y además disponer de una copia de respaldo online.

> Comandos: git remote add, git clone

## Crear un repositorio en GitHub
Ver [Crear un repositorio en GitHub](tutorial-the-git-the-bad-and-the-ugly-crear-un-repositorio-en-github.html).

## Añadir la dirección del repositorio remoto a nuestro repositorio local (git remote add)
La primera opción para trabajar con nuestro repositorio remoto es añadir la dirección del repositorio remoto que acabamos de crear a nuestro repositorio local. Esta es la opción más lógica si ya disponemos
de un repositorio local creado y con algunos contenidos, como el que se creó en el [apartado 02](tutorial-the-git-the-bad-and-the-ugly-creando-un-repo-local.html).

Estando dentro del repositorio que creamos en el [apartado 02](tutorial-the-git-the-bad-and-the-ugly-creando-un-repo-local.html), ejecutaremos el siguiente comando:

```
$ git remote add origin <url de nuestro repo>
```

En el caso del repositorio que yo he creado, el comando quedaría de la siguiente forma:

```
$ git remote add origin https://github.com/UC3Music-e/test-repository.git
```

Si deseamos usar https como protocolo para subir y bajar código, o:

```
$ git remote add origin git@github.com:UC3Music-e/test-repository.git
```

Si preferimos usar ssh. Para usar ssh deberemos [configurar ssh](https://help.github.com/articles/generating-ssh-keys/) previamente, generando y añadiendo nuestras claves a github.

Si nos fijamos en la última captura del apartado anterior, la url de nuestro repositorio aparece en el segundo apartado de las sugerencias que github nos ha hecho para crear el repositorio local.

![](img/tutorials/the-git-the-bad-and-the-ugly/03_remote_add.jpg)

Como podemos ver en la imagen, el nombre del directorio donde está almacenado el repositorio es irrelevante, y aunque no coincide el local con el remoto (test_repo vs test-repository), git no ha devuelto ningún mensaje de error y la operación se ha llevado a cabo correctamente.

## Crear un repositorio local a partir del repositorio remoto (git clone)
La segunda opción, adecuada cuando hemos creado el repositorio remoto en github, pero todavía no existe el repositorio local, es usar el comando git clone para hacer un clon local del remositorio remoto, descargando todos aquellos archivos que se encuentren ya subidos al repositorio. Este es el método que usaremos también cuando queramos bajarnos algún repositorio de github para usarlo.

Para clonar el repositorio, podremos usar el protocolo https:

```
$ git clone https://github.com/UC3Music-e/test-repository.git
```

o el protocolo ssh:
   
```
$ git clone git@github.com:UC3Music-e/test-repository.git
```

Al hacer un clone de un repositorio vacío, git nos avisará:

![](img/tutorials/the-git-the-bad-and-the-ugly/03_git_clone.jpg)

Si el repositorio no está vacío, el mensaje devuelto será distinto:

![](img/tutorials/the-git-the-bad-and-the-ugly/03_git_clone_02.jpg)
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-creando-un-repo-local.html" next="tutorial-the-git-the-bad-and-the-ugly-subir-y-bajar-cambios-a-un-repositorio-remoto.html" %}