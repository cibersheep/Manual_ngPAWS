**WEAR objno**

Si el objeto esta en la localidad actual (pero no puesto o en las manos) el mensaje del sistema 49(“No tengo _.”) sale y se ejecutan [[NEWTEXT|NEWTEXT_ES]] y [[DONE|DONE_ES]]. mensaje del sistema 29(“Ya lo llevo puesto”) y se ejecutan NEWTEXT y DONE.

Si el objeto no lo llevamos en las manos sale el mensaje del sistema 28(“No tengo uno de esos”) y se ejecutan NEWTEXT y DONE.

Si el objeto no es una prenda el mensaje del sistema 40(“No puedo ponerme _”) aparece y se ejecutan NEWTEXT y DONE.

En caso contrario el objeto pasa a estar 'puesto' , se decrementa el flag 1, y sale el mensaje del sistema 37(“Ahora llevo puesto _.”).

Ver también:

* [[REMOVE|REMOVE_ES]]
* [[AUTOW|AUTOW_ES]]