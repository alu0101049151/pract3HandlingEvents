---
layout: post
title:  "Pointer Events"
date:   2020-03-05 23:09:15 +0000
categories: JavaScript Events
---

Debemos de tener claro que hoy día hay dos maneras de apuntar cosas en una pantalla, estas son, o bien con un ratón (lo cual incluye atones normales, trackpads, etc) y las pantallas táctiles. Cada una de estas dos maneras de apuntar, generan un evento diferente. 

## Clicks de Ratón

Cuando pulsamos un botón del ratón, se producen una serie de eventos `mousedown` y `mouseup` que funcionan de manera simlar a los `keydown` y `keyup` de las teclas de teclado.

Cada vez que pulsamos el botón, después del evento `mouseup` se lanza el evento `click` al nodo más específico que contenga tanto la pulsación como la liberación del botón. 

Por ejemplo, si presiono el boón del ratón sobre un párrafo específico y luego muevo el puntero a otro párrafo y suelto el botón, el evento `click` ocurrirá en el elemento que contiene ambos párrafos.

Por otra parte, para cuando hacemos doble click para seleccionar algo, existe el evento `dbclick` que se lanza cada vez que hacemos dos clicks de ratón rápidos. 

Para ser más precisos en la información sobre el lugar donde un evento de ratón ha ocurrido, podemos mirar las propiedades `clientX` y `clientY` que contienen las coordenadas del evento en pixels. Se contabilizan dichas coordenadas desde la esquina superior izquierda de la ventana o `pageX` y `pageY` que son relativas a la esquina superior izquierda de todo el documento (que puede ser diferente cuando la ventana se ha desplazado haciendo scroll).

El programa que se muestra a continuación es un programa de dibujo primitivo (primitive drawing). Cada vez que se hace click en el documento, se añade un punto debajo del puntero del ratón:

{% highlight html %}
<style>
  body {
    height: 200px;
    background: beige;
  }
  .dot {
    height: 8px; width: 8px;
    border-radius: 4px; /* rounds corners */
    background: blue;
    position: absolute;
  }
</style>
<script>
  window.addEventListener("click", event => {
    let dot = document.createElement("div");
    dot.className = "dot";
    dot.style.left = (event.pageX - 4) + "px";
    dot.style.top = (event.pageY - 4) + "px";
    document.body.appendChild(dot);
  });
</script>
{% endhighlight %}