---
layout: post
title: "[Git] Cambiando mensajes de commits anteriores"
date: 2016-06-21T17:06:50-03:00
comments: true
---

## Sobreescribiendo commit anterior

Una de las utilidades que uso muy seguido al querer hacer un pequeño cambio que me olvidé hacer en el último *commit* es:

{% highlight bash %}
git commit --amend
{% endhighlight %}

Este comando me deja pisar el último *commit* que realicé con uno nuevo. Ya sea para agregar algún cambio, o si simplemente quiero cambiar el mensaje de ese *commit*. Si todavía no hice un *push* de los cambios eso es todo, si por el contrario ya lo realizamos, vamos a tener que forzarlo haciendo:

{% highlight bash %}
git push --force
{% endhighlight %}


## ¿Y si quiero cambiar los mensajes de los últimos 3 commits?

En mi caso, me había confundido con el número de *issue* al que hacía referencia en el mensaje de los últimos 3 *commits*. Esto lo pude corregir haciendo uso de `rebase` de la siguiente forma:

{% highlight bash %}
git rebase -i HEAD~4
{% endhighlight %}

Nos da un listado con los últimos 4 *commits*, con la siguiente pinta:

{% highlight bash %}
pick 12039uh No me importa
pick f809asd Alto 3er commit
pick blj0800 Mi super commit 2
pick m24bjk1 EL commit
{% endhighlight %}

Cambiamos el `pick` por `reword` sobre los *commits* cuyos mensajes queremos modificar, para que quede así:

{% highlight bash %}
pick 12039uh No me importa
reword f809asd Alto 3er commit
reword blj0800 Mi super commit 2
reword m24bjk1 EL commit
{% endhighlight %}

Guardamos, y en cada *commit* podemos cambiar el mensaje. Después hacemos un `git push -f`. Y así podemos cambiar varios mensajes de *commits* anteriores.

---
Nota: recomiendo leer más sobre `git rebase` ya que deja hacer más acciones sobre nuestros *commits* anteriores. Quizás más adelante escriba más sobre el tema.
