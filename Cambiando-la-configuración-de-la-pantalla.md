La disposición de la pantalla en ngPAWS está compuesta por tres partes:

![ngpaws layout](http://www.ngpaws.com/wikires/ngpaws_layout.png)

1. La zona gráfica  (50% de alto, en rojo en la gráfica)
2. La zona de escritura (5% de alto, en verde en la gráfica)
3. La zona de texto (espacio restante, en azul en la gráfica)

Si sabes trabajar con CSS, puedes cambiar cualquier cosa en el fichero css que acompaña cada aventura y así cambiar los colores, fondos, etc. de cada DIV, pero hay algo importante que debes saber:

Cuando ngPAWS encuentra que no hay imágen de localidad en una determinada localidad, le asignará la clase "hidden" al DIV de gráficos y la clase "all_text" al DIV de texto. Si hay gráficos, le asignará la clase "half_text" al DIV de texto y  la clase "half_graphics" al DIV de gráficos. En caso de que necesites cambiar el css a las clases de esos DIV de algún modo tenlo en cuenta y cambia también esas clases que se les asignan dinámicamente.

Así es como se ve el layout cuando no hay imágen de localidad:

![ngpaws layout 2](http://www.ngpaws.com/wikires/ngpaws_layout2.png)

Por ejemplo puedes cambiar el CSS de modo que la zona de gráficos quede a la derecha y la de imagenes a la izquierda, pero entonces tienes que cambiar las clases half_text, all_text, hidden y half_graphics (para que afecten al ancho en lugar del alto).

Además, es posible añadir nuevos DIVs particulares a una aventura, cambiando el HTML y poniendo los CSS adecuados, de modo que por ejemplo lleguemos a un layout así, y utilizar los dos DIVs de los lados para poner unos gráficos chulos que integren, o para cosas nuestras (por ejemplo, si sabemos javascript seguro que podemos poner ahí un inventario gráfico o lo que sea):

![ngpaws layout 2](http://www.ngpaws.com/wikires/ngpaws_layout3.png)


Además hay algunas capas que aparecen en determinados casos que ocupan toda la pantalla, cada una de las cuales tienen sus estilos particulares en el css:

- Capa de block (que aparece para el condacto BLOCK)
- Capa de transcript (que aparece con el condacto TRANSCRIPT)
- Capa de anykey (que aparece con condactos que esperan una tecla, como ANYKEY, GETKEY, etc.)

Estas capas también las podemos cambiar si queremos que tengan otro aspecto.

Por último, hay una clase llamada feeback, que es como se muestran las órdenes del jugador cuando son copiadas a la zona de texo.

## Themes

ngPAWS viene con una carpeta llamada "themes" donde puedes encontrar diferentes aspectos sencillos para tus aventuras. En general, basta con copiar el contenido de la carpeta de cada tema en la carpeta de nuestro juego para darle el look (que podemos previsualizar en las imágenes adjuntas).