**LISTCONTENTS locno**

Si hay algún objeto presente en la localidad, son listados entre paréntesis, precedidos del mensaje del sistema 66 si la localidad locno corresponde a un contenedor, o del 67 si corresponde a una superficie. En español ambos mensajes son iguales por defecto (da igual decir "en la caja hay" que "en la mesa hay") pero en inglés son diferentes ("on the table", "in the box").

Notas importantes:

- LISTCONTENTS no se ve afectada por el bit 6 del  [Flag 12](system flags) sobre si listar los objetos uno por fila o todos en una lista continua separada por comas, siempre lo hace en lista continua.
- LISTCONTENTS se ve afectado por el bit 3 del Flag 12, sobre si listar los objetos con atributo aNPC o no.
- Si algún objeto se musetra durante el LISTCONTENTS, el bit 7 del flag 12 se pone a 1, en caso contrario se pone a 0.
- LISTCONTENTS no lista objetos con atributo aScenery o aConcealed.
- Si la localidad no contiene nada, o no contiene objetos que puedan listarse no se escribe nada (si siquiera los paréntesis).

Ver también:

* [INVEN](INVEN_ES)
* [LISTOBJ](LISTOBJ_ES)
* [LISTNPC](LISTNPC_ES)
* [LISTAT](LISTAT_ES)