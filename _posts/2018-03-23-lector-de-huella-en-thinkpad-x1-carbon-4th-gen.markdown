---
layout: post
title: "Lector de Huella en Thinkpad X1 Carbon 4th Gen"
date: 2018-03-23T21:00:59-03:00
comments: true
---

Lo único que no funcionaba en mi X1 sobre linux era el lector de huella, un lujo que era prescindible. Hace tiempo que venía siguiendo el progreso sobre este [repo](https://github.com/nmikhailov/Validity90/) que intentaba tener un driver funcional para Linux haciendo ingeniería inversa sobre el lector.

Hace poco, armó un prototipo y pidió feedback sobre el mismo. A todo esto otro usuario, armó un [driver](https://github.com/3v1n0/libfprint) sobre [fprint](https://github.com/freedesktop/libfprint) en base a este prototipo dando soporte a este lector de huellas.

*Warning: seguir estos pasos es bajo tu responsabilidad, los mismos me funcionaron específicamente sobre mi X1 Carbon 4th gen con Archlinux. Además de ser sobre un prototipo, un driver propiamente desarrollado está en los planes de esta misma gente para un futuro.*

Estos son los pasos que seguí para lograr hacerlo funcionar, en base a lo [escrito](https://gitter.im/Validity90/Lobby?at=5a9ed978f3f6d24c6844244a) por el usuario [@vKnmnn](https://github.com/vKnmnn) en el [Gitter](https://gitter.im/Validity90/Lobby) sobre el prototipo de [@nmikhailov](https://github.com/nmikhailov):

  * Instalar [libfprint-vfs0090-git](https://aur.archlinux.org/packages/libfprint-vfs0090-git/)
  * Editar `/etc/pam.d/system-auth`, agregando `pam_fprintd.so` antes de `pam_unix.so`. Quedando:
{% highlight bash %}
[..]
auth sufficient pam_fprintd.so
auth required   pam_unix.so
[..]
{% endhighlight %}
  Esto habilita a usar sudo con huella.

  * Si usás sddm como tu *display manager* como yo, editamos`/etc/pam.d/sddm` agregando `pam_fprintd.so` como primer línea de `auth`. Quedando:
{% highlight bash %}
  auth sufficient pam_fprintd.so
  [..]
{% endhighlight %}
  Esto nos habilita a utilizar la huella en el *login* apretando *enter* sobre el campo vacío de contraseña previamente a utilizar la huella.

  * En el prototipo todavía no se puede hacer la 'inicialización' de las huellas. Por lo tanto desde un windows, ya sea en disco o en una máquina virtual:
      * si estamos en una virtual, hay que habilitar el dispositivo *usb* del lector para lograr verlo en la virtual
      * si no detecta el dispositivo, buscamos el driver para windows en la página de Lenovo. Yo instalé [este](https://download.lenovo.com/pccbbs/mobiles/n1cgn05w.exe)
      * vamos a Settings -> Users -> Log-in options
          * Agregamos un PIN
          * Y en la sección Windows Hello -> agregamos una huella (no hace falta agregar más que una cualquiera, es sólo para inicializar el lector)
  * Volviendo a nuestro linux
      * registramos nuestras huellas haciendo:
          > for finger in {left,right}-{thumb,{index,middle,ring,little}-finger}; do fprintd-enroll -f "$finger" "$USER"; done
          * Nos va a pedir dedo por dedo, y registra 5 veces cada uno antes de pasar al siguiente.
          * Podemos poner en todos los dedos a registrar un único o unos pocos, repitiendo en los que no nos interese.
  * Ahora haciendo uso de *sudo* o al intentar loguearse por sddm, nos pide una huella y el lector se enciende.

Enjoy. Me voy a mantener al tanto para cuando saquen el *driver* definitivo.
