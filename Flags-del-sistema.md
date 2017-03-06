Los flags del sistema controlan las interioridades del sistema ngPAWS. Muchos de ellos serán muy útiles en tus juegos, pero ten cuidado al modificarlos, asegurate de que sabes lo que haces.

|Flag #| Función|
|--------|-------|
| 0 | Cuando no vale cero, indica que el juego está a oscuras|
| 1 | Guarda la cantidad que el jugador lleva (pero no cuenta los que lleva puestos)|
| 2 | Su valor se autodecrementa cada vez que una localidad es descrita|
| 3 | Su valor se autodecrementa cada vez que una localidad es descrita y  está oscuro (El flag 0 no vale 0)|
| 4 | Su valor se autodecrementa cada vez que una localidad es descrita, está oscuro, y no hay objetos con el atributo de luz presentes.|
| 5 to 8 | Autodecrementados cada turno (cada orden del jugador o timeout)|
| 9 | Cada turno que esta oscuro|
| 10 | Cada turno que está oscuro y no hay objeto con el atributo de luz presente|
| 11 | Usado por  [OBJFOUND](OBJFOUND_ES) y [OBJNOTFOUND ](OBJNOTFOUND_ES) para devolver el número del objeto que hace el condacto tener éxito o fallar.
| 12 | Varias opciones de configuración: Bit 0: si vale 1, el parser entiende las [terminaciones pronominales].  Bit 1: Si vale 1 significa que tras encontrar un verbo al parsear, el parser encontró una palabra desconocida, lo cual implica que el jugador probalemente quería hacer alguna acción sobre algo que el programador no pensó. Se usa para que ngPAWS determine las respuestas por defecto a dar en muchas acciones, dependiendo de su valor puede dar una u otra respuesta. Bit 2: Si vale 1 significa que la primera preposición en la SL se encontró tras el primer nombre. Se usa en lenguajes como el español para poder hacer que  "DAR LA LLAVE A JOSE" y  "DAR A JOSE LA LLAVE" sean lo mismo. Bit 3: si vale , los objetos con el attributo aNPC no son tenidos en cuenta para [OBJAT](OBJAT_ES),  [LISTAT](LISTAT_ES), [LISTOBJ](LISTOBJ_ES), etc. Bit 4: si el valor es 1 significa que la ventana del navegador ha sido redimensionada. Se pone a cero de nuevo al final de cada ejecución del [proceso interrupción]. Bit 5: poner a 1 para definir que el parseado es en español, o a 0, valor por defecto, para inglés. Bit 6: reservado. Bit 7: si vale 0 (valor por defecto) los objetos que estén metidos en contenedores (aContainer) o sobre objetos superficie (aSupporter) serán considerados "presentes" y condactos como AUTOG, GET, PRESENT, ABSENT, etc. reaccionaran teniéndolo en cuenta. Bit 8: si vale 1 el parser no tratará de adivinar la palabra buscando una similar cuando el jugador la escriba mal.
|13-16| Son usados por la librería de inicio para datos temporales |
|17 to 28| libres para ser usados en tus propios juegos, aunque no recomiendo usar estos sino los que quedan libres al final|
| 29 | (obsoleto, antes tenía un uso, pero ya no)|
| 30 | Almacena la puntuación que se muestra con el condacto [SCORE](SCORE_ES)|
| 31 / 32 | Guarda el número de turnos que el se han jugado (en realidad, es la cuenta de las frases que ha tecleado el jugador). Usa dos flags por compatibilidad con otros sistemas.|
| 33 | guarda el verbo de la sentencia lógica actual|
| 34 | guarda el primer nombre de la sentencia lógica actual|
| 35 | guarda el adjetivo para el primer nombre de la sentencia lógica actual|
| 36 | guarda el adverbio de la sentencia lógica actual|
| 37 | almacena el número máximo de objetos llevables, inicialmente 4. Se puede modificar usando [ABILITY](ABILITY_ES).|
| 38 | Guarda la localidad actual del jugador.|
| 39 | (obsoleto, antes tenía un uso, pero ya no)|
| 40 | Guarda el modo de pantalla. Si es 0 al describir una nueva localidad se borrará el contenido de la ventana de texto, en otro caso no se borra.|
| 41 | (obsoleto, antes tenía un uso, pero ya no)|
| 42 | Guarda el mensaje del sistema utilizado para [[PROMPT|PROMPT_ES]]|
| 43 | guarda la preposición de la sentencia lógica actual.|
| 44 | guarda el segundo nombre de la sentencia lógica actual.|
| 45 | guarda el adjetivo para el segundo nombre de la sentencia lógica actual|
| 46 | Guarda el nombre referenciado por el pronombre actual o la [terminación pronomimal](terminación pronomimal) actual|
| 47 | Guarda el adjetivo referenciado por el pronombre actual o la [terminación pronomimal](terminación pronomimal) actual|
| 48 | guarda la duración del timeout|
| 49 | guarda los settings de control del timeout: Los bits 1-6 están obsoletos. El bit 7 se pone a 1 si la ultima entrada del jugador acabó en timeout, y el bit 0 si se pone 1 hace que los timeout puedan ocurrir solo si el jugador no ha tecleado nada . Se puede modificar usando [INPUT](INPUT_ES) y [TIME](TIME_ES) (igual que el flag 48). La orden [TIMEOUT](TIMEOUT_ES) comprueba el bit 7 de este flag.|
| 50 | guarda la localidad para el bucle DOALL activo|
| 51 | guarda el último objeto referenciado por GET / DROP / WEAR / WHATO, etc. |
| 52 | guarda la fuerza del jugador, o el máximo peso de los objetos llevados y puestos| inicialmente es 10)|
| 53 | guarda los settings de listar objetos: Bit 7: Se pone a 1 si algún objeto se listó al hacer [LISTOBJ](LISTOBJ_ES) o [LISTAT](LISTAT_ES). Bit 6: Ponlo a 1 para causar que los listados sean continuos en lugar de un objeto por liena. Por ejemplo LET 53 64 hará que ngPAWS listes los objetos en la misma linea. Bit 5 : Se pone a 1 si algún NPC es listado como parte de  [LISTNPC](LISTNPC_ES).
| 54 | guarda la localidad actual del objeto actualmente referenciado|
| 55 | guarda el peso actual del objeto actualmente referenciado|
| 56 | guarda los primeros 32 (0-31) atributos del objeto actualmente referenciado|
| 57 | guarda los segundos 32 (32-63) atributos del objeto actualmente referenciado|
| 58 & 59| no deben ser usados puesto que se usarán para expansiones.|
| 60 to 255| disponibles para tu uso.|