Esto es muy fácil:

1) Ponemos el fichero en formato png, jpg o gif en la carpeta "dat" que hay en la carpeta de nuestra aventura.
2) Ponemos lo siguiente en el apartado de definiciones (definition, o al principio del fichero .txp si no usamos el editor de ngPAWS):

```
#define pic parque.jpg 1
```

Si lo ponemos después del #define en el que hemos definido lParque como localidad 1, podemos poner incluso:

```
#define pic parque.jpg lParque
```

Nota importante: no se puede poner gráfico a la localidad 0, el gráfico que se asigne a la localidad 0 se usará cuando en el juego esté oscuro.
