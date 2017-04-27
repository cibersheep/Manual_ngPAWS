## Las flags \(o banderas\)

A veces en una aventura tenemos que recordar si algo ha pasado antes o no. Por ejemplo, si entramos en la guarida del dragón no veremos lo mismo si ya lo hemos matamos antes que si aún está vivo. Las _flags_ nos permiten guardar esos estados.

Una _flag_ o bandera es una marca, similar a una caja en la que guardamos una bola con un número. Al principio todas las flags contienen una bola con el número 0 pero podemos meter otra en cualquier momento. Existen **256 **_**flags,**_ numeradas del 0 al 255. Algunas de ellas las usa **ngPAWS** para su uso interno \(ver [flags del sistema](flags del sistema)\).

Si continuamos con el ejemplo anterior, después de matar al dragón, podríamos decidir usar la _flag_ 255 para marcar de alguna manera que así lo hemos hecho y, al volver a entrar en su guarida, ver su cadaver o poder ir al castillo a reclamar una recompensa.

¿Cómo lo hacemos? Pues simplemente cambiando la «bola» que hay en la «caja» 255 \(que por defecto es la «bola» con el número 0\) por la «bola» con el número 1. Luego, cada vez que haya que comprobar si el dragón está muerto, bastará con mirar si en la «caja» \(la flag\) 255 hay una «bola» con el número 0 o con el número 1.

Veamos este código en la [_tabla de respuestas_](/La-tabla-de-respuestas.md):

```
MATAR DRAGON
 AT LGuaridaDragon
 CARRIED oEspada
 WRITELN "Con tu poderosa espada matas al dragón."
 DONE
```

Como puedes ver, se comprueba que estamos en el sitio correcto \(`AT lGuaridaDragon`\), que llevamos el objeto correcto \(`CARRIED oEspada`\) y escribimos el texto de que matas al dragón. ¿Pero qué pasa si tras matar al dragón volvemos a escribir «MATAR DRAGON»? Pues que como no hay control de si lo hemos matado o no, lo podemos matar otra vez.

Veamos cómo mejorar esto:

```
MATAR DRAGON
 AT LGuaridaDragon
 CARRIED oEspada
 ZERO 255
 WRITELN "Con tu poderosa espada matas al dragón."
 LET 255 1
 DONE
```

Ahora, antes de intentar matar al dragón, comprobamos que la caja \(la _flag_\) 255 contiene la «bola» con el número 0 \(`ZERO 255`\) y solo si es así \(y por tanto el dragón está vivo\) lo matamos, se escribe la ación y metemos la «bola» con el número 1 en la «caja» 255 \(con la orden `LET 255 1`\). Ahora, si volvemos a intentar matarlo, como la «caja» 255 ya no contiene la «bola» con el número 0, no se continúa de la instrucción `ZERO 255`.

Si en la sección de definiciones especificamos esta _flag_ usando `#define flg fDragonMuerto 255`, nuestro código de matar al dragón puede ser más legible aún porque en lugar de 255 pondremos fDragonMuerto:

```
MATAR DRAGON
 AT LGuaridaDragon
 CARRIED oEspada
 ZERO fDragonMuerto
 WRITELN "Con tu poderosa espada matas al dragón."
 LET fDragonMuerto 1
 DONE
```

Además, si ahora vamos al castillo, podremos reclamar la recompensa solo si hemos matado al dragón.

```
RECLAMAR RECOMPENSA
 AT lCastillo
 NOTZERO fDragonMuerto
 WRITELN "El alguacil te da 1000 monedas de oro."
 DONE
```

En este caso comprobamos con `NOTZERO` que solo se cumple esta condición si en la _flag_ fDragonMuerto no está la «bola» con el número 0.

Este ejemplo tiene un problema similar no obstante: como no comprobamos si la recompensa ya ha sido entregada, acabaremos pudiendo reclamarala cuantas veces queramos. Lo ideal sería usar otra _flag,_ la 254 por ejemplo, para determinar si ya se ha entregado la recompensa. Así si añadimos en la sección de definiciones `#define flg 254 fEntregadaRecompensa` podremos poner:

```
RECLAMAR RECOMPENSA
 AT lCastillo
 NOTZERO fDragonMuerto
 ZERO fEntregadaRecompensa
 WRITELN "El alguacil te da 1000 monedas de oro."
 SET fEntregadaRecompensa
 DONE
```

En este caso puedes ver que hemos usado la instrucción `SET` en lugar de `LET`. `SET` es una acción que mete la «bola» ccon el número 255 en la _flag._ Como en realidad nos da igual si meter la «bola» con el número 1, 3 o 255 \(siempre que no sea 0\) `SET` resulta más cómodo que `LET` a la hora de escribir porque no necesita más parámetros.

### Contando

A veces tenemos que saber qué cantidad de un determinado objeto lleva el personaje, y para ello también, podemos usar una _flag._ Por ejemplo, si definimos `define flg fMonedas 253` después podremos hacer:

```
CONTAR MONEDAS
 WRITE "Llevas "
 PRINT fMonedas
 WRITELN " monedas."
 DONE
```

Con esto, el valor incluido en la _flag_ 253 \(fMonedas\) se mostrará en al llegar a la instrucción `PRINT`. Si en algún sitio hemos hecho un `LET fMonedas 10`, cuando el jugador esciba «CONTAR MONEDAS» se mostrará el mensaje «Llevas 10 monedas.»

Podemos sumar una cantidad al valor de la _flag_ usando [PLUS](PLUS_ES), restarla usando [MINUS](MINUS_ES), etc. \(ver [acciones con flags](Acciones con flags)\). Así, podemos simular como el jugador gana, gasta o pierde monedas. Por ejemplo, al recibir la recompensa en el ejemplo anterior podríamos hacer:

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

Ahora, se suma 1000 a fMonedas, que guarda la cantidad de monedas que lleva el personaje.

