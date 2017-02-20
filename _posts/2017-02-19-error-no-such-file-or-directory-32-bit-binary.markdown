---
layout: post
title: "Error - No such file or directory (32-bit binary)"
date: 2017-02-19T21:07:35-03:00
comments: true
---

Hay momentos en los que un error poco descriptivo te puede hacer golper la cabeza muchas veces contra el escritorio por horas :P. Este fue el caso de un amigo en un grupo de Telegram, que pidió ayuda porque ya no sabía que pasaba y le tiraba el siguiente error:

{% highlight bash %}
/usr/local/bin/bgdc: No such file or directory
{% endhighlight %}

Quería ejecutar un programa, que estaba en `/usr/local/bin` y que como cualquier programa normal debería dejar ejecutarlo. El PATH estaba bien seteado, los permisos de usuario también y después de varias suposiciones de que podría estar mal, se seguía sin llegar a una solución.

Resulta que el problema era que el binario que se quería ejecutar era de 32-bit, y se estaba intentando correr en ese sistema de 64-bit (lo más normal en la actualidad) sin tener las librerias necesarias de 32-bit para poder lograrlo.

Conclusión, si les tira ese error poco descriptivo de que no encuentra el binario, una gran probabilidad es que sea como este caso. La forma más fácil de saber si un binario es de 32-bit o 64-bit es utilizando `file nombre_binario` en la consola y en el *output* dice si es uno u otro.
