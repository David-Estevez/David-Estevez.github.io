---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-elementos-principales-en-github.html
sidebar: tutorials
title: ' Elementos principales en GitHub'
toc: false
---

GitHub tiene una serie de elementos muy útiles a la hora de trabajar con nuestro proyecto, los cuales se describen a continuación.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_general.png)

## Code
Code es la página principal de un repositorio en GitHub, la cual incluye la descripción del proyecto, unas etiquetas para clasificar la temática del proyecto y una vista de seguidores, estrellas, commits, branches, releases, etc del repositorio.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_code.png)

Esta página también presenta un explorador de archivos desde el que podemos ver los archivos incluidos en el proyecto, y navegar por ellos. En la parte inferior de la página podemos encontrar una visualización del archivo README.md, que suele contener información útil sobre el repositorio.

## Issues
GitHub tiene integrado un gestor de bugs en forma de Issues. Cada Issue representa un problema o mejora del proyecto. Dentro de cada Issue se pueden poner comentarios en los que informar de los progresos o debatir la mejor forma de solucionarla.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_issues.png)

Para poner una nueva Issue, podemos hacer click en "New Issue", tras lo cual nos aparece el siguiente formulario para rellenar. Desde él podemos añadir un título, una descripción, asignar la Issue a una persona concreta (o varias) y etiquetar la Issue.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_issues_new.png)

## Fork
GitHub tiene un sistema de permisos que controla qué usuarios pueden subir código a cada repositorio. Si deseamos hacer alguna modificación al software de una tercera persona, pero no tenemos autorización para publicar en su repositorio, podemos hacer un Fork de dicho repositorio. Un Fork no es más que una copia del repositorio, que pasa a ser propiedad del usuario que hizo el Fork. De esta forma, ese usuario ya podría realizar modificaciones sobre el código del repositorio en su copia, sin necesidad de tener autorización para subir cambios.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_fork.png)

## Pull Requests 
Si has hecho un Fork de un proyecto y has añadido modificaciones útiles para los usuarios del repositorio original, puede ser interesante integrar esos cambios en ese repositorio.  Para ello, podemos hacer una petición al autor en forma de Pull Request, mediante el botón "New Pull Request" de la pestaña "Code".

La  primera pantalla que nos saldrá una vez pulsado el botón nos permitirá comparar ramas del repositorio original con ramas de nuestro repositorio, para ver los cambios realizados. Una vez comprobado, podemos usar el botón "Create Pull Request" para proceder a crear una  Pull Request.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_PR1.png)

En la siguiente pantalla nos aparecerá un formulario muy similar al de una nueva Issue, en el que podremos explicar qué cambios hemos hecho y por qué. El mantenedor del repositorio original podrá entonces revisar nuestros cambios y, si así lo decide, integrarlos en el repositorio principal. 

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_PR2.png)

En proyectos grandes el uso de Forks y Pull Requests entre miembros del mismo equipo ayuda a mejorar la coordinación y a reducir errores.

## Projects
Un Project de GitHub es una forma de organizar tareas e Issues relacionadas entre sí. Está inspirada en el método [Kanban](https://es.wikipedia.org/wiki/Kanban) y tiene un aspecto muy similar al de los tablones de [Trello](https://trello.com/). A cada Project le podremos añadir tarjetas que pueden corresponder o no con Issues del proyecto y moverlas entre las distintas columnas del tablón.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_project.png)

## Wiki
GitHub nos permite también tener documentación asociada a un proyecto en una wiki alojada en GitHub. Esta wiki se puede editar online, y está basada en [Gollum](https://github.com/gollum/gollum).La wiki se almacena en un repositorio independiente que podemos clonar y editar también localmente.
![](img/tutorials/the-git-the-bad-and-the-ugly/elements_wiki.png)


## Graphs
La pestaña Graph nos permite ver distintas visualizaciones de datos relacionadas con nuestro repositorio, como cuántas líneas de código/commits ha aportado cada contribuidor o cuál es la franja horaria en la que se suelen hacer más commits. Uno de los gráficos más útiles es el de Network, que muestra de forma gráfica los commits y branches de nuestro proyecto, así como su estado.

![](img/tutorials/the-git-the-bad-and-the-ugly/elements_graphs.png)

## GitHub Pages
GitHub permite alojar una página web estática asociada a un repositorio, que puede actuar como documentación o como web del proyecto. También nos permite tener una web estática asociada a nuestro usuario, que podemos usar como web personal.

Una forma muy sencilla de generar esta página web es usar [Jekyll](https://jekyllrb.com/) para generar una web estática a partir de archivos markdown.

La guía de configuración de las GitHub Pages se puede consultar [aquí](https://help.github.com/categories/github-pages-basics/).
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-que-es-github.html" next="tutorial-the-git-the-bad-and-the-ugly-crear-una-cuenta-de-github.html" %}