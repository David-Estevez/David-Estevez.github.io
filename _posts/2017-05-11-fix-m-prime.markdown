---
layout: post
title: Arreglando el autolevel de la M Prime One
description: Cómo arreglar el autolevel de la M Prime One
modified: 2017-05-11
tags: [impresión 3D, m-prime, tutorial]
---

La [M Prime One](http://mprime.io/) es una impresora 3D diseñada por [Diego Trapero](https://twitter.com/diegotrap). Desde que la ví en persona en la Maker Faire Madrid me enamoré de su diseño, y me entró un tremendo SAV (Síndrome del Ansia Viva) por tener una. Así que, cuando Diego la puso en oferta, ya no me quedaron excusas para no tener una y me la acabé comprando. Al montarla tuve algunos pequeños problemillas, pero pedí ayuda a Diego y me dió un soporte excelente. Sin mucho esfuerzo mi M Prime estaba ya empezando a imprimir sus primeras piezas. 

Uno de los problemas que más me ocurrió fue que el autonivelado no funcionaba bien, y a veces la punta bajaba demasiado y chocaba con la base al imprimir. Observando un par de impresiones, me di cuenta de que en la secuencia de autonivelado, cuando la punta baja sobre varios puntos para medir la base y calcular el plano real de la base algo iba mal. En una de las esquinas la punta bajaba demasiado al aproximarse al punto de muestreo y no medía el punto correctamente. Pensaba que era un fallo que sólo le ocurría a mi impresora, pero el otro día en el [taller de zowimanoides](http://asrob.uc3m.es/index.php/Taller_de_Zowimanoides) de [ASROB](http://asrob.uc3m.es) Rosa nos trajo su M Prime para que le echásemos un ojo, y le sucedía exactamente lo mismo. Como la solución es sencilla, y puede que le solucione la vida a más gente con una M Prime, he hecho este post explicando cómo arreglarlo.

Como he dicho, la solución es sencilla: aumentar la distancia a la que sube la punta en cada punto antes de medir la distancia a la base. Los pasos para llevar a cabo este cambio son los siguientes:

1. Instalar, si no se tiene ya instalado, el entorno de [Arduino](https://www.arduino.cc/en/Main/Software) y los drivers correspondientes.
2. Ir al [repositorio online de la M Prime](https://github.com/M-Prime/M_Prime_One) y descargarlo. Nos interesan los archivos del firmware, que están en la carpeta `firmware/Marlin`.
3. Abrimos el código descargado con el entorno de Arduino. Tenemos que realizar las siguientes modificaciones al código:
  * Archivo `firmware/Marlin/Configuration.h`: modificar la línea 549, cambiando el valor de 5mm a 1mm:
	
   ```
   #define Z_PROBE_DEPLOY_HEIGHT 1 // Raise to make room for the probe to deploy /
   ```
  * Archivo `firmware/Marlin/Configuration_adv.h`: modificar la línea 316, cambiando el valor de 2mm a 5mm:
   
   ```
   #define Z_HOME_BUMP_MM 5
   ```
4. Subir el código modificado al Arduino Mega de la impresora.

Y ya está. Una vez hechos esos cambios, mi M Prime One empezó a funcionar genial, y no me ha vuelto a dar nada de guerra. ¡Ahora es darle a "imprimir" y listo!