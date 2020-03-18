---
layout: post
title:  "Default Actions"
date:   2020-03-05 23:09:15 +0000
categories: JavaScript Events
---

Muchos eventos tienen una acción asociada a ellos por defecto. Por ejemplo, si clickeamos en un link, nos llevará a esa página. 

Para la mayoría de eventos, los capturadores de eventos de JavaScript son capturados previamente al estas acciones que tienen lugar por defecto. Así pues, es posible manejar estas acciones que se llevan a cabo por defecto, mediante el uso de un métod que tiene JavaScript, llamado `preventDefault`. Dicho método puede ser utilizado para implementar nuestros propios atajos de teclado por ejemplo, o para evitar acciones que los usuarios esperan que se lleven a cabo por defecto pero que no pueden relizarse.

A continuación se muestra un ejemplo en el cual si pinchamos en el link correspondiente, no nos deja ir a la página que nos redirigiría de forma normal el link.

{% highlight html %}
<p>A paragraph with a <button>button</button>.</p>
<a href="https://developer.mozilla.org/">MDN</a>
<script>
  let link = document.querySelector("a");
  link.addEventListener("click", event => {
    console.log("Nope.");
    event.preventDefault();
  });
</script>
{% endhighlight %}

No obstante, siempre debemos evitar utilizar dicho método salvo que sea extrictamente necesario o por una buena razón ya que será incómodo para los usuarios que vayan a utilizar la página. 

**OJO** Esto creo que solo ocurre en el browser, es decir, dicho método no está disponible para Node.js. 

Nota, dependiendo del navegador, hay algunos comandos que JavaScript no puede manejar con dicho método, como es el `contro-W` o `command-W` de Chrome.