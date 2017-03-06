Un bloque de código es una serie de instrucciones que se ejecutan juntas en cualquier caso. Resultan muy cómodos cuando se usan junto con [condactos sharp](condactos sharp) y [condactos colon](condactos colon).

Por ejemplo, en los condactos sharp de este ejemplo:

```
WRITE "Hay un candado."
CARRIED# oLlave WRITE  "Llevas la llave."
CARRIED# oLlave WRITE "Y brilla."
CARRIED# oLlave SET fLlaveBrillanteVista
```

con bloques de código lo puedes escribir así:

```
WRITE "Hay un candado."
CARRIED# oLlave 
{
 WRITE  "Llevas la llave."
 WRITE "Y brilla."
 SET fLlaveBrillanteVista
}
```

Es decir, si el condacto "CARRIED# oLlave" tiene éxito, las tres acciones entre las llaves se ejecutan.

Combinado con condactos colon es aún más potente:

```
LET fCuenta 100
NOTZERO: fCuenta
{
 PRINT fCuenta
 NEWLINE
 MINUS fCuenta 1
}
```

Como las condiciones colon son evaluadas hasta que resultan falsas, y tras cada evaluación verdadera la siguiente instrucción es ejecutada, siendo en este caso la siguiente instrucción un bloque, todo el bloque es ejecutado cada vez. En la práctica el bloque superior imprime los número de 100 a 0.

