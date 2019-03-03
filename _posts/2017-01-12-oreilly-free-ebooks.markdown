---
layout: post
title: Automatizando la descarga de eBooks de O'Reilly
description: Usar Python para automatizar la descarga de eBooks de O'Reilly
modified: 2017-01-12
permalink: oreilly-free-ebooks
tags: [programación, python]
---

Hoy, a través del twitter de Adafruit me he enterado de que O'Reilly tenía disponibles más de 243 eBooks sobre informática y programación gratis desde su web.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Hardware &amp; IoT, Programming, Data, and More: 243 Free E-Books from <a href="https://twitter.com/OReillyMedia">@OReillyMedia</a> | <a href="https://twitter.com/hashtag/ebook?src=hash">#ebook</a> <a href="https://t.co/k4mZ0ukpJp">https://t.co/k4mZ0ukpJp</a></p>&mdash; adafruit industries (@adafruit) <a href="https://twitter.com/adafruit/status/818837538186129408">January 10, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Como hace poco "liberaron" eBooks de manera similar, y me costó un rato hacerme con todos los links y descargar los eBooks, esta vez opté por automatizar el proceso. Para ello, usé [Python](https://www.python.org/) y [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) para extraer de forma automática los links de la web de O'Reilly (y ya de paso no tener que logearme).

El script es sencillo, busca las distintas categorías a partir de la página principal y dentro de cada categoría busca los libros que aparecen disponibles. Una vez se tiene la url de la página de cada libro, con una sencilla modificación se obtiene la url del libro en pdf, mobi y epub. Todas estas urls se guardan en un archivo `books.txt`. Además, como ya tenía descargados algunos de ellos de la vez anterior, he añadido una pequeña comprobación. Si encuentra en la carpeta desde la que se lanza el script un archivo con el mismo nombre que el archivo a descargar, lo ignora.

Una vez se tiene el archivo `books.txt` con el listado de links, se puede usar un programa como wget o curl para descargar de forma automática todos los links.

Este script está disponible en un Gist para todo el que quiera usarlo o simplemente echarle un ojo:

<script src="https://gist.github.com/David-Estevez/4e82161347ee23e5b7ffeb7124347d2a.js"></script>
