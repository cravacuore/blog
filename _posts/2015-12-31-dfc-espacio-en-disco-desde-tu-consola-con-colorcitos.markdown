---
layout: post
title: "dfc - Espacio en disco desde tu consola con colorcitos"
date: 2015-12-31T18:42:12-03:00
---

Nunca usé una GUI para hacer algo tan simple como ver el espacio que tengo disponible en mis discos. De hecho siempre me arreglé usando en consola:

> df -h

o también:

> lsblk

Pero me encontré con una utilidad muy similar que le agrega un poco de color y una barra de porcentaje para obtener la información de mis discos de forma más rápida y visual. Esta herramienta es **dfc**, también para utilizar desde tu consola de preferencia que me pareció muy buena.

Algunas funcionalidades que tiene es la posibilidad de mostrar sólo algunos sectores del disco (*'-p'*), sumar los sectores mostrados (*'-s'*), entre otras. Para más info:

> man dfc

Acá pueden ver una imágen haciendo uso de la herramienta:
![dfc](https://cloud.openmailbox.org/index.php/apps/files_sharing/ajax/publicpreview.php?x=1350&y=770&a=true&file=dfc.png&t=iPDfIK8RIlXgF0a&scalingup=0)

En Archlinux, la encontramos en los repos oficiales de *community*:

> sudo pacman -S dfc

Espero les sirva. Saludos.
