# MANUAL DE USO DE ngPAWS

## INICIO

Bienvenido al _gitbook_ de **ngPAWS.** En las siguientes páginas encontrarás toda la información necesaria para crear tu propio juego de aventuras de texto con gráficos.

Esta guía te enseñará los conceptos básicos de **ngPAWS.** Es recomendable leerla en su totalidad, aunque sea por encima, antes de mirar los tutoriales. Piensa que no tienes que entenderlo todo a la primera, simplemente léela brevemente de modo que, al llegar a los mencionados tutoriales, haya cosas que te suenen.

Antes de empezar, si eres o fuiste un usuario de **PAWS,** te recomiendo leer la documentación de todas formas. Si no puedes esperar, quizá echarle un simple vistazo a este enlace pueda servirte: [ngPAWS para programadores PAWS](/ngpaws-para-programadores-paws.md).

### Guía básica

* Capítulo 1: [¿Qué es ngPAWS?](/que-es-ngpaws.md)
* Capítulo 2: [Instalación](/instalacion.md)
* Capítulo 3: [La base de datos de la aventura](/la-base-de-datos-de-la-aventura.md)
* Capítulo 4: [La base de datos de inicio](/La-base-de-datos-de-inicio.md)
* Capítulo 5: [La tabla de respuestas](/La-tabla-de-respuestas.md)
* Capítulo 6: [Eventos](/Eventos.md)
* Capítulo 7: [El bucle principal](/El-bucle-principal.md)
* Capítulo 8: [Las flags \(o banderas\)](/Los-flags.md)

### Guía avanzada

* Capítulo 9: [El Proceso interrupción](/El-proceso-interrupción.md)
* Capítulo 10: [Depuración de errores con la consola javascript](/depuracion-de-errores-con-la-consola-javascript.md)
* Capítulo 11: [Complementos y extensiones](/Plugins-y-extensiones-de-ngPAWS.md)

### Referencia

* [Condactos de condición](/Condactos-condición.md)
* [Condactos de acción](/Condactos-acción.md)
* [Condactos especiales](https://github.com/Utodev/ngPAWS/wiki/Condactos-especiales) 
* [Lista alfabética de condactos](/Lista-alfabética-de-condactos.md)

### Tutoriales

Existen dos tutoriales para **ngPAWS:**

* El tutorial «La Torre», basado en el que se hizo en los años noventa para el _parser_ **NMP** y que también fue usado más tarde para explicar cómo funciona el _parser_ **Superglús.** Es muy fácil de enteder \(ha servido de ejemplo incluso para otros _parsers_ como **AGE** o **InformATE**\).
* El tutorial clásico de **PAWS** que, aunque no es compatible con **ngPAWS** al cien por cien, da más ideas de cómo hacer ciertas cosas que el tutorial «La Torre». Recomiendo su lectura solo después del primero.

Además, existe una serie de microtutoriales que explican cómo hacer ciertas tareas habituales, desde las más sencillas \(crear una localidad, un objeto\) hasta algunas más complicadas \(crear un NPC que se mueve\). Recomiendo que los leas antes que el «tutorial clásico de **PAWS**».

* \[\[La Torre\]\]
* \[\[microtutoriales\]\]
* \[\[Tutorial clásico\|[http://www.ngpaws.com/wikires/PAWS\_Introduccion.pdf](http://www.ngpaws.com/wikires/PAWS_Introduccion.pdf]\)\] \(empezar a leer en el punto "El Guion inicial"\)

### Tutorial en vídeo

**ngPAWS** no tiene ningún tutorial en vídeo pero dado que es compatible casi en su totalidad con su predecesor \(**Superglús**\) probablemente puedes querer ver este \[\[tutorial en vídeo\]\].

### Crear puzles sin programar

El editor de **ngPAWS** trae incorporado un _asistente de puzles_ que te puede evitar tener que programar, al menos para puzles sencillos. Aquí tienes un tutorial de cómo usarlo:

\[\[El asistente de puzles\]\]

### Mejorar **ngPAWS** \(solo si sabes programar en javascript\)

Es posible mejorar **ngPAWS** añadiendo funcionalidades, _condactos,_ librerías, etc. pero para ello es necesario saber programar en javascript. Si eres nuevo en **ngPAWS** olvídate de esto por ahora porque es muy probable que no lo necesites nunca.

* \[Creando tus propios condactos\]\(Creando tus propios _condactos_\) \(se necesitan conocimientos de javascript\)
* \[\[Expandiendo las funcionalidades de ngPAWS\]\] \(se necesitan conocimientos de javascript\)
* \[Hooks\]\(hooks\_es\) \(se necesitan conocimientos de javascript\)
* \[Cambiando la configuración de la pantalla\] \(Cambiando la configuración de la pantalla\) \(se necesitan conocimientos de CSS\)

### Portar un antiguo juego de ZX Spectrum

Lo primero que debes saber es que no será tan fácil como esperas. Una vez hecho esta advertencia, echa un ojo a los siguientes artículos:

* \[Conversión de PAWS a ngPAWS\] \(Conversión de **PAWS** a **ngPAWS**\)
* \[Compatibildidad hacia atrás\]\(Compatibildidad hacia atrás\)

### Portar un antiguo juego de Superglús

En este caso es más fácil. Ver:

* \[Conversión de Superglús a ngPAWS\]\(Conversión de **Superglús** a **ngPAWS**\)

### Mejorar esta guía

Si encuentras errores o partes confusas en esta guía, no dudes en añadir un comentario en la versión en línea \(pulsa el ![](/assets/maspetit.png) que aparace al pasar el ratón sobre un párrafo\) y haremos lo posible por mejorarla.

### Créditos

Quiero agradecer...

* A Graeme Yeandle y Tim Gilberts, Tim Gilberts y Graeme Yeandle, por crear **PAWS.**
* Yokiyoki, por crear **Paguaglus,** ayudar con **Superglús,** y en el fondo estar en el origen de **ngPAWS.**
* Baltasarq, por crear el preporcesador txtpaws, sin él **ngPAWS** sería realmente difícil de usar.
* Radin, por expandir... bueno, **crear** la base de datos de inicio en español.
* Jay Salvat, por la librería **Buzz** \(sonido javascript\).
* La jQuery Foundation, por crear **jQuery.**
* dddddd, porque sugirió el nombre de esta herramienta.
* A los otros que sugirieron otros nombre que finalmente no fueron elegidos.
* Los logotipos de este documento incluyen el logo de Superglús y otros creados a partir de iconos de:
  * Pluma. ![](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by.svg) Joris Hoogendoorn.
  * Espada. ![](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by.svg) Ilho Byun.

![](/assets/logo-header.svg)

