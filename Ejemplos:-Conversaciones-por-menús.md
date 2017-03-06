Vamos a ver como podemos hacer una conversación con un NPC en ngPAWS al estilo de las aventuras gráficas (de LucasArts por ejemplo), es decir, por menús. Empezamos por un pequeño glosario:

Glosario

* Menú: Un menú es cada uno de los puntos donde la conversación nos muestra una serie de opciones y debemos elegir una. 

* Opción: Cada una de las frases alternativas que podemos decir en un determinado menú.

* Por facilidad del ejemplo, vamos a asumir que solamente se pueden poner tres opciones por menú

* Usaremos las siguientes constantes,que son los códigos de las teclas 1, 2 y 3 (49,50 y 51 respectivamente)

```
#define const KEY_1 49
#define const KEY_2 50
#define const KEY_3 51
```

* Usaremos un flag para guardar el código de la tecla pulsada:

`#define flg fKey 99`

### Comenzamos

Hagamos una entrada en la tabla de respuestas para cada conversación, y además por cada conversación necesitaremos dos procesos: uno para mostrar los menús y otro para dar las respuestas, en nuestro ejemplo pongamos que son el proceso 9 y el 10.

Por ejemplo:

Respuestas:
```
HABLAR LUIS
 PROCESS 9
 DONE
```


Proceso 9:

```
_ _
CLEAR fKey

; Menu inicial
_ _ 
 WRITELN “1. Hola”
 WRITELN “2. Adiós”
 
_  _
 GETKEY fKey
 PROCESS 10

```

Proceso 10:

```
_ _
 EQ fKey KEY_1
 WRITELN “Dices 'Hola'”
 WRITELN “Luis dice 'Hola'”

_ _
 EQ fKey KEY_2
 WRITELN “Dices 'Adiós'”
 WRITELN “Luis dice 'Adiós amigo'”
 NOTDONE

_ _ 
 PROCESS 9
```

Explicación:

Al entrar en el proceso 9 se nos mostrarán ambas opciones gracias a los dos WRITELN, y tras ello esperaremos la pulsación de una tecla gracias a GETKEY. Obviamente es importante que en nuestras opciones del menú se indique que tecla debe pulsar el jugador para elegir cada opción, o no sabrá que hacer. En nuestro caso hemos puesto 1 y 2.

Tras pasar del GETKEY tenemos en el flag fKey el código de la tecla pulsada, momento en el cual pasamos al proceso 10. En el proceso 100 las dos primeras entradas nos permiten contestar según la opción elegida. Se comprueba la tecla pulsada, y se escribe la contestación correspondiente. La segunda opción acaba con NOTDONE, lo cual impide que se llegue a la tercera entrada, que nos devuelve al proceso 9 y se muestre de nuevo el  menú, es decir es opción es una opción de salida del sistema de menús ("Adiós"). En resumen, el “Hola” vuelve al menú, mientras que el “Adiós” nos saca de la conversación.

Finalmente, en prevención de que alguien pulse una tecla que no sea una de las opciones, si así ocurre, volvemos a empezar el proceso de todos modos forzando así que se vuelva a escribir el mismo menú.


### Doble menú

Vamos a hacer una convesación un poco más complicada, usando dos menús, empecemos por poner un par de constantes para entender las cosas mejor, y vamos a usar un flag para guardar el número de menú en el que estamos:

```
#define CONST MENU_INICIAL 0
#define CONST MENU_SECUNDARIO  1

#define flg fMenu 100
```

Vamos con el proceso 9:

```
_ _
 CLEAR fKey

; Menu inicial
_ _ 
 EQ fMenu MENU_INICIAL
 WRITELN “1. Hola”
 WRITELN “2. Adiós”
 WRITELN ”3. ¿Hablas inglés?”

; Otro Menu 
_ _ 
 EQ fMenu MENU_SECUNDARIO 
 WRITELN “1. Hello”
 WRITELN “2. Good Bye”
 WRITELN ”3. Mejor en español por favor”
 
_  _
 GETKEY fKey
 PROCESS 10


```

