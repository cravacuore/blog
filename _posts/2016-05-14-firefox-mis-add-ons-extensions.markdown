---
layout: post
title: "Firefox - Mis Add-ons (Extensions)"
date: 2016-05-14T00:28:09-03:00
comments: true
---

Voy a nombrar los *add-ons* o extensiones que utilizo a diario en mi navegador Firefox, y comentar el porqué los uso brevemente.

Este *post* lo escribo por dos razones: una en forma de recordatorio cuando quiero instalar algunos en alguna instalación ajena y la otra para poder referenciar este *post* cuando me preguntan que extensiones recomendaría o utilizo. Además voy a dejar los *links* a cada uno para instalar rápidamente y no tener que buscarlos.

# Privacidad / Seguridad

## Disconnect

Un *addon open source* que logra que las páginas carguen más rápido y para evitar el "trackeo" de terceros. Lo utilizo principalmente para evitar los botones para compartir por redes sociales (que no utilizo) y por consecuente evitar el "trackeo" de esas redes, y como *plus* las páginas cargan más rápido.

[Link Addon - Disconnect](https://addons.mozilla.org/en-US/firefox/addon/disconnect/)

## uBlock Origin

Esta es la alternativa que prefiero en contraparte a otros bloqueadores de publicidad. Opto por él porque consume menos recursos y no sólo bloquea publicidades, sino también *trackers* y páginas con *malware*. Es un proyecto de *software* libre, con licencia GPLv3 [alojado en Github](https://github.com/gorhill/uBlock/).

### uBlock != uBlock Origin

No se debe confundir el *addon* uBlock con el uBlock Origin. Uno fue un *fork* del otro, y tomaron distintos caminos para su desarrollo. Yo elegí en su momento utilizar uBlock Origin, y al momento de escribir este *post* uBlock hace meses que no tiene actualizaciones, mientras que uBlock Origin las tiene a diario.

[Link Addon - uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)

## HTTPS-Everywhere

> Encrypt the Web!

Logra que toda página que tenga disponible su versión con *HTTPS* se cargue directamente, por ejemplo si escribo github.com me va a cargar automáticamente https://github.com. Una funcionalidad muy útil que hace que siempre que sea posible naveguemos utilizando conexiones cifradas.

[Link página oficial - Descarga](https://www.eff.org/https-everywhere)

## Self-Destructing Cookies

Hay muchas razones por las que las páginas guardan *cookies* en el navegador, puede ser para simplemente saber que cosas ya visitaste en su página, guardar tu *nick*, mantener una *session*, o para "trackearte", o espiarte, etcétera. Lo molesto es que muchas veces se guardan incontables *cookies* incluso de páginas a las que entramos sólo por una vez y quedan indefinidamente, haciendo a largo plazo posiblemente más lenta la navegación, y los problemas de seguridad que pueden causar.

Para evitar todo eso que comentaba antes uso este *addon*, que simplemente cuando cerramos una pestaña automáticamente borra todas las *cookies* que haya generado esa página.

[Link Addon - Self-Destructing Cookies](https://addons.mozilla.org/en-US/firefox/addon/self-destructing-cookies/)

## Privacy Settings

Una de las tareas que más aburren, es acordarse que cosas te conviene modificar entrando al temido *about:config* para deshabilitar opciones que no necesitás y muchas veces pueden repercutir contra tu privacidad. Este *addon* simplifica cambiando las variables de configuración bajo distintos perfiles, desde uno con los valores *defaults* a otros más restrictivos, además de poder prender/apagar a mano los que quieras en el momento si lo necesitás con una interfaz simple a golpe de *click*.

[Link Addon - Privacy Settings](https://addons.mozilla.org/en-US/firefox/addon/privacy-settings/)

## Random Agent Spoofer

Para intentar evitar un poco lo que se llama el *fingerprint*, la "huella digital", de tu navegador. El navegador mantiene un *string* con bastante información llamado "user-agent", como el nombre y versión de tu navegador, que sistema operativo utilizás, entre otras cosas. Este *addon* te provee la facilidad de cambiar estos datos, y cambiar de forma *random* o por elección entre distintos *profiles* de navegadores, sistemas operativos, etcétera; dando datos "falsos" para hacerle creer a quien o lo que lo lea. Además sirve si queremos probar alguna funcionalidad de una página, por ejemplo si una página cambia su formato, color, tamaño, datos o lo que sea dependiendo de estos datos. Y se puede configurar para que se cambie automáticamente cada cierto período de tiempo.

[Link Addon - Random Agent Spoofer](https://addons.mozilla.org/en-US/firefox/addon/random-agent-spoofer/)

# Desarrollo de Software

## Firebug

Este *addon* extiende ampliamente las herramientas para desarrollo web, permitiendo editar, hacer *debug* y monitorear en vivo cualquier elemento en una página web. Imprescindible.

[Link Addon - Firebug](https://addons.mozilla.org/en-US/firefox/addon/firebug/)

## REST Easy

Un cliente REST simple en el navegador. Permite realizar *requests* seleccionando el método HTTP, y pudiendo visualizar la información, y sus *headers*, etcétera.

[Link Addon - REST Easy](https://addons.mozilla.org/en-US/firefox/addon/rest-easy/)

# Otras utilidades

## DuckDuckGo Plus

Si usás [DuckDuckGo](https://duckduckgo.com/) como tu buscador por defecto (lo cual deberías :P), este *addon* permite utilizar este buscador para varias funciones. La que principalmente utilizo es poder realizar búsquedas directamente desde la barra de direcciones. Además permite, seleccionar texto de una página, hacer click derecho y tener la opción de buscar información sobre ese texto, entre otras cosas. Super recomendado si te gusta el pato como buscador.

[Link Addon - DuckDuckGo Plus](https://addons.mozilla.org/en-US/firefox/addon/duckduckgo-for-firefox/)

## KillSpinners

Hay páginas que nunca terminan de cargar, y si tenés una conexión a internet lenta..menos! Para evitar que las páginas se queden cargando indefinidamente gastando esa preciosa cantidad de banda ancha, quizás innecesariamente por causa de algún *script*, o lo que sea; este *addon* corta la carga de una página si esta no se terminó de cargar a los 30 segundos (tiempo *default*). Muy útil, especialmente si abrimos muchas pestañas rápido, mejor aprovechar la conexión para lo que vas utilizando y seguir cargando a medida que es necesario.

[Link Addon - KillSpinner](https://addons.mozilla.org/en-US/firefox/addon/killspinners/)

## VimFx

Si sos un usuario del editor de textos [vim](http://www.vim.org/), y sos feliz con los "movimientos" que se realizan en este, que mejor que poder usar los mismos para manejarte en tu navegador. Este *addon* hace justo eso, te permite manejarte en el navegador sólo con el teclado bajo atajos al estilo de *vim*. Navegación con las teclas `hjkl`, *scroll* por página con `d` y `u`, búsqueda con `/`, y lo mejor, con `f` te despliega letras sobre los *links* visibles de la página que estás viendo, y al apretar esas letras es como hacer *click* sobre ese link, lo mismo con `F` pero te abre en una nueva pestaña; entre muchas otras funcionalidades.

[Link Addon - VimFx](https://addons.mozilla.org/en-US/firefox/addon/vimfx/)

## Tab Groups

Esta era una funcionalidad que antes venía incluída en Firefox, si la extrañabas, la podés agregar nuevamente con este *addon*. Este te permite tener "agrupados" ciertas pestañas y así tener ordenados distintos grupos o áreas.

[Link Addon - Tab Groups](https://addons.mozilla.org/en-US/firefox/addon/tab-groups-panorama/)

## Send Tab to Device

Si como yo utilizás el poder tener sincronizado los Firefox en distintos dispositivos con [Firefox Sync](https://www.mozilla.org/en-US/firefox/sync/), para tener acceso a las páginas guardadas, etcétera; por ejemplo, entre tu computadora y tu celular ambos con Firefox, desde la aplicación de Android se facilita el poder enviar una pestaña a otro dispositivo pero no se tiene la misma facilidad para hacer al revés (de una computadora a otro dispositivo). Este *addon* te deja hacer justo eso, haciendo *click* derecho sobre la página que querés mandar, y `Send this page to device` donde te aparece un listado con tus dispositivos, aceptás y se envía.

[Link Addon - Send Tab to Device](https://addons.mozilla.org/en-US/firefox/addon/send-tab-to-device/)

## OneTab

Si como yo a veces podés llegar a tener 50+ pestañas en tu navegador por 'X' razón (lo cual además de ser un despropósito es un a punto de desatarse **caos** :P), esta es tu salvación. Este *addon* te deja simplemente guardar de forma rápida todas las URLs de las pestañas que tenías abiertas apretando sólo un botón y tenerlas listadas, pero sin estar comiéndote los recursos y con el peligro de perder toda esa vital información que tendrías que ya haber leído pero lo dejabas para otro momento xD. Además te deja exportar los listados, lo cual utilizo para realizar *backups* de mis muchas pestañas que no quiero perder si se cierra el Firefox y surge algún error. Recomiendo dejar "pinneada" la pestaña con el listado de OneTab.

[Link Addon - OneTab](https://addons.mozilla.org/en-US/firefox/addon/onetab/)

## Site Launcher

Si hay páginas que visitás diariamente, y no te gusta tener una barra con los marcadores (*Bookmarks Toolbar*) o no querés usar el mouse para abrir rápidamente ciertas páginas. Este *addon* te permite tener un panel con páginas que se pueden abrir con una combinación de teclas, en mi caso por ejemplo, `Ctrl + Espacio` me abre el panel y dentro del panel aprieto `h` me abre mi Github, entonces para abrir [Openmailbox](https://www.openmailbox.org/) simplemente es `Ctrl + Espacio y letra o`. Totalmente configurable qué páginas y con qué letra.

[Link Addon - Site Launcher](https://addons.mozilla.org/en-US/firefox/addon/sitelauncher/)

## GNotifier

Este *addon* sirve si querés que para las notificaciones de Firefox se utilicen las notificaciones nativas de tu sistema.

[Link Addon - GNotifier](https://addons.mozilla.org/en-US/firefox/addon/gnotifier/)

# Addons en Firefox para Android

En Android no sólo tenemos una [versión de Firefox](https://play.google.com/store/apps/details?id=org.mozilla.firefox) para utilizar, sino que a esta también se le pueden instalar extensiones. Aunque no haya una variedad tan amplia como para el navegador, varias de las esenciales de las nombradas anteriormente se encuentran disponibles.

* [uBlock Origin](https://addons.mozilla.org/en-US/android/addon/ublock-origin/)
* [HTTPS-Everywhere](https://addons.mozilla.org/en-US/android/addon/https-everywhere/)
* [Self-Destructing Cookies](https://addons.mozilla.org/en-US/android/addon/self-destructing-cookies/)
* [Privacy Settings](https://addons.mozilla.org/en-US/android/addon/privacy-settings/)

Eso es todo.
