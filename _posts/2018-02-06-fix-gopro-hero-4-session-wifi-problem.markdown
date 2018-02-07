---
layout: post
title: "[Fix] GoPro Hero 4 Session WiFi Problem"
date: 2018-02-06T21:55:13-03:00
comments: true
---

> Warning: esta solución me dió resultado a mí, pero quizás no sea tu caso. Queda bajo tu responsabilidad cualquier efecto provocado por seguir esta guía correcta o incorrectamente.

Mi GoPro Hero 4 Session no prendía la conexión por WiFi, la cual nos permite hacer uso de la *app* en el celular que entre otras cosas nos da acceso a algunas opciones que desde la propia GoPro no se pueden cambiar. Dejando limitada sus funcionalidades.

Después de más de un año de indignación, tras intentar pedir ayuda a Soporte Técnico de GoPro, que me respondía sin leer atentamente todo lo que le explicaba que ya había probado, seguía con un problema que hasta ahora parecía sin solución.

Un error que parece algo recurrente para varios clientes de este producto, para lo cual proponían básicamente dos "soluciones" actualizar el firmware de la GoPro a su última versión (lo cuál obviamente intenté sin solución alguna) o mandarles el producto en caso de que todavía esté bajo garantía para que te lo reemplazen por uno nuevo, lo cual me era imposible ya que mi compra fue fuera del país hace tiempo, quedando fuera de garantía. Poco soporte ya para un producto que queda fuera del interés de GoPro al haber lanzado ya las versiones 5 y 6 de la línea.

Investigando alternativas encontré este [repo en GitHub](https://github.com/KonradIT/goprowifihack) que habría un camino posible. Ligado a eso me encontré con un [post](https://community.gopro.com/t5/Cameras/Hero4-Session-wifi-not-turning-on/td-p/3886/highlight/true/page/12) en el foro de GoPro, donde el 25 de Diciembre del 2017, recién alguien encontró una posible solución. Este propone con la SD limpia, crear los siguiente 2 archivos:

`no_shutdown.txt`
> 2_mode=0

`cal.txt`
> _tapp factory_reset

Prendemos la GoPro como si fuésemos a grabar algo, y a los pocos segundos en el *display* debería aparecer `Factory Sett. Restored` y hace unos *flash* con los *led* de color azul. Una vez hecho el reseteado, sacamos la SD, eliminamos los archivos creados dejando la SD limpia nuevamente y volvemos a poner la SD. Una vez prendida ya debería funcionar con normalidad, al apretar la conexión por `App` debería ya darnos el *pin* para conectar con el celular. Eureka!

Probado en mi GoPro Hero 4 Session con versión de *firmware* v02.00.
