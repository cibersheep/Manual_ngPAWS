**TIME duración opción**

Permite que el input sea "timed-out" tras una duración específica en intervalos de 1,28 segundos (aprox 1/50 de minuto).

Es decir, el proceso 2 será llamado de nuevo si el jugador no teclea nada en cierto tiempo.

La "opción" permite que el "timeout" pase solo cuando el jugador no ha tecleado nada (valor ), o incluso si lo ha hecho (valor 0) .

`TIME 0 0` evitará que haya timeouts (que es lo que ocurre por defecto)