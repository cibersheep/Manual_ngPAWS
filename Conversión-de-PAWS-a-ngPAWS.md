Antes de nada algunos apuntes:

* PAWS usaba solo 5 caracteres para reconocer las palabras, mientras que ngPAWS usa 10.

* Algunos juegos de ZX Spectrum, al quedarse sin mensajes, usaron los mensajes del sistema sobrantes. Tanto PAW para PC como Superglús añadieron nuevos mensajes al PAW original, y ngwpas aún añade más. Esto puede crear conflictos.

* PAWS no soportaba tantos atributos de objetos como ngPAWS, por lo que todo lo que afecte a los atributos antiguos, especialmente el de luz puede verse afectado. En especial si se hace referencia al flag que mantenía los datos de atributos de objeto, habrá algo muy diferente. 

* PAWS no tenía un atributo específico de *luz* para objetos, simplemente el objeto 0 era la única fuente de luz, y llevaba el atributo implícito.

* Algunos *condactos* no hacen nada porque no tienen sentido en el contexto de ngPAWS, especialmente todos los relacionados con control de la pantalla  (PROTECT, SAVEAT, BACKAT) o colores (INK, PAPER, BORDER, etc.). Además, hay otros *condactos* que pueden no funcionar porque han cambiado sus parámetros (BEEP). Tienes información sobre todo esto en el artículo [Compatibilidad hacia atrás](Compatibilidad hacia atrás). 

* Date cuenta que al portar un juego de Spectrum a ngPAWS, la elaborada base de datos de inicio de ngAPAWS no será incluida. Por ello las respuestas a muchas acciones pueden no estar, y aunque la existencia de muchos «no puedes hacer eso» es más o menos normal en un juego de Spectrum, para los estándares actuales es muy pobre. Se recomienda hacer una mezcla del código original con la librería base de ngPAWS, pero claro, eso es otro reto.

### Conversión paso a paso

* **Herramientas necesarias**

