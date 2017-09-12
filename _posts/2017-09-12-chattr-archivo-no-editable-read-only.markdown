---
layout: post
title: "Chattr - Archivo No Editable (Read-only)"
date: 2017-09-12T09:31:52-03:00
comments: true
---

Si se quiere *settear* un archivo como *read-only*, para que este no pueda ser modificado. Se puede hacer uso de `chattr` de la siguiente manera:

{% highlight bash %}
  # chattr +i /path/to/file
{% endhighlight %}

Y para revertirlo:

{% highlight bash %}
  # chattr -i /path/to/file
{% endhighlight %}

Muy útil cuando cambiamos alguna *setting* de un programa y queremos que quede de forma permanente sin que sea sobrescrita por el programa mismo.
