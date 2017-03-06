*EXITS locno mesno*

EXITS es un potente condacto, un poco complicado de configurar, pero fácil de usar en el fondo.

EXITS lista las salidas existentes de la localidad actual.

Para que eso sea posible, se requiere crear algunos mensajes en la tabla de mensajes:

* El mensajes mesno debe ser un texto como "Salidas visibles:" o "Puedes ir ". 
* El mensaje mesno + 1 debe ser algo como "No hay salidas visibles."
* Del mensaje mesno +2 en adelante, debe haber un mensaje por cada verbo de dirección (norte, sur, este, etc.)

EXITS usa los [[mensajes del sistema]] 46, 47 y 48 para construir una frase como "Salidas visibles: norte, abajo y sur."

Nota: [[la base de datos de inicio]] viene ya con EXITS configurado, por lo que no te debes preocupar demasiado.