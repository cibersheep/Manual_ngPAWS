**AUTOR**

Versión automática de REMOVE.

La búsqueda se hace por un objeto buscado en diferentes localidades en un orden de preferencia determinado. Esta búsqueda priorizada permite a ngPAWS saber qué objeto esta implicado si existe mas de un objeto con el mismo nombre (si el adjetivo no esta especificado) dependiendo de si el objeto esta puesto, en las manos, en la localidad actual o en un contenedor

Prioridad:

* Puesto
* Llevado
* Localidad actual

Se supone que el jugador pretenderá quitarse antes un objeto que lleve puesto. Cuando se encuentra un objeto se le pasa a la acción AUTOR.

Si no se encuentra ninguno el mensaje del sistema 23 (“No puedo hacer eso”) aparece y se ejecutan las acciones [[NEWTEXT|NEwTEXT_ES]] y [[DONE|DONE_ES]].


Ver también:

* [[AUTOW|AUTOW_ES]]
* [[REMOVE|REMOVE_ES]]
