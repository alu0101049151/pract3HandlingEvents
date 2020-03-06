---
layout: post
title:  "Event Objects"
date:   2020-03-05 23:09:15 +0000
categories: JavaScript Events
---

A las _handler functions_ se les pasa un argumento: el _event object_. Dicho objeto, almacena información adicional sobre el evento.
Por ejemplo, a continuación podemos ver un código en el cual se detecta un click de raton pero no solo eso, sino que también podemos detectar qué botón del ratón se ha pulsado:

{% highlight html %}
<button>Click me any way you want</button>
<script>
  let button = document.querySelector("button");
  button.addEventListener("mousedown", event => {
    if (event.button == 0) {
      console.log("Left button");
    } else if (event.button == 1) {
      console.log("Middle button");
    } else if (event.button == 2) {
      console.log("Right button");
    }
  });
</script>
{% endhighlight %}
