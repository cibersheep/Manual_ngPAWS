Vamos a crear una situación en la que tenemos un NPC que nos roba un objeto, al siguiente turno lo examina, y al siguiente nos lo devuelve. Este artículo es una actualización de otro publicado por Carlos Sisí en el [[fanzine CAAD nº13 |http://www.caad.es/fanzines/13/tecnicas.htm]]

Estas son las normas:
- El NPC (un fantasma) debe estar en la misma localidad que nosotros para que nos robe
- El fantasma solo nos roba cosas que llevemos y que hayamos nombrado en ese momento
- El fantasma preguntará ¿qué es esto? el turno siguiente a robarnos algo.
- El fantasma nos devolverá el mismo objeto que nos roba dos turnos más tarde, si seguimos junto a él, en caso contrario lo hará cuando nos vea.

```
_ _  ; Explico esta entrada al final, leer antes el resto
 SAME 38 fLocFantasma
 ZERO 5
 OBJAT lInventarioFantasma fAux
 NOTZERO fAux 
 LET 5 1

_ _  ; Robo
 SAME 38 fLocFantasma  ;Estamos junto al fantasma
 ZERO 5                ; No hay nada robado ahora mismo
 WHATO
 EQ 54 254             ; ¿El objeto referenciado por la frase actual lo llevamos?
 PLACE @51 lInventarioFantasma ; Lo ponemos en el inventario del fantasma
 COPYFF 51 fObjetoRobado ; Y guardamos el número del objeto en fObjetoRobado
 WRITELN "El fantasma te roba {OREF}."
 LET 5 3               ; 3 turnos de proceso de robo->examinado->devolución

_ _ ; Pregunta
 SAME 38 fLocFantasma  ; Estamos junto al fantasma
 EQ 5 2                ; Estamos en el segundo turno
 WRITELN "El fantasma dice '¿Qué es esto?"

_ _ ; Devolucion
 SAME 38 fLocFantasma     ; Estamos junto al fantasma
 EQ 5 1                   ; Estamos en el tercer turno
 COPYFF fObjetoRobado 51  ; restauro el flag 51
 WRITELN "El fantasma te devuelve {OREF}."
 CREATE @fObjetoRobado    ; Pongo el objeto en la localidad actual
 GET @fObjetoRobado       ; Y hago que el jugador lo coja
```
Notas:

* El flag 5 se autodecrementa a cada turno, por lo que no tenemos que hacerlo nosotros, a cada turno entrará en una de las entradas (ZERO 5, EQ 5 1, o EQ 5 2)

* La primera entrada sirve para que si el jugador se fue (o el fantasma si es que puede moverse) el sistema detecte que el fantasma tiene un objeto y si es así pone el flag 5 a 1, forzando el paso de devolver. Debe estar antes que la entrada de devolver por tanto.

* Podría hacerse que al devolver se hiciera PLACE @fObjetoRobado 254, pero eso implica que el objeto acabaría en el inventario aunque el jugador llevara ya demasiados objetos o peso (por eso lo ponemos "en el suelo" con CREATE, y luego hacemos que el jugador lo coja, cosa que ocurrirá si es posible).

