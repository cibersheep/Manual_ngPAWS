Esta acción salta al final de la tabla de procesos en ejecución diciéndole a ngPAWS que se ha finalizado sin un acción. Es decir, no se consideran más condactos o entradas.

Se produce un retorno a la tabla de procesos que llamó a la actual, o al inicio del bucle DOALL si estamos dentro de uno.

Si al finalizar no hay una conexión valida para la frase actual, se muestra el mensaje "No puedes hacer eso."