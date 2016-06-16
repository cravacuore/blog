---
layout: post
title: "[Git] Stashing - Guardando Trabajo en Progreso"
date: 2016-06-15T21:59:52-03:00
comments: true
---

Muchas veces mientras estamos programando sobre algún proyecto, tenemos algún *issue* avanzado pero no completado y nos urge tener que hacer algún cambio en un *branch* distinto al que estamos. Esto puede pasar más o menos seguido dependiendo si estamos en un equipo de trabajo, si usamos *feature branches*, u otras razones.

Hacer *stash* en *git*, nos permite justamente esto, nos guarda todos nuestros archivos estén como *staged* o *unstaged* como un **WIP** (Work In Progress). Para esto hacemos un:

> git stash

Podemos ahora cambiar de *branch* o lo que tengamos que hacer. Cuando querramos volver esos cambios sobre el branch que estábamos trabajando, hacemos:

> git stash apply

Este nos trae el último stash realizado.

Podemos hacer varios *stash* seguidos, para ver el listado de estos:

> git stash list

Y para traer uno de esos cambios en particular, por ejemplo:

> git stash apply stash@{1}

Esto resulta muy útil mientras trabajamos en proyectos versionados con *git*.
