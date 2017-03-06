Para crear nuestro propio mundo tendremos que detallar ciertos datos acerca del mismo:

* Las localidades que lo conforman: una localidad puede ser una habitacion, una zona de un campo, la orilla de un río o la cima de una montaña. En realidad no hay límite en el tamaño de una localidad, tu decides qué consideras una localidad.

* Cómo están conectadas esas localidades. Tradicionalmente en aventuras de texto se usan los puntos cardinales (norte, sur, este, oeste) y alguna otra dirección (arriba, abajo, dentro, fuera) para conectar unas localidades con otras. Si quieres puedes usar otros métodos para tu aventura, pero en definitiva la localidad A estará conectada con la localidad B usando tal orden (ya sea "norte", "abajo" o  "derecha").

* Qué objetos podrá usar el jugador, y qué características tendrán dichos objetos. Las características pueden ser su peso, en que localidad están cuando empezamos a jugar, y otros [atributos de objeto](atributos de objeto) como si producen luz (una linterna), son prendas (un sombrero), contenedores (un baúl), superficies (una mesa) o incluso contenedores/prenda (una mochila).

* Qué personajes poblarán el mundo (NPC, non player character, personaje no jugador), si es que hay alguno. ngPAWS considera los NPCs objetos, en realidad un NPC es un objeto cualquiera con el atributo "aNPC" activo, de la misma manera que la linterna da luz porque se le pone el atributo "aLight". Sin embargo los objetos marcados como NPC son tratados de manera diferente por el sistema, por ejemplo si tratas de tomarlos, el sistema por defecto en lugar de hacerlo, responderá con un "No creo que les gustes". 

* Qué palabras entenderá ngPAWS: aunque ngPAWS contiene una lista de las palabras más usadas, especialmente verbos, es posible que necesites añadir palabras para tu propio mundo (por ejemplo la palabra computadora no está en el vocabulario que tiene ngPAWS, pero si hay una computadora en tu juego tendrás que añadir dicha palabra para que sea entendida). Igualmente, hay verbos que no están incluidos, por ejemplo el verbo "resucitar", pero si tu personaje tiene la capacidad de resucitar personas o animales, tendrás que añadirlo. 

* Respuestas: finalmente, tendrñas que añadir respuestas para las órdenes que el jugador teclee. COmo en muchos casos las respuestas dependerán de la situacion actual, hay una serie de comandos que llamamos [condactos](condactos) (condiciones y actos) que te permitirán que la respuesta a "LANZAR CUCHILLO" no se a la misma si llevas el cuchillo o no lo llevas, o si hay un ogro presente o solo amigos.

[It al siguiente capítulo: la base de datos de inicio](la base de datos de inicio)