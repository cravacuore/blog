---
layout: post
title: "Problema SystemD Espera 90 Segundos Para Apagar"
date: 2016-05-17T01:22:13-03:00
comments: true
---

Dejando de lado los *flamewars* respecto a *systemd*. Vengo usando *systemd* desde que en ArchLinux se adoptó este *init* como el "*default*" y no tuve mayores problemas. Pero hay un [bug](https://github.com/systemd/systemd/issues/1615), el cual me molesta bastante que al intentar apagar la computadora, me deja esperando 90 segundos sobre un error del estilo *"A stop job is running for Session c2 for user..."*.

Una forma de solucionar por lo menos para que la espera sea menor y se fuerce el apagado del sistema, es cambiando este tiempo predeterminado de 90 segundos. Para esto modificamos nuestro archivo de configuración `/etc/systemd/system.conf`, y descomentamos de la sección `[Manager]` la propiedad `DefaultTimeoutStopSec` y le ponemos el tiempo deseado. En mi caso lo dejé de la siguiente forma:

{% highlight python %}
[Manager]
[...]
#DefaultStandardError=inherit
#DefaultTimeoutStartSec=90s
DefaultTimeoutStopSec=10s
#DefaultRestartSec=100ms
#DefaultStartLimitInterval=10s
[...]
{% endhighlight %}

Quedando así de un tiempo aceptable el apagado del equipo. Mientras se espera que se resuelva este problema.
