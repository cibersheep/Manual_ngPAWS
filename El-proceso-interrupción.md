El proceso interrupción es como cualquier otro proceso, con una única diferencia: se ejecuta cada 50 milisegundos, independientemente de lo que está haciendo el jugador.

Cualquier proceso de usuario puede ser proceso interrupción, pero solo uno de ellos. Para marcarlo como tal simplemente añade "INT" tras la sección correspondiente, o si estás usando el IDE, pulsa botón derecho sobre el mismo y selecciona "Interrupt".

Por ejemplo en lugar de 

```/PRO 4```

escribes

```/PRO 4 INT```

Los usos más comunes de este proceso son:

* Cambiar la música, reproducir efectos de sonido, etc. aleatoriamente en cualquier momento.
* Hacer imágenes de localidad animadas usando el condacto [PICTUREAT](PICTUREAT_ES), aunque probablemente en ngPAWS esto no es necesario dado que el gráfico de una localidad puede ser un GIF animado.
* Hacer que ocurran eventos basados en el tiempo, no en turnos.
