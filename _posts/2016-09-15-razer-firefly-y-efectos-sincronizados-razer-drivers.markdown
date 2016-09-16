---
layout: post
title: "Razer Firefly y efectos sincronizados (razer-drivers) - ArchLinux"
date: 2016-09-15T20:26:28-03:00
---

Vinculado al reciente cambio de mi teclado por uno mecánico, como conté [acá](http://cravacuore.com.ar/blog/2016/09/14/razer-blackwidow-chroma-tournament-edition-archlinux.html), vino la idea de cambiar mi *mouse pad* que desde hace muchos años era un [SteelSeries Qck Mini](https://steelseries.com/gaming-mousepads/qck-mini) por uno nuevo un poco más grande. Por comodidad y principalmente para lograr mejores matanzas en mis ocasionales partidas de Urban Terror :D.

Así fue como empecé a buscar el reemplazo ideal, y dado mi anterior compra *Razer* con el teclado Chroma (RGB retroiluminado. a.k.a. colorcitos locos) me encontré con su *mouse pad* [Razer Firefly](http://www.razerzone.com/gaming-mouse-mats/razer-firefly) también de la línea *Chroma*.

![razer-firefly](https://cloud.openmailbox.org/index.php/apps/files_sharing/ajax/publicpreview.php?x=1875&y=1052&a=true&file=razer-firefly.jpg&t=R211Kf4JxA2Giky&scalingup=0)

Tan lindo como se ve, como notan lo terminé adquiriendo :P. Pero sin olvidar antes de revisar si tenía soporte por parte de [razer-drivers](https://github.com/terrycain/razer-drivers) que también usé para lograr los efectos colorinches en mi teclado.

### Sincronización de efectos

Un pequeño detalle era que se puedan sincronizar estos efectos para que trabajen al mismo tiempo. Después de dar algunas vueltas, terminó siendo bastante simple. Hay que fijarnos que en el archivo de configuración `~/.razer-service/razer.conf` en nuestro *HOME* tenga la siguiente línea:

> sync_effects_enabled = True

Como ven, tiene que quedar en True para habilitar la sincronización entre dispositivos. Aunque debería estar habilitada por *default*.

### Problemas con GUI

El único problema que me encontré fue con [razerCommander](https://github.com/GabMus/razerCommander), una de las dos *GUI* que mencioné en el [post previo](http://cravacuore.com.ar/blog/2016/09/14/razer-blackwidow-chroma-tournament-edition-archlinux.html). En este no me tomaba mis dos dispositivos en el listado, por lo tanto no podía seleccionarle un efecto particular para en este caso el *mouse pad*. Sin embargo, al estar sincronizados el efecto que elegía para el teclado se hacía sincronizado con el mismo.

Por otro lado, con [Polychromatic](https://github.com/lah7/polychromatic) se me listaban ambos dispositivos como pueden ver en la siguiente imagen.

![polychromatic-devices-list](https://cloud.openmailbox.org/index.php/apps/files_sharing/ajax/publicpreview.php?x=1875&y=1052&a=true&file=polychromatic-devices-list.png&t=14ZTg698Xb1sKwS&scalingup=0)

Pero si bien funciona correctamente los efectos sólo son sincronizados cuando aplico el efecto deseado como si fuese sólo para el teclado, si elijo desde la pestaña de Razer Firefly este sólo se aplica para el este y no es sincronizado.

### Efectos

En cuanto a los efectos, estos quedan un poco más limitados si queremos que sean sincronizados, volviendo al listado que comenté en el post anterior:

  * *Spectrum*: funciona de mil maravillas y es uno de mis favoritos para tener sincronizado.
  * *Wave*: también funciona correctamente pasando del teclado y siguiendo por el *pad* desde el borde superior izquierdo haciendo rotación inversa a las agujas del reloj (en el caso de que el efecto sea en dirección derecha o 'Right').
  * *Reactive*: este no me funcionó, se supone debería hacer el efecto para el *pad* cuando apretamos algo con el *mouse*.
  * *Breath*: este funciona correctamente, pero al elegir los colores tanto para uno o dos colores de este efecto. En el caso de 'Random' el color no es sincronizado sino que sólo el efecto es sincronizado pero cada dispositivo hace un color aleatorio diferente. Estoy intentando agregar un modo que sea 'Dual Random' donde los colores aleatorios se repliquen sincronizadamente.
  * *Ripple*: este efecto no hace reacción alguna en el *mouse pad* al apretar una tecla ni con click del mouse. Me gustaría que continúe el barrido que hace este efecto desde una tecla pasando por el borde del *mouse pad*.
  * *Static*: funciona correctamente sin problemas.
  * *None*: Idem.

### Conclusión

El *pad* Razer Firefly queda en magnífica combinación con el teclado, aún con los efectos limitados. Me costó acostumbrarme a la nueva textura del *pad* pasando del anterior de tipo tela (*cloth*; de hecho ahora Razer está por sacar una edición de este mismo *pad* pero con tela), pero resultó ser muy cómodo y el ser un poco más grande me dejó bajar la sensibilidad del mouse para tener más control sobre la mira para pegar esos *super 360 no scope headshots* en el Urban Terror xD.
