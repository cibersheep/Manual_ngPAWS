En general, el jugador utilizará la clásica forma 

`DECIR A MANOLO "TAL Y CUAL"`

Para dar soporte a esto tenemos que hacer lo siguiente:

En la tabla de respuestas (RESP) añadimos esta entrada en el sitio habitual:

```
DECIR MANOLO
 PROCESS 4
 DONE
```
`
En el proceso 4 ponemos esto
```
_ _
 PARSE
 WRITE "Manolo te mira extrañado."
 DONE

AYUDAME _
 WRITELN "Manolo: Ya tengo bastante con lo mío."
 DONE

SUBE CAMPANARIO
 WRITELN "Manolo: Ok, voy para allá."
 DOONE

_ _
 WRITELN "Manolo: No te entiendo."
 DONE 
```

Ni que decir tiene, que si el proceso 4 ya lo tenemos usado para alguna otra cosa, podemos usar cualquier otro número.

Esto funciona así:

* Desde la tabla de respuestas se llama al proceso 4 cuando el jugador escribe "DECIR MANOLO...". En el ejemplo no hemos comprobado que Manolo esté presente, pero obviamente sería bastante importante hacerlo. 

- En el proceso 4 primero habrá un PARSE, que lo que hace es tratar de sacar la frase siguiente de lo que tecleó el jugador (por ejemplo si tecleó DECIR MANOLO "SUBE CAMPANARIO"  la siguiente frase es SUBE CAMPANARIO). Si no lo consigue PARSE, que es además una condición, tiene éxito, y por tanto se pasa a las siguientes entradas (Manolo te mira extrañado, y DONE para que termine el proceso). 

- Después podéis ver una entrada por cada respuesta lógica que puede dar Manolo (en este ejemplo no ninguna tiene condiciones, pero obviamente podéis ponerlas, y también acciones). Por ejemplo podríamos poner:

```
DAME LLAVES
 ISAT oLLaves 252
 PLACE oLlaves 254
 WRITELN "Manolo: aquí tienes."
 DONE
```

- Finalmente hay una entrada para dar una respuesta genérica si el jugador no escribió ninguna de las frases que habíais considerado (Manolo: No te entiendo.).

La diferencia entre el primer mensaje de que Manolo te mira extrañado, y el de no te entiendo, es que en el primer caso el parser no consiguió encontrar nada después del DECIR MANOLO, bien porque no lo había (el jugador escribió "DECIR MANOLO", bien porque no había ninguna palabra válida (DECIR MANOLO "YQWTEUFHASD"). En el segundo caso sí se encontró una frase válida, pero no concordaba con ninguna de las que habíamos previsto (En el ejemplo ocurriría si ponemos DECIR MANOLO "ARREGLA LAVADORA" por ejemplo).
