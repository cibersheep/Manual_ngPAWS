txtpaws es una herramienta incluida en el paquete de Superglús, que permite definir identificadores para referirnos a los objetos, localidades, flags, etc. mediante nombres y no mediante números.

En el PAWS clásico, había que hacer referencia a todo por el número (localidad 8, flag 102, objeto 4, etc.), pero usando txtpaws eso no es necesario.

Por ejemplo, si al principio del fichero .txp escribes:

`##define loc lPuente 12`

más tarde puedes hacer:

`AT lPuente` en lugar de  `AT 12`

o puedes añadir esto en las sección de conexiones:

`N lPuente`

Esto hará tu código:

* más fácil de escribir
* más fácil de entender si un día tienes que modificar algo

### ¿Qué puedo definir con los identificadores de txtpaws?

* Localidades: `##define loc lPuente 12`
* Flags: `##define flg fDragonEsLibre 129`  y mas tarde hacer `NOTZERO fDragonEsLibre` para comprobar si el dragón ha sido liberado.
* Objetos: `##define obj oLlavero 7` y más tarde hacer `CARRIED oLlavero`  para comprobar si el jugador lleva el llavero.
* Constantes: a veces usas un valor en muchos sitios, por ejemplo el máximo de oro que un jugador puede llevar. Si más tarde decides cambiar el máximo de otro, tienes que buscar por todas partes donde pusiste ese valor (donde el jugador gana oro, lo roba, encuentra tesoros, vende algo, etc.) para cambiarlo. Para evitar eso puedes hacer `##define const MAXIMO_ORO 100`, y usar MAXIMO_ORO donde fueras a poner ese 100. Si más tarde decides cambiar 100 por 150 o por 35, solo tendrás que cambiar la linea a `##define const MAXIMO_ORO 150` o `##define const MAXIMO_ORO 35`

### Recursos multimedia

txtpaws también puede usarse para definir recursos multimedia que puedan usarse después. Estos son los tipos que pueden crearse:

* Gráfico de localidad: `##define pic loc1.jpg 1` donde "1" es el la localidad a la que corresponde loc1.jpg
* Gráfico suelto: `##define grf escena.gif 1` donde "1" es cualquier número, pero diferente por cada gráfico suelto.
* Música de localidad: `##define msc loc1.ogg 1` donde 1 es la localidad donde debe reproducirse dicha música.
* Música o efecto de sonidos sueltos: `##define sfx rugido.mp3 1` donde 1 es cualquier número, pero diferente para cada efecto.

Para que estos identificadores funcionen, tienes que poner los ficheros en la carpeta "dat" que hay en la carpeta donde está el fichero .txp de tu aventura.

Notese que debido a las diferencias en relación a la reproducción de músicas y efectos entre los distintos navegadores, no todos los navegadores aceptan ficheros ogg o mp3. Por ello, si quieres que la música y efectos suenen en todos los navegadores (al menos en los más habituales: Internet Explorer, Firefox, Safari, Chrome y Ópera) añade cada música y efecto en los dos formatos (ogg y mp3) y ngPAWS se encarga de reproducir el que corresponda (es decir, aunque le digas que reproduzca el ogg, si el navegador no soporta ogg pero sí mp3, reproducirá el mp3, y viceversa). Si solo hay un formato intentará reproducir el que haya, y si el navegador no lo soporta no sonará nada.

### ¿Dónde puedo definir los identificadores?

En cualquier sitio en el fichero txp, aunque se recomienda que se haga al principio y agrupando objetos, localidades, etc. Los identificadores solo pueden usarse después de ser definidos.

### ¿Cuando serán ignorados los identificadores?

Cuando:

* Están dentro de una cadena entre comillas (por ejemplo en un [WRITE](WRITE_ES)
* Como efecto colateral de lo anterior, no puedes usar identificadores en los [tags de secuencia](tags de secuencia).

### ¿Por qué pones esos identificadores tan extraños en los ejemplos? (oLlavero, lPuente)

Es una convención, los objetos empiezan por 'o', las localidades por 'l', los flags por 'f' y las constantes en mayúsculas. ¿Por qué? Bueno, es una costumbre, si no te gusta no tienes por que usarla, pero hace tu código más fácil de entender.