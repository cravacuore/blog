---
layout: post
title: "Pactl - Controlando Pulseaudio Desde Consola"
date: 2016-12-15T20:08:56-03:00
comments: true
---

En el [anterior post](http://cravacuore.com.ar/blog/2016/10/16/pavucontrol-pestaa-predeterminada-al-ser-iniciado.html), comentaba sobre una comodidad con *pavucontrol* para acelerar algo rutinario. Vamos avanzando poco a poco a algo un poco más rápido para esta tarea, la cual de forma ideal quiero automatizarla lo más posible.

La tarea rutinaria es cambiar los perfiles de la placa "integrada" que me da la salida de *jack 3.5mm" común y la placa USB de mis auriculares Razer Megalodon. Activando y desactivando una u otra respectivamente.

Bajando un poco de nivel, pasando de lo gráfico a la consola, descubrí que *pactl* permite realizar el manejo mediante consola de el servicio de *Pulseaudio*.

Para esto, primero tenemos que saber cuáles son las placas, para esto:

{% highlight bash %}
pactl list short cards
{% endhighlight %}

En mi caso, me muestra lo siguiente:
{% highlight bash %}
0       alsa_card.usb-Razer_Razer_Megalodon-00  module-alsa-card.c
1       alsa_card.pci-0000_00_1b.0      module-alsa-card.c
{% endhighlight %}

De ese listado sacamos el número de índice que aparece como primera columna. En mi caso, sólo aplicaría el cambio de perfiles sobre la placa Razer (índice 0). Y cambio su perfil a *"Surround 5.1 + Input"* de la siguiente manera:

{% highlight bash %}
pactl set-card-profile 0 output:analog-surround-51+input:analog-mono
{% endhighlight %}

Y para revertir, simplemente *seteo* el perfil como Apagado:

{% highlight bash %}
pactl set-card-profile 0 off
{% endhighlight %}

Estos comandos los agrego como alias en mi *config* de *zsh* (~/.zshrc):

{% highlight bash %}
alias ron="pactl set-card-profile 0 output:analog-surround-51+input:analog-mono"
alias roff="pactl set-card-profile 0 off"
{% endhighlight %}

Hasta acá voy a avanzar por el momento, ya es mucho más rápido cambiar desde consola mi configuración de audio. El próximo paso sería crear una función para *zsh* que sepa el último cambio de configuración y revierta al anterior, y esa función ejecutarla desde un atajo de teclado. Quizás ese sea un próximo *post*.