inPAWS (http://inpaws.speccy.org/Descargas.html)

* **Imagen del juego de Spectrum original**

Cualquier formato que inPAWS pueda leer (por ejemplo SNA)

* **Convirtiendo a inPAWS**

Con el ejecuable de inPAWS y el SNA en al misma carpeta, ejecuta:

`inpaws e fichero.sna -o fichero.inp`

Obtendás un fichero «fichero.inp».

* **Arreglando caracteres extraños** (para aventuras en español)

Si nuestro juego no está en inglés, es posible que tuviera vocales acentuadas u otros símbolos especiales (como la Ñ o la Ç) que aparezcan mal. Esto ocurre porque el Spectrum no tenía vocales con tilde, y cada juego usaba unos caracteres especiales paar representarlas. Para la mayoría de juegos españoles, añadir el siguiente código al principio del fichero *fichero.inp* lo arreglará, si no es así, tendrás que revisarlo caracter por caracter:

```
SUBCHAR "@" "á";
SUBCHAR "#" "é";
SUBCHAR "$" "í";
SUBCHAR "%" "ó";
SUBCHAR "&" "ú";
SUBCHAR "|" "ñ";
SUBCHAR "[" "¡";
SUBCHAR "]" "¿";
```

* **Arreglando el vocabulario**

Como PAWS solo reconocía 5 caracteres pero ngPAWS necesita 10, es necesario alargar las palabras que tengan más de 5 letras hasta su longitud real o hasta 10 caracteres (lo que ocurra antes).

* No arregles las palabras excepto que sea necesario, simplemente añade sinónimos con el mismo número y tipo de palabra. Esto es así porque a veces la palabra es también usada en los procesos, y si reemplazas la versión corta (CALEN) por la larga (CALENDARIO) al final dará error donde ponía «MIRAR CALEN». Solo reemplázalas si con ellos se resuelve una ambigüedad.

* Si estás convirtiendo un juego en español, o cualquier otro idioma donde la conjugación del verbo difiere en imperativo e infinitivo, asegúrate de añadir ambos:  (por ejemplo para EMPUJ deberás añadir EMPUJAR y EMPUJA).

* Si no estás conpletamente seguro de una palabra (5 letras no te permiten reconocerla), trata de encontrarla en el fichero inp, probablemente hay una referencia a ella en el código. También puedes mirar el tipo de palabra (probablemente saber si es un nombre, verbo, adjetivo, etc. puede ayudar)

* **Arreglando los mensajes del sistema**

ngPAWS utiliza más mensajes que el PAW original, lo que puede provocar dos cosas:

* Un juego de PAWS contiene menos de los 66 mensajes del sistema que tiene ngPAWS. Los mensajes que falten puedes extraerlos de la base de datos de inicio de ngPAWS.

* Debido a los limites de PAWS, algunos programadores de Spectrum usaron mensajes del sistema como mensajes (porque se les acabaron los mensajes de usuario). Si los mensajes del sistema 54 y susperiores son usados por tu juego, y ngPAWS usa los mensajes 54-67, aparece un conflicto. Tendrás que mover manualmente esos mensajes a la tabla de mensajes de usuario (que en ngPAWS admite más de 25%) y luego buscar donde aparezcan las llamadas a los mensajes antiguos con [SYSMESS](SYSMESS) y sustituirlas con MESSAGE y el nuevo número del mensaje. Después, traernos los mensajes de la base de datos de ngPAWS (punto anterior).

* **Obteniendiendo el fichero code.txp **

Una vez parcheado nuestro fichero *fichero.inp,* podemos exportar a ngPAWS usando inPAWS así:

`inpaws ct fichero.inp`

Esto devolverá un fichero llamado *fichero.inp.txp* que debe ser renombrado como code.txp and y usado como código fuente para nuestra aventura:

* **Parcheando el code.txp**

Tienes que buscar la linea /STX y quitar el comentario que hay justo detrás para que ponga solo /STX.

* **Cosas a comprobar**

Ahora que tenemos nuestro juego en ngPAWS, es hora de chequearlo. Échale un ojo a la [Compatibilidad hacia atrás](Compatibilidad hacia atrás).

Aparte de otras cosas generales, deberás tener especial cuidado con: 

* *Condacto* ANYKEY: es difícil de implementar en javascript así que ngPAWS lo hace de una manera un tanto precaria. Intenta comprobar cada uso del mismo, y si no fucniona, trata de utilizar [BLOCK](BLOCK_ES) en su lugar.

* Otros *condactos* a comprobar especialmente son:

  * [BEEP](BEEP_ES) (sus parámetros cambian)
  * [GRAPHIC](GRAPHIC_ES)(sus parámetros y uso cambian)
  * [EXTERN](EXTERN_ES) (por su contenido diseñado explícitamente para el ZX Spectrum, portarlo no es posible)

* También hay otros *condatos* que no harán nada pero no recibirás ningún aviso: : [INPUT](INPUT_ES), [SAVEAT](SAVEAT_ES), [BACKAT](BACKAT_ES), [PRINTAT](PRINTAT_ES), [RESET](RESET_ES), [PROMPT](PROMPT_ES), [PROTECT](PROTECT_ES), [LINE](LINE_ES), [MODE](MODE_ES), [CHARSET](CHARSET_ES), [BORDER](BORDER_ES), [INK](INK_ES), [PAPER](PAPER_ES) y [TIME](TIME_ES).

* Cualquier proceso que compruebe los flags 56 o 57 encontrarán diferentes datos (ver [mensajes del sistema](mensajes del sistema) y su definición en PAWS para entender la diferencia).

*ngPAWS usa el flag 12 como flag del sistema. Si el juego usa el flag 12 para sus propios asuntos habrá un conflicto que hay que solucionar.

* **Gráficos**

Puedes extraer los gráficos del *snapshot* usando PAWGR (http://www.caad.es/modulos.php?modulo=descarga&id=588) 

Eso sí, las imágenes extraídas son realmente pequeñas (256x192 píxeles) y contienen la pantalla completa del Spectrum por lo que las filas de abajo estarán en blanco. Te sugiero que las uses más como base para nuevos gráficos que tal cual están, porque a resoluciones actuales serán casi como *thumbnails.*

