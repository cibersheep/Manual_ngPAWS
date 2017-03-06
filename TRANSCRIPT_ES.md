**TRANSCRIPT** valor

ngpAWS almacena todo el texto escrito y las respuestas en un buffer de trasncripcion, cuando el condacto TRANSCRIPT se ejecuta el buffer es mostrado de modo que el jugador pueda copiar el contenido.

La transcripción es muy útil para beta testing, porque el betatester puede mandar transcripciones a los autores.

El parámetro "valor" es un legado de parsers anteriores (Superglús), y puede ser 1 o 0, pero para ngPAWS da igual que valor se ponga.

Los betatesters pueden añadir comentarios al fichero trancript precediendolos del símbolo almohadilla (#), de modo que puedan hacer algo como esto:

```
Puedes ver una alfombra.
>COGER ALFOMBRA
No puedes coger eso.
>#Estaría bien que dijera por qué no puedo cogerla.
>
```
Como puedes ver, el juego no responde a la fase tecleada con el símbolo almohadilla, y solo va a la transcripción, no pasan turnos, nada pasa en el juego/historia.