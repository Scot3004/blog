---
title: Uso de jquery con ajax
author: Sergio C. Orozco Torres
tags:
- tutorial
- jquery
- html
blogger_id: tag:blogger.com,1999:blog-3290987933179858425.post-2111565777799621636
blogger_orig_url: http://scot3004.blogspot.com/2011/07/uso-de-jquery-con-ajax.html
category: dev
---

~~Recientemente ando~~ experimentando con ajax, usando como framework jquery, implementando elementos css3 y entre todo ese sancocho he encontrado lo siguiente:<br />
<!-- more -->
claro no aspiren que sea eficiente
Para cargar una pagina y un script

{% codeblock lang:javascript %}
function contenido(pagina){
  $('#content').load(pagina+".html");
  //cargar una pagina dada en un div cuyo id sea content
  $.getScript(pagina+".js"); //cargar un script
}
{% endcodeblock %}

Para cargar un date query en el main
{% codeblock lang:javascript %}
$(document).ready(function(){
  $( "#datepicker" ).datepicker();
});
{% endcodeblock %}
usado en el documento externo
cargar un formulario enviarlo por post y que lo procese un php, forma ideal
{% codeblock lang:javascript %}
$("#formulario").submit( function () {
  $.ajax({
    type: 'POST',
    url: $(this).attr('action')
    data: $(this).serialize(),
    // Mostramos un mensaje con la respuesta de PHP
    success: function(data) {
      alert(data);
    }
  });
  return false;
});
{% endcodeblock %}

forma exageradamente burda y funcional
{% codeblock lang:javascript %}
 <form action="recibidos.php" autocomplete="on" id="formulario"
    method="POST" name="formulario" onsubmit="
    $.ajax({
      type: "POST",
      url: "recibidos.php",
      data: $(this).serialize(),
      // Mostramos un mensaje con la respuesta de PHP
      success: function(data) {
        alert(data);
      }
    });
    return false;"
    </form>
{% endcodeblock %}
