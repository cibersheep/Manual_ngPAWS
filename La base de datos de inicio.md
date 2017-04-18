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

En esta sección se enumeran los textos de las localidades. Se define cada una como «/» seguido del número de localidad y su descripcion en la siguiente línea. Deben ser correlativas por lo que no puede haber huecos.

```
/0
Estás en tu casa, puedes ver una puerta al este.
/1
Estás en tu jardín, puedes ver la puerta de entrada al oeste.
```

**Importante**: los objetos que son _contenedores_ \(una caja\) o _superficies_ \(una mesa\) utilizan la localidad de igual número para depositar los objetos que tienen dentro o encima, por lo que, tales números, no deben usarse como localidad. En caso contrario, lo que se metiera o posuera sobre dichos objetos aparecería en la localidad con la que comparte número. Como los número de localidad han de ser consecutivos, simplemente se define una localidad "en blanco" para los objetos contenedores o superficie. Por ejemplo, si definimos un objeto «caja» como **objeto 1** y la localidad 1 es un jardín todo lo que metieramos en la caja aparecería en el jardín. Así, para resolverlo se "salta" la localidad 1 así:

```
/0
Estás en tu casa, puedes ver una puerta al este.
/1
/2
Estás en tu jardín, puedes ver la puerta de entrada al oeste.
```

### La sección de conexiones \(/CON\)

Esta seccion detalla las conexiones existentes entre localidades al **inicio del juego** \(luego pueden cambiarse si, por ejemplo, abrimos una puerta o dinamitamos una pared\).

La seccion es similar a la de localidades, excepto que tras cada número de localidad, se enumera una serie de conexiones. Los números de localidad deben ser consecutivos. Si una localidad no tiene conexiones simplemente se pone su número y se deja en blanco.

```
/0
SALIR 2
ESTE 2
/1
/2
OESTE 0
ENTRAR 0
```

Como ves, nada impide poner más de una conexión que lleve al mismo sitio \(ESTE o SALIR, OESTE o ENTRAR\).

### La sección de texto de objetos \(/OTX\)

Es similar a la sección de mensajes pero cada textos se refiere a un objeto, quedando así los objetos numerados.

```
/0
una antorcha
/1
una caja
```

En este caso NO puede haber _huecos_ en el listado, los números deben ser consecutivos.

### La sección de datos de objetos \(/OBJ\)

Además del texto que describe al objeto, es necesario asignarle unas propiedades, y eso es lo que hacemos en esta sección:

* La localidad donde el objeto está cuando empezamos a jugar.
* El peso del objeto.
* El nombre \(y si es necesario el adjetivo\) que identificará el objeto en el vocabulario. Por ejemplo «LLAVE» para el objeto «la llave».
* Los [atributos de objeto](atributos de objeto).

Un objeto puede estar situado al iniciar la partida en un lugar \(la orilla del río, la habitación amarilla, el hall, etc.\), puede llevarlo el jugador, puede llevarlo puesto o simplemente no estar accesible todavía.

**ngPAWS** tiene tres localidades especiales que se pueden usar para decirle al sistema que el objeto está en ellos:

| Localidad especial | Nº delocalidad | Identificador |
| :--- | :---: | :---: |
| Llevado por el jugador | 254 | CARRIED |
| El jugador lo lleva puesto | 253 | WORN |
| No accesible | 252 | NON\_CREATED |

Al definir dónde está un objeto, puedes usar su número de localidad o un identificador de [txtpaws](txtpaws_es).

Por otro lado, un objeto puede ser ligero como una pluma o pesado como un cofre de hierro, y es decisión tuya como autor definir cuánto pesa cada uno. En **ngPAWS** no se define una unidad de peso \(gramos, kilos, libras, etc.\), eso es decisión tuya también, como la de utilizar la misma medida para todos los objetos. Por defecto, un jugador puede llevar 10 unidades de peso pero eso también puede cambiarse según el contexto.

Puedes referirte un objeto «la linterna» como «LINTERNA» o añadiendo un adjetivo como «la caja blanca» que definiríamos con el sustantivo «CAJA» y el adjetivo «BLANCA». Normalmente no nos molestaremos en añadir adjetivos salvo que sea necesario para diferenciar dos objetos similares, por ejemplo si tenemos una caja blanca y otra roja.

Finalmente, en **ngPWS,** los objetos pueden tener un atributo o no. Por ejemplo, el atributo «grande», un objeto puede tener dicho atributo y por tanto ser _grande,_ o no tenerlo y _no ser grande_ pero no puede ser \_un 20% grande. \_Es todo o nada.

**ngPAWS** incluye algunos [atributos estándar](atributos de objeto) que son manejados de manera automática por la _base de datos de inicio._ Puedes asignarlos y luego usarlos en tus propias respuestas, comprobando si un objeto tiene o no ese atributo. Por ejemplo, si el jugador dice «DAR LUZ A LA CAVERNA CON XXXXX» podemos comprobar si _XXXX_ es un objeto que tiene el atributo de «dar luz» y en ese caso permitir ver e impedirlo en caso contrario si por ejemplo se intentar «DAR LUZ A LA CAVERNA CON EL ALTAVOZ».

**ngPAWS** te permite además definir tus propios atributos. En ese caso tú decides para qué usarlos. Por ejemplo, puedes decidir que el jugador debe cruzar una pequeña grieta en una cueva pero no puede pasar si lleva objetos grandes. Si creas un atributo «grande» y se lo asignas a aquellos objetos que lo sean, luego podrás comprobar si el jugador lleva alguno de ellos y responder con el mensaje "No puedes pasar, algunas cosas que llevas no caben".

