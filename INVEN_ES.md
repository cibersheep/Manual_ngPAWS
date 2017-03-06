**INVEN**

Lista los objetos en el inventario del jugador.

* INVEN no se ve afectada por el bit 6 del [Flag 12](flags del sistema), en relacion a si se escriben como una lista con un objeto por linea, o como una lista separada por comas.
* INVEN sí se ve afectada por el bit 3 del [Flag 12](flags des sistema), en relacion a si los objetos marcados con el atributo aNPC deben ser mostrados o no.
* INVEN no activa o desactiva el bit 7 del [flag 12](flags del sistema).
* INVEN lista todos los objetos, no importa si tiene el atributo aConcealed, aNPC o aSecenery. Si el jugador consiguió tomar alguno de esos objetos y están en su inventario, deben listarse.

Ver también:

* [LISTAT](LISTAT_ES)
* [LISTOBJ](LISTOBJ_ES)
* [LISTNPC](LISTNPC_ES)
* [LISTCONTENTS](LISTCONTENTS_ES)