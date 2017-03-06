**NEWTEXT**

Fuerza el borrado de cualquier órden del jugador que permaneciera sin ejecutar. Se usa para prevenir que tras el fallo de una acción se siga con el resto de órdenes, que han dejado de tener sentido. Por ejemplo [[GET|GET_ES]]ejecuta un NEWTEXT si falla a la hora de coger el objeto, para prevenir un desastre como:


`COGE ESPADA Y MATA AL ORCO CON ELLA`

¡atacar al orco sin la espada sería peligroso!