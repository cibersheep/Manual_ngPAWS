**MOVE flagno**

Esta es una acción muy poderosa diseñada para manipular NPCs. Permite que el verbo de la sentencia lógica actual
se revise para la conexiones de la localidad cuyo número ahora está en el flag flagno.

Si se encuentra una conexión en la localidad indicada en la dirección indicada por el verbo de la frase actual, el flag flagno cambiará su valor al de la localidad destino de dicha conexión.

Si el verbo no se encuentra en la tabla de conexiones, o la localidad original contenida en el flag no es válida, ngPAWS ejecuta el siguient condacto.

Esta funcionalidad puede usarse para dotar a los personajes de un movimiento aleatorio en direcciónes válidas, cambiando el verbo de la sentencia actual al de cualquier dirección aleatoria, y ejecutar MOVE.

Notese que movimientos especiales entre localidades que no estén en la tabla de conexiones nos serán considerados por MOVE.