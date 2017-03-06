Un bloque de código es un grupo de instrucciones que van juntas no importa lo que pase, y resultan muy poderosas combinadas con [condactos sharp](condactos sharp) y [condactos colon](condactos colon).

Por ejemplo, en la explicación de [condactos sharp](condactos sharp) teníamos este ejemplo:

```
WRITE "Hay un candado."
CARRIED# oLlave WRITE  "Llevas una llave."
CARRIED# oLlave WRITE "Y brilla."
CARRIED# oLlave SET fLlaveBrillanteVista

```

con bloques de código se puede escribir así:

```
WRITE "Hay un candado."
CARRIED# oLlave 
{
    WRITE  "Llevas una llave."
    WRITE "Y brilla."
    SET fLlaveBrillanteVista
}
```

Esto es, si la condición "CARRIED# oLlave" tiene éxito, todas las acciones entre las llaves se ejecutarán.

* Ten en cuenta eso sí, que si una de las instrucciones entre las llaves es una condición, entonces la ejecuciñon del bloque se para en ese punto.

Combinado con condiciones colon es aún más poderoso. Ver este ejemplo:

```
LET fCuenta 100
NOTZERO: fCuenta
{
 PRINT fCuenta
 NEWLINE
 MINUS fCuenta 1
}
```

Como las condiciones colon son evaluadas hasta ser falsas, y cada evaluación verdadera la siguiente instrucción es ejecutada, y en este caso la siguiente instrucción no es una instrucción sino un bloque, por cada evaluación verdadera el bloque entero (las tres instrucciones) es ejecutado.

Ese código escribe en pantalla todos los números del 100 al 1.
