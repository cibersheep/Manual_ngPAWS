En algunas aventuras es posible controlar a más de un personaje (PJ), vamos a ver como podemos hacer esto con ngPAWS. Primero algunos datos:

* Tendremos dos PJs: Pedro y Pablo.
* Inicialmente empezaremos manejando a Pedro.
* Para cambiar de uno a otro ejecutaremos la órden CAMBIO (en tu aventura puedes decidir como llegas a manejar a cada uno).
* La localidad del PJ que manejamos estará en el flag 38, como siempre, la localidad del PJ que no manejamos estará en el flag fOtroPJLoc.
* Los objetos que lleve el otro jugador estarán el la localidad lOtroPJLlevados, y los que lleve puestos en lOtroPJPuestos. Obviamente debemos dejar sin usar dichas localidades. Además tendremos una localidad lAux para hacer algunas cosas (tampoco debe usarse), y un flag auxiliar fAux.
* Tendremos una constante que definimos previamente llamada NUMERO_ULTIMO_OBJETO, que contendrá el número del último objeto.

### El proceso de cambio

Para cambiar de un jugador a otro debemos, básicamente :+1: 

* Intercambiar los valores de los flags de localidad (38 y fOtroPJLoc)
* Intercambiar los objetos de la localidad 254 y lOtroPJLlevados
* Intercambiar los objetos de la localidad 253 y lOtroPJPuestos


Bien, manos a la obra, por comodidad pondremos todo en un proceso:

```
CAMBIO _
 PROCESS 10
 DESC
```

En el proceso 10:

```
_ _ ; Cambio de flags
 COPYFF 38 fAux          
 COPYFF fOtroPJLoc 38
 COPYFF fAux fOtroPJLoc

_ _; Cambio de objetos llevados
 CLEAR fAux                          
 LE. fAUX NUMERO_ULTIMO_OBJETO       ; Primero pongo todos los que lleva el jugador en la localidad lAux
 {
   CARRIED @fAux
   PLACE @fAux lAux
   PLUS fAux 1
 }
 CLEAR fAux
 LE. fAUX NUMERO_ULTIMO_OBJETO       ; Ahora muevo todos los que estaban en la localidad del PJ inactivo 
 {
   ISAT @fAux lOtroPJLlevados
   PLACE @fAux 254
   PLUS fAux 1
 }
 CLEAR fAux
 LE. fAUX NUMERO_ULTIMO_OBJETO       ; Y ahora muevo todos los que había en lAux al inventario inactivo
 {
   ISAR @fAux lAux
   PLACE @fAux lOtroPJLlevados
   PLUS fAux 1
 }

_ _; Cambio de objetos puestos
 CLEAR fAux                          
 LE. fAUX NUMERO_ULTIMO_OBJETO       ; Primero pongo todos los que lleva puestos el jugador en la localidad lAux
 {
   WORN @fAux
   PLACE @fAux lAux
   PLUS fAux 1
 }
 CLEAR fAux
 LE. fAUX NUMERO_ULTIMO_OBJETO       ; Ahora muevo todos los que estaban en la localidad de puestos del PJ inactivo 
 {
   ISAT @fAux lOtroPJPuestos
   PLACE @fAux 253
   PLUS fAux 1
 }
 CLEAR fAux
 LE. fAUX NUMERO_ULTIMO_OBJETO       ; Y ahora muevo todos los que había en lAux al inventario de puestos inactivo
 {
   ISAR @fAux lAux
   PLACE @fAux lOtroPJPuestos
   PLUS fAux 1
 }

```

Como podéis ver, hago uso de los [[condactos colon]] y [[bloques de código]] para recorrer la lista completa de objetos comprobando si están en un sitio concreto y moviendolos. Existe otra aproximación, que es usar [[DOALL|DOALL_ES]], al viejo estilo de PAWs o ngPAWS.

No voy a dar la solución completa con DOALL, porque es un método algo arcaico, pero puedo dejar apuntado que para mover todos los objetos llevados a la localidad lOtroPJLlevados sería

```
 _ _
  DOALL 254
  PUTO lOtroPJLlevados
````

Sin embargo hay que entender bien DOALL porque ejecutará para cada objeto no solo ese PUTO, sino todas las entradas posteriores, con lo cual hay que controlar eso de modo que no se produzcan ejecuciones anidadas. Para ello el condacto [[ISDOALL|ISDOALL_ES]] puede ser útil.

Aparte de el proceso de cambio, es posible que en vuestras aventuras tengáis que llevar un control de qué personaje jugador estáis controlando (Pedro o Pablo), si los PJs son diferentes (por ejemplo si uno es fuerte, pero el otro es alto, puede que Pedro pueda cargar con más objetos, con lo cual en el momento del cambio habrá que llamar a ABILITY para marcar esos limites, y puede que Pablo pueda coger objetos que están situados sobre armarios, que Pedro no pueda, con lo que a la hora de COGER CAJA, quizá sea  necesaria una comprobación de quien manejamos)