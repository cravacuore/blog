---
layout: post
title: "[Firefox] Deshabilitar abrir Url del clipboard con click del medio"
date: 2016-06-08T23:52:56-03:00
---

Ya hacía rato que al estar usando Firefox en la notebook, mientras *scrolleaba*, se me abría alguna página que tenía copiada en mi *clipboard*.

Esto se debía a que si en el *pad* hago un *tap* con dos dedos separados me lo tomaba como hacer *click* del medio, el cual Firefox tiene como predeterminado para abrir en la pestaña actual la *url* que tengas copiada en tu *clipboard*.

Simple y rápido, vamos a:

> about:config

Buscamos:

> middlemouse.contentLoadURL

Y cambiamos su valor *default* de `true` a `false`.
