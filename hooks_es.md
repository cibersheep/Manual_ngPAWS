Los hooks (ganchos) son la manera que da ngPAWS para que los autores de librerías plugin enganchen con determinadaos procesos internos de ngPAWS.

Por ejemplo, digamos que tenemos un plugin que permite manejar atributos para las localidades (como los que vienen de base para los objetos). Probablemente la librería incluirá algún tipo de locationAttributes[] array, y también un locationAttributes_start[] para guardar los estados originales. En fin, que tenemos unos datos que hacen que las cosas funcionen como se espera, pero ahora cuando vamos a grabar la partida, queremos que esos datos se graben, para que al cargar la partida todo quede como estaba.

Hay un hook que ocurre justo antes de grabar partida, y otro justo antes de cargarla. Estan hechos para que el autor de librerías se enganche ahí, y meta en el savegame o saque lo que quiera.

Los hooks son funciones que ocurren en algun momento del runtime de ngPAWS y cuya implementación por defecto no hace nada, pero si el autor de librerías reemplaza la funcion por una suya, pues se ejecutará el código que él/ella ponga.

Para reemplazar un hook, una librería plugin puede simplemente reemplazar dicha función, por ejemplo:

```
\\LIB Reemplazo de WriteHook 

var old_writeHook = h_writeText;

h_writeText = function (text)
{
        text = text.toUpperCase();
	text = old_writeHook(text);
	return text;
}
``` 

h_writeText es un hook que ocurre cada vez que ngPAWS va a escribir texto en pantalla. Por defecto recibe el texto a escribir, y devuelve el mismo. En esta implementacion sin embargo cambia todo el texto a mayúsculas. Una librería plugin que simplemente contuviera el código de arriba, haría que todo el juego saliera en mayúsculas, sin cambiar nada en los fuentes.

Este sistema podría tener otras utilidades, como reemplazar "cuchillo" por "cuchillo ensangrentado" siempre que el flag tal valga tal (por ejemplo tras matar algun orco perdido), o incluso implementar un sistema anti palabrotas (de modo que aunque el autor escribiera alguna palabra malsonante, o incluso el jugador la tecleara, al escribirla ngPAWS la sustituyera por ***** o similar).


### Los hooks

**h_init = function()**

Es llamado al principio de la función start() que se ejecuta cuando el juego arranca o reinicia.

**h_post =  function()**

Es llamado al final de la función start() que se ejecuta cuando el juego arranca o reinicia.

**h_writeText =  function (text)**

Es llamado cuando el sistema va a escribir cualquier texto, recibe el texto y debe retornar lo que debe escribirse (por defecto devuelve lo mismo que recibe).

**h_playerOrder = function(player_order)**

Es llamado cada vez que el jugador teclea una orden, y debe retornar un texto. Por defecto devuelve el mismo pero podría utilizarse para cambiar la ordenes del autor (imagina por ejemplo que el jugador está poseido, y aunque escriba "MATAR BRUJO" la orden escrita sea "MATAR AMIGOS").

**h_description_init =  function ()**

Es llamada cada vez que una localidad es descrita, justo después de escribir el texto de localidad.

**h_description_post = function()**

Es llamada cada vez que una localidad es descrita, justo después de ejecutar el proceso 1.

**h_saveGame = function(savegame_object)**

Es llamada cuando el objeto "savegame" es creado, para que sea posible añadirle propiedades personalizadas antes de ser grabado. Debe devolver dicho objeto (por defecto lo devuelve sin modificarlo).


`savegame_object.locationsAttributes = locationsAttributes;`

**h_restoreGame = function(savegame_object)**

Se llama tras restaurar todos los parámetros estándar de un "savegame", para permitir que se restauren parámetros personalizados. 

**h_invalidOrder = function(player_order)**

Es lamada cada vez que el usuario escribe algo imposible de entender. Un buen uso de este gancho podría ser hacer una llamda ajax a un servidor que permita recopilar que frases escriben los usuarios y así sacar una versión mejorada del juego. 

**h_sequencetag = function (tagparams)**

Es llamado cada vez que un [tag de secuencia](tag de secuencia) escrito por el autor es desconocido, como última oportunidad para que un sistema externo realice una implementación del mismo. EL parámetro tagparams recibe un array con los parámetros del tag, por ejemplo {SUMFLAGS|12|23} enviará ['SUMFLAGS','12','13']. Hay una librería hook en la carpeta sample plugins que es mucho mejor que cualquier documentación.

**h_keydown = function (event)**

Este hook es llamado cada vez que se pulsa una tecla, por lo que es muy potente y puede permitir a un plugin hacer muchas cosas. Notese que es llamado cada vez que se pulsa una tecla, incluso en el input del jugador. El dato recibido es el típico evento recibido en javascript en un "onkeydown", por ejemplo event.keyCode contendrá el código de la tecla pulsada.

Por defecto este evento devuelve true, y al volver del mismo si devuelve true se ejecutarán las acciones estándar de ngpaws para la pulsación de una tecla (comprobar que es ESC si estamos en transcript, salir del ANYKEY si está activo, del GETKEY, etc.) pero si es false no se procesan. Devolver false puede servir para impedir que tras tratar un resultado en una funcion h_keydown alternativa, se ejecute la acción estándar de dicha pulsación.

**h_code = function (str)**

Este es un hook muy especial, porque permite un enlace hacia atrñas desde la tabla de respuestas/procesos hacia javascript.

Es le llama cada vez que en dichas tablas aparece el condacto HOOK, seguido de un string, que se recibe como parámetro. Por ejemplo si en la tabla hay un HOOK "HELLO" se recibirá el parámetro "HELLO" en este hook. Puede utilizarse desde librerías plugin, para implementar algunas respuestas o comportamientos en las tablas de respuesta, al margen del código propiamente ngPAWS.

Por ejemplo una librería que implemente una manera de mezclar objetos que son liquidos, puede implementar sus propias respuetas en javascript mediante este hook.

Notese que hay varias llamadas ya en la base de datos de inicio, aunque ninguna hace nada:


* HOOK "RESPONSE_START" -> Al principio de la tabla de respuestas
* HOOK "RESPONSE_USER" -> En la zona de la tabla de respuestas donde las respuestas el programador empiezan
* HOOK "RESPONSE_DEFAULT_START" -> En la zona de la tabla de respuestas donde las respuestas por defecto empiezan
* HOOK "RESPONSE_DEFAULT_END" -> Al final de la tabla de respuestas
* HOOK "PRO1" -> Al principio del proceso 1
* HOOK "PRO2" -> Al principio del proceso 2

**h_preProcess = function (procno)**

Este gancho se llama cada vez que un proceso es ejecutado, justo antes de ejecutar la primera instrucción del mismo.

**h_postProcess = function (procno)**

Este gancho es ejecutado cada vez que un proceso se ejecuta (incluido el proceso 0, respuestas), justo después de salir del mismo, independientemente de como se salió del proceso (DONE, NOTDONE, etc.)

La diferencia con el gancho h_code con el parámetro RESPONSE_DEFAULT_END es que este último solo se ejecutará si la ejecución del proceso llega a la posición donde está el condacto HOOK dentro del proceso, mientra que con h_postProcess se ejecutará en cualquier caso.

### Hooks en cadena

Es posible que varias librerías usen el mismo hook para sus funciones, siempre que cada nueva librería, llame al hook que se encontró al ejecutarse, de la manera que se ve en el código al principio de esta página. Si una librería no lo hiciera así, es posible que otras librerías que usen el mismo hook y se carguen antes no funcionen.

