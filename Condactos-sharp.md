Todos los condactos condición pueden ser modicados añadiendo el símbolo sharp/almohadilla (#) como sufijo (Por ejemplo NOTZERO# en lugar de NOTZERO).

Cuando una condición es modificada con sharp y la condición falla, no dejará de ejecutarse la entrada completa, sino solamente el siguiente condacto.

Por ejemplo, el siguiente código escribirá "Hay un candado." si no llevas la llave. Y el texto "Hay un candado. Llevas la llave." si la llevas. Si el condacto CARRIED no llevara el modificador sharp, no se escribiría nada de no llevar la llave.
```
WRITE "Hay un candado."
CARRIED# oLlave
WRITE "Llevas la llave."
```

También puee escribir este código así, que probablemente es más claro:

```
WRITE "Hay un candado."
CARRIED# oKey WRITE "Llevas la llave."
```

porque queda como  _si llevas la llame escribe "...._

En este ejemplo, "hay un candado" siempre es escrito, pero "llevas la llave" solo se escribe si la llevas.

### Notas
* Los condactos sharp pueden ser concatenados de manera que todos los condactos sharp en fila deben tener exito para que el primer condacto no sharp tras ellos se ejecute.:

```
```

Esto sería como  _si llevamos la llave y el flag fCerradoConLLave es cero entonces escribe "...._

Escrito de la otra manera:

```
WRITE "Hay un candado." 
CARRIED# oLlave ZERO# fCerradoConLlave WRITE "Llevas la llave."
```

* ¿y si queremos que se ejecuten varias acciones si la condición es cierta?

Entonces puedes hacerlo así:

```
WRITE "Hay un candado."
CARRIED# oLlave WRITE  "LLevas la llave."
CARRIED# oLlave WRITE "Y brilla."
CARRIED# oLlave SET fLlaveBrillanteVista

```

o puedes usar [bloques de código](bloques de código) junto con los condactos sharp.


**Ver también:**

[Condactos colon](Condactos colon)