Hay 64 \(del 0 al 63\) atributos diferentes, aunque los primeros están usados ya por los atributos estándar de ngPAWS, el resto están libres. Si vas a crear tu propio atributo, te recomendamos que empieces por el 63, luego si necesitas otro, usa el 62, etc.

Esto sería una sección de _datos de objetos_ típica:

```
/0    CARRIED        1        ANTORCHA   _           ATTR aLight aFemale
/1    WORN           1        MOCHILA    _           ATTR aWear aContainer aFemale
/2    7              1        CAJA       BLANCA      ATTR aContainer aFemale
/3    252            1        CAJA       ROJA        ATTR aContainer aFemale
/4    12             3        MANDOBLE   _           ATTR
```

#### ¿Qué tenemos aquí?

En la primer fila vemos los datos para el objeto 0. Objeto definido por el nombre «ANTORCHA» \(y como no le hace falta un adjetivo, ponemos un caracter de subrayado en su lugar que significa uno «cualquiera»\), que pesa una unidad, que está en la _localidad_ CARRIED \(que significa que el jugador la lleva consigo al empezar\), que produce luz \(aLight\), y que es femenino \(aFemale\).

Es importante marcar los objetos con su género y número. Por defecto son neutros y singulares, por lo que órdenes como "TOMAR LLAVE" produciría el texto «Tomas _un_ llave.»  si no especificamos que **llave** es femenino. Así mismo, «TOMAR CARTAS» produciría el texto «Tomas un cartas.» si no especificamos que es fememino y plural. Si estamos haciendo una aventura en inglés, hay que especificar también cuándo el objeto es masculino, porque en inglés se diferencian los géneros neutros y masculino, y no es lo mismo decir «HIM» que «IT».

En la segunda fila, se define el objeto mochila como «MOCHILA», sin adjetivo. Que pesa 1 y es una prenda \(aWear\), un contenedor \(aContainer\) y femenino \(aFemalie\). También se especifica que el jugador lleva puesta la mochila al empezar \(WORN\).

El tercer objeto \(el número 2\), queda definido como «CAJA BLANCA», que pesa una unidad y que está en la localidad 7. Tambíen que es un contenedor \(aWear\) femenino \(aFemale\).

El siguiente objeto \(el número 3\) es otra caja, esta vez definida con el adjetivo «ROJA». Es similar a la anterior excepto que al empezar la prtida está en la localidad 252 \(que es lo mismo que poner NON\_CREATED, es decir, que no está _en ninguna parte_\).

El objeto 4 \(fila 5\) es un mandoble, definido por la palabra «MANDOBLE», que inicialmente está en la localidad 12 y no tiene ningún atributo en especial \(con lo que es considerado neutro y en español funcionará bien\). Tampoco  pasaría  nada si le hubieramos puesto el atributo aMale pero he preferido dejarlo en blanco para que veáis** que es obligatorio poner ATTR** aunque no haya ningún atributo.

Si hubieramos definido un atributo personal, uno creado por nosotros, llamado aBig \(grande\), hubiese quedado así \(y suponiendo que las cajas y la antorcha son pequeñas\):

```
/0    CARRIED        1        ANTORCHA   _           ATTR aLight aFemale
/1    WORN           1        MOCHILA    _           ATTR aWear aContainer aFemale aBig
/2    7              1        CAJA       BLANCA      ATTR aContainer aFemale
/3    252            1        CAJA       ROJA        ATTR aContainer aFemale
/4    12             3        MANDOBLE   _           ATTR aBig
```

**Importante: ** Para poder usar cualquier palabra en esta sección, debe estar definida previamente como sustantivo \(o adjetivo\) en la sección de vocabulario \(/VOC\).

### Los mensajes de usuario \(/MTX\)

Son mensajes definidos por el usuario de la siguiente forma: «/» seguida del número de mensaje y, en la siguiente línea, el texto a mostrar. En realidad esto, un legado de PAWS, se usa muy poco en **ngpAWS.** Es más común que los mensajes se escriban directamente con la instrucción WRITE \(muestra el texto\) o WRITELN \(muestra el texto y hace saltar a la línea siguiente\):

`WRITE "Abres la puerta."`

Antes se definía como mensaje 50 en la tabla de mensajes

`/50     
Abres la puerta.`

Luego en un condacto, se hacía que se mostrara dicho mensaje poniendo:

`MESSAGE 50`

En cualquier caso, hoy en día aún hay casos en los que puede ser útil un mensaje de este tipo pero este no es el momento de explicarlo por ser bastante avanzado.

Los números de mensajes no tienen por que ser consecutivos, puede haber huecos.

### Los mensajes del sistema \(/STX\)

**Los mensajes del sistema** son una serie de mensajes que se definen comenzando por un caracter «/» y un número. Este número se corresponde al _número de mensaje._

Cada uno de estos mensajes es una respuesta por defecto del sistema, en general heredadas de PAW y otros sistemas anteriores. Puedes modificarlos si crees que son demasiado serios, demasiado informales o que simplemente no encajan con el tono de tu aventura. Asegúrate de que mantienen son coherentes en su conjunto.

Normalmente no es necesario añadir más mensajes de sistema de los que hay. De hecho, es poco recomendable porque podrían entrar en conflicto con futuras expansiones de **ngPAWS**.

### Las respuesta y procesos \(/PRO x\)

La sección **respuestas** es un proceso y es en dichos procesos donde ocurren las contestaciones a lo que escribe el jugador, debes añadirlas en el Proceso 0 \(RESP\) o tabla de respuestas.

Algunos de los procesos tienen funciones predefinidas

* Proceso 0: la tabla de respuestas.
* Proceso 1: eventos que ocurren **sin la acción del jugador** y tras describir una localidad.
* Proceso 2: eventos que courren **sin la acción del jugador** y tras cada una de sus órdenes

Veremos más en detalle los procesos en el siguiente capítulo.

