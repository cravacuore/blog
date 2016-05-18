---
layout: post
title: "[Django] MultipleSelectField y su filtrado"
date: 2016-05-13T17:51:59-03:00
comments: true
---

En una aplicación [Django](https://www.djangoproject.com/) sobre la que estoy trabajando me surgió la necesidad de tener un campo al que le pueda asignar más de una opción dentro de mis *choices* (que no es más que una lista de tuplas representando valores, como por ejemplo estados). En este caso quería evitar tener que crear una clase para representar esto, ya que ya se utilizaban las *choices* y no quería tener que guardar estos valores en la base de datos.

Dando vueltas me encontré con [django-multiselectfield](https://github.com/goinnn/django-multiselectfield) y fue justo lo que necesitaba. Este lo que nos termina guardando es una lista de *strings* con los valores seleccionados.

## Instalando

Para poder usarlo es bastante simple, lo agregamos en nuestro *requirements* y hacemos un:

> pip install

Después lo agregamos a nuestro listado de *"INSTALLED_APPS"* en el *settings* de la aplicación:

`app/settings.py`

{% highlight python %}
 INSTALLED_APPS = (
   ...
   'multiselectfield',
   ...
 )
{% endhighlight %}

## Cambiando models

Y tan sólo nos queda usarlo en nuestro campo del modelo, suponiendo los siguientes estados como *choices*:

`dasa/models.py`

{% highlight python %}
ESTADO_FOO = (0, 'Foo')
ESTADO_BAR = (1, 'Bar')
ESTADO_ASD = (2, 'Asd')

ESTADOS = [
  ESTADO_FOO,
  ESTADO_BAR,
  ESTADO_ASD,
]
{% endhighlight %}

En nuestro modelo el campo era de la siguiente forma:

{% highlight python %}
estado = models.PositiveIntegerField(max_length=1, choices=ESTADOS)
{% endhighlight %}

Y ahora, importamos el multiselectfield y nos queda:

{% highlight python %}
from multiselectfield import MultiSelectField

estado = MultiSelectField(choices=ESTADOS)
{% endhighlight %}

## Cambiando forms

Ahora hay que ajustar los formularios que se usen, para que se pueda seleccionar más de una opción.

`dasa/forms.py`

Antes era simplemente un campo para seleccionar una opción:

{% highlight python %}
estado = forms.ChoiceField(required=False, choices=ESTADOS)
{% endhighlight %}

Ahora tengo que poder seleccionar más de uno:

{% highlight python %}
estado = forms.MultipleChoiceField(required=False, choices=ESTADOS)
{% endhighlight %}

Y por comodidad se quería utilizar *checkboxes* en vez de un *select*, así que hice uso de un *widget* que me provee Django entre sus *forms*:

{% highlight python %}
estado = forms.MultipleChoiceField(widget=forms.CheckboxSelectMultiple, required=False, choices=ESTADOS)
{% endhighlight %}

## Lograr filtrado para este campo

Lo que costó un poco más fue delucidar como lograr el filtrado para la búsqueda sobre este campo, teniendo en cuenta que quería filtrar eligiendo los "estados" que por lo menos debían tener el listado de resultantes, pero sin excluir aquellos que tenían los elegidos y más. Lo cual lo resolví de la siguiente manera.

En nuestro `dasa/views.py` que es donde realizo mi filtrado, obtengo los campos seleccionados de mi formulario:

{% highlight python %}
estados = custom_form.cleaned_data['estados']
{% endhighlight %}

Y luego, haciendo un método para filtrar los estados creando un *query* "a mano" importando y utilizando **Q**:

{% highlight python %}
from django.db.models import Q

def filtrar_estados(pre_query, estados):
  if estados:
    for estado in estados:
      pre_query = pre_query.filter(Q(estado__icontains = estado))

  return pre_query
{% endhighlight %}

El *for* sobre los estados lo hago para obtener todas mis opciones seleccionadas, y realizar un filtrado por cada uno de estos.

Y con esto logré el propósito deseado.
