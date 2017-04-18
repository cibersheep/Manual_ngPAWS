# La tabla de respuestas

**ngPAWS** facilita un sencillo lenguaje de programación para que puedas generar las respuestas que dará el sistema al jugador. Si programar no es lo tuyo, siempre puedes usar \[\[el asistente de puzles\]\], que te permitirá añadir puzles pero **ngPAWS** programará por ti \(tú solo tienes que decirle qué condiciones deben cumplirse para que el jugador tenga éxito y qué hacer si lo tiene\).

El _asistente de puzles_ es válido tanto para personas que no sepan programar como para personas que sí sepan pero prefieran un método más cómodo. Aun así, es posible hacer cosas más sofisticadas programando, por lo que te recomendamos que le eches un ojo y verás que no es tan difícil como te imaginas.

Algunos de los capítulos siguientes se dedicarán a aprender a «programar» con **ngPAWS,** empezando por la tabla de respuestas, que es donde se definen las respuestas que se dan a las órdenes del jugador: Para ello debes añadir entradas a la _tabla de respuestas_ \(**/PRO 0** si estás mirando el fichero desde un editor de texto\).

En la base de datos de inicio observaréis que ya hay un montón de código en esa sección, y es así porque ya hay un montón de respuestas prefijadas por el sistema, que evitan que tengamos que preparar respuestas para las acciones mas básicas \(tomar, dejar, abrir, slatar, escuchar, romper, etc.\). Por supuesto esas respuestas por defecto son genéricas, y probablemente tendréis que cambiarlas para algunos juegos/historias. Por ejemplo, la respuestas por defecto para atacar algo o alguien es "la violencia no es la solución", pero si en vuestro juego el protagonista es un guerrero que debe matar varios trasgos, probablemente esa respuesta por defecto no es muy adecuada.

Por ahora, busquemos en dicha sección una linea que tiene este aspecto:

`;  ********************* [[[  Coloca aqui tus propias respuestas  ]]] *********************`

Justo debajo de esa línea, puedes añadir tus respuestas, pero ¿Cómo?

Veamos este código:

```
ROMPER CRISTAL
 AT lInvenadero
 WRITELN "Rompes el cristal y este salta en pedazos."
 DONE
```

Cuando ngPAWS recibe una orden del jugador como "rompe el cristal", obtendrá una frase cuyo verbo es ROMPER y cuyo nombre es "CRISTAL", y empezará a revisar la tabla de respuestas hasta encontrar una entrada que precisamente empiece así "ROMPER CRISTAL", como la que hemos puesto arriba, y solo en ese caso empezará a ejecutar las lineas que hay debajo de dicha entrada.

### Los condactos

Los condactos de ngPAWS \(condiciones y acciones\) son una manera de que puedas hacer ciertas acciones bajo ciertas condiciones. En el ejemplo de arriba el sistema primero comprobará si el jugador está en el invernadero \(AT lInvernadero\), si es aí , escribirá el texto "Rompes el cristal y este salta en pedazos." y finalmente el condacto DONE le indica a ngPAWS que ya se ha terminado de responder al jugador y no tiene que buscar más entradas que cuadren con ROMPER CRISTAL. Si no hubiera un DONE el sistema seguiría buscando más entradas.

Hay muchos condactos en ngPAWS, y aunque puedes verlos todos en la referencia que veis en el menú de la derecha \(enlaces rápidos\), no es muy adecuado leerselos todos, sino que es mejor ir entendiéndolos con ejemplos.

Importante: las entradas en la tabla de respuestas pueden contener un verbo y un nombre, solo un verbo, solo un nombre, o incluso ninguno de los dos. Cualquiera de las dos partes puede ser sustituida por un símbolo de subrayado "\_", y su presencia indica que cualquier palabra podría valer para acceder a esa entrada.

Por ejemplo:

```
LLORAR _ 
 WRITELN "Lloras sin esperanza."
 DONE

_ PLATANO
 WRITELN "Hmmmm... adoras los plátanos, ¡ojala tuvieras uno a mano!."
 DONE
```

La primera entrada será ejecutada si el jugador escribe "LLORAR", pero tambien si pone "LLORAR INTENSAMENTE", o "LLORAR COMO SI ACABARA DE NACER", incluso si el jugador pone un sinsentido como "LLORAR PLATANOS" funcionaría.  
La segunda entrada funcionaría tanto si el jugador poner COGER PLATANO, como si pone TIRAR PLATANO o simplemente PLATANO. Si el jugador escribiera "LLORAR BANANA" se ejecutaría la primera entrada, pero la segunda no, porque al ejecutarse la primer y llegar al DONE, el sistema no seguiría mirando más entradas.

\[Ir al siguiente capítulo: Eventos\] \(Eventos\)

