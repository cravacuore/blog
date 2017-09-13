---
layout: post
title: "[Javascript] Toggle Icon Class - cambiar ícono con click sobre botón"
date: 2017-09-13T01:31:09-03:00
comments: true
---

Buscando una manera simple de cambiar un ícono por otro al hacer click sobre un botón, haciendo uso Javascript solamente (sin JQuery). Encontré sobre [classList](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList#Methods), en particular `classList.toggle` que justamente nos permite agregar o quitar una propiedad de un elemento.

En este caso estaba jugando para cambiar un ícono de [FontAwesome](http://fontawesome.io/) de *Play/Pause* en esta [sección](http://cravacuore.com.ar/music) de mi página.

Entonces simplemente encontrando mi elemento y usando *toggle* pude quitar la clase de "play" y agregar la clase de "pause".

{% highlight javascript %}
  var icon = document.getElementById('icon');
  icon.classList.toggle('fa-pause');
  icon.classList.toggle('fa-play');
{% endhighlight %}

Como quiero que esto ocurra cuando hago click, lo agrego como evento de *click* al botón.

{% highlight javascript %}
document.getElementById('play-button').addEventListener('click', function(){
  var icon = document.getElementById('icon');
  icon.classList.toggle('fa-pause');
  icon.classList.toggle('fa-play');
})
{% endhighlight %}

Pueden ver los cambios completos hechos en este [*commit*](https://github.com/cravacuore/cravacuore.github.io/commit/fb05c94ccab030ac6cd0de6d6bd825e9df1f5062).
