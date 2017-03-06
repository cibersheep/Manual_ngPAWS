**AUTOD**

Versión automática de [[DROP|DROP_ES]]

La búsqueda se hace por un objeto buscado en diferentes localidades en un orden de preferencia determinado. Esta búsqueda prioritaria permite a ngpaws saber qué objeto esta implicado si existe mas de un objeto con el mismo nombre (si el adjetivo no esta especificado) dependiendo de si el objeto esta puesto, en las manos, en la localidad actual o en un contenedor

Prioridad:

* Llevado
* Puesto
* Localidad actual

Se supone que el jugador pretenderá dejar antes un objeto que lleve. Cuando se encuentra un objeto se le pasa a la acción DROP.

Si no se encuentra ninguno el mensaje del sistema 28 (“No tengo uno de eso”) aparece y se ejecutan las acciones [[NEWTEXT|NEwTEXT_ES]] y [[DONE|DONE_ES]].

Ver también:

* [[DROP|DROP_ES]]
* [[AUTOG|AUTOG_ES]]