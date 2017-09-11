---
layout: post
title: "[Workaround] Problema de líneas horizontales en Konsole"
date: 2017-09-11T19:16:08-03:00
comments: true
---

En la consola de plasma [Konsole](https://www.kde.org/applications/system/konsole/), tuve un problema durante bastante tiempo y no le dí mayor importancia hasta que me decidí por arreglarlo.

El problema es que al escribir, mover el cursor o seleccionar texto en la consola me aparecían líneas horizontales a lo largo de la terminal que aparecían y desaparecían. Pensé que era cuestión de la fuente, o el *theme* que estaba usando.

Resulta que es un [bug](https://bugs.kde.org/show_bug.cgi?id=373232) de Konsole que tiene con el escalado de la *UI* en Plasma. De modo que si modifica el escalado en Plasma, surge este problema. Yo había modificado el escalado a '1.1' al empezar a utilizar Plasma en mi notebook.

Como *workaround* se puede poner el escalado por *default* en **1**. Para esto vamos a 'Displays' buscamos 'Scale display' y cambiamos el valor a '1'. Aplicamos los cambios, y reiniciamos 'X' o el sistema por completo.
