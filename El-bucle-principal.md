Así es como funciona ngPAWS. Abajo hay un diagrama que permite verlo más visualmente.

1. Se describe la localidad
2. Se ejecuta el proceso 1
3. Se piden órdenes del jugador hasta que se recibe alguna
4. Se forma una sentencia lógica (SL) analizando la frase y desgranando verbo, nombres, adverbios, adjetivos, etc. y se recorre la tabla de respuestas. 
5. Si se encuentran entradas acordes se ejecutan hasta que se encuentra un DONE. Después se ejecuta el proceso 2 y se vuelve al punto 3. Si en lugar de DONE se encuentra un DESC es igual, solo que se vuelve al punto 1 (DESC obliga a redescribir la localidad)
6. Si no se encuentra ninguna entrada en la tabla , o ninguna acaba en un DONE, se comprueba la tabla de conexiones, a ver si lo que pusimos es una orden para movernos de sitio. Si hay éxito al mirar la tabla, se mueve al jugador y se vuelve al punto 1.
7. Si tampoco hay éxito en la tabla de conexiones, se muestra el mensaje "No puedes hacer eso", se ejecuta el proceso 2,  y se vuelve al punto 3.

![ngPAWS main loop](http://www.ngpaws.com/wikires/ngpawsloop_es.png?1)

[[Ir al siguiente capítulo: los flags|los flags]]