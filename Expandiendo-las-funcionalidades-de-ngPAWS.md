Como con los condactos, ngPAWS permite al autor añadir nuevas librerías que permitan nuevas funcionalidades en sus juegos, o hacer de soporte a otras librerías o condactos nuevos.

Para crear una nueva librería, simplemente crea un fichero .jsp en la carpeta jsl (ya sea en la de ngpaws o en una carpeta jsl local en la carpeta de tu aventura),con el nombre que prefieras.

Veamos un ejemplo:

```
//LIB ejemplo


function nada()
{

}
```

Como puedes ver, el fichero empieza con //LIB seguido del nombre (que en realidad es irrelevante) y después puedes añadir una o más funciones, clases, etc.

Algunos condactos requieren grabar datos en un fichero "savegame". Si es tu caso, puede usar una librería para manejar esto (ver [[hooks|hooks_es]]) o hacerlo desde el propio fichero del condacto.
