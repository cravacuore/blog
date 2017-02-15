---
layout: post
title: "Error De Sonido \"SDLAUDIO: SDL_OpenAudioDevice() Failed\""
date: 2017-02-14T23:30:43-03:00
comments: true
---

Me compré ayer el *bundle* de juegos ["Freedom"](https://www.humblebundle.com/freedom) de **Humble Bundle**, principalmente porque la gran mayoría de estos juegos están disponibles nativamente para Linux y esa es suficiente razón para comprarlo ;).

Entre estos juegos uno de los que más me interesaba y de los primeros que descargué del *bundle* fue [The Stanley Parable](http://www.stanleyparable.com/). Al instalarlo y ejecutarlo, lo primero que noté fue la falta de audio, ejecutándolo desde consola me salía el siguiente error:
{% highlight bash %}
SDLAUDIO: SDL_OpenAudioDevice() failed: No such audio device
{% endhighlight %}

Haciendo una búsqueda rápida, encontré [esta información](https://askubuntu.com/questions/148514/sdl-openaudio-failed-no-available-audio-device-while-starting-psychonauts) que me dió a entender que me faltaba `libpulse` (utilizo pulseaudio, no alsa). Para lo cual, instalando [`lib32-libpulse`](https://www.archlinux.org/packages/multilib/x86_64/lib32-libpulse/) resolvió mi problema al instante para mi caso con ArchLinux 64-bit y pulseaudio.
