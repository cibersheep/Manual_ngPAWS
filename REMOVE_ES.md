**REMOVE objno**

Si el objeto lo llevamos o esta en la localidad actual (pero no puesto) sale el mensaje del sistema 50(“No llevo puesto _.”) y se ejecutan [[NEWTEXT|NEWTEXT_ES]] y [[DONE|DONE_ES]].

Si el objeto no lo llevamos puesto aparece el mensaje del sistema 23(“No llevo puesto uno de esos”) y se ejecutan NEWTEXT y DONE.

Si el objeto no es una prenda aparece sale el mensaje del sistema 41(“No puedo quitarme _.”) y se ejecutan NEWTEXT y DONE.

Si el máximo numero de objetos que se pueden llevar en las manos es excedido (flag1 >= flag37), sale el mensaje del sistema 42 (“No puedo quitarme _. Mis manos están llenas.”) y se ejecutan NEWTEXT y DONE.

En otro caso el objeto pasa a estar 'llevado', se incrementa en 1 el flag 1 y se muestra el mensaje del sistema 38(“Me he quitado _.”).

Ver también:

* [[WEAR|WEAR_ES]]
* [[AUTOR|AUTOR_ES]]