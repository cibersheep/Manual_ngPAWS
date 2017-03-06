**AUTOG**

Versión automática de [[GET|GET_ES]]

La búsqueda se hace por un objeto buscado en diferentes localidades en un orden de preferencia determinado. Esta búsqueda priorizada permite a ngPAWS saber qué objeto esta implicado si existe mas de un objeto con el mismo nombre (si el adjetivo no esta especificado) dependiendo de si el objeto esta puesto, en las manos, en la localidad actual o en un contenedor.

Prioridad:

* Localidad actual
* Llevado
* Puesto

Se supone que el jugador pretenderá coger antes un objeto que este en la localidad actual. Cuando se encuentra un objeto se le pasa a la acción GET.

En otro caso si el nombre  estaba en el vocabulario se muestra el mensaje del sistema 26 (No hay un de esos por aquí) y en caso contrario el mensajes del sistema 8 (no puedes hacer eso). En cualquiera de los casos se ejecutan [[NEWTEXT|NEWTEXT_ES]] y [[DONE|DONE_ES]].

Ver también:

* [[AUTOD|AUTOD_ES]]
* [[GET|GET_ES]]
