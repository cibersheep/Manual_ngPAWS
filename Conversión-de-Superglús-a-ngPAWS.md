### ¿Por dónde empiezo?

Sencillo, sigue estos pasos:

* Mira como se llama el .TXP de tu aventura en Superglús, y crea en ngPAWS una juego de igual nombre (con su carpeta particular).

* Copia el .TXP de tu juego Superglús en esa carpeta (reemplazando al que hay por defecto)

* Copia todos los recursos gráficos y sonoros (si los hay) en la carpeta "dat"

* Compila, y si no da errores, prueba la aventura a fondo (podría haber problemas ocultos). Si da errores repasa los puntos comentados abajo en este artículo.

* Si te aparecen mal los acentos, tendrás que cambiar la codificación del fichero txp original a UTF-8. Esto lo puedes hacer con distintos editores de texto, por ejemplo para Windows podéis usar [Notepad++](http://notepad-plus-plus.org/) (abrís el fichero, y dais al menú "Enconding/Convert to UTF-8" y grabáis el fichero).

* Si tu aventura es de una versión antigua de Superglús, añade el mensaje del sistema 62 (lo puedes coger de la base de datos de inicio de ngPAWS). Si te faltan más cógelos del mismo sitio.

* Si no funcionan las terminaciones pronominales (cogerlo, dejarlo, saltarla) asegúrate de añadir BSET 12 5 al principio de tu aventura para marcar idioma español.

### Puntos problemáticos

Existen algunos condactos o funcionalidades que podrían no funcionar bien en ngPAWS, por los cambios a los que ha sido sometido. Paso a enumerar algunos:

* Condacto ANYKEY: en general debería funcionar bien, aunque hay determinados casos, en los que el ANYKEY pueda estar tras una condición y tras otro ANYKEY donde podría no funcionar bien. También podrían dar problemas ANYKEYs que tengan detrás llamadas a procesos . Tras compilar comprobar todos los casos en los que se usaba para ver que va bien. Si algo no va bien quizá sea mejor cambiarlo por [BLOCK](BLOCK_ES) o [SOFTBLOCK](SOFTBLOCK_ES).

* Condacto PAUSE: realiza la pausa, pero para el juego 100%, música o efectos sonando incluidos, por lo que no vale para temporizaciones de intros y cosas similares. En caso de haber usado PAUSE para eso recomiendo que hagáis la temporización en [[el proceso interrupción]].

* Condacto DEBUG: no está soportado, pero no hace ninguna falta, el depurador de la consola de los navegadores Chrome, Firefox, Explorer, etc. es mil veces más potente que el de Superglús.

* Condacto GETKEY: se verá afectado por lo mismo que ANYKEY pero es aún más difícil que funcione. Si lo usáis, probar bien cada caso. La alternativa viene por el uso del condacto [COMMAND](COMMAND_ES) para esconder el input, y del [hook](hooks_es) h_keydown. Es complejo pero por suerte no es un condacto muy usado. 

* Secuencias de escape: ngPAWS no soporta ninguna secuencia de escape de Superglús, excepto el carácter de subrayado (_), todos los demás se mostrarán tal cual. Conviene repasar todos los mensajes y writes para detectarlos y substituirlos por [tags de secuencia](tags de secuencia). Afortunadamente al compilar ngPAWS genera un fichero spellcheck que contiene todos los textos de la aventura, por lo que buscarlos es fácil.

* Formatos de sonido: ngPAWS necesita tener los ficheros de sonido en formato ogg y mp3 (cada fichero debe tener el mismo nombre y las dos extensiones, dado que algunos navegadores soportan ogg y otros mp3).

* Todos los parámetros de formato de texto que se ponían en la primera sección de Superglús no valen para ngPAWS, se hace todo por CSS. Para cambiar de estilo lo mejor es usar los [[tags de secuencia]] CLASS o STYLE.

* ngPAWS tiene nuevos atributos de objeto, y su librería base a veces hace referencia a los mismos para determinar como hacer ciertas cosas, en concreto es importante diferenciar género y número. Por eso es importante repasar la lista de objetos y si alguno es femenino, plural o ambas cosas, ponerle los atributos correctos (aPlural, aFemale o ambos) para evitar ver mensajes como  "Dejas un llave." al entender ngPAWS que por defecto los objetos son singular y neutro. Con los masculinos no hay graves problemas porque en español el neutro es idéntico al masculino. Si la aventura estuviera en inglés (hasta donde yo se no hay ninguna pero bueno) sería importante también marcar el masculino aMale para evitar que objetos o NPCs masculinos fueran referenciados por "IT" en lugar de "HIM".

Además, conviene que echéis un ojo a [este hilo del foro de CAAD](http://foro.caad.es/viewtopic.php?f=6&t=5761), con los problemas aparecidos durante la conversión a ngPAWS de "Las aventuras de Rudolphine Rur".

Hay una lista  completa de compatibilidades en este artículo, aunque habla también de las de PAW (de hecho el 90% del artículo es de PAW): [Compatibilidad hacia atrás](Compatibilidad hacia atrás).
