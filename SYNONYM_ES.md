**SYNONYM verbo nombre**

Reemplaza la frase actual por la especificada por verbo+nombre

Es útil para crear frases sinónimas en lugar de palabras sinónimas:

Ejemplo:

```
INSERTAR MONEDA
 SYNONYM JUGAR MAQUINA

PULSA 1PLAYER 
 SYNONYM JUGAR MAQUINA

JUGAR MAQUINA
 AT lEsquinaMaquinaArcade
 ....
 DONE

```

Este ejemplo funcionará si el jugador escribe "JUGAR MAQUINA", "INSERTAR MONEDA" o "PULSA 1PLAYER".

Algunos preferiréis escribirlo así:

```
INSERTAR MONEDA SYNONYM JUGAR MAQUINA
PULSA 1PLAYER  SYNONYM JUGAR MAQUINA
JUGAR MAQUINA
 AT lEsquinaMaquinaArcade
 ....
 DONE

```

