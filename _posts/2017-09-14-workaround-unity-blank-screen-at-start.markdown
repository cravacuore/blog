---
layout: post
title: "[Workaround] Pantalla negra al iniciar aplicación hecha en Unity"
date: 2017-09-14T16:15:58-03:00
comments: true
---

Este problema me aparece con varios juegos hechos sobre [Unity3d](https://unity3d.com/). Básicamente al iniciar en *fullscreen* la pantalla queda totalmente negra, en algunos casos se puede escuchar el audio dando a notar que de todas formas está iniciando.

Como *workaround* sobre este problema se puede hacer lo siguiente:

Primero localizamos la carpeta con las configuraciones de Unity sobre la aplicación que queremos arreglar, deberíamos encontrarla en `~/.config/unity3d/app-que-buscamos`. En esta carpeta deberíamos encontrar un archivo llamado `prefs`. Entonces con el ejemplo anterior, la ruta sería `~/.config/unity3d/app-que-buscamos/prefs`. El contenido de dicho archivo tendría que ser similar a esto:

{% highlight bash %}
  <unity_prefs version_major="1" version_minor="1">
    <pref name="Screenmanager Is Fullscreen mode" type="int">1</pref>
    <pref name="Screenmanager Resolution Height" type="int">1080</pref>
    <pref name="Screenmanager Resolution Width" type="int">1920</pref>
    <pref name="UnityGraphicsQuality" type="int">3</pref>
    <pref name="UnitySelectMonitor" type="int">0</pref>
    <pref name="unity.cloud_userid" type="string"> ... </pref>
    <pref name="unity.player_session_background_time" type="string"> ... </pref>
    <pref name="unity.player_session_elapsed_time" type="string"> ... </pref>
    <pref name="unity.player_sessionid" type="string"> ... </pref>
  </unity_prefs>
{% endhighlight %}

Recomendado hacer un copia del archivo, en mi caso hago la copia en la misma carpeta llamándolo `prefs.bkp`.

Lo que nos interesa modificar (sobre el archivo original) es la línea de `Fullscreen mode`, poniéndole como valor `0`:

{% highlight bash %}
    <pref name="Screenmanager Is Fullscreen mode" type="int">0</pref>
{% endhighlight %}

Una vez modificado y guardado, procedemos a abrir la aplicación.

De forma opcional, podemos modificar los valores de `Resolution Height` y `Resolution Width` para que coincidan con la resolución de nuestro monitor. Por ejemplo si tenemos una pantalla fullHD, los valores serían 1080 y 1920 respectivamente.

Es muy probable que al cerrar e iniciar nuevamente la aplicación, estos valores que modificamos sean sobrescritos automáticamente. Tendríamos que volver a modificar nuevamente siguiendo los mismos pasos o podemos poner el archivo `prefs` en modo de sólo lectura, esto último lo podemos lograr haciendo uso de chattr como les explico en [este otro *post*](http://cravacuore.com.ar/blog/2017/09/12/chattr-archivo-no-editable-read-only.html).
