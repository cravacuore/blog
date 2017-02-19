---
layout: post
title: "[Ranger] Previsualización de Imágenes"
date: 2017-02-19T20:32:30-03:00
comments: true
---

Ranger es el file manager que más utilizo, seguido de *dolphin* para tareas más "complejas". Es un file manager para la consola, muy rápido y completo que uso desde hace años.

Reinstalando en la notebook nueva, una funcionalidad de *ranger* que todavía me faltaba configurar era la previsualización de imágenes. Para lograr esto en ArchLinux, simplemente realizamos lo siguiente:

{% highlight bash %}
pacaur -S ranger w3m imlib2 # Instalamos lo necesario (con el gestor que usen, yo utilizo pacaur pero puede ser pacman)
ranger                      # Abrimos por primera vez ranger para que cree la carpeta default para configuración
ranger --copy-config=all    # esto nos da los archivos default de config de ranger en nuestro home
{% endhighlight %}

Seteamos en ~/.config/ranger/rc.conf para la previsualización

> set preview_images true

Eso es todo, y ya deberíamos poder previsualizar las imágenes en ranger como vemos acá.
![ranger](https://cloud.openmailbox.org/index.php/apps/files_sharing/ajax/publicpreview.php?x=1875&y=1017&a=true&file=ranger-image-preview.png&t=XhfUq69OruU5qjq&scalingup=0)
