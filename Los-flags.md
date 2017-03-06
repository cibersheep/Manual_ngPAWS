### Los flags

A veces en una aventura tenemos que recordar si algo ha pasado antes, por ejemplo si entramos en la guarida del dragón no veremos lo mismo si ya lo matamos antes, que si aún está vivo. Los flags nos permiten guardar esos estados.

Un flag es como una caja, en la que guardamos una bola con un número, al principio todos los flags contienen una bola con el número 0, pero podemos meter otra en cualquier momento. Hay 256 flags, del flag 0 al 255, aunque algunos los usa ngPAWS para cosas suyas (ver [flasg del sistema](flags del sistema). Así por ejemplo si matamos al dragón podríamos decidir usar el flag 255 para marcar de alguna manera que lo hemos hecho, y así, por ejemplo, al entrar en su guarida ver su cadaver, o poder ir al castillo a reclamar la recompensa).  

¿Cómo lo hacemos? Pues simplemente cambiando la "bola" que hay en la "caja" 255, que por defecto es la bola 0, por la bola "1". Así luego, cada vez que haya que comprobar si el dragón murió, bastara con mirar si en la "caja" (el flag) 255 hay una bola "0" o una bola "1".

Veamos este código de la tabla de respuestas:

```
MATAR DRAGON
 AT LGuaridaDragon
 CARRIED oEspada
 WRITELN "Con tu poderosa espada matas al dragón."
 DONE
```

Como podéis ver comprobamos que estamos en el sitio correcto (AT lGuaridaDragon), que llevamos el arma correcta (CARRIED oEspada) y escribimos el texto de que matas al dragón. ¿Pero que pasa si tras matar al dragón volvemos a escribir "MATAR DRAGON"? Pues que como no hay control de si lo hemos matado o no, le podemos matar otra vez.

Veamos esta mejora:

```
MATAR DRAGON
 AT LGuaridaDragon
 CARRIED oEspada
 ZERO 255
 WRITELN "Con tu poderosa espada matas al dragón."
 LET 255 1
 DONE
```
Ahora antes de intentar matar al dragón comprobamos que la caja (el flag) 255 contiene la bola "0" (ZERO 255) y solo si es así, y por tanto el dragón está vivo le matamos. Al matarlo además de escribir que lo matamos metemos la bola 1 en la caja (el flag) 255 (LET 255 1). Así si volvemos a intentar matarlo, como la caja 255 ya no contiene la bola 0, no pasaremos del ZERO 255.

Si en la zona definiciones definimos el flag usando `#define flg fDragonMuerto 255` nuestro código de matar al dragón puede ser más legible aún, porque en lugar de 255 pondremos fDragonMuerto

```
MATAR DRAGON
 AT LGuaridaDragon
 CARRIED oEspada
 ZERO fDragonMuerto
 WRITELN "Con tu poderosa espada matas al dragón."
 LET fDragonMuerto 1
 DONE
```

Además, si ahora vamos al castillo podremos reclamar la recompensa, solo si hemos matado al dragón.

```
RECLAMAR RECOMPENSA
 AT lCastillo
 NOTZERO fDragonMuerto
 WRITELN "El alguacil te da 1000 monedas de oro."
 DONE
```

En este caso comprobamos con NOTZERO, que solo se cumple si en el flag fDragonMuerto no está la bola "0". 

Este ejemplo tiene un problema similar no obstante: como no comprobamos que la recompensa ha sido entregada ya, acabaremos pudiendo reclamarala cuantas veces queramos. Lo ideal sería usar otro flag, el 254 por ejemplo, para determinar si hemos entregado ya la recompensa,así si ponemos en la zona de definiciones `#define flg 254 fEntregadaRecompensa` podremos poner:

```
RECLAMAR RECOMPENSA
 AT lCastillo
 NOTZERO fDragonMuerto
 ZERO fEntregadaRecompensa
 WRITELN "El alguacil te da 1000 monedas de oro."
 SET fEntregadaRecompensa
 DONE
```

En este caso podéis ver que hemos usado SET en lugar de LET. SET es una acción que mete la bola "255" en el flag, como en realidad nos da igual si meter la bola "1" o la "3" o la "255" siempre que no sea la "0", SET resulta más cómodo que LET a la hora de escribir.

### Contando

A veces tenemos que saber que cantidad de un determinado objeto lleva un personaje, y para ello también podemos usar un flag, por ejemplo si definimos `define flg fMonedas 253` después podremos hacer:

```
CONTAR MONEDAS
 WRITE "Llevas "
 PRINT fMonedas
 WRITELN " monedas."
 DONE
```

y el valor incluido en el flag 253 (fMonedas) se mostrará en el PRINT. Si en algún sitio hemos hecho `LET fMonedas 10` ese mensaje saldrá como "Llevas 10 monedas."

Podemos sumar una cantidad al valor del flag usando [PLUS](PLUS_ES), restarla usando [MINUS](MINUS_ES), etc. (ver [acciones con flags](Acciones con flags)). Así podemos simular como el jugador gana, gasta o pierde monedas. Por ejemplo al recibir la recompensa en el ejemplo anterior podríamos hacer:

```
RECLAMAR RECOMPENSA
 AT lCastillo
 NOTZERO fDragonMuerto
 ZERO fEntregadaRecompensa
 WRITELN "El alguacil te da 1000 monedas de oro."
 SET fEntregadaRecompensa
 PLUS fMonedas 1000
 DONE
```
