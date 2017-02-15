---
layout: post
title: "Gtk-WARNING - Theme Not Found Warning"
date: 2017-02-15T12:18:07-03:00
comments: true
---

A pesar de ser un simple *warning* que se puede desestimar, es algo que es recurrente ver al ejecutar algún programa por consola. Por ejemplo:

{% highlight bash %}
Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita"
{% endhighlight %}

Para solucionar esto, basta con instalar [`gnome-themes-standard`](https://www.archlinux.org/packages/extra/x86_64/gnome-themes-standard/) que nos brinda justamente eso, los themes standard para las aplicaciones de Gnome. Entre ellos el *adwaita*. Una vez instalado no aparece más el molesto *warning*.
