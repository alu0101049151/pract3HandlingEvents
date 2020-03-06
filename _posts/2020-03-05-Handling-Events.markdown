---
layout: post
title:  "Events Handlers"
date:   2020-03-05 23:09:15 +0000
categories: JavaScript Events
---

Tal y como sabemos, muchos programas funcionan mediante entradas que suministra el usuario al  con el uso del teclado o el ratón, así pues, para poder trabajar con ellos, es necesario "Capturar" dichas entradas que calificaremos como "eventos". Por lot tanto, un evento será por ejemplo, aquello que sucede cuando el usuario pulsa con el ratón sobre algún botón del programa, o escribe algo por teclado.

Para trabajar con dichos eventos, JavaScript posee unos mecanismos conocidos como "handlers" (manejadores) que se utilizarán para manejar estos eventos mencionados previamente. 

A continuación se muestra un ejemplo en el cual se muestra por pantalla el texto: "You knocked?" cuando el usuario hace click en alguna parte de la pantalla:

{% highlight html %}
<p>Click this document to activate the handler.</p>
<script>
  window.addEventListener("click", () => {
    console.log("You knocked?");
  });
</script>
{% endhighlight %}