**PICTUREAT x y resno**

Dibuja el gráfico resno en la ventana gráfica en la posición relativa x,y sobre el gráfico de localidad actual.

Como ngPAWS escala el gráfico de la localidad dependiendo de la resolución del navegador, las imágenes dibujadas por PICTUREAT se escalarán igualmente.

Por ejemplo, si nuestro gráfico de localidad tiene 1024x384 pixels y es mostrado a su tamaño original, si llamamos a PICTUREAT con coordenadas (100,100) y una imagen de 50x50 pixels, la imagen se pintará en la posición 100x100  desde la esquina superior izquierda del gráfico de localidad y no será escalada.

Pero si la imagen de localidad es escalada al 50%  (512x192) porque se ejecuta en una pantalla pequeña, el gráfico de PICTUREAT aparecerá a 50,50 de la esquina superior izquierda del gráfico de localidad, y con un tamaño de 25x25  (escalada al 50% también).

Así que para dibujar una imagen sobre otra no es necesario calcular la resolución actual, simplemente saber donde quiere que se ponga sobre la imagen tal cual es en origen, y ngPAws haáa el resto.

Nota: una imagen pintada con PICTUREAT se borrará si se redescribe la localidad, si nos vamos a otra localidad y volvemos, o simplemente si se redimensiona la ventana del navegador. Por eso generalmente hay que usar el [proceso interrupcion](el proceso interrupcion) para restablecerlo si es importante. Para ayudar con ello cada vez que hay un resize el bit 4 del [flag 12](flags del sistema) se pone a uno cada vez que hay un evento "resize" y a cero de nuevo cuando el proceso de interrupción acaba.

Nota: PICTURE_AT solía utilizarse en Superglús para hacer gráficos móviles (pintando distintas imágenes en secuencia desde el proceso de interrupción). Dado que ngPAWS permite gráficos en formato GIF (incluido GIF animado), es posible que sea mejor hacerlo así que usar PICTUREAT.

Ver también:

* [PICTURE](PICTURE_ES)
* [TEXTPIC](TEXTPIC_ES)