---
layout: post
title: "[Git] .gitignore sólo para archivos locales"
date: 2016-06-14T12:19:08-03:00
comments: true
---

# Ignorando archivos localmente

Cuando uno trabaja en un proyecto git, se tiene un archivo `.gitignore` para que no se versionen ciertos archivos del proyecto. A veces algunos de estos sólo nos incumben localmente para nuestro entorno y no son específicos del proyecto, por ejemplo archivos de configuración del IDE que estemos utilizando. Agregarlos no tiene sentido e ignorarlos a través de esta configuración tampoco sería apropiado.

Para esto podemos hacer uso del archivo `.git/info/exclude` dentro de nuestro proyecto. En este se utiliza la misma sintaxis que en el *gitignore* y sólo se mantiene localmente, evitando así agregar archivos innecesarios de nuestro entorno.
