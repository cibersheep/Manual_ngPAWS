**TAKEOUT objno locno**

Si el objeto lo llevamos puesto o en las manos sale el mensaje del sistema 25 (“Ya tengo _.”) y se ejecutan [[NEWTEXT|NEWTEXT_ES]] y [[DONE|DONE_ES]].

Si el objeto esta en la localidad actual sale el mensaje del sistema 45 (“_ no esta en ”), seguido de la descripción del objeto cuyo numero coincide con locno, seguido del SM51(”.”) y se ejecutan NEWTEXT y DONE.

Si el objeto no esta en la localidad actual ni en la localidad indicada sale el mensaje del sistema 52(“No hay uno de esos en”), seguido de la descripción del objeto cuyo numero coincide con locno, seguido del mensaje del sistema 51(”.”) y se ejecutan NEWTEXT y DONE.

Si el objeto no lo llevamos puesto o en las manos, y el peso total de los objetos llevados y puestos por el jugador mas el del objeto en cuestión exceden el máximo peso que el jugador puede llevar (flag 52) sale el mensaje del sistema 43 (“Pesa demasiado”) y se ejecutan NEWTEXT y DONE.

Si el jugador ya lleva el máximo numero de objetos que puede llevar (flag1>=flag37) sale el mensaje del sistema 37 (“No puedo llevar mas cosas”) y se ejecutan NEWTEXT y DONE. Adicionalmente se interrumpe cualquier bucle DOALL.

En otro caso el objeto pasa a ser llevado, se incrementa en 1 el flag 1 y sale el mensaje del sistema 36 (“Coges _.”).

Nota: No se comprueba, por parte de PUTIN y TAKEOUT, que el objeto referenciado por locno (generalmente un contenedor) esta presente. Esto debe ser comprobado por el programador.

Ver también

* [[PUTIN|PUTIN_ES]]
* [[AUTOT|AUTOT_ES]]
