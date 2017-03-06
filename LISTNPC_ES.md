**LISTNPC locno+**

Si hay objetos con el atributo aNPC en la locaidad indicada por locno, los mensajes del sistema 63, 64 y 65 son mostrados para hacer una lista "Puedes ver a ", seguido de la lista de objetos aNPC. Si no hay ninguno, no se muestra nada.

Notas:

- LISTNPC se ve afectado por el bit 6 del [Flag 12](flags del sistema), sobre si listar los NPC uno por línea o de manera continua separados por comas.
- LISTNPC no se ve afectado por el bit 3 del  Flag 12, sobre si deben o no mostrarse objetos con el atributo aNPC (por razones obvias).
- Si se encontró algún objeto durante LISTNPC, el bit 5 del flag 12 se pone a 1, en caso contrario a 0.
- LISTNPC no lista objetos con el atributo aNPC que además tienen el atributo aConcealed.

Ver también:

* [LISTAT] (LISTAT_ES)
* [LISTOBJ] (LISTOBJ_ES)
* [INVEN] (INVEN_ES)
* [LISTCONTENTS](LISTCONTENTS_ES)