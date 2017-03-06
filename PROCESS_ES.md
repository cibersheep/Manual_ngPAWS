**PROCESS procno.**

Trasnfiere la acción de ngPAWS al proceso correspondiente. El subproceso tendrá las mismas caracterísitcas que el que lo ha llamado, por ejemplo si se llama desde la tabla de respuestas, ngPAWS intentará comprobar verbo y nombre en las entradas, pero si se hace desde el proceso 1, no.

Ten en cuenta que esto es una verdadera subrutina, y cuanlquier salida de la nueva tabla ([[DONE|DONE_ES]], [[OK|OK_ES]], etc. devolverá el control al condacto que sigue a la acción PROCESS.

Desde un proceso llamado con process se puede a su vez llamar a otros procesos.

