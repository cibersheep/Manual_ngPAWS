## Generador automático de puzles - Parte II

En este segundo artículo pasaremos a explicar como realizar un puzle en el que hay una trampilla que se abre. Hay ciertas diferencias con el puzle anterior que conviene remarcar:

* Al abrir una trampilla damos acceso a una nueva localidad
* Es necesario mantener el control de si la trampilla esta cerrada o no

### El puzle de la trampilla

Como en el caso anterior, lo primero que necesitamos es decidir como va a funcionar el puzle, y esta es la definición: “Para abrir la trampilla el jugador necesitará la llave, por lo cual la orden adecuada para abrirla es [ABRIR TRAMPILLA]“. Además, hay determinadas cosas que están implícitas que conviene detallar:

* Debemos llevar la llave
* Debemos estar en la misma localidad que la trampilla
* La trampilla debe estar cerrada para poder abrirla
* No vamos a pedir al jugador que escriba “ABRIR TRAMPILLA CON LLAVE”. Podríamos hacerlo, pero en este puzle no lo haremos, primero para facilitar la jugabilidad, y segundo porque ya explicamos en el capítulo I cómo realizar comprobación de palabras adicionales.

Vamos a dar por supuesto que las palabras necesarias ya existen en el vocabulario (abrir, trampilla) , y que estamos usando identificadores de txtpaws, por lo que podremos referirnos a la llave por “oLlave” y a la localidad de la trampilla como “lTrampilla”. Por último, la localidad a la que podemos acceder por la trampilla (que esta en el techo), la llamaremos 'lAtico'.

Además, vamos a necesitar un método de comprobar que la trampilla se encuentra cerrada. Para ello en ngPAWS hay dos maneras:

* Comprobar que la salida correspondiente no existe utilizando el condacto GETEXIT
* Mantener el estado de la trampilla en un flag o bandera

Nosotros vamos a usar la segunda opción, y para ello usaremos el flag 100, que bautizaremos como “fTrampillaAbierta” con txtpaws, y tendrá los siguientes valores:

* Valor 0: La trampilla está cerrada
* Valor 1: La trampilla está abierta

Comencemos...

### Condiciones  de vocabulario y localidad

Veamos como rellenamos esta primera pantalla: hemos quedado que el puzle requiere que escribamos “ABRIR TRAMPILLA”, por lo cual vamos a rellenar el campo “Verbo” con “ABRIR”, el campo “Nombre” con “TRAMPILLA”.

Además, dijimos como condición que para poder abrir la trampillas es que debemos estar en ella localidad de la trampilla, así que añadimos la condición de localidad: marcamos “Puzle ligado a localidad” y ponemos “lTrampilla” en el campo “Localidad”. También ponemos “No veo ninguna trampilla.” en el campo “Texto si no se cumple” (que corresponde al texto a mostrar si no estamos en la localidad).

![Condiciones de vocabulario y localidad](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_2.1.png)

### Otras condiciones

Hemos quedado en que es necesario tener la llave para poder realizar el puzle, con lo cual vamos a añadir una condición "El jugador lleva el objeto ..." con el objeto "oMoneda" y con texto de fallo "Está cerrada con llave", que añadimos a la lista de la derecha pulsando en "Añadir".

Por último, vamos a comprobar que la trampilla está cerrada, y para ello vamos a comprobar que el flag oTrampillaAbierta tiene como valor cero.

Para ello seleccionamos en el desplegable "El valor del flag <...> es <...>" y añadimos "Ya está abierta" en el texto de fallo, "fTrampillaAbierta" en el campo del flag, y 0 en el campo "valor". Le damos a "Añadir" para incluir la condición en la lista.

![Otras condiciones](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_2.2.png)

### Acciones

Pues bien, ya tenemos todas nuestras condiciones, vamos a pasar a las acciones. Cuando abrimos la trampilla deben pasar dos cosas, siendo la primera bastante obvia y la segunda no tanto:


* La trampilla debe abrirse, por lo que la salida desde lTrampilla a lAtico debe aparecer.
* La trampilla debe ser marcada como “abierta”, por lo que el valor del flag fTrampillaAbierta debe pasar a valer 1. Esto evitará que podamos abrir la trampilla cuando ya lo está.

Vamos a añadir por tanto dos acciones, una seleccionado "El valor del flag <...> es puesto a <...>", e indicando "fTrampillaAbierta" como flag, y 1 como valor (y dar a añadir), y otra seleccionando "Crea o modifica la conexión en la dirección <...>" añadiendo "ARRIBA" como dirección y "lAtico" como Localidad (y pulsar añadir).

Añadimos finalmente el texto "Usas la llave para abrir la tampilla, dejando abierta la entrada al ático" al campo 

![Otras condiciones](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_2.3.png)

Hecho esto pasamos a opción final y damos a finalizar.

