**LISTAT locno+**

Si hay objetos presentes en la localidad locno son listados, en caso contrario se muestra el mensaje del sistema 53 ("Nada de nada"). Normalmente tendrás que preceder el listado con algún texto ("En la caja hay:" o similar)

Es posible crear una alternativa a [INVEN](INVEN_ES) usando los parámetros 253 y 254 (objetos puestos o llevados)con LISTAT.

Notas:

- LISTAT se ve afectado por el bit 6 del [Flag 12](flags del sistema), sobre si debe hacerse el listado con cada objeto en una línea, o como una lista continua separada por comas.
- LISTAT se ve afectado por el bit 3 del [Flag 12](flags del sistema), sobre si deben incluirse o no los objetos marcados con el atributo aNPC en la lista.
- Si algún objeto fue mostrado durante LISTAT, el bit 7 del [flag 12](flags del sistema) se pondrá a uno, en caso contrario se pondrá a 0.
- LISTAT no lista objetos con [atributos](atributos de objeto) aScenery o aConcealed. 

Ver también:


* [INVEN](INVEN_ES)
* [LISTOBJ](LISTOBJ_ES)
* [LISTNPC](LISTNPC_S)
* [LISTCONTENTS](LISTCONTENTS_ES)