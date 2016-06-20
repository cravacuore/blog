---
layout: post
title: "[Django] Upload Multiple FileField"
date: 2016-06-20T09:43:30-03:00
comments: true
---

Por defecto un **FileField** de los *forms* de Django sólo te deja subir de a un archivo. Si lo que se necesita en tu proyecto es subir varios archivos desde un mismo campo del formulario, ya sea de forma *drag&drop* o seleccionando varios en el *browser* de archivos manteniendo apretada la tecla *Ctrl*. Se puede lograr sin *plugins* de la siguiente manera.

### Cambiando forms

En nuestro *form*, debemos especificar el campo como un *FileField* de la siguiente forma.

`dasa/forms.py`

{% highlight python %}
class DasaForm(forms.Form):
  lala_field = forms.FileField(widget=forms.ClearableFileInput(attrs={'multiple': True}))
{% endhighlight %}

### Cambiando views

Y por el lado de nuestro *views*, en el método que se esté utilizando obtenemos la lista de archivos, e iteramos con lo que queramos hacer.

`dasa/views.py`

{% highlight python %}
    files = request.FILES.getlist('lala_field')
    if form.is_valid():
    for file in files:
        ... # Do something
{% endhighlight %}

[Fuente](https://docs.djangoproject.com/en/1.9/topics/http/file-uploads/#uploading-multiple-files)
