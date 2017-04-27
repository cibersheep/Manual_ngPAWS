## El Proceso interrupción

El _Proceso interrupción_ es como cualquier proceso \(que no sea Proceso 0, Proceso 1 o Proceso 2\) pero que tiene una única diferencia: se ejecuta cada 50 milisegundos, independientemente de lo que esté haciendo el jugador.

Cualquier proceso de usuario puede ser _Proceso interrupción_ pero solamente puede existir uno. Para marcarlo como tal simplemente añade `INT` tras la sección correspondiente. Si estás usando el IDE, pulsa botón derecho sobre la zona de los _condactos_ del mismo y selecciona «Activar/desactivar marca de interrupción».

Por ejemplo, en el editor de texto, en lugar de

`/PRO 4`

escribe

`/PRO 4 INT`

Los usos más comunes de este proceso son:

* Cambiar la música, reproducir efectos de sonido, etc. aleatoriamente en cualquier momento.
* Hacer imágenes de localidad animadas usando el condacto [PICTUREAT](PICTUREAT_ES) \(probablemente en ngPAWS esto ya no es necesario dado que el gráfico de una localidad puede ser un GIF animado\).
* Hacer que ocurran eventos basados _en tiempo_ en lugar de _en turnos._



