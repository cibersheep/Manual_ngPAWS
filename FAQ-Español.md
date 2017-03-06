
### ¿Cómo defino localidades?
Ver el artículo [[Cómo definir localidades e interconectarlas]].

### ¿Cómo defino objetos?
Ver el artículo [[Cómo definir objetos para las aventuras]].

### ¿Cómo controlo los gráficos de las localidades?

Ver los artículos [[Cómo poner un  gráfico en una localidad]]  y [[Cómo cambiar el gráfico de una localidad]].

### ¿Cómo hago sonar un efecto de sonido o música?
Ver el artículo [[Cómo hacer sonar un efecto o música]].

### ¿Cómo cambio el tipo de letra de la aventura?

Ver los artículos [[Cómo cambiar el tipo de letra de la aventura]] y [[Cómo cambiar el tipo de letra en parte del texto]]

### Mi juego muestra líneas en blanco detrás de un mensaje/texto de localidad/descripción de objeto.

Asgurate de que la definición del siguiente objeto, localidad o mensaje está justo detrás de la del objeto afectado, sin espacio:

Mal:
```
\7
Texto primera localidad



\8
Texto segunda localidad
```

Bien:
```
\7
Texto primera localidad
\8
Texto segunda localidad
```

La razón es que ngPAWS permite que los mensajes, localidad y objetos sean multilínea, así que si añades retornos de carro tras un mensaje ngPAWS los considera parte del mismo y los muestra cada vez.

### ¿Cómo hago para que si el jugador escribe tal, el parser responda cual?

Ver el artículo [[Cómo añadir una respuesta a una acción del jugador]].

### ¿Cómo hago para que el jugador pueda hablar con los personajes del juego?

Ver el artículo:  [[Como hablar con un NPC]].

### Tengo un objeto del que debe haber varias unidades, como monedas o balas. ¿Cómo lo manejo?

Ver el artículo [[Objetos contables]].

### Cuantas localidades, objetos, mensajes, etc.... son soportados por ngPAWS?

Por razones de compatibilidad ngPAWS tiene lo que PAWS en la mayoría de los casos, sin embargo es bastante fácil cambiar estos limites por defecto, si lo necesitas pregunta. Los valores "de fábrica" son:

* Localidades: 252 (252,253, 254 and 255 cannot be used as locations) 
* Mensajes: 2^32
* Mensajes del sistema: 2^32
* Mensajes creados por  [WRITE](WRITE) o [WRITELN](WRITELN) : 2^32
* Palabras de vocabulario: 255 por cada tipo de palabra (nombres, verboss, preposiciones, etc.)
* Objetos: 255

### Puede convertise un juego de PAWS a ngPAWS?

Ver: [Conversión de PAWS a ngPAWS](Conversión de PAWS a ngPAWS)

### Puede convertise un juego de Superglús a ngPAWS?

Ver: [Conversión de Superglús a ngPAWS](Conversión de Superglús a ngPAWS)

### Vas a crear un GUI para linux?

Puede.


