## Creando puzles sin programar con ngPAWS

Este artículo pretende ilustrar como conseguir crear puzles para nuestra aventura sin programar, por medio del Asistente de Puzles de ngPAWS. Para ello pondremos dos ejemplos en dos capítulos: como extraer un refresco de una máquina de refrescos, y como abrir una trampilla que está cerrada con llave.

### El puzle del refresco

Bien, lo primero que necesitamos es decidir como va a funcionar el puzle, y esta es la definición: “El jugador deberá introducir o meter una moneda en la ranura de la maquina, por lo cual, el modo de resolver el puzle será [METER MONEDA EN RANURA]. “. Bien, esta es la definición del puzle, pero hay determinadas cosas que están implícitas que conviene detallar:

* Debemos llevar la moneda
* Debemos estar en la misma localidad de la máquina para poder usarla

Vamos a dar por supuesto que las palabras necesarias ya existen en el vocabulario (meter, introducir, ranura, moneda, refresco), que “meter” es sinónimo de “introducir”, y que estamos usando identificadores de txtpaws para los objetos, por lo que podremos referirnos a la moneda por “oMoneda”, al refresco como “oRefresco”  y a la localidad de la maquina como “lMaquina”.

Lo primero que tenemos que hacer es ir a la table de respuestas, y en el sitio donde queramos colocar el puzzle, hacer click con el botón derecho, y seleccionar la opción "Asistente de puzles". Se abrirá la ventana del asistente. Lo normal es buscar en la tabla de respuestas la zona donde pone 

```;  ********** [[[  Coloca aqui tus propias respuestas  ]]] ************```

y colocarlo allí mismo. Ten en cuenta que algunos puzles deberán preceder a otros en orden, si están relacionados, porque lo primer que se encuentre es lo primero que se ejecuta.

![Menú contextual](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_1.png)

Dicho asistente se rellenará en cuatro pasos, tras cada uno de los cuales tenemos que pulsar en "siguiente" (o en finalizar en el último de ellos). Los pasos son los siguientes:

1) Condiciones de vocabulario y localidad: en esta solapa se marcan las condiciones necesarias para que el puzle pueda ser realizado con éxito por el jugador, que están basadas en las órdenes que da el jugador o en la localidad en que está.
2) Condiciones adicionales: otras condiciones necesarias (como que se lleve un objeto, que esté presente, que un flag valga tal, etc.)
3) Acciones: acciones que van a ocurrir cuando el jugador realice el puzle con éxito y texto que se muestra.
4) Código y finalización. Aquí puedes ver el código generado y copiarlo, o bien simplemente dar a "Finalizar" para que se copie en tu aventura.

### Condiciones de vocabulario y localidad

Veamos como rellenamos esta primera pantalla: hemos quedado que el puzle requiere que escribamos “METER MONEDA EN RANURA”, por lo cual vamos a rellenar el campo “Verbo” con “METER”, el campo “Nombre” con “MONEDA”, el campo preposición con “EN” y el campo “Otro nombre” con “RANURA”. Para rellenar las dos últimas opciones hay que marcar primero la casilla de “Requiere preposición” y “Requiere 2º nombre”.

Por último, dijimos como condición que para poder meter la moneda en la máquina es requisito indispensable que estemos en la localidad de la máquina, así que añadimos la condición de localidad: marcamos “Puzle ligado a localidad” y ponemos “lMaquina” en el campo “Localidad”. También ponemos “¿Dónde quieres meter la moneda?” en el campo “Texto en caso de falla” (que corresponde al texto a mostrar si no estamos en la localidad).

![Condiciones de vocabulario y localidad](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_2.png)

### Otras condiciones

Hemos quedado en que es necesario tener la moneda para poder realizar el puzle, con lo cual vamos a añadir una condición de objeto llevado. Para ello en el desplegable elegimos "El jugador lleva el objeto...", y añadimos “¿Qué moneda?” en el campo "texto en caso de fallo", y "oMoneda" en el campo "Objeto". Seguidamente pulsamos "Añadir", y veremos como la condición aparece al lado de derecho.

Dicha condición puede borrarse seleccionandola en la lista de la derecha y haciendo click con el botón derecho, y también puede subirse o bajarse en la lista si tenemos más de una condición, y queremos que una se evalue antes que otra (no es el caso en nuestro ejemplo)

![Otras condiciones](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_6.png)

Obviamente, si no estamos usando identificadores de txtpaws siempre podemos poner el número de objeto, o el de localidad en el paso anterior.

### Acciones

Ya tenemos todas nuestras condiciones, vamos a pasar a las acciones. Cuando metemos la moneda y por tanto hay éxito en el puzle lo que tiene que pasar son dos cosas:

* La moneda debe desaparecer
* El refresco debe aparecer

De la misma manera que en el caso anterior, seleccionamos "El objeto <...> aparece", y ponemos "oRefresco" en el campo. Seguidamente pulsamos "Añadir" para colocar la acción en la lista de la derecha.

Después, seleccionamos "El objeto <...> desaparece" y ponemos "oMoneda" en el campo, y le damos a añadir.

Finalmente, rellenamos el campo "texto cuando se tiene éxito", que mostrará al jugador un mensaje, con el texto "Metes la moneda en la ranura y una lata de refresco cae de la misma".

![Acciones](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_3.png)

### Éxito y generación de código

En la última solapa simplemente podemos ver una vista previa del código generado, y al dar a finalizar se añadirá a nuestra tabla de respuestas.

![Finalizar](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_4.png)

**Importante:** Cuando ngPAWS añade el código a la tabla de respuestas, observaremos que todas las posibilidades se han tenido en cuenta y se ha generado nuestro código, pero además se añaden dos comentarios sobre el mismo y bajo el mismo:

![Comentarios](http://www.ngpaws.com/wikires/puzzlegen_new/puzzlegen_es_5.png)

Esos comentarios no debemos borrarlos, porque en cualquier momento, si hacemos click en el token (ese montón de letras y números) para que el cursor se quede en cualquier parte del mismo, y luego click derecho sobre el mismo, seleccionando entonces el asistente, este se abrirá con los datos del puzzle en cuestión, permitiéndonos editarlo, y al dar a finalizar, si hicimos cambios, el código entre ese token y la marca de fin de puzzle del comentario inferior, será modificado de acuerdo a los cambios.

Por esa misma razón no debe modificarse el código del puzzle a mano, porque si se hace y después abrimos el asistente con el token, este retomaría el código original y perderíamos los cambios.


[[Siguiente capítulo|El generador automático de puzles- Segunda parte]]