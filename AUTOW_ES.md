**AUTOW**

Versión automática de WEAR.

La búsqueda se hace por un objeto buscado en diferentes localidades en un orden de preferencia determinado. Esta búsqueda priorizada permite a ngPAWS saber qué objeto esta implicado si existe mas de un objeto con el mismo nombre (si el adjetivo no esta especificado) dependiendo de si el objeto esta puesto, en las manos, en la localidad actual o en un contenedor

Prioridad:

* Llevado
* Puesto
* Localidad actual

Se supone que el jugador pretenderá ponerse antes un objeto que lleve. Cuando se encuentra un objeto se le pasa a la acción WEAR. 

Si no se encuentra ninguno el mensaje del sistema 8 (“No puedo hacer eso”) aparece y se ejecutan las acciones [[NEWTEXT|NEwTEXT_ES]] y [[DONE|DONE_ES]].


Ver también:

* [[WEAR|WEAR_ES]]
* [[AUTOR|AUTOR_ES]]