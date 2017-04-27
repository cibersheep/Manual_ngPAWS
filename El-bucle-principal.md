## El bucle principal

**ngPAWS** funciona ejecutando varias acciones o comprobaciones en blucle \(el bucle principal\) que poodría dividirse en siete apartados. Más abajo encontrarás un diagrama que muestra este bucle más visualmente.

1. Se describe la localidad actual.
2. Se ejecuta el _Proceso 1._
3. Se espera una orden del jugador hasta que se reciba alguna.
4. Se forma una _sentencia lógica_ \(SL\) analizando la frase que ha escrito el jugador y desgranando verbo, sustantivo, adverbios, adjetivos, etc. y se recorre la [_tabla de respuestas_](/La-tabla-de-respuestas.md)_._ 
5. Si se encuentran entradas que concuerden con la setencia lógica, se ejecuta todas las instrucciones hasta que se llegue a un **DONE**. 
   Después se ejecuta el _Proceso 2_ y se vuelve al punto 3. 
   Si en lugar de **DONE** se encuentra un **DESC** \(que obliga a describir la localidad actual\) se vuelve al punto 1.
6. Si no se encuentra ninguna entrada en la tabla, o ninguna acaba con un **DONE,** se comprueba la _tabla de conexiones,_ a ver si la sentencia lógica es una orden para moverse de localidad. Si hay éxito, se coloca al jugador a la nueva localidad y se vuelve al punto 1.
7. En caso de que tampoco haya concordancia en la _tabla de conexiones,_ se muestra el mensaje «No puedes hacer eso.» o similar. Luego, se ejecuta el _Proceso 2,_  y se vuelve al punto 3.

![](/assets/bucle-principal.png)

