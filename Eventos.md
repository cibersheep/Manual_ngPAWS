## Eventos

### A veces las cosas simplemente pasan

Quiero decir: el sol sale, llueve, un meteorito cae. En una aventura de texto también pasan cosas que nada tienen que ver con lo que hace el jugador. Para manejar este tipo de eventos **ngPAWS** usa la sección Proceso 2 \(**/PRO 2**\).

El _Proceso 2_ es como el _Proceso 0_ pero se comprueba después de cada orden del jugador, incluso si la tabla de respuestas acabó con un DONE. Su función es hacer que ciertas cosas ocurran cada turno o al menos que cada turno se pueda decidir si algo debe pasar.  
Generalmente las entradas en el _Proceso 2_ no tienen verbo ni sustantivo \(si no dos subrayados en su lugar «\_ _ \__»\).

Veamos un ejemplo:

```
_ _
 AT lCamposDeFresas
 CHANCE 1
 WRITE "Ves una estrella fugaz..."
```

Fíjate que hemos añadido un _condacto_ [CHANCE](CHANCE_ES). Este _condacto_ es una condición, que funciona de forma similar a `AT` \(que comprueba si estamos en el campo de fresas\) pero en este caso, la condición se cumple aleatoriamente. CHANCE 1 indica que hay un 1% de que se cumpla, y por tanto un 1% de que se ejecuten las otras instrucciones, es decir, la que escribe el texto "Ves una estrella fugaz".

Al final, cuando estemos en los campos de fresas, hay una posibilidad del 1% de que a cada turno caiga una estrella y la veamos.

### El jugador afecta al entorno

A veces el jugador tiene un efecto sobre el entorno. Por ejemplo, si rompe el cristal del invernadero, cuando vuelva a esa localidad debería ver que el cristal está roto. El _Proceso 1_ se ejecuta tras la descripción de cada localidad, y permite añadir frases a la descripción que la complementan.

En la sección _Proceso 1_ \(**/PRO 1**\):

```
_ _ 
 AT lInvernadero
 WRITE "Puedes ver restos de cristales en el suelo."
```

Así, cada vez que visitemos el invernadero, veremos su descripción y, justo después, aparecerá el texto «Puedes ver restos de cristales en el suelo.».

### Procesos de usuario

Aparte de los procesos 1 y 2, el autor puede crear nuevos procesos, simplemente añadiendo secciones \(**/PRO 3, /PRO 4,** etc.\), o usando la opción del menú **Proyecto &gt; Nuevo proceso** para crear un nuevo proceso. Generalmente estos procesos se usan para organizar mejor las respuestas, utilizando el _condacto_ [PROCESS](PROCESS_ES).

Por ejemplo, podríamos añadir una entrada en la tabla de respuestas como esta:

```
_ PLATANO
 PROCESS 3
```

Cualquier verbo seguido del sustantivo PLATANO hará que se comprueben todos los _condactos_ del _Proceso 3_. Luego, definimos el _Proceso 3_ como:

```
COMER PLATANO
 WRITE "¡Buenísimo!"
 DONE

LANZAR PLATANO
 WRITE "Podría ser peligroso."
 DONE
```

En el que se comprobará si existe concordancia on el verbo escrito.

### Resumen

El _Proceso 1_ se ejecuta después de cada descripción de localidad, el _Proceso 2_ después de cada orden del jugador, y el _Proceso 0_ o _tabla de respuestas,_ evalúa las frases del jugador para decidir qué responder.

Para entender cómo ocurre todo en **ngPAWS** es mejor echar un ojo al siguiente capítulo.

