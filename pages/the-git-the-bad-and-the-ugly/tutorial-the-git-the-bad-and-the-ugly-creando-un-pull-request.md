---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-creando-un-pull-request.html
sidebar: tutorials
title: ' Forkeando un repositorio'
toc: false
---

    
Una vez hemos creado nuestro fork y hemos añadido los cambios oportunos, el siguiente paso es proponer al dueño del repositorio original que los incluya en su proyecto. Para ello existen en GitHub los pull request.

## Añadiendo cambios al repositorio
Antes de hacer un pull request hay que tener algún cambio en nuestro repositorio. A modo de ejemplo, podemos crear un archivo `fork.md` 

Al igual que en la sección [usando Git](), esto se puede hacer con un editor de texto, o directamente desde la terminal:

```bash
$ echo "Cambios hechos desde un fork" > fork.md
```
![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-01.png)


A continuación, creamos un commit con estos cambios y lo subimos a nuestro fork (`origin`):

```bash
$ git add fork.md
$ git commit -m 'Añadidos cambios al fork'
$ git push origin master
```

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-02.png)

Una vez subidos los cambios, aparecerán en nuestro repositorio en GitHub:

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-03.png)


## Abriendo un pull request
Para abrir un pull request vamos a la web del repositorio original a partir del cual hicimos nuestro fork, y hacemos click en **"New pull request"**.

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-04.png)

GitHub nos llevará a una página en la que podremos comparar los cambios entre las diversas ramas y, seleccionando la opción **"compare across forks"** también entre los forks del repositorio. A continuación, seleccionaremos como *"base fork"* la rama `master` del repositorio original, y como *"head fork"* la rama `master de nuestro fork.

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-05.png)

GitHub nos mostrará una página similar a la que nos muestra al crear una issue. Es esta página podremos resumir y explicar los cambios realizados para que al autor del repositorio original le resulte más sencillo saber qué cambios hemos hecho y con qué fin. También podremos pedir a usuarios concretos de GitHub que revisen los cambios para darles el visto bueno. Normalmente estos usuarios serán las personas encargadas de mantener el proyecto.

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-06.png)

Una vez rellenado el formulario, hacemos click en **"Create pull request"**. Ya sólo queda esperar a que nos acepten los cambios (o nos pidan una revisión).


## Aceptando un pull request
Una vez creado, el pull request aparecerá en la pestaña **"Pull requests"**. Para aceptar un pull request es necesario tener permisos de escritura en el repositorio. Si no los tienes no te quedará más remedio que esperar a que sea aceptado por las personas encargadas de mantener el proyecto. Para aceptar el pull request, una vez revisado, sólo hay que hacer click en **"Merge pull request"**. 

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-07.png)

En caso de que se haya llevado a cabo la integración con éxito de nuestros cambios, el pull request pasará  estar marcado como **"merged"**.

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-08.png)

Visitando la página principal podremos comprobar que los cambios se han aplicado con éxito al repositorio original:

![](img/tutorials/the-git-the-bad-and-the-ugly/github-pr-09.png)
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-forkeando-un-repositorio.html" next="tutorial-the-git-the-bad-and-the-ugly-buenas-practicas-al-trabajar-con-git.html" %}