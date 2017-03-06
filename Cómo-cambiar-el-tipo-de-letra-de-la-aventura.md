Muy sencillo, editamos el fichero css.css que hay en la carpeta de nuestra aventura y modificamos el font-family y si queremos el font-size que hay al principio.

En [[esta página|http://en.wikipedia.org/wiki/Font_family_%28HTML%29]] hay un montón de fuentes posibles para elegir.

### Quiero cambiar la fuente solo en algunos sitios

En ese caso, edita el fichero css.css y al final añade algo como esto:

```
.miclase {
  font-family:  Verdana, Arial, Helvetica;
  font-size: 20px;
}
```
Elige tu el nombre "miclase" según para que quieras el tipo de letra, y elige tamaño y familia.

Después cuando escribas mensajes en ngPAWS haz lo siguiente:

```
WRITELN "Este texto sale normal. {CLASS|miclase|Este texto sale con la fuente 'miclase'.} Este texto sale normal de nuevo."
```