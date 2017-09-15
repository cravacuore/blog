---
layout: post
title: "[Workaround] Little Racers Streets crash on linux"
date: 2017-09-15T15:46:32-03:00
comments: true
---

Al querer iniciar el juego [Little Racers Streets](http://store.steampowered.com/app/262690/Little_Racers_STREET/) desde Steam (que por cierto es muy divertido), me tiraba un error similar a esto `An error ocurred: An exception was thrown by the type initializer for System.Drawing.GDIPlus`.

Encontré la solución [acá](https://steamcommunity.com/app/262690/discussions/0/358416600605446480/?ctp=4#c1291816569120425810), usando ArchLinux hacemos los siguiente:

{% highlight bash %}
  sudo pacman -S sdl2_mixer
  cd "$HOME/.local/share/Steam/steamapps/common/Little Racers STREET/lib64"
  mkdir ../bak64/
  mv libSDL2_mixer-2.0.so.0 ../bak64/
  ln -s /usr/lib/libSDL2_mixer-2.0.so.0 ./
{% endhighlight %}
