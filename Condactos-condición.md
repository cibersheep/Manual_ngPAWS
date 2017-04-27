## _Condactos_ de condición

### _Condiciones_ de localidad

Las siguientes condiciones tiene éxito o no, dependiendo de la localidad actual del jugador:

* [AT](/Lista-alfabética-de-condactos.html#at)
* NOTAT
* ATGT
* ATLT
* ATGE
* ATLE
* ZONE

### Condiciones de objetos

Estas condiciones tendrán éxito o no, dependiendo de dónde estén determinados objetos:

* ABSENT
* PRESENT
* CARRIED
* NOTCARR
* WORN
* NOTWORN
* ISAT
* ISNOTAT

### Condiciones de atributos de objetos

Estas condiciones tienen éxito o no, dependiendo de los atributos de los objetos consultados:

* OZERO
* ONOTZERO
* ISLIGHT
* ISNOTLIGHT
* OBJFOUND
* OBJNOTFOUND

### Condiciones de _flags_

Las siguientes condiciones tienen éxito o no, dependiendo del valor de los _flags:_

* EQ
* NOTEQ
* LT
* GT
* ZERO
* NOTZERO
* GE
* LE
* SAME
* NOTSAME

**Uso de flags a nivel de bit**

* BZERO
* BNOTZERO

### Condiciones de vocabulario

Estas condiciones tiene éxito dependiendo de la orden dada por el jugador:

* NOUN2
* PREP
* ADVERB
* ADJECT1
* ADJECT2

### Condiciones de sonido o música

Estas condiciones tienen éxito o no, dependiendo de si se está reproduciendo determinada música o efectos:

* ISMUSIC
* ISNOTMUSIC
* ISSOUND
* ISNOTSOUND

### Condiciones aleatorias o de tiempo

Estas condiciones tienen éxito dependiendo de eventos basados en el tiempo o la aleatoriedad:

* CHANCE
* TIMEOUT

### Condiciones de control del _parser_

En general, estas condiciones son solo para expertos porque permiten cambiar la manera en que el [bucle principal](/El-bucle-principal.md) de **ngPAWS** funciona. Te recomiendo que las leas más adelante si es la primera vez que vas a usar **ngPAWS.** En caso contrario, no te preocupes si no entiendes bien alguna de ellas.

* ISDONE
* ISNOTDONE
* ISDOALL
* ISNOTDOALL
* ISMOV
* ISNOTMOV
* ISRESP
* ISNOTRESP



