**PUTIN objno. locno.**

Si el objeto locno no existe o no es un contenedor o superficie, se muestra el error "Illegal Argument".

Si el objeto objno lo llevamos puesto, el [[mensaje del sistema 24|mensajes del sistema]] ("No puedo llevo el....") se muestra y las acciones  [[NEWTEXT|NEWTEXT_ES]] y  [[DONE|DONE_ES]] son ejecutadas.

Si el objeto objno. está en la localidad actual,  el mensaje del sistema 49 ("No tengo el....") se
muestra y las acciones [[NEWTEXT|NEWTEXT_ES]] y  [[DONE|DONE_ES]] son ejecutadas.

Si el objjeto objno no está en la localidad actual, pero no lo llevamos, se muestra el mensaje del sistema 28 ("No tengo eso.") se muestra y las acciones [[NEWTEXT|NEWTEXT_ES]] y  [[DONE|DONE_ES]] son ejecutadas.

En caso contrario, la localidad del objeto objno es cambiada a la localidad locno, el flag 1 es decerementado, y el mensaje del sistema 44 o 68 ("Pones _ en _" o "Pones el _ sobre _" se muestra, utilizando la descripción del objeto objno y el objeto locno, seguido del mensaje 51 (".").

Notese que el mensaje 44  o 68 son elegidos dependiendo de si locno es una superficie (68) o contenedor (44).

Notese igualmente que PUTIN no comprueba que el objeto locno esté presente.