Y en el proceso 10

```
; Menu inicial
_ _
 EQ fMenu MENU_INICIAL
 EQ fKey KEY_1
 WRITELN “Dices 'Hola'”
 WRITELN “Luis dice 'Hola'”


_ _
 EQ fMenu MENU_INICIAL
 EQ fKey KEY_2
 WRITELN “Dices 'Adiós'”
 WRITELN “Luis dice 'Adiós amigo'”
 NOTDONE


_ _
 EQ fMenu MENU_INICIAL
 EQ fKey KEY_3
 WRITELN “Dices '¿Hablas inglés?”
 WRITELN “Luis dice 'Yes, I do.''”
 LET fMenu MENU_SECUNDARIO  ; ¡Cambiamos de menú!

; Otro Menu 
_ _
 EQ fMenu MENU_SECUNDARIO
 EQ fKey KEY_1
 WRITELN “Dices 'Hello'”
 WRITELN “Luis dice 'Hello'”
 
_ _
 EQ fMenu MENU_SECUNDARIO
 EQ fKey KEY_2
 WRITELN “Dices 'Good Bye'”
 WRITELN “Luis dice 'Good bye my friend'”
 NOTDONE

_ _
 EQ fMenu MENU_SECUNDARIO
 EQ fKey KEY_3
 WRITELN “Dices '¿Mejor en español por favor'”
 WRITELN “Luis dice 'Vale.''”
 LET fMenu MENU_INICIAL 

_ _ 
 PROCESS 9

````

Bueno, aquí tenemos dos menús, controlados por el flag fMenu, que por defecto vale 0, por lo que la primera vez que entremos a la conversación se llegará al menú inicial. Como se puede ver, al elegir las distintas opciones, si elegimos la opción 3 del menú principal, además de contestar cambiamos el valor de fMenu. Así, al hacer el llegar de nuevo al proceso 9, no volveremos a entrar en el mismo menú, sino que entraremos en el secundario. Lo mismo ocurre con la opción 3 del menú secundario, de elegirla nos llevará de vuelta al menú principal.

Si os fijáis, al salir con la opción 2 del menú secundario, no restablecemos el valor del flag fMenu a 0 (MENU_INICIAL) por lo que salvo que lo hagamos desde fuera, la próxima vez que hablemos con este PSI, se entrará directamente en el menú secundario. De no quererlo así, antes del NOTDONE, deberíamos hacer un LET fMenu MENU_INICIAL.

### Opciones opcionales

Es posible que en algunos casos, la aparición de una opción concreta dependa de cosas externas. Por ejemplo no debería aparecer una opción para preguntarle a Luis por una determinada planta, hasta que la encontramos. En esos casos es perfectamente posible poner opciones condicionales, por ejemplo así


```
_ _ 
 EQ fMenu MENU_INICIAL
 WRITELN “1. Hola”
 WRITELN “2. Adiós”

_ _ 
 EQ fMenu MENU_INICIAL
 CARRIED oPlantaEnigmatica
 WRITELN "3. ¿Sabes qué es esta planta?"
```

Como véis, las opciones 1 y 2 son fijas, pero la 3 solo sale si llevamos la planta

En el proceso 10 tendríamos que hacer algo como esto:

```
_ _
 EQ fMenu MENU_INICIAL
 EQ fKey KEY_3
 CARRIED oPlantaEnigmatica
 WRITELN “Dices '¿Sabes qué es esta planta?”
 WRITELN “Luis dice 'Es mandrágora.''”
 DESTROY oPlantaEnigmatica
 PLACE oPlantaMandragora 254
```

Así cuando Luis nos informa que nuestra planta es mandrágora, cambiamos el objeto planta enigmática por el objeto mandrágora en nuestro inventario. Fijaos que en la respuesta también pongo la condición de "CARRIED", para evitar que el jugador haga trampas pulsando opciones imposibles "a ver que pasa" (o simplemente pulse 3 por error cuando no hay opcion 3)


