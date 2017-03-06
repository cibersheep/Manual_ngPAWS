Para crear tu propio juego o historia, tendrás que instalar ngPAWS primero. Por favor sigue las instrucciones:

### Windows

1. Descarga la instalación para Windows desde la [página de descargas](descargas) y extrae el fichero en una carpeta de tu ordenador, por ejemplo  c:\ngpaws.

2. Ejecuta el el programa "ngpaws"

3. Es posible que recibas una alerta al iniciarlo indicando que no se encuentra el navegador. Esto es así porque al ser ngPAWS un sistema que genera HTML para ejecutarlo en un navegador, necesita que le indiques la ruta al navegador de tu preferencia. Estos navegadores suelen estar en la carpeta "C:\Program Files" o "C:\Program Files(x86)" en Windows Vista y superiores, o en la carpeta "C:\Archivos de Programa" en Windows XP. por favor busca dentro de esas carpetas la carpeta e tu navegador favorito (Chrome, Firefox, Internet Explorer, etc.) y seleccionalo. Para ello desde dentro de ngPAWS, selecciona el menú Tools, luego Options  y selecciona el navegador en el apartado "Browser Path".

3. Para crear una nueva aventura simplemente selecciona el menú File, luego "New" y elige un sitio donde grabar tu aventura. Tendrás que elegir un nombre, y te recomiendo que crees una carpeta específica para cada aventura que crees, para que los datos estén separados.

### Linux

1. Descarga el instalable desde la [página de descargas](descargas) y extraelo en alguna carpeta de tu equipo (por ejemplo ~/ngpaws). Asegúrate de que dicha carpeta se añade al path en tu fichero .bashrc o similar.

2. Copia la carpeta new_game_pack folder en alguna otra carpeta. Cada vez que quieras crear un juego nuevo tienes que copiar esa carpeta en otro sitio, digamos que esa carpeta es la base para empezar cualquier aventura. 

4. En la carpeta que has creado teclea `txtpaws code.txp`. Si no se producen errores habrán aparecido algunos ficheros, incluyendo uno llamado code.sce. Si te dice que no se encuentra txtpaws, asegurate que añadiste la carpeta de ngpaws al path.

5. Ahora teclea `ngpc code.sce`. Si no hay errores un fichero llamado code.js aparecerá. En ese momento puedes abrir el fichero index.html con tu navegador favorito para jugar al juego.

Cada vez que hagas cambios en code.txp tendrás que ejecutar txtpaws y ngpc para obtener un code.js actualizado.

Notas:
- Si prefieres otro nombre para el fichero code.txp (por ejemplo GranCaverna.txp) puedes renombrarlo, pero en ese caso tienes que editar el fichero index.html y reemplazar "code.js" por "GranCaverna.js", y obviamente llamar a txtpaws y ngpc con los nombre adecuados (txtpaws GranCaverna.txp , ngpc GranCaverna.sce)


### Mac

No hay binarios generados para Mac, y no poseo un Mac personalmente, por lo que no puedo generarlos, pero cualquier que tenga un Mac puede descargar las fuentes de ngpc y txtpaws y compilarlas.


[[Ir al siguiente capítulo: La base de datos de inicio|la base de datos de inicio]]