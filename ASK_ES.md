**ASK "pregunta" "opciones" flagno**

ASK muestra la pregunta y espera a que una de las teclas en "opciones" es pulsada. En ese momento el flag flagno tomará el valor de la posición de la tecla pulsada en "opciones". La primera letra en opciones es la posición 0.

Ejemplo:

```
ASK "¿Quieres (V)olver, (S)ubir o (M)atar al orco? " "VSM" 100
```

Cuando se ejecute, el juego parará hasta que el jugador pulse "V", "S" o "M". Si el jugador pulsa V el flag 100 se pondrá a 0, si pulsa S a 1, y si pulsa M a 2.

