## INSTALACIÓN {#instalación}

Para crear tu propio juego o historia, tendrás que instalar **ngPAWS** primero. Por favor, sigue las instrucciones siguientes:

### Windows

1. Descarga el instalador para Windows desde la [página de descargas](http://www.ngpaws.com/es.html#Downloads) y extrae el fichero en una carpeta de tu ordenador, por ejemplo  `c:\ngpaws`.

2. Ejecuta el el programa **ngpaws**

3. Es posible que recibas una alerta al iniciarlo indicando que no se encuentra el navegador. Esto es así porque al ser **ngPAWS** un sistema que genera HTML para ejecutarlo en un navegador, necesita que le indiques la ruta al que tú prefieras. Suelen estar en la carpeta `C:\Program Files` o `C:\Program Files(x86)` en Windows Vista y superiores, o en la carpeta `C:\Archivos de Programa` en Windows XP. Por favor, busca dentro de la que corresponda, la de tu navegador favorito \(Chrome, Firefox, Internet Explorer, etc.\) y selecciónalo. Para ello, dentro de **ngPAWS,** ve el menú Herramientas &gt; Opciones  y selecciona el navegador en el apartado «Ruta al navegador».

4. Para crear una nueva aventura simplemente selecciona el menú Archivo &gt; Nuevo y elige un sitio donde grabar tu aventura. Tendrás que elegir un nombre. Te recomiendo que crees una carpeta específica para cada aventura que crees y así que los datos estén en el mismo lugar.

### Linux

1. Descarga el archivo comprimido desde la [página de descargas](http://www.ngpaws.com/es.html#Downloads). Asegúrate de que dicha carpeta se añade al path en tu fichero `.bashrc` o similar o de incluir la ruta completa a la carpeta de **ngPAWS.**

2. Descomprime el archivo descargado y copia la carpeta `dat` y los archivos `buzz.js`, `css.css`, `index.html` y `jquery.js` en una nueva carpeta. Ahora copia también `database.start`y nómbralo `code.txp`. Cada vez que quieras crear un juego nuevo tienes que copiar esa misma carpeta en otro sitio. Por tanto, esta será la base para empezar cualquier aventura.

3. En la carpeta que has creado teclea `txtpaws code.txp`. Si no se producen errores habrán aparecido algunos ficheros, incluyendo uno llamado `code.sce`. Si en el terminal te aparece un mensaje que dice que no se encuentra txtpaws, asegúrate de haber añadido la carpeta de ngPAWS al path.

   1. También puedes llamar a txtpaws con la ruta completa `~/ruta/completa/txtpaws code.txp` o entrando en la carpeta desde la terminal `cd ~/ruta-a-la-carpeta` y luego `./txtpaws ruta-de-la-carpeta-donde-está/code.txp`.

4. Ahora teclea: `ngpc code.sce` \(añadiendo la ruta completa a la carpeta o `./ngpc ruta-de-la-carpeta-donde-está/code.sce`\). Si no se muestra ningún error, un fichero llamado `code.js` será creado. En ese momento puedes abrir el fichero `index.html` con tu navegador favorito para jugar.

Cada vez que hagas cambios en `code.txp` tendrás que ejecutar **txtpaws** y **ngpc** para obtener un code.js actualizado.

**Notas:**

* Si prefieres otro nombre para el fichero code.txp \(por ejemplo GranCaverna.txp\) puedes renombrarlo, pero en ese caso tienes que editar el fichero index.html y reemplazar `code.js` por `GranCaverna.js`, y obviamente, llamar a **txtpaws** y **ngpc** con los nombre adecuados \(`txtpaws GranCaverna.txp`, `ngpc GranCaverna.sce`\).
* Es importante que no crees el archivo `code.txp` en la misma carpeta donde se encuentra ngpc o los _scripts_ que están dentro de `/jsl` se añadirán dos veces \(los _scripts_ por defecto se guardan detro de `/jsl` de la carpeta de **ngPAWS** y los particulares de la aventura en `/jsl` de la carpeta donde se halla `code.txp`\).

### Mac

Solo hay binarios generados para Mac de la [versión 8](http://ngpaws.com/es.html#Downloads) porque no poseo uno personalmente y no puedo generar los nuevos pero se pueden [descargar tanto las fuentes](https://github.com/Utodev/ngPAWS/) de **ngpc** y **txtpaws** y compilarlas.

