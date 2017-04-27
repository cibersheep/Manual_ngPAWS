## Depuración de errores con la consola javascript

Algunas veces, al crear un nuevo juego, algo no funciona como debería. Para que puedas comprobar qué funciona mal, algunos sistemas de creación de aventuras tienen lo que se denomina _depurador_ o _debugger._ Como **ngPAWS** usa el navegador para ejecutar los juegos, estamos de suerte, ya que prácticamente todos los navegadores incluyen una consola javascript.

No voy a explicar como funciona la consola Javscript, pero os facilito algunos enlaces. Por otro lado, os contaré que variables de javascript convienen los flags, objetos, conexiones, etc. de modo que podáis comprobar cuando sea necesario.

Enlaces interesantes:

* [La consola de Chrome / Chromium](https://developers.google.com/web/tools/chrome-devtools/console/?hl=es)
* [La consola del navegador](https://developer.mozilla.org/es/docs/Tools/Browser_Console) de Firefox \(en inglés\)
* [La consola javascript en Edge](https://docs.microsoft.com/es-es/microsoft-edge/f12-devtools-guide)

### Variables internas de ngPAWS

* Encontrarás las _flags_ en la matriz o _array_ `flags[]`.
* Encontrarás la última orden del jugador en la variable `last_player_order`.
* Encontrarás el resto de órdenes del jugador en `player_order_buffer`.
* Encontrarás información sobre los sonidos que están siendo reproducidos en la matriz o _array_ `soundChannels[]` y el número de iteraciones pendientes en `soundLoopCount[]`.
* Las conexiones están en la matriz `connections[]` y las conexiones iniciales en `connections_start[]`.
* Los recursos multimedia están en el _array_ `resources[]`.
* Las localidades de los objetos están en `objectsLocation[]` y las iniciales en `objectsLocation_start[]`.
* Los pesos de los objetos están en `objectsWeight[]` y los iniciales en `objectsWeight_start[]`.
* Los atributos de los objeto están en `objectsAttrLO[]` y `objectsAttrHI[]`, los iniciales en `objectsAttrLO_start[]` y `objectsAttrHI_start[]`. Donde _LO_ \(de LOW\) designa los atributos que van de 0 a 31 y _HI_ \(de HIGH\) para los que van de 32 a 63.

Para hacer la comprobación más habitual cuando se depuran los errores de una aventura \(comprobar el valor de una _flag_\) simplemente escribe en la consola:

```
flags[28]
```

Lo que nos dará el valor de la bandera 28. Para cambiar el valor de la _flag_ 34, escribe:

```
flags[34]=7
```

Ahora la bandera 34 valdrá 7.

Ten en cuenta que la consola no sabe cuáles son los identificadores de txtpaws por lo que siempre tendrás que usar el número al que corresponden para todo \(objetos, _flags,_ localidades, etc.\).



