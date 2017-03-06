A veces en una aventura no vamos a tener un objeto concreto, sino varios de un mismo tipo. Un ejemplo podrían ser monedas de oro, o balas de nuestra munición. En estos casos no tendremos una bala o una moneda, sino n balas o n monedas.

Lo primero que tenemos que hacer es utilizar un [[flag|los flags]], para lo cual vamos a usar uno que no hayamos usado antes y poner en el apartado de definiciones (DEF), si usamos el flag 150:

`#define flg fContadorMonedas 150`

Ahora, en la descripción del objeto monedas, que tenemos en el apartado de textos de objeto (OTX) en lugar de poner "unas monedas" ponemos lo siguiente: 

`{FLAG|150} moneda(s) de oro`

y añadimos la palabra moneda y monedas al vocabulario, y colocamos el objeto monedas en el apartado de datos de objeto (OBJ) en el inventario el jugador (CARRIED).

Si jugamos ahora veréis que si hacemos inventario saldrá el texto "0 moneda(s)". Como no queremos que el jugador empieze tan pobre, en el proceso 1, pondremos lo siguiente:

````
AT 0
 LET fContadorMonedas 1000
```

Y así cuando el jugador pase por la localidad 0 (al empezar el juego), le asignaremos 1000 monedas. Ahora al hacer inventario veremos "1000 monedas(s)".

**_¿Y si el jugador se gasta monedas_**

Si por ejemplo el jugador compra una espada de 500 monedas, ponemos en la tabla de respuesta:

````
COMPRAR ESPADA
 AT lArmeria
 ISAT oEspada 252 ; O sea, no se ha creado aún
 GE fContadorMonedas 500 ; Tenemos al menos 500 monedas
 PLACE oEspada 254 ; La ponemos en el inventario
 MINUS fContadorMonedas 500 ; y decrementamos el flag en 500
 WRITELN "Compras la espada a cambio de 500 monedas."
 DONE
```

**_¿Y si el jugador consigue monedas_**

Pongamos el ejemplo de que matamos a un troll y nos quedamos con sus monedas:

```
MATAR TROLL
 PRESENT oTroll ; Está aquí el troll
 CARRIED oEspada ; LLevamos la espada
 PLUS fContadorMonedas 200 ; Aumentamos las monedas en 200
 WRITELN "Matas al troll con tu espada. Tras examinar el cuerpo encuentras 200 monedas de oro."
 DONE
```

Como veis, la idea es ir incrementando o decrementando (con [[PLUS|PLUS_ES]] o con [[MINUS|MINUS_ES]]) según convenga.

 



