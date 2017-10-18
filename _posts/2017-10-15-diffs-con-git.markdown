---
layout: post
title: Trabajando con Git y archivos binarios
description: Cómo añadir archivos binarios a un repositorio de git
modified: 2017-10-15
tags:  [software, tutorial, git]
---

Git es un sistema de control de versiones ideal para guardar el código de nuestros proyectos en distintas etapas de su desarrollo. Pero a veces necesitamos guardar otros archivos que no son código. Por ejemplo, si estamos diseñando una placa o un robot, querremos guardar también las fuentes de los esquemáticos de la placa o de las piezas que lo componen.

Git fue diseñado para almacenar código fuente, que normalmente se guarda en archivos de texto. La forma que tiene Git de guardar internamente las distintas versiones del código es analizando los ficheros de texto y guardando los cambios de una versión a la siguiente. De esta forma, aunque el código sea muy largo, si sólo cambiamos una línea el repositorio no guardará dos copias de nuestro código (que serían idénticas salvo por una línea), sino el archivo original y la línea cambiada. Con esta  información git es capaz de reconstruir ambas versiones. Eso está muy bien si lo que queremos guardar son archivos de texto, pero deja de funcionar cuando lo que guardamos son archivos binarios como imágenes o archivos de FreeCAD. En este caso, cada vez que hacemos cambios en los archivos git no es capaz de analizar cuáles han sido los cambios de una versión a otra, y guarda ambos archivos. Esta es la razón por la que los repositorios en los que guardamos imágenes crecen tanto de tamaño en disco.

No obstante, en algunos casos hay solución. Si tenemos alguna forma de obtener un archivo de texto a partir del binario que queremos guardar, hoy nos permite usar ese archivo en lugar del binario dentro del repositorio. En este post voy a dar dos ejemplos de uso de este truco: ficheros de FreeCAD y bases de datos de SQLite.

## Archivos de FreeCAD
Este truco lo aprendí de [Jaime ](https://github.com/gvJaime) cuando ambos trabajábamos en BQ. En aquella época Jaime, que es un mago del FreeCAD, se encontraba trabajando en la  [Sunrise](https://github.com/gvJaime/Sunrise), una impresora de resina libre. Durante el desarrollo guardaba el progreso en un repositorio de git que, como los archivos de FreeCAD son binarios, comenzó a crecer desorbitadamente de tamaño. Investigando un poco descubrimos que los archivos de FreeCAD no eran más que varios archivos de texto comprimidos en un archivo Zip, entre ellos un XML con los datos del diseño mecánico. Esto significa que, si git fuese capaz de descomprimir el archivo Zip y analizar ese archivo de texto, podría guardar sólo las diferencias entre versiones, ahorrando un montón de espacio en disco. Y lo grande de git es no solo que puede, sino que resulta que esto se tuvo en cuenta al programarlo, por lo que no hace falta hackear git para conseguirlo. Sólo hay que editar un par de archivos de configuración.

Primero, tenemos que especificar qué tipo de acción queremos ejecutar cuando git se encuentre con un archivo de FreeCAD. Para ello escribimos un archivo `.gitattributes` con el siguiente contenido:

```
*.FCStd diff=zip
*.fcstd diff=zip
```
 
 Este archivo lo que le dice a git es que los archivos con la extensión `*.FCStd` o `*.fsctd` (archivos de FreeCAD) debe tratarlos como archivos comprimidos zip. Pero git no sabe todavía cómo descomprimir un zip. Para especificar la acción que git tiene realizar para poder acceder al texto plano, tenemos que crear un archivo `.gitconfig` en el que explicaremos a git qué hacer con un archivo zip:
 
```
 [diff "zip"]
 textconv = unzip -c -a
```
 
Este archivo lo podemos instalar a nivel de un repo concreto, editando el archivo `.git/config` dentro de nuestro repo y añadiendo esas líneas. También podemos optar por instalarlo a nivel global para todos nuestros repos, editando el archivo `~/.gitconfig`.

## Bases de datos de SQLite
El otro caso de uso en el que este truco nos puede resultar útil es con bases de datos SQLite. En mi caso, me interesaba tener una copia de seguridad diaria de de una base de datos SQLite, pero no quería guardar cientos de copias de la misma base de datos. Ya que es incremental, pensé en git para guardar la copia de seguridad, pero las bases de datos de SQLite son binarias. Solución: usar el comando `dump` para convertir la base de datos en un archivo de texto con los comandos SQL que generan esa base de datos. De esta forma el repositorio puede guardar los cambios en los comandos SQL.

En este caso los cambios a realizar son parecidos al caso anterior. Primero tenemos que crear el archivo `.gitattributes` que le dice a git que trate los archivos con extensión `*.sqlite`como bases de datos de sqlite3:

```
*.sqlite diff=sqlite3
``` 

Y luego definimos en el archivo `.git/config` (o `~/.gitconfig`) lo que debe hacer con una base de datos de sqlite3 para extraer una versión de la base de datos en texto plano (usar el comando dump de sqlite):

```
[diff "sqlite3"]
textconv = echo ".dump" | sqlite3
```

## ¡Y más!
Todo esto se puede aplicar a cualquier fichero que se pueda convertir en un archivo de texto plano, como por ejemplo un archivo `*.docx`, que no es más que un archivo zip con archivos xml dentro. No hay más que adaptar los ejemplos de este post con los comandos necesarios para el tipo de archivo en el que estés interesado.

### Referencias

* https://github.com/gvJaime/Sunrise
* https://ongardie.net/blog/sqlite-in-git/