**AUTOP locno**

Versión automática de PUTIN.

La búsqueda se hace por un objeto buscado en diferentes localidades en un orden de preferencia determinado. Esta búsqueda priorizada permite a ngPAWS saber qué objeto esta implicado si existe mas de un objeto con el mismo nombre (si el adjetivo no esta especificado) dependiendo de si el objeto esta puesto, en las manos, en la localidad actual o en un contenedor

Prioridad:

* Llevado
* Puesto
* Localidad actual

Se supone que el jugador pretenderá poner antes un objeto que lleve encima que uno que lleve puesto. Cuando se encuentra un objeto se le pasa a la acción PUTIN. Si no se encuentra ninguno y además no hay ningún objeto en el juego que corresponda se escribe el mensaje del sistema 8 (“No puedo hacer eso”) , si hay algún objeto en el juego que corresponda en algún lugar aparece el mensaje del sistema 28 (“No tengo uno de esos”). En cualquier se ejecutan las acciones [[NEWTEXT|NEwTEXT_ES]] y [[DONE|DONE_ES]].


Ver también:

* [[PUTIN|PUTIN_ES]]
* [[AUTOT|AUTOT]]