En cualquier mensaje de nfPAWS, independientemente si es un texto de localidad, objeto, mensaje, textos ecritos con [WRITE](WRITE_ES), etc. se pueden incluir tags de secuencia. Un tag de secuencia es un grupo de caracteres especials que cuando van a ser escritos se convierten en otra cosa.

Por ejemplo, solo tenemos un mensaje para cuando se va a tomar un objeto ("Tomas "), pero ese mensaje esta en realidad definido como "Tomas {OREF}.", y cuando va a ser impreso ese {OREF} es sustituido por la descripción del objeto referenciado por la sentencia actual. Así, si pusimos "TOMAR LLAVE" el objeto referenciado es la llave, y la descripción de la llave es "una llave" por lo que el mensaje escrito es "Tomas una llave."

Aquí hay una tabla con las diferentes tags de secuencia disponibles, cada una ilustrada con un ejemplo. Los tags de secuencia pueden ser anidados, sigue leyendo para entender qué quiere decir eso:

| TAG DE SECUENCIA        | DESCRIPCION           |
| ------------- |-------------|
|{URL&#124;http://www.caad.es &#124;CAAD} muestra un link a CAAD con el texto "CAAD" que abre en otra pestaña o ventana del navegador|
| {CLASS&#124;testclass&#124;hola} | mustra el texto "hola" usando la clase css "testclass" |
| {STYLE&#124;display:block;margin:3px&#124;hola}| muestra el texto "hola" usando CSS inline "display:block;margin:3px"|
| {INK&#124;red&#124;hola} | muestra el texto "hola" usando el color rojo. Puedes usar cualquier color CSS (tnto usando nombres de color como red, blue, yellow o usando un color descrito mediante RGB como #77AA89). Para dealles sobre los colores en HTML/CSS ver: http://www.w3schools.com/cssref/css_colornames.asp y http://www.w3schools.com/cssref/css_colors.asp|
| {PAPER&#124;blue&#124;texto} | similar a INK pero para el color de fondo|
| {FLAG&#124;38} | displays flag flagno value .|
| {OREF} | Muestra el objeto referenciado por la orden del jugador actual. Por compatibilidad hacia atras con PAWS también puede usarse el caracter subrayado '_' pero no se recomienda.|
| {OBJECT&#124;flagno} | Muestra el objeto referenciado por el contenido del flag flagno. Notese que debe expresarse por el número (no pueden usarse identificadores [txtpaws](txtpaws_es)). {OREF} is es un atajo para poner {OBJECT&#124;51} , dado que el flag 51 contiene el número de objeto referenciado por la sentencia actual|
| {WEIGHT&#124;flagno} | muestra el peso del objeto referenciado por el flag flagno|
| {OLOCATION&#124;flagno} | muestra la localidad actual del del objeto referenciado por el flag flagno|
| {LOCATION&#124;flagno} | muestra la descripcion de la localidad actual del objeto referenciado por el flag flagno|
| {MESSAGE&#124;flagno} | muestra el mensaje referenciado por el flag flagno|
| {SYSMESS&#124;flagno} | muestra el mensaje del sistema del objeto referenciado por el flag flagno|
| {TEXTPIC&#124;ejemplo.jpg&#124;orientation} | muestra la imagen ejemplo.jpg. La imagen debe estar en la carpeta "dat". Ver [TEXTPIC](TEXTPIC_ES) para entender el parámetro "orientacion"|
| {ACTION&#124;examinar llave&#124;llave} | Muestra el texto "llave" con un link que hace que cuando se hace click automáticamente se ejecute la acción "examina llave".|
| {RESTART&#124;reiniciar} | Muestra un link con el texto "reiniciar" que al pulsarlo se reinicia el juego|
| {PROCESS&#124;valor} | Ejecuta el proceso de número "valor". Tengase en cuenta que no es recomendable que el proceso imprima ningún texto dardo que será mostrado antes de que el mensaje que contenía el tag de secuencia es escrito. El uso habitual de esta acción es asegurarse de que cada vez que un determinado mensaje es escrito alguna acción es ejecutada también.|
| {EXTERN&#124;ACCsave()&#124;GRABAR} | muestra un linke "GRABAR" que lanza el javascript "ACCSave()". Si sabes como funciona javscript puedes poner cualquier código para ser ejecutado al lanzar el link, o puedes añadir nuevas funcionalidades usando librerias (ver [ampliando ngPAWS](ampliando ngPAWS))|
| {OPRO}| Es reemplazado por el pronombre correspondiente al objeto referenciado por la frase actual. En españolo no tiene mucho uso, pero en inglés es usado profusamente.
| {TOOLTIP &#124;texto del tooltip &#124; texto} | Muestra un tooltip al pasar el ratón sobre el texto. hay una versión corta usando solo TT {TT &#124; texto del tooltip &#124; texto}


Notas:

* Las secuencias de escape pueden anidarse, así por ejemplo si queremos un texto con fondo amarillo y texto rojo podemos hacer esto:

{PAPER|yellow|{INK|red|hola}} que es anidar {INK|red|hola} dentro de {PAPER|yellow|_____}.

* Si sabes programar en javascript, o conoces a alguien quesepa, puedes crear tus propios tags de secuencia. Por favor mira la seccion [hooks](hooks_es) para saber como.

### Tags de secuencia de legado

* Por compatibildiad on PAWS, el guion bajo sera reemplazado por la descripción del objeto referencia por la frase actual, si es que hay alguno, exactamente lo mismo que {OREF}, pero sin tener en cuenta los artículos.

* También, para permitir escribir caracteres en blanco al final de lineas en aquellos editores que no lo permite, el caracter ¬ será reemplazado por un espacio.

* Finalmente, añadir \n a un texto produce un salto de línea.