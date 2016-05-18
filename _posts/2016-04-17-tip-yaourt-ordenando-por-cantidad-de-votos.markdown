---
layout: post
title: "[Tip] Yaourt - Ordenando por cantidad de votos"
date: 2016-04-17T13:32:12-03:00
comments: true
---

Si como yo usás [**ArchLinux**](https://archlinux.org/) y [*yaourt*](https://aur.archlinux.org/packages/yaourt/) como manejador de los paquetes en [**AUR**](https://aur.archlinux.org/), este es un *tip* que quizás te venga bien.

La mayor cantidad de veces en las que busco un paquete para instalar de AUR, busco el más conocido y votado con el nombre del paquete. Y aprovechando que en AUR se tiene el sistema de votos para puntuar cada paquete, lo más práctico es poder ordenar bajo este criterio. Para esto buscamos de la siguiente forma:

> yaourt 'nombre_paquete' --sort w

o:

> yaourt -Ss 'nombre_paquete' --sort w

También pueden ordenar por popularidad:

> yaourt 'nombre_paquete' --sort p

Estas opciones y otras opciones son heredadas por el uso de *package-query*, para más información:

> man package-query

Saludos.
