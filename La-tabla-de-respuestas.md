# La tabla de respuestas

**ngPAWS** facilita un sencillo lenguaje de programación para que puedas generar las respuestas que dará el sistema al jugador. Si programar no es lo tuyo, siempre puedes usar \[\[el asistente de puzles\]\], que te permitirá añadir puzles pero **ngPAWS** programará por ti \(tú solo tienes que decirle qué condiciones deben cumplirse para que el jugador tenga éxito y qué hacer si lo tiene\).

El _asistente de puzles_ es válido tanto para personas que no sepan programar como para personas que sí sepan pero prefieran un método más cómodo. Aun así, es posible hacer cosas más sofisticadas programando, por lo que te recomendamos que le eches un ojo y verás que no es tan difícil como te imaginas.

Algunos de los capítulos siguientes se dedicarán a aprender a «programar» con **ngPAWS,** empezando por la tabla de respuestas, que es donde se definen las respuestas que se dan a las órdenes del jugador: Para ello debes añadir entradas a la _tabla de respuestas_ \(**/PRO 0** si estás mirando el fichero desde un editor de texto\).

En [la base de datos de inicio](/la-base-de-datos-de-inicio) observarás que ya hay un montón de código en esa sección, y es así porque ya hay muchas de las respuestas prefijadas por el sistema que evitan que tengas que prepararlas tú para las acciones más básicas \(tomar, dejar, abrir, saltar, escuchar, romper, etc.\). Por supuesto, esas respuestas por defecto son genéricas y probablemente tendrás que cambiarlas para algunos juegos o historias. Por ejemplo, la respuestas por defecto para atacar a algo o a alguien es «La violencia no es la solución» pero si en tu juego el protagonista es un guerrero que debe matar varios trasgos, probablemente esa respuesta por defecto no es muy adecuada.

Por ahora, busca en dicha sección una linea que tiene este aspecto:

`;  ********************* [[[  Coloca aquí tus propias respuestas  ]]] *********************`

Justo debajo de esa línea, puedes añadir tus respuestas pero ¿cómo?

Veamos este código:

```
ROMPER CRISTAL
 AT lInvenadero
 WRITELN "Rompes el cristal y este salta en pedazos."
 DONE
```

Cuando **ngPAWS** recibe la orden del jugador «rompe el cristal», obtendrá una frase cuyo verbo es ROMPER y cuyo nombre es CRISTAL, y empezará a revisar por orden la tabla de respuestas hasta encontrar una entrada que precisamente empiece así «ROMPER CRISTAL», como la que hemos puesto arriba, y solo en ese caso empezará a ejecutar las líneas que hay debajo de dicha entrada, también por oden: Primero `AT lInvernadero`, etc.

### Los _condactos_

Los _condactos_ \(condición-acciones, **cond**ition-**act**ions\) de **ngPAWS** son una manera de que puedas realizar ciertas acciones bajo ciertas condiciones. En el ejemplo de arriba, el sistema primero comprobará si el jugador está en el invernadero \(`AT lInvernadero`\), si es así , escribirá \(`WRITELN`\) el texto «Rompes el cristal y este salta en pedazos.» y finalmente, el _condacto_ DONE \(_hecho,_ en inglés\) le indica a **ngPAWS** que ya se ha terminado de responder al jugador y no tiene que buscar más entradas que correspondan con ROMPER CRISTAL. Si no hubiera un DONE, el sistema seguiría buscando más _condactos._

Hay muchos _condactos_ en **ngPAWS** pero no es muy adecuado leérselos todos de tira, si no que es mejor ir entendiéndolos con ejemplos.

**Importante: **las entradas en la _tabla de respuestas_ pueden contener un verbo y un nombre, solo un verbo, solo un nombre o incluso ninguno de los dos. Cualquiera de las dos partes puede ser sustituida por un símbolo de subrayado «\_», y su presencia indica que cualquier palabra podría valer para acceder a esa entrada.

Por ejemplo:

```
LLORAR _ 
 WRITELN "Lloras sin esperanza."
 DONE

_ PLATANO
 WRITELN "Hmmmm... adoras los plátanos, ¡ojala tuvieras uno a mano!."
 DONE
```

La primera entrada será ejecutada si el jugador escribe LLORAR pero también si pone LLORAR INTENSAMENTE o LLORAR COMO SI ACABARA DE NACER, incluso si el jugador pone un sinsentido como LLORAR PLÁTANOS, funcionaría.  
La segunda entrada funcionaría tanto si el jugador pone COGER PLÁTANO, como si escribe TIRAR PLÁTANO o simplemente PLÁTANO. Si el jugador escribiera LLORAR BANANA, se ejecutaría la primera entrada pero la segunda no, porque al ejecutarse la primera y llegar al DONE, el sistema no seguiría mirando más entradas.

