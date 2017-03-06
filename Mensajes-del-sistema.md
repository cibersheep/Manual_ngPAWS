Los mensajes del sistema son mensajes predeterminados usados por ngpaws (por ejemplo los mensajes que aparecen cuando se toman o dejan objetos, los movimientos en distintas direcciones, etc.). Puedes cambiarlos en caso que quieras que dichos mensajes encajen mejor con el contexto de tu aventura.

Para notas sobre compatibilidad hacia atrás con PAW y Superglús tienes estes artículo: [compatibilidad hacia atras](compatibilidad hacia atras)



|Nº de mensaje| Función|
|----------|------------|
|0 | aparece en lugar de la descripción de localidad si la localidad está oscura.|
|1 | aparece si la lista escrita por [LISTBOBJ](LISTOBJ_ES) tiene al menos un objeto.|
|2 to 5 | (obsoletos, no se usan) |
|6 | aparece cuando el parser no puede entender nada de lo tecleado por el jugador.|
|7 | aparece cuando no se ha ejecutado ningun acción (o se ejecutó [NOTDONE](NOTDONE_ES)) en la tabla de respuesta y el verbo es inferior al verbo 14|
|8 | aparece cuando no se ha ejecutado ningun acción (o se ejecutó [NOTDONE](NOTDONE_ES)) en la tabla de respuesta y el verbo es superior o igual al verbo 14|
|9 | Llevas (acción [INVEN](INVEN_ES) )|
|10 | Mensaje mostrado al listar objetos si el objeto lo llevamos puesto "(puesto)" |
|11 | Mensaje mostrado por la acción INVEN cuando el jugador no lleva nada.|
|12 | Mostrado por [QUIT](QUIT_ES)|
|13 y 14 | mostrados por la acción [END](END_ES)|
|15 | El mensaje de la acción [OK](OK_ES).|
|16 | "Pulsa una tecla", el mensaje para la acción [ANYKEY](ANYKEY_ES)|
|17 a 20 | Son los mensaje de la acción [TURNS](TURNS_ES) : Has jugado xx turno(s).|
|21 y 22 | Son los mensajes para la acción  [SCORE](SCORE_ES) : Tu puntuacion es del xx%.|
|23| Mensaje mostrado cuando el jugador trata de quitarse un objeto que no lleva puesto.|
|24| Mensaje usado por varios [condactos](condactos) para evitar que el jugador haga algo con ese objeto mientras lo lleva puesto.|
|25| Mensaje mostrado cuando el jugador trata de tomar un objeto que ya tiene.|
|26| Mensaje mostrado cuando el jugador trata de tomar un objeto que no está accesible o simplemente no está presente.|
|27| Mensaje mostrado cuando el jugador trata de tomar más objetos de los que puede llevar. Ver la acción [ABILITY](ABILITY_ES)y el [flag 37](flags del sistema)|
|28| Mensaje mostrado en varias situaciones en las que el jugador trata de interactuar con un objeto que no tiene: No tienes eso.|
|29 | Mostrado cuando el jugador trata de ponere un objeto que ya lleva puesto.|
|30 | La respuesta positiva esperada por [END](END_ES) y [QUIT](QUIT_ES).|
|31 | La respuesta negativa esperada por [END](END_ES) y [QUIT](QUIT_ES).|
|32 | Mostrado cuando se llena la pantalla de texto (obsoleto).|
|33 | (obsoleto)|
|34 | (obsoleto)|
|35 | Mostrado cuando ocurre un timeout|
|36| Mostrado cuando el jugador toma un objeto: Tomas xxxx|
|37| Mostrado cuando el jugador se pone un objeto: Te pones xxxx|
|38| Mostrado cuando el jugador se quita un objeto:Te quitas xxxx|
|39| Mostrado cuando el jugador deja un objeto: Dejas xxxx |
|40| Mostrado cuando el jugador trata de ponerse un objeto que no es una prenda: : No te puedes poner eso|
|41| Mostrado cuando el jugador trata de quitarse un objeto que no es una prenda: No te puedes quitar eso|
|42| Mostrado cuando el jugador trata de quitarse un objeto pero ya lleva demasiadas cosas en las manos. Ver la acción [ABILITY](ABILITY_ES) y el [flag 37](flags del sistema)|
|43| Mostrado cuando el jugador trata de tomar un objeto, pero el peso del objeto, o del objeto combinado con los objetos que el jugador ya lleva, excede del peso máximo soportado por el jugador. Ver la acción [ABILITY](ABILITY_ES) y el [flag 37](flags del sistema)|
|44| Mostrado cuando el jugador pone un objeto en un contenedor o superficie: pones xxxx en yyyy|
|45| Mostrado en varios casos en los que el jugador trata de sacar algo de un contendor o tomarlo de una superficie y no es posible|
|46 | el nexo de unión en las listas de objetos cuando se listan en una sola fila (generalmente una coma)|
|47 | el nexo de unión entre los dos últimos elementos de una lista ("y")|
|48 | la terminación de una lista de objetos (usado por [LISTOBJ](LISTOBJ_ES) y [LISTAT](LISTAT_ES))|
|49|  Mensaje mostrado cuando el usuario trata de hacer algo con un objeto que no lleva.|
|50 | Mostrado cuando el jugador trata de quitarse un objeto que no lleva puesto.|
|51 | La terminación para una frase compuesta en [PUTIN](PUTIN_ES) / [TAKEOUT](TAKEOUT_ES) and [AUTOP](AUTOP_ES) / [AUTOT](AUTOT_ES))|
|52 | Fin de frase para los mensajes que empiezan por el 51|
|53 | Mensaje para [LISTAT](LISTAT_ES) si no hay objetos.|
|54-60 | Varios mensajes para las acciones de LOAD/SAVE|
|61| (obsoleto)|
|62| Mensaje similar al mensaje 6, pero para cuando el parser no solo no entendio ninguna frase, sino que fue incapaz de entender una sola palabra.|
|63-65|	 Usados por  [LISTNPC](LISTNPC_ES) para listar NPCs.|
|66| Usado por [LISTAT](LISTAT_ES) para listar los contenidos de contenedores transparentes: "dentro puedes ver"|
|67| Usado por [LISTAT](LISTAT_ES) para listar los objetos sobre superficies: "encima puede ver"|
|68| Similar al mensaje 44, pero para objetos superficie: Pones xxxx sobre yyyy|
|69| Similar al mensaje 45, pero para objetos superficies: No puedes coger xxxx de encima de yyyy.|