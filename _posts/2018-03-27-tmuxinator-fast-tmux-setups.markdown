---
layout: post
title: "Tmuxinator - fast tmux setups"
date: 2018-03-27T12:51:23-03:00
comments: true
---

Ya hace tiempo que venía utilizando [Tmux](https://github.com/tmux/tmux) como '*terminal multiplexer*', tanto para trabajo como otras tareas habituales. Algo que me molestaba era que ante cualquier reinicio perdía el 'estado' de mis sesiones de *tmux*. Por lo tanto, tenía que volver a crear mis *N* sesiones y en cada una abrir las múltiples aplicaciones, servicios y entornos de desarrollo teniendo en cuenta también de activar el *virtualenv* correspondiente a cada proyecto en cada *tab* dentro de *tmux*, algo engorroso de hacer.

Previamente había utilizado los *plugins* de *tmux*: [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect) y [tmux-continuum](https://github.com/tmux-plugins/tmux-continuum) con los cuales me guardaba automáticamente el estado de las sesiones cada tanto, y ante un reinicio este me creaba todas las sesiones anteriormente creadas con los *tabs* y paneles correspondientes, pero con esto no mantenía ni las *apps*, ni servicios, ni los *virtualenv* ejecutados.

Y hace poco me encontré con [este post](https://andrewbrookins.com/tech/instant-django-dev-environments-with-tmux-tmuxinator-and-virtualenvwrapper/) que me iluminó de la existencia de [Tmuxinator](https://github.com/tmuxinator/tmuxinator) contenida en una gema Ruby, este me resuelve en mayor medida lo que venía necesitando. Prácticamente este te deja crear una *config* `.yml` donde definir la creación de sesiones '*custom*' en *tmux*.

### Instalación y configuración

Siguiendo los pasos de instalación y configuración en el mismo [repo](https://github.com/tmuxinator/tmuxinator#installation). (*Warning*: los resultados y pasos efectuados son en mi entorno con Archlinux, estos pueden variar en tu caso.)

#### Instalación

Primero instalamos la gema:
{% highlight bash %}
gem install tmuxinator
{% endhighlight %}

#### Consola

Hay que asegurarse que tengamos definida la variable de editor *default* `$EDITOR`. En mi caso usando *zsh*, en la *config* `~/.zshrc` la tengo definida como `export EDITOR="vim"`.

#### Tmux

Tmuxinator funciona para versiones de 1.8 en adelante, exceptuando la versión 2.5. Vemos la versión haciendo en consola `tmux -V` en mi caso me devuelve `tmux 2.6`.
Además si utilizamos en nuestra *config* de *tmux* (/etc/tmux.conf) la opción `base-index` distinta a la *default* (que es 0) también hay que setear `pane-base-index`.
En mi caso entonces, tengo:

{% highlight bash %}
[..]
set -g base-index 1
set-window-option -g pane-base-index 1
[..]
{% endhighlight %}

#### Completion

Para conseguir autocompletado de los comandos de *tmuxinator* en la consola, hay que hacer un *source* sobre los que correspondan a tu *shell*. En mi caso, haciendo uso de *zsh* en `~/.zshrc` encuentro el archivo de *completion* haciendo `source ~/.gem/ruby/2.5.0/gems/tmuxinator-0.10.1/completion/tmuxinator.zsh`.

#### Verificación

Podemos ahora hacer un `tmuxinator doctor` para confirmar que tenemos todo lo necesario instalado y configurado. Si nos muestra algo como esto:

{% highlight bash %}
Checking if tmux is installed ==> Yes
Checking if $EDITOR is set ==> Yes
Checking if $SHELL is set ==> Yes
{% endhighlight %}

Estamos listos. En caso contrario, vuelvan a leer los pasos anteriores a ver qué les faltó. Y/o lean el error y resuelvan.

### Ahora ¿cómo lo uso?

Para crear una nueva *config* de *tmuxinator*, simplemente hacemos:

{% highlight bash %}
tmuxinator new foobar
{% endhighlight %}

Esto nos crea un nueva *config* en `~/.config/tmuxinator/foobar.yml` con contenido de ejemplo para completar.

#### Editando config

Una vez creada esta nueva *config*, la abrimos con nuestro editor de preferencia y podemos ver entre los distintos parámetros cosas como:
  * `name`: setea nombre del proyecto de tmuxinator.
  * `root`: la ruta raíz de nuestro proyecto sobre el que se ejecutan todas las operaciones. Por default abre cualquier *tab* de tmux sobre este directorio.
  * `on_project_first_start`: ejecuta lo que pongamos en esta línea al iniciar el proyecto con `tmuxinator start foobar` (útil para inicializar servicios, como base de datos).
  * `pre_window`: ejecuta esta línea sobre cada nueva *window* abierta en tmux (muy útil para inicializar virtualenvs).
  * `windows`: acá definimos la estructura de *windows* por nombre y qué se ejecuta inicialmente en cada una. De similar forma se pueden gestionar los *tabs* y *panes*, además del *layout* en cada uno.

Esta es un ejemplo de configuración propia sobre un proyecto Django:

{% highlight yml %}
# ~/.tmuxinator/django_project.yml

name: django_project
root: ~/work/django_project/

on_project_first_start: sudo systemctl start mysqld.service && sudo systemctl start postgresql.service

pre_window: workon django_project

startup_window: vim

windows:
  - vim: vim
  - server: ./manage.py runserver --configuration=Dev
  - test:
  - python: ./manage.py shell
  - zsh:
{% endhighlight %}

#### Otras opciones

  * `tmuxinator list` nos lista todos nuestros proyectos creados en tmuxinator.
  * `tmuxinator delete foobar` borra el proyecto foobar.

Pueden ver otras opciones disponibles haciendo `tmuxinator --help`.

#### Extra

Una comodidad extra que nos brinda este *workflow* es que al cambiar de branch sobre un proyecto, si este tiene varios servicios y/o comandos que se tienen que verificar o ejecutar al levantar este proyecto. Podemos simplemente hacer un `kill-session` sobre *tmux* y volver a inicializar el proyecto con *tmuxinator*.


Espero les sea tan útil como me es útil a mí. Lo utilizo para prácticamente todos mis proyectos en desarrollo e incluso para otros casos recurrentes, como una sesión para escribir en este mismo *blog* ;).
