---
layout: post
title: "Razer BlackWidow Chroma Tournament Edition - ArchLinux"
date: 2016-09-14T18:30:53-03:00
comments: true
---

> Nota: tenía la intención de hacer este _post_ ni bien conseguí el teclado, pero pasó el tiempo y no lo escribí (quedó en borradores desde el 25/05 e.e). De hecho mucho de lo que escribí lo voy a borrar porque la herramienta de las que les voy a hablar ya simplificó mucho su forma de instalarla y usarla.

Hace rato que venía mirando con cariño los teclados mecánicos, en particular dos modelos:

* [WASD Code](http://www.wasdkeyboards.com/index.php/products/code-keyboard/code-87-key-mechanical-keyboard.html)
    * retroiluminado blanco
    * *switches Cherry MX Clear*
    * *10-keyless* (sin *numpad*)
* [Razer BlackWidow Chroma Tournament Edition](http://www.razerzone.com/gaming-keyboards-keypads/razer-blackwidow-tournament-edition-chroma#clicky)
    * retroiluminación RGB "Chroma"
    * *switches Razer Green*
    * *10-keyless* (sin *numpad* = "Tournament Edition")
    * trae un estuche, para llevarlo a tus más arduas batallas en Lan Party xD.

Hace unos meses pude conseguir uno. En particular este fue, como lo dice el título, un *Razer BlackWidow Chroma Tournament Edition* con los *switches Razer Green*.

![razer-keyboard](https://cloud.openmailbox.org/index.php/apps/files_sharing/ajax/publicpreview.php?x=1299&y=770&a=true&file=razer-keyboard-wave-effect.jpg&t=SduLVmIYbQgSfBe&scalingup=0)

La experiencia de un teclado mecánico era algo que tenía que probar y este fue el reemplazo de mi querido y muy hermoso [Razer Lycosa Mirror](http://www.razerzone.com/gaming-keyboards-keypads/razer-lycosa-mirror).

Desde ya puedo comentar que la experiencia de escribir en este nuevo teclado es simplemente genial, el teclado tiene el tamaño que yo considero ideal y un peso considerable que hace pensar en un antiguo teclado IBM.

Algo que puede o no gustarte es el sonido al teclear, a mí me encanta xD. Estos *switches* son un equivalente a unos *Cherry MX Blue* pero con una actuación al presionarlos un poco más ligera (por lo que pude leer).

## Colores

El gran tema de este *post* es lograr hacer funcionar los efectos de colores que trae este teclado en ArchLinux, una tarea que pensé que iba a ser mucho más sencilla (de hecho al momento de publicar este _post_ ya es mucho más sencilla :P).

Ya había tomado el recaudo de verificar si era factible el poder controlar estas opciones desde Linux antes de realizar la compra, encontrando la siguiente herramienta:

  * [https://github.com/terrycain/razer-drivers](https://github.com/terrycain/razer-drivers)

La cual tiene una [página](https://terrycain.github.io/razer-drivers/) donde se listan los dispositivos que actualmente soporta entre otra información.

### Instalando

Anteriormente se tenía que hacer un clon del repo e instalar cada paquete a mano, además de encontrar e instalar todas las dependencias necesarias por cada uno. Ahora para ArchLinux está en **AUR** (wiiii :D), así que simplemente buscamos el paquete *razer-driver-meta* que nos instala todo lo necesario.

`Edit: cerca de Septiembre del 2017 cambiaron el nombre del proyecto a openrazer, el paquete se llama ahora openrazer-meta`

> yaourt -S razer-driver-meta

O cada uno de los paquetes necesarios por separados, que serían *razer-driver-dkms*, *razer-daemon*, *python-razer* también desde **AUR**.

> yaourt -S razer-driver-dkms razer-daemon python-razer

Y se recomienda después agregar tu usuario al grupo `plugdev` para completar la instalación, haciendo:

> sudo gpasswd -a «tu_usuario» plugdev

#### Instalar GUI

Por el momento no tiene ni se recomienda una forma de manipular los efectos desde consola, para lo cual hay que instalar una GUI. Hay dos opciones que son directamente recomendadas en este repo:

  * [razerCommander](https://github.com/GabMus/razerCommander): hecha con GTK, es simple y funciona bastante bien. Había empezado a utilizar esta, de hecho incluso empecé a contribuir con algunos arreglos en el código, pero me terminé decantando por la que les nombro siguiente. Este tiene la ventaja de que también se encuentra vía **AUR** para los usuarios de ArchLinux:

  > yaourt -S razerCommander

  ![razerCommander](https://cloud.openmailbox.org/index.php/apps/files_sharing/ajax/publicpreview.php?x=1299&y=770&a=true&file=razer-gui-razerCommander.png&t=3SYH3rE6eo9ulpj&scalingup=0)

  * [Polychromatic](https://github.com/lah7/polychromatic): esta me parece está un poco más completa. Además de incluir un *applet* para el *traybar* desde donde controlar los efectos, la interfaz me parece un poco más cómoda y limpia. A su vez con esta última en particular me lista bien en caso de tener otros dispositivos Razer Chroma, cosa que no me funcionaba hasta el momento con razerCommander.

{% highlight bash %}
git clone https://github.com/lah7/polychromatic.git
cd polychromatic
git checkout stable
sudo ./install/install.sh
{% endhighlight %}

  ![Polychromatic](https://cloud.openmailbox.org/index.php/apps/files_sharing/ajax/publicpreview.php?x=1299&y=770&a=true&file=razer-gui-polychromatic-controller.png&t=PFNnwRkG1NnpWY8&scalingup=0)

Ambas funcionan correctamente, y dejan hacer lo deseado. Incluso crear nuevos perfiles *custom*. Depende de gustos personales, alguna característica particular, o la comodidad de que esté en **AUR** (caso de razerCommander) el que te decidas por una o la otra.

### Efectos

Al momento de publicar este _post_ tenemos disponibles los siguientes efectos:

  * *Spectrum*: hace un barrido lento cambiando de colores.
  * *Wave*: hace una 'ola' de colores a lo largo del teclado, se puede elegir que vaya de derecha a izquierda o de forma inversa.
  * *Reactive*: este 'reacciona' al tocar cada tecla y se ilumina para después disfuminarse, se puede elegir el color con el que se hace este efecto y 3 niveles de velocidad del efecto.
  * *Breath*: este hace un efecto en el que se prende lentamente de un color y se apaga lentamente. Se pueden elegir para que cicle entre 2 colores a elegir o que cambie de color de forma aleatoria.
  * *Ripple*: hace un efecto como si tiráramos una piedra al agua al apretar cada tecla desde esa tecla y hacia afuera. Se puede elegir un color o que cambie aleatoriamente cada vez que se aprieta una tecla.
  * *Static*: simplemente deja de un solo color todo prendido.
  * *None*: sin efecto, todo apagado.

Además de este listado de efectos, que por cierto son puro chiches :P, se puede elegir la intensidad de la retroiluminación y se pueden crear perfiles decidiendo el color de cada tecla en particular.

## Conclusión

Como conclusión puedo decirles que escribir en teclado mecánico es un placer, y le recomiendo conseguirse uno a toda persona que se pase horas de horas usándolo como es mi caso como programador. Pero ya sea que escribas novelas, seas un *Pro Player* de **LoL** o escribas recetas para un blog; te super recomiendo te consigas uno de estos teclados mecánicos.

Además la travesía para lograr hacer funcionar los millones de colores RGB en el teclado fue muy poco doloroso, gracias a los genios que crearon *razer-drivers*. Funciona sin problemas, y siguen agregando soporte para tener colorcitos en otros dispositivos Razer Chroma. En forma de agradecimiento, y aprovechando a mi beneficio les hice unos muy pequeños aportes al código y documentación en su repo, espero poder contribuir próximamente más substancialmente.

Quien sabe quizás termine haciendo efectos locos, se me ocurren algunos que quisiera como por ejemplo: un perfil para Vim que cambie dependiendo el modo en el que esté, otro que haga flash de colores para distintas notificaciones ya sea desktop o vinculadas al celular, o incluso alguno efecto que siga el ritmo de la música en Spotify o Vlc para que disfruten de horas mirando como hace el ciclo de colores y sean unos enfermos hipnotizados de la emoción como yo..ya veremos xD
