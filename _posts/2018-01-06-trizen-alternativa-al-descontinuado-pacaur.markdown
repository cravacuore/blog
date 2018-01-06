---
layout: post
title: "Trizen - Alternativa Al 'Descontinuado' Pacaur"
date: 2018-01-06T00:30:12-03:00
comments: true
---

[Pacaur](https://aur.archlinux.org/packages/pacaur/) fue durante mucho tiempo mi *helper* por defecto para la instalación y manejo de paquetes tanto de repos oficiales como de [AUR](https://aur.archlinux.org/). Y hace no mucho tiempo quien lo mantenía [anunció](https://bbs.archlinux.org/viewtopic.php?pid=1755144#p1755144) que iba a dejar de dar soporte al proyecto.

Buscando una alternativa para un rápido cambio, cruzando la *data* de la [tabla comparativa de helpers](https://wiki.archlinux.org/index.php/AUR_helpers#Comparison_table) y este [thread](https://www.reddit.com/r/archlinux/comments/7k5suz/pacaur_now_unmaintained/) de Reddit donde se trató la temática, me terminé por decidir por [Trizen](https://aur.archlinux.org/packages/trizen/) al ofrecer la experiencia más similar.

Dando uso por última vez de pacaur para la instalación de su sucesor:

{% highlight bash %}
  pacaur -S trizen
{% endhighlight %}

Y un leve cambio en la configuración de trizen, para que los paquetes clonados se guarden en `.cache` en vez de `/tmp`:

`~/.config/trizen/trizen.conf`
{% highlight bash %}
  clone_dir => ".cache/trizen",
{% endhighlight %}

Podríamos desinstalar pacaur y utilizar normalmente trizen prácticamente como si de pacaur se tratase. Para más info `man trizen`.

PS: pongo 'descontinuado' ya que pacaur es open source (https://github.com/rmarquis/pacaur) y quien quiera podría agarrar la posta y continuar su desarrollo aunque su propio desarrollador principal (quien dejó el proyecto) ya no lo mantenga.
