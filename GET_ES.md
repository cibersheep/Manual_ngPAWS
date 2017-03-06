**GET objno**

Si llevamos el objeto puesto o en el inventario, el [[mensaje del sistema 25|mensajes del sistema]] (“Ya tengo _.”) sale, y las acciones [[NEWTEXT|NEWTEXT_ES]] y [[DONE|DONE_ES]] se ejecutan.

Si el objeto no está en la localidad actual sale el mensaje del sistema 26 (“No hay uno de esos por aquí”) y se ejecutan NEWTEXT y DONE.

Si el peso tal de los objes llevados y puess por el jugador excede del máximo que puede llevar (flag 52) ennces aparece el mensaje del sistema 43 (“Eso pesa demasiado”), y se ejecutan NEWTEXT y DONE. Además cualquier acción DOALL es cancelada.

Si el jugador lleva el máximo numero de objes que puede llevar (el flag 1 es mayor o igual que el flag 37) el mensaje “No puedo llevar mas cosas” aparece, y se ejecutan NEWTEXT y DONE. Además cualquier acción DOALL es cancelada.

En otro caso el objeto pasa a estar 'llevado', se incrementa el flag 1 en 1 y se muestra el mensaje del sistema 36 (“Coges _.”).

Ver también:

* [[DROP|DROP_ES]]
* [[AUTOG|AUTOG]]
