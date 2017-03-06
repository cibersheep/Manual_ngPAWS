**AUTOT locno**

Versión automática de TAKEOUT.

La búsqueda se hace por un objeto buscado en diferentes localidades en un orden de preferencia determinado. Esta búsqueda priorizada permite a ngPAWS saber qué objeto esta implicado si existe mas de un objeto con el mismo nombre (si el adjetivo no esta especificado) dependiendo de si el objeto esta puesto, en las manos, en la localidad actual o en un contenedor

Prioridad:

* En contenedor marcado por locno
* Llevado
* Puesto
* Localidad actual

Se supone que el jugador pretenderá sacar antes un objeto que este en el contenedor. Cuando se encuentra un objeto se le pasa a la acción TAKEOUT

Si no se encuentra ninguno y además no hay ningún objeto en el juego que corresponda se escribe el mensaje del sistema 8 (“No puedo hacer eso”) , si hay algún objeto en el juego que corresponda en algún lugar aparece el mensaje del sistema 28 (“No hay _ en ”), seguido de la descripción del objeto cuyo numero concuerda con locno, seguido del mensaje del sistema 51(”.”). En cualquier caso se ejecutan las acciones [[NEWTEXT|NEwTEXT_ES]] y [[DONE|DONE_ES]].

Ver también:

* [[TAKEOUT|TAKEOUT_ES]]
* [[AUTOP|AUTOP_ES]]
