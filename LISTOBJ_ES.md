**LISTOBJ**

Si hay objetos en la localidad actual del jugador se muestra el mensaje 1 ("Puedes ver:"), seguido de una lista de objetos presentes. Si no hay ningún objeto no se escribe nada.

Notas:

- LISTOBJ se ve afectado por el bit 6 del [Flag 12](flags del sistema), sobre si el listado debe hacerse con un objeto por línea, o todos en la misma línea separados por comas.
- LISTOBJ se ve afectado por el bit 3 del [Flag 12](flags del sistema), sobre si deme mostrar los objetos con atributo aNPC o no.
- Si algún objeto se mostró durante LISTOBJ, el bit 7 del [flag 12](flags del sistema) se pone a uno, en caso contrario se pone a 0.
- LISTOBJ no lista objetos con el atributo aScenery o aConcealed.

Ver también:

* [LISTAT](LISTAT_ES)
* [LISTNPC](LISTNPC_ES)
* [INVEN](INVEN_ES)
* [LISTCONTENTS](LISTCONTENTS_ES)