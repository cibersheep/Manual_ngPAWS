# La base de datos de inicio

Para que el autor de una nueva aventura no tenga que crearla desde cero, se ha creado lo que llamamos \_la base de datos de inicio, \_que no es más que una aventura básica para poder ser usada como esquema. Esta aventura ya contiene un objeto y una localidad de ejemplo, bastante vocabulario y respuestas predeterminadas para las acciones más comunes que pueda teclear el jugador  \(tomar, dejar, poner, atacar, hablar, saltar, etc.\).

Se usará esta base de datos cada vez que se cree una aventura nueva con el editor gráfico. De forma alternativa, se puede hacer una copia de la carpeta descargada para cada aventura.

![](/assets/Nueva aventura.png)

Si se abre el fichero con extensión **txp** desde el editor gráfico, se creará una solapa para cada sección. En el caso de usar un editor de texto cualquiera, veremos cada una de estas secciones es precedida por el símbolo «/».

Para que esta guía sirva para todos el mundo, encontraréis el nombre de cada sección del editor gráfico y entre paréntesis lo que se muestra en el fichero de texto.

### La sección de definiciones \(-\)

En el editor de textos se encuentra al principio, antes de la sección **/CTL**.

En esta sección se escriben las definiciones de [txtpaws](txtpaws_es). Quizá es un poco prematuro explicar esto aquí, así que te recomiendo que leas el apartado de txtpaws cuando hayas avanzado algo más en la lectura.

![](/assets/Definiciones.png)

### Las sección de control \(/CTL\)

Esta sección se mantiene por compatibilidad con otros sistemas como _PAW PC_ o _Superglús_ pero no tiene uso alguno en **ngPAWS** por lo que en el editor gráfico ni se ve. En el editor de texto, esta sección ha de estar vacía.

### La sección de vocabulario \(/VOC\)

En esta sección se incluyen las palabras que entiende el intérprete \(o _parser_ en inglés\). Se trata de una lista de palabras, seguida cada una de un número y un tipo. Los **números pueden ir de 0 a 254** y los **tipos pueden ser **_**verb**_** \(verbo\), **_**noun**_** \(sustantivo\), **_**adjecti**_**ive \(adjetivo\), **_**adverb**_** \(adverbio\), **_**preposition**_** \(preposición\) y **_**conjunction**_** \(conjunción\).**

Para que dos palabras sean sinónimas y por tanto, se puedan usar indistintamente, se les asigna a ambas el mismo tipo y número \(por ejemplo "puñal" y "navaja" serán el _sustantivo_ 178\).

```
PUÑAL   178 noun
NAVAJA  178 noun
```

Algunas notas sobre el vocabulario:

* Las palabras con el mismo número pero distinto tipo **no son consideradas sinónimos.**
* Los sustantivos con número **por debajo del 20 son considerados «convertibles»** que quiere decir que, si no hay verbo en la frase, se _convertirán_ en el verbo. De esa manera «norte» e «ir norte» se comportarán igual.
* Los verbos cuyo número sea **inferior a 14 son considerados verbos de dirección.** De modo que si el autor no da una respuesta específica a los mismos \(ej: «Ir al norte sería precipitado.»\) el sistema comprobará las conexiones entre localidades y tratará de mover el personaje si la localidad actual tiene una salida en esa dirección.
* **Puedes dejar **_**huecos**_ en el vocabulario, es decir, no es necesario que los números en el mismo sean consecutivos.

### La sección de localidades \(/LTX\)

Similar a las secciones anteriores, pero para los textos de las localidades, que igualmente quedan numeradas y no puede haber huecos.

```
/0
Estás en tu casa, puedes ver una puerta al este.
/1
Estás en tu jardín, puedes ver la puerta de entrada al oeste.
```

Importante: los objetos que son contenedores \(una caja\) o superficies \(una mesa\) utilizan la localidad de igual número para depositar los objetos que tienen dentro o encima. Es por eso que no debe usarse como localidad, aquellas que compartan número con un objeto de ese tipo, o todo objeto puesto en el contenedor o superficie aparecería allí. Como "no usar un número de localidad es incompatible con que los números sean consecutivos, simplemente definiremos una localidad "en blanco". Por ejemplo en los casos anteriores el objeto "caja" es el objeto 1, y la localida 1 es el jardín. Si lo dejaramos así todo lo que metieramos en la caja aparecería en el jardín. Lo que hacemos es "saltarnos" la localida 1 así:

```
/0
Estás en tu casa, puedes ver una puerta al este.
/1
/2
Estás en tu jardín, puedes ver la puerta de entrada al oeste.
```

### La sección de conexiones \(/CON\)

