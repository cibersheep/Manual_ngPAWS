### Tutorial: La Torre


Este tutorial fue originalmente creado para el parser NMP, y editado en un fanzine, por lo que fue creado en varios capítulos. Dichos capítulos se mantienen en esta documentación.

_Nota: Esta serie de artículos se realizaron para el parser NMP y han sido adaptados a ngPAWS. Dado que la serie original quedó incompleta este tutorial tampoco finaliza. No obstante esperamos que lo visto hasta aquí os sirva de ayuda para entender ngpAWS y que vosotros mismos podáis finalizar esta aventura._

_Nota 2: En 2015, el usuario El Testigo realizó la aventura completando la parte que faltaba en la misma. Podéis descargarla [en este enlace](http://www.caad.es/fichas/la-torre-tutorial-para-superglus-y-ngpaws.html). Es muy recomendable porque incluye el código fuente con muchos comentarios. Si al seguir el tutorial os perdéis en algo os puede ser de mucha ayuda._


## Capítulo 1


Esta serie de artículos esta dedicada a todos aquellos que nunca habéis programado vuestra propia aventura, y que pensáis que crear una incluso con un parser ha de ser difícil, por ello comienzo estos artículos en los que enseñaré, paso a paso, el modo de crear una aventura con ngPAWS.

Lo primero que lógicamente tendremos que hacer es tener un sencillo guión, sencillo porque lógicamente no voy a crear aquí una aventura de cientos de localidades. Por ello voy a realizar una mini-aventura en la que el único objetivo es salir de una torre en la que nos han encerrado.

Espero que esto os pueda servir como punto de inicio para crear vuestras propias aventuras, dejando claro que nada de lo que yo escriba aquí es dogma de fe y por tanto si no os gusta lo podéis cambiar en vuestras creaciones. 

**POR DONDE EMPEZAR**

Pues quizá lo más normal es comenzar detallando las localidades, es decir, tener un pequeño mapa. Esto no es imprescindible pero sí lo más usual. 

![mapa](http://www.ngpaws.com/wikires/latorremap.png)

Nota: las líneas con flechas quieren decir subir/bajar y la que tiene una equis o cruz (x) no existe en un principio. 

Ahora, y antes de comenzar a programar nada deberemos de crear la aventura en ngPAWS, para ello pulsaremos en el menú situado en la parte superior de la pantalla, elegimos la opción _Archivo->Nuevo_ (o _File->new_) e introducimos entonces el nombre de la aventura que queremos crear y pulsamos en guardar. Con esto ya tendremos creados el ficheros correspondiente a nuestra aventura. Ahora es momento de comenzar a introducir la información de las localidades. 

Nota: los usuarios de linux que no usan el editor de ngPAWS copiar la carpeta "new_game_pack" en otro directorio.

Nuestro siguiente cometido es crear las descripciones, aunque si aún no las tenemos muy claras bastará con que pongamos un texto identificativo y las conexiones, de modo que al menos podamos movernos por el mapa. Como podéis ver todas las localidades tienen un nombre (etiqueta) dentro de ellas, esto nos será útil para referenciarlas en nuestro programa y también para describir las conexiones. Fíjate que también aparece, al lado de cada localidad, un número. Éste número, como veremos a continuación, tendremos que emplearlo la principio, cuando definamos la localidad, asociándolo con su etiqueta.

Por otro lado, te darás cuenta de que no hemos escogido el mismo nombre directo como etiqueta para cada una de las localidades. Esto es debido a que, si se encuentra el mismo nombre en otro lugar (un mensaje, por ejemplo), también será sustituido, lo cuál no es lo que pretendemos. Así, debemos ponerle un prefijo ("l", en el listado más abajo), o un sufijo (por ejemplo, "_loc"), eso es preferencia de cada uno. Ésto se hará también para los mensajes, objetos, ...



Para poner las descripciones en ngPAWS pulsamos sobre la pestaña de la parte superior identificada como Localidades (o el apartado LTX en el fichero TXP si no usas el editor) y sustituir los textos que aparecen por los siguientes:

```
/0
La Torre
Buscas fama y gloria, pero la fama y la gloria cuestan ...
¿Cuánto estás dispuesto a pagar?

/1
Estás junto a la puerta principal. A su lado puedes una mesa de guardia y en la pared norte hay una chimenea.

/2
Varios maltrechos catres se amontonan en esta habitación.

/3
El viento ulula a través de la empinada escalera de caracol, una vieja armadura parece vigilar la escalera.

/4
Una silenciosa estancia débilmente alumbrada por los rayos de luna que se filtran a través de un pequeño ventanuco. El suelo está lleno de paja, colgando de unos grilletes en la pared observas un esqueleto humano.

/5
Los desgastados peldaños de piedra resbalan en ocasiones. A mitad de la escalera una antorcha en la pared impide que la oscuridad sea completa.

/6
Una gran cama preside la estancia, los gruesos barrotes no permiten la salida por la ventana, aunque de todos modos estaría demasiado alta.

```

Además, para poder después referenciar a las localidades por su nombre si tener que acordarnos de su número, vamos a las solapa "Definiciones" ("Definitions", o si no usamos el editor, la zona al principio del código anterior a la sección "CTL") y ponemos esto al final de la misma:

```
#define loc lIntro 0
#define loc lHall 1
#define loc lBarracon 2
#define loc lEscalera 3
#define loc lCelda 4
#define loc lEscalera2 5
#define loc lDormitorio 6
```


Ahora nos dirigimos a la pestaña _Conexiones_ ("Connections" o el apartado CON si no usamos el editor) y sustituimos el texto existente por el que sigue a continuación:

```
/0
/1
	ESTE lBarracon
/2
	OESTE lHall
	ESTE lEscalera
/3
	SUBIR lEscalera2
	OESTE lBarracon
/4
	ESTE lEscalera2
/5
	BAJAR lEscalera
	SUBIR lDormitorio
/6
	BAJAR lEscalera2
```

Veamos que es todo esto: a la primera localidad (0, ó lInicial) no se le pone una descripción como a las otras, pues será la empleada para presentar el juego. Supongo que no os será demasiado difícil ver como se describen las conexiones, baste decir que no hay más que poner cada una de las salidas de la localidad seguida de la localidad a la que se llega por ellas. Como podéis ver no he puesto la salida que esta tachada en el plano (la de la equis o cruz), pues en un principio no existe.

Como hemos dicho, la localidad 0 o lInicial, la usaremos de presentación, para ello, copiaremos este código en la solapa Process 1 (Proceso 1, o sección PRO 1 si no usamos el editor), al final (sin substituir lo que hay ya):

```
_ _
 AT lIntro
 GOTO lHall
 ANYKEY
 DESC
```

Este código, básicamente hace que tras describirse la localidad, si estamos en la localidad lIntro, nos mueve a la localidad lHall, espera la pulsación de una tecla, y la describe.

Bien, hecho esto si ejecutamos el test del juego (F5), podremos ya movernos por la torre, excepto por la localidad lCelda (ó 4).

En la pantalla de presentacion veremos un mensaje que pone que podemos ver una antorcha. Esto es así porque ngPAWS trae un objeto de ejemplo en la aventura "base" de la que partimos, la antorcha, que precisamente está en la localidad 0. Nos libraremos de ese mensaje más tarde.

**LA PUERTA SECRETA**

Bien, ahora quizá debería empezar a hablar de los objetos, pero entonces no veríais nada de programación en esta entrega, por lo que lo que voy a hacer es las órdenes encargadas de permitirnos el acceso a la localidad de la celda. Para ello debéis saber que (como muchos habréis ya supuesto), la antorcha que hay en mitad de la escalera sirve para abrir una puerta secreta, que nos da acceso a la localidad lCelda. 

En primer lugar bastará con que empujemos la antorcha para que la puerta se abra, y tirar de ella para cerrarla.

Bien, vamos allá: abramos la tabla de respuestas (Alt+R, o sección PRO 0 si no usamos el editor) y escribamos lo siguiente justo debajo de la linea que pone "Coloca aquí tus propias respuestas". Todas nuestras respuestas deben situarse en esa zona, que está a mitad del código de esa solapa, el resto de código conforma las respuestas por defecto que ya da ngPAWS a un montón de frases del jugador. Bien, pues ponemos esto:

```
#define flg fConex = 100

EMPUJAR ANTORCHA        
 AT lEscalera2
 GETEXIT _voc_OESTE fConex
 EQ flgConex 255
 SETEXIT _voc_OESTE lCelda
 WRITELN "Al empujar la antorcha una porción de pared se abre al oeste dando acceso a una estancia."
 DONE

EMPUJAR ANTORCHA
 AT lEscalera2
 GETEXIT _voc_OESTE fConex
 NOTZERO flgConex
 WRITELN "La antorcha no cede más."
 DONE    

```

Explicaciones: 

"#define flg fConex = 100". Definimos la etiqueta fConex como que va a identificar a un flag, y va a valer 100. El signo igual ('=') entre la etiqueta y el valor es totalmente opcional. Un flag es un sitio donde podemos guardar un valor (un número).

Realizamos la entrada EMPUJAR ANTORCHA, por lo que las siguientes instrucciones sólo se ejecutarán si el jugador teclea eso. 

Luego comprobamos que estamos en la localidad adecuada ([[AT|AT_ES]] lEscalera2), si no es así tampoco se ejecutarán las siguientes ordenes. 

_voc_OESTE aparece en el ejemplo varias veces. Todo el vocabulario se almacena en identificadores, que no interfieren con los identificadores del usuario porque llevan como prefijo “_voc_”. Así, por ejemplo, el verbo empujar puede ser referenciado como el identificador _voc_EMPUJAR (en mayúsculas o minúsculas según se haya definido en el juego), con el valor del número asignado al citado verbo. En este caso, se trata de poder indicar, en los condactos [[GETEXIT|GETEXIT_ES]] y [[SETEXIT|SETEXIT_ES]], como se verá a continuación, la dirección de una salida. 

La siguiente instrucción ([[GETEXIT|GETEXIT_ES]]) nos devuelve el número de localidad al que nos lleva determinada salida (en este caso, la OESTE) de la localidad actual, o 255 si esa salida no existe, por tanto lo usaremos para saber si la entrada secreta está abierta. El valor será almacenado en el flag fConex, que es el flag 100, porque así se ha definido antes. 

"[[EQ|EQ_ES]] fConex 255": De nuevo una condición, que de no cumplirse impedirá la ejecución de las ordenes siguientes. Esta se cumple si el flag flgConex contiene un valor de 255, lo cual será así si no hay salida al oeste (la puerta cerrada), pues GETEXIT habrá puesto un 255 en el flag fConex. 

Ahora ya hemos comprobado que todo está en regla, por lo que no tenemos más que informar al jugador y abrir la puerta, para lo cual primero se usa [[SETEXIT|SETEXIT_ES]], que crea una salida al OESTE (definida según el verbo de vocabulario, accesible mediante _voc_OESTE) en la localidad actual y que tiene por destino la localidad lCelda, y luego muestra el mensaje adecuado usando [[WRITELN|WRITELN_ES]]. 

La orden [[DONE|DONE_ES]] final indica que ya se ha contestado al jugador, por lo que no sigue buscando más entradas que coincidan con lo que el jugador tecleo (EMPUJAR ANTORCHA), así que no llega a la siguiente entrada: 

La segunda entrada está pensada para que responda al jugador si este trata de empujar más aún la antorcha, su estructura es muy similar, excepto en que comprueba que el flag fConex *no* es 255 (es decir, que hay una salida al oeste) y pone el mensaje en ese caso. 

Bueno, pues por esta entrega nada más, en la siguiente trataremos acerca de los objetos y veremos como cerrar esta puerta secreta (cosa que ya podéis ir pensando por vuestra cuenta, no es muy diferente a la manera de abrirla). 

Solo un último detalle: la definición del flag fConex en la tabla de respuestas es posible, porque siempre que no se use fConex antes de definirlo funcionará, sin embargo es preferible tener todas las definiciones juntas en un mismo sitio, para poder revisarlas si es necesario, por eso vamos a tomar la línea
`#define flg fConex = 100` y la vamos a mover al apartado de definiciones (donde pusimos los "define" de las localidades) y la ponemos justo debajo.

## Capítulo 2

En esta entrega hablaremos de los siempre necesarios objetos y de como cerrar aquella dichosa puerta de la que hablábamos en el número anterior. 

**LA PUERTA** 

En el anterior capítulo vimos como abrirla, y os dejaba a vosotros intentar el proceso de cerrarla. Pues bien, esta es mi solución, lo cual no quiere decir que no pueda haber otras tan buenas o mejores que esta: 

Bien, en la tabla de respuestas, detrás de los "EMPUJAR" de antes,  escribamos lo siguiente: 

```
TIRAR ANTORCHA     
 AT lEscalera2
 GETEXIT _voc_OESTE fConex
 NOTEQ fConex 255
 CLEAREXIT _voc_OESTE
 WRITELN "Al tirar de la antorcha la porción de pared que se abrió vuelve a cerrarse."
 DONE

TIRAR ANTORCHA     
 AT lEscalera2
 GETEXIT _voc_OESTE fConex
 EQ fConex 255
 WRITELN "La antorcha no cede más."
 DONE
```

Explicaciones: 

Añadimos la entrada TIRAR ANTORCHA, por lo que las siguientes instrucciones sólo se ejecutarán si el jugador teclea eso. 

Luego comprobamos que estamos en la localidad adecuada ([[AT|AT_ES]] lEscalera2), si no es así tampoco se ejecutarán las siguientes ordenes. 

Obtenemos con [[GETEXIT|GETEXIT_ES]] la localidad a la que iríamos al oeste. 

Comprobamos que no es 255 (en cuyo caso la puerta ya está cerrada). 

Ahora ya hemos comprobado que todo está en regla, por lo que no tenemos más que informar al jugador y cerrarla, para ello lo primero es usar [[CLEAREXIT|CLEAREXIT_ES]], para destruir la salida. 

La orden DONE final indica que ya se ha contestado al jugador, por lo que no sigue buscando más entradas que coincidan con lo que el jugador tecleó (TIRAR ANTORCHA), así que no llega a la siguiente entrada: 

La segunda entrada está pensada para que responda al jugador si este trata de tirar aún más la antorcha, su estructura es muy similar, excepto en que comprueba que el flag fConex sí es 255 (es decir, que no hay una salida al oeste) y pone el mensaje en ese caso.

**Código sobrante**

En el código de abrir la puerta y en el de cerrarla hay en cada uno dos líneas de código innecesarias, el próximo capítulo hablaré de ellas, pero vosotros podéis ir buscándolas por vuestra cuenta. 

**OBJETOS** 

Los objetos son fundamentales en casi cualquier aventura conversacional, y nos servirán como herramientas para hacer algo, como piezas para trueque, como armas e incluso algunos absolutamente para nada (los llamados _red herrings_). Vamos a ver los objetos que vamos a tener en nuestra aventura: 

  * una barra de hierro 
  * un trozo de carbón 
  * unas raídas sábanas 
  * un pequeño cuchillo 
  * una funda de colchón

Por tanto su descripción en la pestaña Objetos (ALT+O, Objects o sección OTX) quedaría de la siguiente forma (reemplazar lo que hay): 

```
/0
una barra de hierro
/1
un trozo de carbón
/2
unas raídas sábanas
/3
un pequeño cuchillo
/4
unas fundas de catre
```

Además, vamos a añadir al final de la zona de definiciones los siguiente:

```
#define obj oBarra 0
#define obj oCarbon 1
#define obj oSabanas 2
#define obj oCuchillo 3
#define obj oFunda 4
```   

Y en la pestaña Objetos [2] (ALT+B, Object data, o sección OBJ si no usais el editor) quedaría la siguiente forma (reemplazar lo que hay): 

```
/oBarra      252          2        BARRA        HIERRO   ATTR aFemale
/oCarbon     252          1        CARBON       _        ATTR
/oSabanas    252          1        SABANAS      _        ATTR aFemale aPluralName
/oCuchillo   252          1        CUCHILLO     _        ATTR
/oFunda      252          1        FUNDA        _        ATTR aFemale
```

Por último, en la solapa de Vocabulario (Vocabulary, o sección VOC si no usáis el editor), buscad la palabra "ANTORCHA" y justo detrás añadimos lo siguiente:

```
BARRA 51 noun
CARBON 52 noun
SABANAS 53 noun
CUCHILLO 54 noun
FUNDA 55 noun
```

Nota: en el momento de crear este documento el último nombre que aparece en la lista antes de añadir nuestros nombres, es "ANTORCHA", con numero 50. En caso de que existan más simplemente empieza a numerar por el número siguiente al último, en lugar del 51.

Finalmente, buscamos los adjetivos, y al final, añadimos:

```
HIERRO 10 adjective
```

Bien, ahora viene la explicación: 

Para cada objeto ponemos primero su número y seguidamente su nombre, todo ello en la solapa Objetos (Objects, OTX) y les asignamos a cada uno una "etiqueta" para poder referirnos a ellos en el apartado de definiciones. Después, en la tabla "Objetos [2]" (Object Data, OBJ) volvemos a teclear primeramente su numero (o etiqueta en este caso), después la localidad inicial en la cual se encontrará el objeto, seguimos colocando ahora el peso del objeto indicados en unidades de peso. 

Tras esto viene el nombre que identifica al objeto y que será el que el jugador habrá de teclear para referirse a el. También podemos añadir un adjetivo como en el caso de la barra u omitirlo utilizando el carácter especial _ si no necesitamos especificar adjetivo. Una vez descrito todo eso sólo nos quedan los [[atributos de objeto]], cuya funcionalidad la podéis ver en en esté link: [[atributos de objeto]].

Ademas de las localidades definidas por el programador hay tres números asignados a localidades especiales que son las siguientes: 

  * 252: El objeto no está en ninguna parte (de momento no es visible).
  * 253: El objeto lo llevamos puesto (es una prenda).
  * 254: El objeto lo llevamos.

Como podéis ver todos los objetos de nuestra aventura son inaccesibles de primeras. 

Para finalizar este capítulo vamos a hacer aparecer el trozo de carbón, que está en la chimenea. Comencemos añadiendo en la tabla de respuestas, justo detrás de la última entrada de "TIRAR ANTORCHA": 

```
EXAMINAR CHIMENEA        
 AT lHall
 WRITE "La chimenea está muy sucia y no hay fuego en ella.¬"
 ISAT oCarbon 252
 WRITELN "Hay un gran trozo de carbón en ella."
 CREATE oCarbon
 DONE

EXAMINAR CHIMENEA        
 AT lHall
 NEWLINE
 DONE
```

Añadimos también, al vocabulario, la palabra chimenea:

```
CHIMENEA 56 noun
```

Bien, ¿cómo funciona esto?: 
Primero al examinar la chimenea comprobamos que estamos en la localidad correcta (AT lHall), en cuyo caso ponemos la descripción general de la misma pero usando [[WRITE|WRITE_ES]] en lugar de WRITELN, de modo que el cursor no pase a la siguiente línea. 

Luego comprobamos que el objeto oCarbon está en la localidad 252, siguiendo la ejecución de esta entrada sólo en ese caso.

Bien, en caso de que el carbón estuviera inaccesible lo que haremos será poner el otro mensaje (que aparecerá justo tras el anterior, no en la siguiente línea), crear el objeto ([[CREATE|CREATE_ES]] oCarbon), poniéndolo de este modo en la localidad actual y dar por concluido (DONE). 

Si el objeto no estaba en la localidad 252 nos saldremos de esa entrada para caer irremisiblemente en la segunda, en la que pasaremos el cursor a la línea siguiente ([[NEWLINE|NEWLINE_ES]]) y finalizaremos (DONE). Esta entrada es fundamental, pues de no existir nos encontraríamos con que si el objeto no está en la 252 nos pondría: "La chimenea está muy sucia y no hay fuego en ella. No puedes hacer eso. ". 

Bien, pues aquí llega a su fin esta segunda entrega. En la próxima veremos como interactuar con otros objetos y desvelaré el secreto de las instrucciones de más. Hasta pronto. 

## Capítulo 3

Pues bien, veíamos en el anterior capítulo que la forma de cerrar la puerta secreta, y decíamos que tanto en él como en el otro había dos instrucciones sobrantes. Os voy a decir cuales son las de la parte de cerrar la puerta y espero que deduzcáis cuales son las de abrirla. Teníamos el siguiente código: 

```
TIRAR ANTORCHA     
 AT lEscalera2
 GETEXIT _voc_OESTE fConex
 NOTEQ fConex 255
 CLEAREXIT _voc_OESTE
 WRITELN "Al empujar la antorcha una porción de pared se abre al oeste dando acceso a una estancia."
 DONE

TIRAR ANTORCHA
 AT lEscalera2
 GETEXIT _voc_OESTE fConex;--->Sobra.
 EQ fConex 255            ;--->Sobra.
 WRITELN "La antorcha no cede más."
 DONE
```

Como veis he marcado las dos instrucciones sobrantes. ¿Y por qué sobran? Pues bien, dado que el código se va ejecutando de arriba a abajo en el caso de que estemos en la localidad lEscalera2 y el jugador teclee "TIRAR DE ANTORCHA" entraremos en la primera entrada, en la cual se guarda en el flag fConex la conexión al oeste y se comprueba que no es 255, en cuyo caso la destruimosy se muestra el mensaje, pero lo fundamental es que la entrada acaba con DONE, por lo que el resto del proceso (o tabla de respuestas en este caso) es ignorado. 

Por tanto si el programa está ejecutando la segunda entrada, y tras el AT lEscalera2, podemos estar seguros de que la conexión de la localidad está a 255 (o sea, la puerta está cerrada), porque de otro modo nunca habríamos llegado hasta allí. Es por esto que guardar de nuevo el valor de la conexión en el flag fConex y comprobar su valor carece de sentido y por eso sobran ambas órdenes. Lo cierto es que no es que esté mal, es que simplemente, es redundante. 

**SIGAMOS CON NUESTRA FUGA**

Bien, vimos en el capítulo anterior la forma de hacer aparecer el carbón (oCarbon), veamos ahora dónde está el cuchillo (oCuchillo). El cuchillo resultará estar entre los huesos del esqueleto de la habitación oculta, para encontrarlos por supuesto que deberemos examinar dicho esqueleto. Como veremos estas órdenes serán muy similares a las de encontrar el carbón. 

Pongamos las siguientes ordenes en la tabla de respuestas, detrás de las entradas de "EXAMINAR CHIMENEA": 

```
EXAMINAR ESQUELETO       
 AT lCelda
 WRITELN "Los huesos amarillentos, las cuencas vacías."
 ISAT oCuchillo 252
 CREATE oCuchillo
 WRITELN "Junto a él observas un viejo cuchillo."
 DONE

EXAMINAR ESQUELETO       
 AT lCelda
 NEWLINE
 DONE
```

En el vocabulario añadiremos: 

```
ESQUELETO       57      noun
```
      
de modo que la palabra esqueleto quede añadida al vocabulario. 

**VOLVIENDO A LA PUERTA**

Vamos a continuar viendo la utilidad de una sección de procesos que no es la tabla de respuestas, en concreto la sección procesos 1, que ya hemos usado brevemente para saltar de la pantalla de presentación a la localidad lHall.

Este proceso se ejecuta tras describir las localidades, por lo cual es ideal para describir cosas de las mismas que no sean fijas, como por ejemplo el estado de la puerta que se abre con la antorcha. Añadamos esto al final del proceso 1 (Alt-1, Process 1 o  seccion "PRO 1" si no usamos el editor): 

```
_ _
 AT lEscalera2
 GETEXIT _voc_OESTE fConex
 NOTEQ fConex 255
 WRITELN "Cierta porción de la pared se ha movido dando acceso a otra sala."
 NOTDONE
```

Bien, ¿qué es lo que hacemos aquí?. Pues de nuevo usamos la orden GETEXIT para saber a que localidad nos lleva la direción OESTE en la localidad locEscalera2. En caso de que ésta no sea 255 quiere decir que la puerta secreta está abierta, en cuyo caso mostramos el texto indicándolo, que aparecerá justo tras la descripción de la localidad tal que así: 

"Los desgastados peldaños de piedra resbalan en ocasiones. A mitad de la escalera una antorcha en la pared impide que la oscuridad sea completa. Cierta porción de la pared se ha movido dando acceso a otra sala." 

En caso de que la puerta esté cerrada, el texto adicional no aparece. 

**LOS FLAGS**

En los ejemplos anteriores hemos tenido la primera toma de contacto con un flag. Los flags nos servirán para controlar cosas en nuestra aventura, y algunos como el flag número 38, llamados [[flags del sistema]] contienen un valor dado por el parser.

El flag 38, por ejemplo, contiene siempre el número de localidad en que estamos. 

A su vez el signo @ es el signo de indirección, que hace que lo que le siga sea tomado como un número de flag y substituye el conjunto "@número" por el contenido del flag que tiene ese número. Que lío ¿no? Para que se vea más claro ahí va esto: 

Supongamos que estamos en la localidad locBarracon (número 2), por tanto el flag 38 contiene un dos, y entonces la orden [[EXITS|EXITS_ES]] @38 68 la traducirá el parser por: 

```
      EXITS 2 1000
```
      
mostrando de este modo las salidas de la localidad locBarracon (número 2 ).

Supongamos que nos vamos a la localidad locCelda (4), por lo que el flag 38 pasa a valer 4, pues entonces la misma orden (EXITS @38 1000) sería traducida por EXITS 4 68, puesto que ahora el flag 38 vale 4, y listaría las salidas de la localidad locCelda. 

## Capítulo 4 (y último)
 
Bien, nuestra mini-aventura está casi terminada, al menos en su esqueleto principal, aunque aún nos falta saber que hemos de hacer para escapar. Los pasos que nos quedan serán los siguientes, que pasaremos a programar a continuación: 

  - Usar el cuchillo para romper las ataduras que sujetan la funda a la cama. 
  - Coger funda. 
  - Examinar los barrotes de la ventana (uno estará flojo). 
  - Coger/Tirar del barrote suelto. 
  - Atar la funda a otro barrote. 
  - Salir. 

Como veréis he dejado de lado las sábanas, mas que nada por simplificar el código y que resulte más fácil de entender, así que las sabanas no aparecerán nunca. 

Bien, vayamos por partes: 

Para que el jugador sepa que hay una funda deberá examinar la cama, por lo que añadiremos las siguientes entradas en la tabla de respuestas: 

```
EXAMINAR CAMA            
 AT lDormitorio
 ISAT oFunda 252
 WRITELN "Una funda de tela cubre la cama."
 DONE

EXAMINAR CAMA            
 AT lDormitorio
 ISNOTAT oFunda 252
 WRITELN "Solo restos de paja cubren la cama."
 DONE
```

Añadiremos también "cama" al vocabulario:

```
CAMA 58 noun
```

¿Y que hacemos con ésto? 

Pues si la funda esta en la localidad 252 (no creada, tal como es al principio) es que está puesta, y si está en cualquier otro sitio es que está quitada, por lo que ponemos uno u otro mensaje según donde esté. Si sois perspicaces os habréis dado cuenta de que de nuevo hay código sobrante: Sí, el "ISNOTAT oFunda 252" sobra en la segunda entrada, pues no llegará a ella si, estando en la localidad locDormitorio, la funda está en la localidad 252, pues se comprueba en la entrada anterior. 

Veamos ahora como impediremos que el jugador coja la funda cuando aún está atada. 

Bien, primeramente, y ya sin otra salida posible, tendremos que usar un flag. También le daremos un nombre, en este caso hemos escogido "fFundaAtada". La utilidad del flag será la de guardar el estado de la funda, es decir, el siguiente: 

Si el flag vale 0 (que es el valor por defecto), querrá decir que las ataduras están intactas. Si vale 1 querrá decir que las ligaduras han sido cortadas. 

Añadamos las siguientes entradas en la tabla de respuestas: 

```
COGER FUNDA        
 AT lDormitorio
 ISAT oFunda 252   ; Funda está en la cama.
 ZERO fFundaAtada  ; ¡¡¡Está atada!!!
 WRITELN "La funda está atada a la cama por fuertes ligaduras."
 DONE
```

Añadir esto también en la zona de definiciones:

```
#define flg fFundaAtada = 255
```  

No necesitamos añadir la palabra FUNDA al vocabulario porque ya lo hicimos cuando creamos los objetos (Está como `FUNDA         55       noun`).

El condacto "DONE" es muy importante, puesto que evita que se siga ejecutando la tabla de respuestas, impidiendo así que se llegue a la entrada por defecto "COGER _", que está más abajo, cosa que no nos interesa. Así hemos impedido que el jugador coja la funda, a pesar de que con un EXAMINAR la ve.

Añadamos esto para poder coger la funda si ya no está atada:

```
COGER FUNDA        
 AT lDormitorio
 ISAT oFunda 252
 NOTZERO fFundaAtada ; No está atada
 CREATE oFunda  ; Creamos la funda
 GET oFunda     ; La cogemos, ahora la
                  ; funda ya es un objeto
 DONE             ; normal.
```

¿pero como la desatamos?
 
Vamos a añadir la palabra ligaduras al vocabulario: 

```
LIGADURAS 59 noun
```

Y en la tabla de respuestas añadimos: 

```
CORTAR LIGADURAS       
 AT lDormitorio
 ISAT oFunda 252   ; ¿funda en cama?
 ZERO fFundaAtada  ; ¿y atada?
 CARRIED oCuchillo ; ¿lleva cuchillo?
 WRITELN "Cortas las ligaduras con el cuchillo."
 LET fFundaAtada 1 ; ligaduras rotas
 DONE
```

Algunos autores de aventuras obligan al jugador a teclear la orden completa "CORTAR LIGADURAS CON CUCHILLO", en mi opinión resta jugabilidad, puesto que el jugador, si lleva el cuchillo, se da por supuesto que lo usará en lugar de usar las uñas o los dientes ¿no?. En todo caso, si lo preferís, bastará con añadir las condiciones: 

```
 PREP CON
 NOUN2 CUCHILLO
```

... después de "AT lDormitorio". 

Además, si forzáis a que escriba "con cuchillo" Es necesario añadir, por supuesto, las palabras del vocabulario necesarias, si no lo están ya. En este caso, debemos comprobar que "con" y "cuchillo" está en la sección de vocabulario, el primero como preposición, y el segundo como nombre. Lo cierto es que ambas están, porque la preposición CON viene ya puesta de serie, y el nombre CUCHILLO lo añadimos cuando pusimos los objetos.

Añadamos justo debajo la entrada para el caso de que el jugador quisiera desatar la funda pero falle en alguna de las condiciones: 

```
DESATAR FUNDA           
 AT lDormitorio
 WRITELN "No puedes desatarlas."
 DONE
```

_Bien, pues aquí termina el tutorial tal y como se creó. Como veis está incompleto, pero espero que haya servido para que tengáis una buena iniciación en la programación en ngPAWS.

Dejamos aquí disponible el [código fuente](http://www.ngpaws.com/wikires/tutorial_la_torre.txp) de esta aventura tal como está.