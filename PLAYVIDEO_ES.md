**PLAYVIDEO "fichero" cuenta settings**

Mostrará el video fichero.mp4, fichero.ogg o fichero.webm en la zona de gráficos. El fichero debe estar en la carpeta "dat" dentro de la carpeta de nuestro juego/historia. La mayoría de los navegadores modernos soportan el formato mp4 (siempre que esté con el codec H.264)  pero es una buena idea disponer del formato ogg o webm también. ngPAWS decidirá cual de los tres reproducir si hay más de uno dependiendo de la compatibilidad del navegador.

Si tu video no tiene música, considera usar una solución más compatible como el GIF animado, ya sea como imagen de localidad o para mostrarlo en un momento dado usando [[PICTURE|PICTURE_ES]].

Deberás especificar cuantas veces quieres que se reproduzca el video (en bucle), si especificas 0 veces, el video se reproducira una y otra vez.

El valor de Settings, por ahora solo puede tener dos valores:

1 : El vídeo puede ser parado pulsando la tecla ESC
2 : El vídeo no puede ser parado

Ten en cuenta que al parar un video con ESC solo lo pausas, de la misma manera que con [[PAUSEVIDEO|PAUSEVIDEO_ES]], por lo que se quedará en el ultimo frame mostrado y no se esconderá.

Si quieres que pase algo cuando el video es interrumpido o finaliza, tendrás que hacerlo tú mismo (puedes comprobar si el video está siendo reproducido desde el [[proceso interrupción|el proceso interrupción]]usando el condacto [[ISVIDEO|ISVIDEO_ES]] ).

**RESUMEVIDEO**

Si hay algún vídeo pausado, se continuará la reproducción.

Ver también:

* [[PAUSEVIDEO|PAUSEVIDEO_ES]]
* [[RESUMEVIDEO|RESUMEVIDEO_ES]]
* [[VOLUMEVIDEO|VOLUMEVIDEO_ES]]
* [[ISVIDEO|ISVIDEO_ES]]