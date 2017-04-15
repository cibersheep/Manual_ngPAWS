## La base de datos de la aventura

Para crear el mundo de nuestra aventura tendremos que detallar ciertos datos acerca del mismo:

* Las localidades que lo conforman: una localidad puede ser una habitación, una zona de un campo, la orilla de un río o la cima de una montaña. En realidad no hay límite en su tamaño: tú decides qué se considera **una localidad.**

* Cómo están conectadas esas localidades. Tradicionalmente en las aventuras de texto se usan los puntos cardinales \(norte, sur, este, oeste\) y alguna otra dirección \(arriba, abajo, dentro, fuera\) para conectar unas localidades con otras. Si quieres, puedes usar otros métodos pero en definitiva: la **Localidad A** estará conectada con la **Localidad B** usando una orden \(ya sea «norte», «abajo» o «derecha»\).

* Qué objetos podrá usar el jugador y qué características tendrán dichos objetos. Ejemplos de características pueden ser: su peso, en qué localidad se halla cuando empezamos a jugar, etcétera.

  Mira los demás [atributos de objeto](atributos de objeto%29 como si producen luz %28una linterna%29, son prendas %28un sombrero%29, contenedores %28un baúl%29, superficies %28una mesa%29 o incluso contenedores/prenda %28una mochila) que hay disponibles.

* Qué personajes no jugadores \(en inglés: NPC o _non player character_\) poblarán el mundo, si es que hay alguno. En **ngPAWS** se considera a los NPCs como un objeto con el atributo **aNPC** activo, de la misma manera que la linterna da luz porque se le pone el atributo **aLight.** Sin embargo, los objetos marcados como NPC son tratados de manera diferente por el sistema, por ejemplo, si tratas de tomarlos, por defecto el sistema en lugar de permitirte esta acción, responderá con un «No creo que le gustes».

* Qué palabras entenderá **ngPAWS.** Aunque **ngPAWS** contiene una lista de las palabras más usadas, especialmente verbos, es posible que necesites añadir palabras para tu propio mundo \(por ejemplo, la palabra «computadora» no está en el vocabulario que tiene **ngPAWS** por defecto pero si hay una computadora en tu juego tendrás que añadir dicha palabra para que sea reconocida\). Lo mismo sucede con los verbos. Los hay que no están incluidos, como por ejemplo «resucitar» pero si tu personaje tiene la capacidad de resucitar personas o animales, tendrás que añadirlo a la lista.

* Respuestas. Finalmente, tendrás que añadir respuestas para las órdenes que el jugador teclee. Como en muchos casos las respuestas dependerán de la situacion actual en la partida. Hay una serie de comandos que llamamos [_condactos_](condactos%29 %28condiciones y actos) que te permitirán que la respuesta a «LANZAR CUCHILLO» no sea la misma dependiendo de si llevas un cuchillo o no, si hay un ogro presente o solo los amigos del personaje.

Todos estos aspectos se definen en el archivo `code.txp` siguiendo las reglas que verás en esta documentación.

