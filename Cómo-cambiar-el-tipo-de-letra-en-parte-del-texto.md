Esto es bastante sencillo, por pasos:

1) Busca el fichero css.css en la carpeta de tu juego, y editalo con un editor de textos, por ejemplo el notepad (Windows) o el vi (linux).

2) Añade al final algo parecido a esto:

```
.formateado1 {
  font-family: Verdana;
  font-size: 20px;
  color: red;
}
```

3) Cuando vayas a escribir un texto y quieras que salga con el formato elegido lo pone así:

```
WRITELN "Este texto sale normal pero {CLASS|formateado1|este otro sale con el otro formato} y este vuelve a salir normal"
```

así el texto hasta la segunda llave sale con el formato especificado en el fichero css.

**_¿Y qué puede poner en ese CSS_**

Pues hay muchas opciones que no vamos a poner aquí porque esto no es un manual de CSS, pero podéis ver en el ejemplo que puedes cambiar el color (aquí os dejo una lista de colores http://html-color-codes.info/codigos-de-colores-hexadecimales/), el tipo de letra (Verdana), el tamaño (20px), etc.

**_¿Y puedo hacer más formatos_**

Todos los que quieras, simplemente añade otro apartado al CSS igual que ese pero con otro nombre (por ejemplo "formateado2", y luego igual:

```
WRITELN "Este texto sale normal pero {CLASS|formateado2|este otro sale con el otro formato nuevo} {CLASS|formateado1@y este sale con el primer formateado.}"
```