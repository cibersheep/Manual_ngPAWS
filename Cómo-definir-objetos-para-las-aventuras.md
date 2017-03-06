### Textos de los objetos

Primero empezamos por definir los textos de los objetos. En el apartado "Objects" (Objetos, OTX si no usamos el editor de ngPAWS) ponemos lo siguiente:

```
\0 
unas llaves
\1
un cuchillo
\2
una mesa
\3
una mochila
\4
un sombrero
```

Además, es recomendable que en el apartado "Definitions" (Definiciones, o al principio del fichero .txp si no usamos el editor de ngPAWS) añadamos unas lineas semejante a estas por cada localidad:

```
#define obj oLlaves 0
#define obj oCuchillo  1
#define obj oMesa 2
#define obj oMochila 3
#define obj oSombrero 4
```

Así después cada vez que queramos hacer referencia al objeto chuchillo  (que sería el objeto 1) lo haremos poniendo oCuchillo en lugar de 1 (que es más difícil de recordar).

### Vocabulario

Cada objeto necesita un nombre por el que referirnos a él, para lo cual tenemos que añadirlo como tal en la solapa Vocabulary (Vocabulario, VOC si no usas en editor de ngPAWS). Buscamos la última palabra añadida como "noun" y añadimos detrás una palabra "nombre" para cada objeto:

```
LLAVES 51 noun
CUCHILLO 52 noun
MESA 53 noun
MOCHILA 54 noun
SOMBRERO 55 noun
```

Como veis le ponemos un número diferente a cada uno. Si queremos podemos poner dos palabras del mismo tipo con el mismo número, en cuyo caso serían consideradas sinónimas y daría lo mismo escribir una que otra. Por ejemplo si añadimos esto daría lo mismo que el jugador escribiera "sombrero" que "gorro":

```
GORRO 55 noun
```

También podemos definir adjetivos para los objetos (blanco, amarillo, grande, pesado, etc.), pero en general no deberíais hacerlos salvo que sea necesario para diferenciar dos objetos con igual nombre (por ejemplo la caja amarilla y la caja roja, o la espada pequeña y la espada grande).

```
ROJA 11 adjective
BLANCA 12 adjective
```
De la misma manera, podemos crear sinónimos:

```
COLORADA 11 adjective
```

### Datos de objetos

En el apartado "Object Data" (Datos de objetos, u OBJ si no usamos el editor de ngPAWS) ponemos lo siguiente:

```
\oLLaves   lLago   1 LLAVES   _ ATTR aFemale aPluralName
\oCuchillo 254     1 CUCHILLO _ ATTR
\oMesa     252     1 MESA     _ ATTR aSupporter aFemale
\oMochila  lParque 1 MOCHILA  _ ATTR aContainer aWear aFemale
\oSombrero WORN    1 GORRO    _ ATTR aWear
```

Aquí hay varias cosas:

* el número o etiqueta que identifica al objeto
* la localidad en la que está el objeto cuando empezamos. Podemos poner una localidad concreta o una de las tres localidades comodín (252 o NON_CREATED, el objeto no están en ninguna parte, 253 o WORN, el objeto lo lleva puesto el jugador, y 254 o CARRIED, el objeto lo lleva el jugador)
* el peso del objeto
* la palabra que identifica al objeto (el nombre que hemos puesto en el vocabulario), fijaos como podemos poner el sinónimo GORRO en lugar de SOMBRERO, da igual uno que otro.
* el adjetivo si lo hubiera, si no lo hay se pone un guión bajo
* la palabra ATTR, seguida de los atributos de objeto. Hay muchos atributos de objeto posibles, y en el ejemplo vemos algunos: aWear (es una prenda), aContainer (es un contenedor), aSupporter (es una superfie sobre la que se pueden dejar cosas), a Female (es femenino ) y a PluralName (es plural). Se escapa del objetivo de este mini-tutorial explicarlos, pero si quieres verlos todos los tienes [[aquí:atributos de objeto]]. Por ahora lo más importante es que no te olvides de poner el atributo aFemale a los femeninos y a PluralName a los plurales, o te encontrarás con cosas desagradables como esta al jugar "Coges el mochila" o "Dejas la llaves".

Notas importantes:

* Si un objeto es contenedor (aContainer) o superficie (aSupporter) la localidad de igual número no debe usarse en el juego, porque es en ella donde se dejarán los objetos que se metan o se pongan encima. Por ejemplo en este caso no debería haber una localidad 2 ni 3 (por la mesa y la mochila). Como es obligatorio crear las localidades todas seguidas (no podemos crear la 1 y luego la 4, hay que crear la 2 y la 3 pero la dejamos sin texto de descripción, y la dejamos sin conexiones que permitan llegar a ella).

* Un objeto no puede ser contenedor y superficie a la vez. Si lo fuera no habría diferencia entre poner algo encima o dentro (no se separarían los objetos).



