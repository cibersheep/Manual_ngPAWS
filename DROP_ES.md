**DROP objno**

Si el objeto lo llevamos puesto sale el mensaje del sistema 24 (“No puedo, lo llevo puesto”) y [[NEWTEXT|NEWTEXT_ES]] y [[DONE|DONE_ES]] se ejecutan.

Si el objeto está en la localidad actual (pero no lo llevamos en las manos ni puesto) se muestra el mensaje del sistema 49 (“No tengo el _.”) y NEWTEXT y DONE.

Si el objeto no esta en la localidad actual el mensaje del sistema 28 (“No tengo uno de esos”) sale, y se ejecutan NEWTEXT y DONE

En otro caso el objeto pasa a estar en la localidad actual, se decrementa en 1 el flag 1 y el mensaje del sistema 39 (“Dejas _.”) se muestra.

Ver también:

* [[DROPALL|DROPALL_ES]]
* [[GET|GET_ES]]
* [[AUTOD|AUTOD_ES]]