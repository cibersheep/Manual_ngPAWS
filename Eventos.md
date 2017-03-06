### A veces las cosas simplemente pasan

Quiero decir: el sol sale, llueve, un meteorito cae. En una aventura de texto tambien pasan cosas que nada tienen que ver con lo que hace el jugador. Para manejar este tipo de eventos ngPAWS usa el proceso 2 (/PRO 2)

El proceso 2 es como el proceso 0, y es comprobado después de cada orden de jugador, incluso si la tabla de respuestas acabó con un DONE.

Su función es hacer que cosas ocurran cada turno, o al menos que cada turno se pueda decidir si algo debe pasar.
Generalmente las entradas en el proceso 2 no tienen verbo ni nombre (dos subrayados en su lugar). 

Veamos un ejemplo:


```
_ _
 AT lCamposDeFresas
 CHANCE 1
 WRITE "Ves una estrella fugaz..."
 
```

Fijaros que añadimos un condacto: [CHANCE](CHANCE_ES). Este condacto es una condición, similar a la condicion AT que comprueba si estamos en el campo de fresas, pero en este caso la condicion se cumple aleatoriamente, ese CHANCE 1 indica que hay un 1% de que se cumpla, y por tanto un 1% de que las otras instrucciones, es decir la que escribe el texto "Ves una estrella fugaz", se ejecute.

Al final, cuando estemos en los campos de fresas, hay una posibilidad del 1% de que a cada turno caiga una estrella y la veamos.

### Los jugadores afectan al entorno

A veces los jugadores tienen un efecto sobre el entorno. Por ejemplo , si el jugador rompió el cristal del invernadero, cuando el jugador vuelva a la localidad debería ver que el cristal está roto. El proceso 1 se ejecuta tras la descripción de cada localidad, y permite añadir frases a la descripción que complementan la misma. 


En las sección Proceso 1 (/PRO 1):

```
_ _ 
 AT lInvernadero
 WRITE "Puedes ver restos de cristales en el suelo."
```

Así cada vez que visitemos el invernadero, veremos la descripción del mismo, y justo después aparecerá este texto.

### Procesos de usuario

Aparte de los procesos  1 y 2, un autor puede crear nuevos procesos, simplemente añadiendo secciones(/PRO 3, /PRO 4, etc.), o en Windows usando la opción del menu File para crear un nuevo proceso. Generalmente estos procesos se usan para organizar mejor las respuestas, utilizando el condacto [PROCESS](PROCESS_ES).

Por ejemplo podríamos añadir una entrada en la tabla de respuestas como esta:

```
_ PLATANO
 PROCESS 3
```

Y luego en el proceso 3:

```
COMER PLATANO
 WRITE "¡Buenísimo!"
 DONE

LANZAR PLATANO
 WRITE "Podría ser peligroso."
 DONE
```

### Resumen

El proceso 1 se ejecuta después de cada descripción de localidad, el 2 después de cada orden del jugador, y el 0 o tabla de respuestas evalua las frases del jugador para decidir qué responder.


Para entender como ocurre todo en ngPAWS es mejor echar un ojo al siguiente capítulo.

[Ir al siguiente capítulo: el bucle principal] (El bucle principal)