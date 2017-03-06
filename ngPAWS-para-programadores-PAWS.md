Si has programado en PAWS con anterioridad, ¿qué debes saber para usar ngPAWS?

Algunos puntos importantes:


* En general, ya no necesitas usar los mensajes, si quieres escribir algo en pantalla simplemente usa los condactos  [[WRITE|WRITE_ES]] o [[WRITELN|WRITELN_ES]]. Puedes además usar [[tags de secuencia]] en esos textos (y también en los mensajes tradicionales, descripciones de localidades y de objetos) para hacerlos parcialmente variables. Por ejemplo puedes hacer el texto para una linterna sea "una linterna cargada al xx%" describiéndola como "una linterna cargada al {FLAG|100}%", y el texto mostrado será "una linterna cargada al 50%" cuando el valor del flag 100 sea 50.

* No necesitas anotar los números de objetos, flags, etc. para recordar después que objeto es el 4 o que flag usaste para guardar el estado del dragón (vivo o muerto). Simplemente usa las funcionalidades que da [[txtpaws|txtpaws_es]] para hacerlo más fácil. Así en la primera sección del código (o en cualquier sitio en realidad) puedes poner:

```
#define flg fDragonIsDead 100
#define loc lDragonslair 4
#define obj oSword 5
...
...
...
KILL DRAGON
 AT lDragonsLair
 CARRIED oSword
 NOZTERO fDragonIsDead
 WRITELN "The Dragon is already dead."
 DONE

```

* Puedes añadir una imagen de localidad con solo añadir la imagen a la carpeta "dat" de tu aventura, y poniendo esto en la zona de definiciones (al principio):

```
#define pic GuaridaDragon.png 4
```

Ten en cuanta que la imagen que utilices para la localidad 0 será usada para las localidades sin luz.

* El onjeto 0 no es una fuente de luz, si quieres que lo sea, le tienes que poner el atributo aLight en la sección de objetos.

*  Hay muchos más [atributos de objeto](atributos de objeto) en ngPAWS.

* Hay muchos [[condactos]] nuevos.

* La base de datos de inicio es enorme comparada con la de PAW, y facilita respuestas por defecto para muchísimas cosas.

* Puedes marcar un proceso que crees como "interrupción". Eso hará que el proceso se ejecute cada 40 milisegundos, permitiendo hacer cosas mientras el jugador teclea (como reproducir sonidos, cambiar el gráfico de localidad, hacer que determinados eventos ocurran en tiempo real y no por turnos, etc.)

* ngPAWS te permite hacer cierto programación estructuradas, usando [[condactos sharp]], [[condactos colon]]y [[bloques de código]].

* ngPAWS no es expandible usando EXTERN para ejecutar código máquina del Z80. En su lugar usa javascript. Si sabes javascript puedes crear condactos (ver [[creando tus propios condactos]]) o añadiendo librerías (ver [[Expandiendo las funcionalidades de ngPAWS]].)


