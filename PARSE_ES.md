**PARSE**

Esta acción está diseñada para manejar las convesaciones con NPC. Cualquier frase, es decir, cualquier orden del jugador englobada en comillas [" "], es convertida en una sentencia logica, sobreescribiendo la actual sentencia lógica. Si no había frase o no es válida, ngPAWS ejecutará el siguiente condacto. En otro caso la siguiente entrada es evaluada, pero ya con la nueva SL.

Dado que sobreescribe la actual sentencia lógica debe ser usado solo una sub-tabla de respuestas (normalmente un proceso) :


```
_	_	PARSE			
		WRITELN "No te entiendo" ; No hay más frases pendiente o no se entendió
		DONE

verbo  nombre	Lista de CondActos		; Cualquier frase que el NPC entienda

_	_	WRITELN "No te entiendo" ; o mensaje similar para cualquier LS que sí tenía sentido pero no habíamos considerado
```

Habrá una o más entradas que llamen a ese proceso:

```
DECIR	nombre
 SAME	pos 38	; Está aquí
 PROCESS y	; Hablar...
 DONE		; la SL destruida así que siempre DONE

DECIR NOMBRE	
 WRITELN "¡No está aquí!"
 DONE
```

Por supuesto, cada frase que el NPC pueda entender debe tener sus verbos o nombres en el vocabulario.