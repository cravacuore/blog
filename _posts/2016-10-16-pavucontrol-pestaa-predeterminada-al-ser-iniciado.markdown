---
layout: post
title: "Pavucontrol - Pestaña predeterminada al ser iniciado"
date: 2016-10-16T20:26:08-03:00
comments: true
---

Algo que suelo hacer bastante seguido es abrir pavucontrol para cambiar por dónde escucho el audio, para esto tengo que ir hasta la última pestaña de "Configuración" y ahí *scrollear* los perfiles para cada dispositivo de salida.

Descubrí que para ahorrarme un poquito de tiempo al realizar esta tarea, se puede seleccionar en qué pestaña abre pavucontrol al ser iniciado. Para esto se hace uso del *flag* '--tab' o abreviado '-t' y el número de la pestaña. En mi caso la que más frecuento es la pestaña de "Configuración" que es la 5ta pestaña, entonces abro pavucontrol de la siguiente manera:

{% highlight bash %}
pavucontrol -t 5
{% endhighlight %}

En mi caso este comando lo puse reemplazando mi atajo de teclado en plasma para abrir pavucontrol. También se podría crear un alias para pavucontrol reemplazando por lo mismo. Este simple truquito me ahorra un paso, por lo menos hasta el día que le dedique otro rato para semi-automatizar esta tarea mediante *script*.
