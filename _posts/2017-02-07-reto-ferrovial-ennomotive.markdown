---
layout: post
title: Reto Ferrovial-Ennomotive
description: Resumen de nuestra participación en el Reto Ferrovial-Ennomotive
modified: 2017-02-07
tags: [robótica, competición]
image:
  feature: 2017-02-07/header.jpg
---

El [Reto Ferrovial-Ennomotive](http://www.ennomotive.com/autonomous-robot-arduino-challenge-prizes/) es una competición internacional de robótica que tuvo lugar durante la [Robot Global Expo](http://www.globalrobotexpo.com/es/ferrovial-challenge_esp/) de este año. El objetivo de este reto era construir un robot móvil que, de forma autónoma, fuese capaz de recorrer un circuito desde un punto a otro sin chocar con ningún obstáculo.

<figure align="center">
	<img src="/img/blog/2017-02-07/ennomotive-01.jpg" alt="El circuito emulaba una construcción" width="450px">
	<figcaption>El circuito emulaba una construcción.</figcaption>
</figure>


Como en ASROB nos van los retos más que a un tonto un lápiz, formamos un equipo para competir en el reto. El equipo lo componíamos [Juan G. Víctores](http://roboticslab.uc3m.es/roboticslab/people/jg-victores), [Víctor Díaz](https://github.com/victordiazobregon), [Ignacio Montesino](https://github.com/imontesino) y un servidor (me refiero a mi, no a las cosas esas que se conectan a internet, aunque también paso bastante tiempo conectado...).

Nuestra idea inicial era resucitar la plataforma [ECRO](http://asrob.uc3m.es/index.php/Proyecto_Ecro), que por su tamaño y forma nos pareció perfecta para el transporte de objetos desde un punto A hasta un punto B. Además, como mecánicamente ya estaba prácticamente montado eso nos quitaría mucho trabajo. Error número 1. Al leer las bases del concurso, nos dimos cuenta de que el ECRO sobrepasaba ampliamente los límites de tamaño. Vamos, que si lo metíamos tal cual en el circuito, en lugar de evitar los obstáculos pasaría por encima de ellos.

El siquiente paso fue hacerle al [ECRO](http://asrob.uc3m.es/index.php/Proyecto_Ecro) una reducción de tamaño considerable, conectando todas las piezas (motores, ruedas, drivers, etc) del robot original a una nueva base de plástico. Al quitarle la plancha metálica original, además, perdió bastante peso, aunque seguía pesando un quintal. A esta versión de ECRO la llamamos cariñosamente NECRO (New ECRO). Con el robot ya hecho, pasamos a cablearlo todo y conectar los contorladores de las ruedas con el PC para poder encender los motores. Tras muchos quebraderos de cabeza conseguimos que los motores se movieran, justo el día antes de que empezase la expo.


<figure class="half">
	<img src="/img/blog/2017-02-07/ennomotive-02.jpg" alt="ECRO antes" >
<img src="/img/blog/2017-02-07/ennomotive-03.jpg" alt="ECRO después (NECRO)" >
	<figcaption>ECRO vs New ECRO</figcaption>
</figure>

El primer día de la competición era de entrenamientos libres para poner a punto el robot en el circuito. En nuestro caso, el primer día consistió en volver a hacer que los motores se volviesen a mover. En algún momento del transporte del ECRO y su reconexión cometimos el error número 2, y una de las controladoras de las ruedas dejó de funcionar. Tras estar hasta las tantas en la uni solucionando el problema los motores volvieron a funcionar, esta vez hablando directamente con un Arduino a los drivers.

Y así llegó el segundo día de competición, en el que tendría lugar la clasificación para la final. Y nosotros todavía con el robot sin programar. Tras muchas pruebas en el circuito, Juan se curró un pedazo de algoritmo reactivo que usaba la imagen de profundidad de una ASUS XTION Pro para evitar obstáculos y navegar por el circuito. El robot se portó muy bien y quedamos terceros, lo que nos aseguraba un puesto en la final.

El tercer y último día tuvo lugar la final, casi sin tiempo para más pruebas. Esta vez, al comenzar la prueba, el NECRO empezó a arrasar con todos los obstáculos, como si no los viera. Error número 3. Con las prisas, no comprobamos hacia donde miraba la cámara del robot antes de arrancar el programa.Y resulta que la cámara estaba mirando hacia el techo (ligeramente). Cuando lo corregimos ya iba por la recta final, pero aún así empatamos en el tercer puesto. La organización decidió hacer otra ronda de desempate, y esta vez nuestro robot miraba correctamente a los obstáculos, así que quedamos terceros. ¡Todo un éxito!



<figure class="third">
	{% for i in (1..12) %}
	{% if i < 10 %}
	<a href="/img/blog/2017-02-07/gallery-0{{i}}.jpg"><img src="/img/blog/2017-02-07/gallery-0{{i}}.jpg" alt=""></a>
	{% else %}
	<a href="/img/blog/2017-02-07/gallery-{{i}}.jpg"><img src="/img/blog/2017-02-07/gallery-{{i}}.jpg" alt=""></a>
	{% endif %}
	{% endfor %}
</figure>

