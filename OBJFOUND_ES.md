**OBJFOUND attrno locno+**

Esta condición tiene éxito si hay algun objeot en la localidad locno con el atributo attrno a uno. Si así ocurre el flag 11 contendrá el número delprimer objeto con ese atributo que se encontró. Si falla, el valor 255 quedará en el flag 11.

_Notas importantes:_

* Si queremos usar OBJFOUND con la localida actual hay que poner @38 como "locno".
* OBJFOUND ifnora el bit bit 3 del flag 12, es decir, comprobará el atributo pedido también el los objetos con el atributo aNPC.

Ver también:

[OBJNOTFOUND](OBJNOTFOUND_ES)
