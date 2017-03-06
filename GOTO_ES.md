**GOTO locno**

Cambia la localidad del jugador, es equivalente a [[LET|LET_ES]] 38 locno.

Ejemplo:

```
USAR TELETRANSPORTADOR
 AT lTeletransportador
 WRITE "Pulsas el botón y notas como tu cuerpo se disuelve y eres teletransportado. Estás en el planeta Zyrox."
 GOTO lZyroxBase
 ANYKEY
 DESC
```