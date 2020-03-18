---
layout: post
title:  "Propagation"
date:   2020-03-05 23:09:15 +0000
categories: JavaScript Events
---

Si estamos trabajando con un evento de un nodo (del DOM) que tiene a su vez un hijo al cual le llegan eventos también, estos eventos que llegan al nodo hijo, se propagan al nodo padre. Por ejemplo, si tenemos un párrafo con un handler y dicho párrafo a su vez, contiene en su interior un botón; si pulsamos el botón, dicho evento será recibido también por el handler del párrafo.

Sin embargo, si ambos nodos (padre e hijo) tienen su propio handler cada uno, el más específico (en este caso el del ratón) va en primer lugar. 

Por otra parte, en cualquier momento, es posible que un capturador de evento llame al método `stopPropagation` en el _event object_ para prevenir a los _handlers_ de los eventos externos y que no lo capturen. Esto es muy útil si por ejemplo, queremos que si tenenmos un botón dentro de otro elemento clickable y no queremos que los clicks del botón activen el comportamiento del evento externo al botón.

A continuación se muestra un ejemplo en el cual, cuando se pulsa el botón con el click izquierdo del ratón, se propaga el evento al capturador del párrafo, sin embargo, si se pulsa el botón con el click derecho del ratón, no se propaga el evento hacria "arriba":

{% highlight html %}
<p>A paragraph with a <button>button</button>.</p>
<script>
  let para = document.querySelector("p");
  let button = document.querySelector("button");
  para.addEventListener("mousedown", () => {
    console.log("Handler for paragraph.");
  });
  button.addEventListener("mousedown", event => {
    console.log("Handler for button.");
    if (event.button == 2) event.stopPropagation();
  });
</script>
{% endhighlight %}

Así mismo, los _event objects_ poseen una propiedad llamada *target* que se refiere al nodo en el que fue originado el evento. Así pues, se puede utilizar dicha propiedad para asegurarnos de que no capturamos accidentalmente algún evento que no queremos capturar que se ha propagado desde "abajo" hacia el nodo.
Así mismo, es posible también usar la propiedad *target* para lanzar una amplia "red" que capture una serie de eventos específicos.
Por ejemplo, si tienemos un nodo que contiene una lista de botones, puede que sea más conveniente registrar un capturardor para un único click en el nodo más externo y usar su propiedad *target* para comprobar cuando otro nodo ha sido pulsado, que registrar cada uno de los capturadores de cada botón individualmente:

{% highlight html %}
<button>A</button>
<button>B</button>
<button>C</button>
<script>
  document.body.addEventListener("click", event => {
    if (event.target.nodeName == "BUTTON") {
      console.log("Clicked", event.target.textContent);
    }
  });
</script>
{% endhighlight %}