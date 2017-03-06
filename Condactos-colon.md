Si no has leido [condactos sharp](condactos sharp) aun, por favor hazlo ahora, y después lee esta entrada.

Los condactoscolon son condactos de condición modificados con un sufijo "dos puntos" (colon en ingléS) 

`NOTZERO:`

Puedes usarlos de la misma manera que usas los [condactos sharp](condactos sharp) pero en lugar de evaluar la condicion una vez, esta será evaluada hasta que sea falsa. Mientras tanto el condacto que va después del condacto colon será ejecutado una y otra vez.

Ejemplo:

```
NOTZERO: fCuenta MINUS fCuenta 1
 PRINT fCuenta
```

NOTZERO fCuenta es evaluado, y si es verdadero, entonces MINUS fCuenta 1 es ejecutado. Entonces NOTZERO fCuenta es evaluado, y si es verdadero, entonces MINUS fCuenta 1 es ejecutado, etc. Una vez el valor de fCuenta es cero, la condición fallará y se ejecutará la siguiente entrada (PRINT fCuenta).

Importante: cuando usamos condactos colon, debemos asegurarnos de que la acción tras la condición, tarde o temprano hará la condición falsa, porque de oto modo el juego entraría en un bucle sin fín. En el ejemplo anterior el flag fCuenta es decrementado hasta que llega a cero, cosa que ocurrirá tarde o temprano.

En realidad, el uso de condactos colon tal como hemos explicado es limitado, pero su poder se desata cuando se usa combinado con [bloques de codigo](bloques de codigo).

**Ver también:**

* [condactos sharp](condactos sharp)
* [bloques de codigo](bloques de codigo)