Esta seccion detalla las conexiones existentes entre localidades al inicio del juego \(luego pueden cambiarse si por ejemplo abrimos una puerta o dinamitamos una pared\).

La seccion es similar a la de localidades, excepto que tras cada número de localidad, hay una serie de conexiones. Los números de localidad deben ser consecutivos, si una localidad no tiene conexiones simplemente se pone su número y se deja en blanco.

```
/0
SALIR 2
ESTE 2
/1
/2
OESTE 0
ENTRAR 0
```

Como veis, nada impide poner más de una conexión que lleve al mismo sitio \(ESTE o SALIR, OESTE o ENTRAR\).

### La seccion de objetos \(/OTX\)

Es similar a las secciones de mensajes, pero los textos se refieren a cada objeto, quedando así los objetos numerados.

```
/0
una antorcha
/1
una caja
```

En este caso NO puede haber huecos en el listado, los números deben ser consecutivos.

### La sección de objetos 2 \(/OBJ\)

Además del texto que describe al objeto, es necesario asignarle unas propiedades, y eso es lo que hacemos en esta sección:

* La localidad donde el objeto está cuando empezamos a jugar.
* El peso del objeto.
* El nombre \(y si es necesario el adjetivo\) que identificará el objeto en el vocabulario. Por ejemplo "LLAVE" para el objeto "la llave".
* Los [atributos de objeto](atributos de objeto).

Un objeto puede estar situado inicialmente en algun lugar \(la orilla del río, la habitación amarilla, el hall, etc.\), puede llevarlo el jugador, puede llevarlo puesto, o simplemente no estar accesible al inicio.

ngPAWS tiene tres localidades especiales que pueden ser usadas para decir al sistema que el objeto está en esos sitios especiales:

| Localidad especial | Loc \# | shortcut |
| --- | --- | --- |
| Llevado por el jugador | 254 | CARRIED |
| Puesto por el jugador | 253 | WORN |
| No accesible | 252 | NON\_CREATED |

Cuando defines dónde está un objeot, puedes usar su número de localidad o un identificador de [txtpaws](txtpaws_es).

Por otro lado, un objeto puede ser ligero como una pluma, o pesado como un cofre de hierro, y es decisión tuya como autor definir cuanto pesa cada uno. ngPAWS no define una unidad de peso \(gramos, kilos, libras, etc.\), eso es decisión tuya también y utiliza la misma medida para los objetos. Por defecto un jugador puede llevar 10 unidades de peso, pero eso también puede cambiarse, así que es una decisión tuya según el contexto.

Un objeto puede ser referido como "LINTERNA"  para el objeto "la linterna" o añadiendo un adjetivo como en "la caja blanca" que pondríamos "CAJA" y "BLANCA". Normalmente no nos molestaremos en añadir adjetivos salvo que sea necesario para diferenciar dos objetos similares, por ejemplo si tenemos una caja blanca y otra roja.

Finalmente, los objetos pueden tener atributos, que en ngPWS es algo que un objeto tiene o no. Por ejemplo podría tener un atributo "grande", y un objeto puede tener el atributo y por tanto ser grande, o no tenerlo y no ser grande, pero no puede ser que sea "un 20% grande", o lo es o no lo es.

ngPAWS incluye algunos [atributos estándar](atributos de objeto), que son manejados de manera automática por la base de datos de inicio.

Puedes asignar esos atributos en esta sección, y luego puedes usarlos para tus propias respuestas, comprobando si un objeto tiene o no ese atributo. Por ejemplo si el jugador dice "DAR LUZ A LA CAVERNA CON XXXXX" podemos comprobar si XXXX es un objeto que tiene el atributo de "dar luz" y en es caso permitir que se haga la luz, denegandolo en caso contrario \("DAR LUZ A LA CAVERNA CON EL ALTAVOZ"\)

ngPAWS te permite además definir tus propios atributos. En ese caso tú decides para qué usarlos. Por ejemplo puedes decidir que el jugador debe cruzar una pequeña grieta en una cueva, pero no puede pasar si lleva objetos grandes. Si creas un atributo "grande" y se lo asignas a aquellos objetos que lo sean, luego podrás comprobar si el jugador lleva alguno de ellos, y poner el mensaje "No puedes pasar, algunas cosas que llevas no caben." si lleva alguno.

Hay 64 \(del 0 al 63\) diferentes atributos, aunque los primeros están usados ya por los atributos estándar de ngPAWS, el resto están libres. Si vas a crear tu propio atributo, te recomendamos que empieces por el 63, luego si necesitas otro el 63, etc.

Esto sería una sección de objetos 2 típica:

```
/0    CARRIED        1        ANTORCHA   _           ATTR aLight aFemale
/1    WORN           1        MOCHILA    _           ATTR aWear aContainer aFemale
/2    7              1        CAJA       BLANCA      ATTR aContainer aFemale
/3    252            1        CAJA       ROJA        ATTR aContainer aFemale
/4    12             3        MANDOBLE   _           ATTR
```

¿Qué tenemos aquí?

En la primer fila vemos los datos para el objeto 0, al cual podemos referirnos por el nombre "ANTORCHA" \(y como no hace flata adjetivo ponemos un caracter de subrayado en su lugar, que significa "cualquiera"\), pesa una unidad, el jugador lo lleva al empezar \(CARRIED\), produce luz, y es femenino. Es importante marcar los objetos con su género y número. Por defecto son neutros y singulares, por lo que ordenes como "TOMAR LLAVE" producirían el texto "Tomas un llave."  si no especificamos que llave es femenino. Así mismo "TOMAR CARTAS" producirían el texto "Tomas un cartas" si no especificamos que es fememino y plural. Si estamos haciendo una aventura en inglés, hay que especificar también cuando es masculino, porque el inglés diferencia los géneros neutros y masculino, y no es lo mismo decir "HIM" que "IT".

En la segunda fila, al objeto mochila se le puede referencia por "MOCHILA" sin adjetivo, pesa 1 y es prenda, contenedor y femenino. El jugador lleva puesta la mochila al empezar.

El tercer objeto \(objeto número 2\), puede ser referido por "CAJA BLANCA", pesa una unudad y está en la localidad 7. Es un contenedor femenino.

El siguiente objeto \(el 3\) es otra caja, esta vez con el adjetivo "ROJA". Es similar a la anterior excepto que al empezar está en la localidad 252, que es lo mismo que poner NON\_CREATED, es decir, en ninguna parte.

El objeto 4 \(fila 5\) es un mandoble, referido por la palabra "MANDOBLE", que inicialmente está en la localidad 12 y no tiene ningún atributo en especial \(con lo cual es considerado neutro y en español funcionará bien\). Tampoco  pasaría  nada si le hubieramos puesto el atributo "aMale", pero he preferido dejarlo en blanco para que veáis que es obligatorio poner ATTR aunque no haya ningún atributo.

Si hubieramos definido un atributo personal llamado aBig \(grande\), deberíamos haber definido esto así, suponiendo que las cajas y la antorcha son pequeñas:

```
/0    CARRIED        1        ANTORCHA   _           ATTR aLight aFemale
/1    WORN           1        MOCHILA    _           ATTR aWear aContainer aFemale aBig
/2    7              1        CAJA       BLANCA      ATTR aContainer aFemale
/3    252            1        CAJA       ROJA        ATTR aContainer aFemale
/4    12             3        MANDOBLE   _           ATTR aBig
```

**Importante:**

* Para poder usar cualquier palabra en esta sección, debe estar definida previamente como nombre \(o adjetivo\) en la sección de vocabulario.

### Los mensajes de usuario \(/MTX\)

Son mensajes como los anteriores pero que pueden ser definidos por el usuario. En realidad este legado de PAWS es muy poco usado en ngpAWS, porque puedes hacer directamente WRITE:

`WRITE "You open the door."`

Antes, definias el mensaje 50 en la tabla de mensajes, y luego ponías:

`MESSAGE 50`

En cualquier caso, hoy en día aún hay casos en los que puede ser útil un mensaje de este tipo, pero no es el momento de explicarlo, por ser bastante avanzado.

Los números de mensajes no tienen por que ser consecutivos, puede haber huecos.

### Los mensajes del sistema \(/STX\)

**Los mensajes del sistema** son una serie de mensajes que se definen comenzando por un caracter «/» y un número. Este número se corresponde al _número de mensaje._

Cada uno de estos mensakes es una respuesta por defecto del sistema, en general heredadas de PAW y otros sistemas anteriores. Puedes modificarlos si crees que son demasiado serios, demasiado informales o que simplemente no encajan con el tono de tu aventura. Asegúrate de que mantienen un sentido en su conjunto.

Normalmente no tiene es necesario añadir más mensajes de sistema de los que hay. De hecho, es poco recomendable porque podrían entrar en conflicto con futuras expansiones de **ngPAWS**.

### Los procesos \(/PRO x\)

Los procesos es donde ocurren las respuestas a lo que escribe el jugador, debes añadirlas en el proceso 0, o tabla de respuestas.

Hay algunos procesos con funciones predefinidas

* Proceso 0: la tabla de respuestas
* Process 1: eventos que ocurren sin la acción del jugador tras describir una localidad
* Process 2: eventos que courren sin la acción del jugador tras cada orden del mismo

Lo detallaremos mejor en el siguiente capítulo.

[Ir al siguiente capítulo: La tabla de respuestas](La tabla de respuestas)

