**DOALL locno+**

Esta potente acción permite la implementación de órdenes con "TODO" (COGER TODO, DEJAR TODO, etc.)


1. Se intenta encontrar un objeto en la localida locno. Si no encuentra se cancela el DOALL y se ejecuta [[DONE|DONE_ES]].

2. El número de objeto es convertido en el nombre de la sentencia lógica, y el adjetivo si lo tiene, usando los dato de la tabla de objetos. Si la frase tuviera un segundo nombre (y adjetivo) y justo fueran los encontrados, pasaríamos al punto 1 de nuevo (esto implementa el DEJAR TODO EXCEPTO XXXXX).

3 - El siguiente condacto o entrada es considerado, esto efectivamente convierte una frase "VERBO TODO" en "VERBO OBJETO", que después es procesada por el parser como si el jugador la hubiera tecleado.

4 - Cuando se acaba la tabla actual, si el DOALL está aún activo, entonces volvemos a donde estaba el DOALL, al proceso 1, y buscaríamos el siguiente objeto de la localidad locno.

