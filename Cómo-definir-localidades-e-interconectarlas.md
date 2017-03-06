### Localidades
Definir localidades es muy sencillo, accedemos al apartado "Locations" (Localidades, o si no usamos el editor de ngPAWS, al apartado \LTX del fichero .txp), y añadimos una por localidad de este modo:

```
\0
Bienvenido a tu primera aventua.
\1
Estás en el parque.
\2
Estás junto al lago.
\3
Estás en el tiovivo.
```

Así cuantas localidades queramos, pero sin dejar huecos (no podemos poner la 1 y luego la 7).

Además, es recomendable que en el apartado "Definitions" (Definiciones, o al principio del fichero .txp si no usamos el editor de ngPAWS) añadamos unas lineas semejante a estas por cada localidad:

```
#define loc lIntroduccion 0
#define loc lParque 1
#define loc lLago 2
#define loc lTiovivo 3
```

Así después cada vez que queramos hacer referencia a la localidad del parque (que sería la localidad 1) lo haremos poniendo lParque en lugar de 1 (que es más difícil de recordar).

### Conexiones

Para conectar las localidades tenemos que crear las conexiones, para lo cual basta con poner en el apartado Connections (Conexiones, o CNX si no usamos el editor de ngPAWS) algo parecido a lo siguiente:

```
\lIntroduccion

\lParque
NORTE lLago
ESTE lTiovivo

\lLago
SUR lParque

\lTiovivo
OESTE lParque
```

Así la localidad 0 no tiene salidas, la 1 al norte iríamos a la 2 y al este a la 3, en la 2 al sur iríamos a la 1, y en la 3 al oeste iríamos a la 1. Fijaos que hay que poner cada conexión vista por los dos lados, no basta con decir que desde la 1 al norte se va a la 2, para que desde la 2 al sur se vaya a la 1, hay que especificarlo.

Fijaos que aunque las conexiones son como he dicho en el punto anterior, no hemos usado para nada los números, porque usamos en su lugar las "etiquetas" que hemos creado antes (lParque, lLago, etc.)