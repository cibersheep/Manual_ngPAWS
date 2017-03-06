Si quereremos en un momento dado cambiar el gráfico de localidad, solo tenemos que hacer lo siguiente:

1) Ponemos el fichero en formato png, jpg o gif en la carpeta "dat" que hay en la carpeta de nuestra aventura.
2) Ponemos lo siguiente en el apartado de definiciones (definition, o al principio del fichero .txp si no usamos el editor de ngPAWS):

```
#define grf anillo.jpg 1
```

Al definir el gráfico con "grf" en lugar de "pic" no lo enlazamos con una localidad completa, digamos que sería un gráfico _suelto_. 

El número que ponéis al final es indiferente, pero debe ser un número distinto para cada gráfico suelto que creéis.

Una vez tenemos esto solamente hay que usar el condacto [[PICTURE|PICTURE_ES]] para dibujar el gráfico cuando queramos. Por ejemplo:

```
#define grf anillo.jpg 1

...

EXAMINAR CHARCO
 AT lParque
 WRITE "¡En el charco encuentras un anillo!"
 PICTURE anillo.jpg
 DONE

```