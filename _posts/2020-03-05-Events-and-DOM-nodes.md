---
layout: post
title:  "Events and DOM Nodes"
date:   2020-03-05 23:09:15 +0000
categories: JavaScript Events
---

Los métodos controladores de eventos, también se pueden encontrar en elementos del DOM y algunos otros tipos de objetos. Los capturadores de eventos, sólo se llaman cuando el evento en cuestión, ocurre en el contexto del objeto en el que está registrado.

{% highlight html %}
<button>Click me</button>
<p>No handler here.</p>
<script>
  let button = document.querySelector("button");
  button.addEventListener("click", () => {
    console.log("Button clicked.");
  });
</script>
{% endhighlight %}

En este ejemplo, cuando se pulsa el botón con el ratón, se muestra por pantalla el handler. 

A la hora de capturar eventos con un handler, es mejor utilizar el método `addEventListener` para añadir un capturador y el método `removeEventListener` que nos permite eliminar el métodoa que le pasemos por argumentos. 

Un ejemplo del uso de estos métodos se ve en el siguiente código:

{% highlight html %}
<button>Act-once button</button>
<script>
  let button = document.querySelector("button");
  function once() {
    console.log("Done.");
    button.removeEventListener("click", once);
  }
button.addEventListener("click", once);
</script>
{% endhighlight %}
