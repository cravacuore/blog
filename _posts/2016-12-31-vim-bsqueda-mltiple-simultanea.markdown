---
layout: post
title: "[Vim] Búsqueda Múltiple Simultánea"
date: 2016-12-31T19:04:46-03:00
comments: true
---

Antes que nada, por si no lo saben, Vim es mi editor de texto de preferencia. Ya lo vengo usando hace mucho tiempo, y si hay algo que hay que entender es que siempre hay algo nuevo para aprender y/o mejorar nuestra forma de manejarnos en Vim. Seguramente vaya a hacer varios *posts* comentando sobre utilidades, *plugins* o *tips* para o sobre Vim.

En este caso, es algo simple. Cuando uno quiere realizar una búsqueda en Vim, simplemente hace `/loquebusco`. El *tip* que vengo a dar, es cómo buscar más de un término al mismo tiempo y así ir pasando por los distintos encontrados sin tener que hacer dos búsquedas por separado.

Para esto hacemos: `/loquebusco\|otra_cosa` y se pueden concatenar términos sucesivamente.
