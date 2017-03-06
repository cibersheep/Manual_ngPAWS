**PROMPT** sysno.

El valor sysno se almacena en el flag 42. ngPAWS mostrará el mensaje del sistema indicado en el interior de la caja de input hasta que el jugador teclee algo.

Si el valor es 0, entonces los mensajes del sistema 2, 3, 4 y 5 se mostrarán aleatoriamente con una probabilidad de 30:30:30:10 respectivamente.

Si no quieres que salga ningún mensaje en la caja de input del jugador, puedes crear un mensaje del sistema vacío en la solapa STX (por ejemplo el 1000):

```
\1000
```

Y luego, en el proceso 1, al principio de la aventura (entrada "AT 0") poner:

```
PROMPT 1000
```