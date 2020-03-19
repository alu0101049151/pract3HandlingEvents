---
layout: post
title:  "Key Events"
date:   2020-03-05 23:09:15 +0000
categories: JavaScript Events
---

Existe un tipo de evento denominado **"keydown"** que sucede cuando presionamos una tecla del teclado y un evento **"keyup"** el cual sucede cuando una tecla no está pulsada. 

A continuación se muestra un ejemplo en el cual, durante la letra "v" del teclado es pulsada, se pone el fondo de la pantalla de color violeta, y cuando no, no:

{% highlight html %}
<p>This page turns violet when you hold the V key.</p>
<script>
  window.addEventListener("keydown", event => {
    if (event.key == "v") {
      document.body.style.background = "violet";
    }
  });
  window.addEventListener("keyup", event => {
    if (event.key == "v") {
      document.body.style.background = "";
    }
  });
</script>
{% endhighlight %}

Hay que tener cuidado, porque el evento "keydown" se da todo el tiempo que tengamos la tecla pulsada, así pues, si por ejemplo en vez de ser el fondo, fuera un botón el que apareciese cuando pulsamos una letra determinada, podrían generarse muchísimos botones distintos.

Cuando se pulsa una tecla, el ejemplo mira la propiedad "key" del evento y comprueba qué valor tiene. Normalmente suele valer lo que pone en la tecla, es decir, en este caso al ser la letra 'v' su valor es "v". Este valor cambia para eclas especiales como enter, shift, etc. En el caso de "Enter por ejemplo, su valor es "Enter".

También podemos hacer combinaciones de algunas teclas especiales como `shiftKey`, `ctrlKey` y `altKey` (entre otras) con teclas normales.
En el siguiente ejemplo, se muestra como si pulsamos `ctrl + space` se muestra por pantalla un mensaje:

{% highlight html %}
<p>Press Control-Space to continue.</p>
<script>
  window.addEventListener("keydown", event => {
    if (event.key == " " && event.ctrlKey) {
      console.log("Continuing!");
    }
  });
</script>
{% endhighlight %}

El nodo del DOM en el que se genera el evento de teclado, depende del elemento que tiene la "atención" en el momento en el cual es presionada la tecla y ocurre el evento. Sin embargo, cuando nada en particular tiene el foco de atención, el `document.body` tiene el foco de atención.