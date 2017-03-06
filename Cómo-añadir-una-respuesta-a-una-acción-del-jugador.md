**_Quiero que si el jugador escribe tal pase cual..._**

Si quieres añadir una respuesta a una frase del jugador, deberás añadirla en la tabla de respuestas (RESP), en la cual te encontrarás ya un montón de respuestas que están "precocinadas" para que no tengas tú que poner las respuestas para las acciones más comunes. Para añadir tus propias respuestas solo tienes que buscar en esa sección un sitio donde pone "Aquí puedes añadir tus propias respuestas",  y escribir debajo de eso.

Una respuesta puede ser a una frase con un verbo (COCINAR) o con verbo + nombre (COCINAR HUEVOS). Pongamos por ejemplo que queremos dar una respuesta a "COCINAR HUEVOS", ponemos lo siguiente:

```
COCINAR HUEVOS
 WRITELN "Te pones a cocinar y haces un par de huevos fritos."
 DONE
```

Como veis, primero ponemos la frase que queremos que diga el jugador, y después ponemos unas órdenes ([[condactos]]). En concreto [[WRITELN|WRITELN_ES]] escribe el texto entre comillas y [[DONE|DONE_ES]] le dice al parser que ya está contestado el jugador, que ya no tiene que mirar más a ver si hay otra respuesta.

**_Pero... ¿y si el jugador no lleva los huevos?_**

Pues para eso hay otro condacto, una condición, llamada [[CARRIED|CARRIED_ES]]:

```
COCINAR HUEVOS
 CARRIED oHuevos
 WRITELN "Te pones a cocinar y haces un par de huevos fritos."
 DONE
```

Ahora pasará lo mismo, pero [[CARRIED|CARRIED_ES]] es una condición que solo se cumple si el jugador lleva el objeto correspondiente, y si no se cumple, ninguna de las órdenes que hay detrás (WRITELN y DONE) se ejecutarán, y como consecuencia ni se escribirá el texto, ni se marcará la frase como contestada, con lo cual al final el jugador verá el mensaje "No puedes hacer eso".

**_Pues he puesto eso pero me dice que no entiende la palabra COCINAR_**

Eso es porque como cuando [[definíamos los objetos|Cómo definir objetos para las aventuras]], es necesario añadir tanto COCINAR como HUEVOS al vocabulario.

**_¿y si mi frase no lleva nombre sino solo un verbo?_**

Pues muy fácil, sustituimos el nombre por un símbolo de subrayado (guion bajo), así:

```
COCINAR _
 WRITELN "No te apetece ponerte a cocinar sin objetivos."
 DONE
```
**_¿y como hago para que si ponen COCINAR a secas les diga una cosa y si ponen COCINAR HUEVOS les diga otra?_**

Pues muy sencillo, poniendo una "entrada" detrás de otra:

```
COCINAR HUEVOS
 CARRIED oHuevos
 WRITELN "Te pones a cocinar y haces un par de huevos fritos."
 DONE

COCINAR _
 WRITELN "No te apetece ponerte a cocinar sin objetivos."
 DONE
```

Fijaos que pongo primero la de "COCINAR HUEVOS" porque las entradas se ejecutan en orden, y si la pongo delante y el jugador escribe "COCINAR HUEVOS" entraría en esa entrada, pondría que no te apetece y haría un DONE, y DONE hace que no siga mirando más entradas así que nunca llegaría a la de COCINAR HUEVOS.

Con las entradas tal y como están, si el jugador escribe COCINAR HUEVOS y los lleva, saldrá el mensaje de los huevos fritos, si no los lleva o escribe COCINAR a secas, o incluso COCINAR FILETES, saldría el de que no te apetece.


