---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-control-de-versiones.html
sidebar: tutorials
title: ' ¿Por qué quiero usar un gestor de versiones?'
toc: false
---


[Git](https://en.wikipedia.org/wiki/Git) es un software de control de versiones (VCS) creado originalmente por [Linus Tovalds](https://en.wikipedia.org/wiki/Linus_Torvalds) para el desarrollo del [kernel de Linux](https://en.wikipedia.org/wiki/Linux_kernel). 

En lugar de tener en nuestros ordenadores varios archivos distintos por cada versión, lo cual puede llevar a confusión y errores, Git se encarga de gestionar las distintas versiones, almacenándolas y pudiendo revertir los archivos a cualquier versión anterior de los mismos. Así evitamos tener varios archivos llamados `archivo.txt`, `archivo_v2.txt` , `archivo_definitivo.txt`, `archivo_definitivo_v2.txt` y no saber qué cambios hicimos en cada uno de ellos. 

Como Git mantiene información de los cambios efectuados en cada versión, también es más fácil saber qué versión fue la última que funcionaba o en cuál se introdujo cierto bug. Esto supone una ventaja no sólo para nosotros como desarrolladores, sino también para los usuarios, que pueden bajarse una versión estable del software mientras nosotros seguimos añadiendo mejoras.

Si combinamos Git con un repositorio online, como los proporcionados por [github](https://github.com) o [bitbucket](https://bitbucket.org), podremos además trabajar de forma colaborativa con un equipo de desarrolladores. En este caso, Git se encargará de coordinar los distintos cambios para que varios desarrolladores puedan trabajar a la vez sobre un código.

Este manual te enseñará como usar los comandos básicos de Git de forma que puedas beneficiarte de todas estas ventajas en tus proyectos.
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-README.html" next="tutorial-the-git-the-bad-and-the-ugly-github.html" %}