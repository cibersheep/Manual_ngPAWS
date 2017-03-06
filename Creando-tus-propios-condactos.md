Para crear nuevos condactos necesitarás:

1. Saber programar en javascript
2. Conocer que funciones te facilita ngPAWS (si necesitas trabajar con las localidades, objetos, etc.)

Para crear un condacto nuevo , simplemente crea un fichero en la carpeta "jsl"  (javascript libraries) de la instalación de ngPAWS, llamado igual que el condacto, y con la extensión "jsp" (javascript plugin). Desde la beta 6 de ngPAWS también puedes crear una carpeta "jsl" dentro de la carpeta del juego en cuestión, y crear el fichero en su interior. La diferencia es que si lo creamos en la carpeta de ngPAWS el plugin se añadirá a todas las aventuras, lo usemos o no lo usemos, mientras que si lo añadimos en la carpeta del juego, solo se añadirá a ese juego en cuestión.

Veamos un ejemplo del contenido de uno de esos ficheros:

```
//CND EJEMPLO A 0 0 0 0

function ACCejemplo()
{
   // Hacer algo aquí
}
```

La primera línea es la cabecera, que debe ser un comentario en javascript con doble contrabarra, seguido de los caracteres CND (condacto). Justo después, en letras mayúsuculas, el nombre del condacto, seguido de una A si se trata de una acción, o una C si es una condición. También puedes poner una W si el condacto es de tipo 'waitkey' (ver más adelante). Le siguen el tipo de los parámetros de la función, siendo 0 el que indica que no hay parámetro.

Añadiremos un 0 más al final en todos nuestros condactos de usuario.

Tras la cabecera, debe haber una función cuyo nombre empiece por ACC si es una accion o CND si es una condición, seguido del nombre del condacto en minúsculas. Si el condacto es una condición, la función debe devolver true o false.

En el ejemplo anterior el condacto no hace nada y no tiene parámetros. Veamos uno un poco más complicado:


```
//CND ADDSUM A 1 2 2 0

function ACCaddsum(flagno, value1, value2)
{
 setFlag(flagno, value1+value2)
}
```

En este caso la suma del valor 1 y el valor 2 se almacena en el flag "flagno".

Estos son los diferentes tipos para los parámetros. Si tienes alguna duda, en la carpeta jsl de ngPAWS hay decenas de condactos plugins que puedes mirar. Además, en condacts.js verás los condactos base de ngPAWS.


|Tipo| Función|
|---|----|
|0 | sin parámetro|
|1 | flagno|
|2 | valor |
|3 |porcentaje|
|4 |objno|
|5 |mesno|
|6|sysno|
|7|procno|
|8|locno|
|9|locno+|
|10|adjetivo|
|11|adverbio|
|12|preposición|
|13|nombre|
|14|string|
|15|verbo|

Notas importantes:

* Todo el contenido del fichero del condacto es añadido al juego. Si necesitas variables globales para ti condacto, funciones auxiliares o lo que sea lo puedes añadir antes o después de la funcion ACCxxxxx() o CNDxxxx() * Cuando crees nuevos condactos, trata de usar las funciones estándar facilitadas por runtime.js (ver abajo)
* Trata de no hacer los condactos intensivos en uso de CPU.
* Si tus condactos contienen datos que necesitan ser grabados cuando se graba la partida, echale un ojo a la seccion [hooks] (Hooks_ES).
* En general, trata no acceder a objetos, localidades, flasg leyendo directamente los arrays que contienen sus datos. Ha varias funciones creadas para hecer eso, y aunque ahora no hacen nada en especial (la función setFlag se limita a grabar el valor en el flag) en el futuro podrían hacer algo diferente, y tu plugin puede quedar anticuado o ser incompatible.

### Funciones útiles

|función|útil para|
|----|----|
|getFlag(flagno)| obtiene el valor de un flag|
|setFlag(flagno, value)| establece el valor de un flag|
|loc_here()|obtiene la localidad actual del jugador|
|setConnection(locno1, dirno, locno2)| establece la localidad desde locno1 a locno2 via la dirección dirno|
|getConnection(locno, dirno)|obtiene la conexión entre de la localidad locno en la dirección dirno|
|filterText(text)|aplica los tags de secuencia a un texto|
|writeText(text)|escribe texto|
|writelnText(text)|excribe texto, luego un retorno de carro|
|writeText(filterText(text))|escribe el texto, sustituyendo secuencias de escape|
|writeObject(objno)|escibre la descripción del objeto objno tal|
|writeText(getObjectFixArticles(objno))| escribe la descripción del objeto objno, remplazando el artículo indeterminado por determinado (Ej. "una llave"-->"la llave")|
|writeLocation(locno)|escribe el texto de descripción del la localidad locno|
|clearScreen()|borra la pantalla|
|getResourceById(resource_type, id)| obtiene el nombre de fichero para el recurso id, o false si no existe|
|objectIsNPC(objno)|devuelve true si el objeto objno es un NPC|
|objectIsLight(objo)|devuelve true si el objeto objno es una fuente de luz|
|objectIsWearable(objo)|devuelve true si el objeto objno es una prenda|
|objectIsContainer(objo)|devuelve true si el objeto objno es un contenenedor|
|objectIsAttr(objno, attrno)| devuelve true si el objeto objno tiene el atributo especificado|
|setObjectLowAttributes(objno, attrs)|establece los primeros 32 atirbutos de un objeto todos de una vez|
|setObjectHighAttributes(objno, attrs)|establece los segundos 32 atirbutos de un objeto todos de una vez|
|getObjectLowAttributes(objno)|obtiene los primeros 32 atirbutos de un objeto todos de una vez|
|getObjectHighAttributes(objno)|obtiens los segundos 32 atirbutos de un objeto todos de una vez|
|getObjectLocation(objno)|obtiene la localidad de un objeto|
|setObjectLocation(objno, locno)|mueve un objeto a una localidad dada|
|getObjectWeight(objno)|obtiene el peso de un objeto|
|getNextFreeAttribute()|obtiene el número del primer atributo de objeto no usado (*)|

Hay más, si quieres saber de todos mira en runtime.js para más información. También recuerda que puedes llamar a cualquier condacto existente llamando a su función (CNDat, CNDcarried, ACCprint, ACCoset, etc.)

(*) Esta función es bastante útil para implementar una librería plugin que incorpore un nuevo atributo de objeto. Si tu librería va a manejar un nuevo atrubuto (por ejemplo a Big para objetos grandes) y haces que el atributo aBig sea el 44, ¿que pasaría si otra librería decide usar el mismo? La solución es que la librería llame a esta funcion que le da un atributo libre, y la otra librería si hace lo mismo se asegurará de que no sea el mismo.

### Condactos Waitkey

Los condactos waitkey son condactos que esperan una pulsación de tecla. Son considerados acciones, por lo que la función debe comenzar por ACC. El condacto plugin ASK es un buen ejemplo de este tipo de condactos.