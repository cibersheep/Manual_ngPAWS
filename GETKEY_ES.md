**GETKEY flagno**

Esta acción espera a que el jugador pulse una tecla, y guarda el código de dicha tecla en el flag flagno.

Los navegadores suelen devolver código ASCII para las teclas estándar (letras, números, signos de puntuación, etc.). Aquí hay una tabla:

[http://www.asciitable.com/]
También hay una lista de códigos especiales aquí:

[http://www.javascripter.net/faq/keycodes.htm]

Nota importante: debido al modo de funcionar de javascript, implementar este condacto es complicado Como consecuencia funciona, pero no dentro de bloques de código. Usarlo dentro de un bloque hará el bloque entrar en un estado indeseado y el juego/historia puede colgarse. Tampoco funcionará bien dentro de un bucle RESTART.