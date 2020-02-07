---
folder: the-git-the-bad-and-the-ugly
permalink: tutorial-the-git-the-bad-and-the-ugly-usando-etiquetas.html
sidebar: tutorials
title: ' Usando etiquetas'
toc: false
---


En este apartado aprenderemos qué son las etiquetas de git y cómo usarlas.

> Comandos: git tag

## ¿Por qué usar etiquetas?
Las etiquetas de git se usan para marcar un commit específico. Imagina que acabas de hacer un commit con el que completas la versión 1.0 de tu software. Resulta interesante marcar el commit con una etiqueta que indique que es la versión 1.0 para ser capaz de encontrar esa release de forma sencilla entre todos los commits. También sería útil para los usuarios de nuestro repositorio, porque distinguirían fácilmente entre el código que está siendo desarrollado y las distintas releases. 

En git existen dos tipos de etiqueta: ligera (lightweight) y anotada (annotated). Una etiqueta ligera es un puntero a un commit, de forma parecida a una rama, pero fija en ese commit. Sería como asignar un nombre lógico a un commit. Las etiquetas anotadas tienen la misma función, pero se almacenan como objetos de git, con checksum, nombre del autor, fecha y mensaje de etiquetado. Debido a todos estos datos extra se suele recomendar usar etiquetas anotadas, aunque si quieres una etiqueta rápida puedes usar una etiqueta ligera.

## Creando una etiqueta ligera (lightweight)
Para crear una etiqueta ligera se usa el comando `git tag` sin ningún flag extra:

```
$ git tag <nombre_etiqueta>
```

Por ejemplo:

```
$ git tag etiqueta_ligera
```

Podremos ver las etiquetas creadas con el comando `git tag :

```
$ git tag
```
   
## Creando una etiqueta anotada (annotated) 
Si en lugar de una etiqueta ligera queremos crear una etiqueta anotada, añadimos el flag "-a". Las etiquetas anotadas son objetos de Git, como los commits, y tiene asociados un autor y un mensaje.

```
$ git tag -a <nombre_etiqueta> -m "Mensaje descriptivo aquí"
```

## Etiquetando un commit pasado 
Al crear una etiqueta con el comando tag, por defecto estamos etiquetando el commit más reciente. Si queremos etiquetar un commit pasado distinto, bastará con usar el hash de ese commit al ejecutar el comando:

```
$ git tag -a <nombre_etiqueta> <hash_commit>
```


### Borrando etiquetas
Para borrar una etiqueta en nuestro repositorio local usaremos el flag "-d", de forma similar a las ramas:

```
$ git tag -d <nombre_etiqueta>
```

Si la etiqueta que queremos borrar está en un repositorio remoto, el comando a ejecutar es el siguiente:

```
$ git push origin :refs/tags/<nombre_etiqueta>

```

### Subiendo etiquetas al repositorio remoto
Hay dos formas de subir etiquetas al repositorio remoto. La primera es subiendo cada etiqueta de forma individual, usando su nombre:

```
$ git push origin <nombre_etiqueta>
```

Si en lugar de subirlas una a una queremos subirlas todas de golpe, añadimos el flag "--tags":

```
$ git push origin --tags
```
{% include book_footer.html previous="tutorial-the-git-the-bad-and-the-ugly-trabajando-con-ramas.html" next="tutorial-the-git-the-bad-and-the-ugly-y-si-uso-windows.html" %}