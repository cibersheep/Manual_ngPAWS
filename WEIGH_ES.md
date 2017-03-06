**WEIGH objno. flagno.**

El verdadero peso edl objeto objno es calculado y almacenado en el flag flagno. 

El verdadero peso se calcula contando el peso del objeto, más el de los objetos dentro del mismo si es un contenedor, o el de lo que hay encima si es una superficie. Si a su vez hay objetos contenedores dentro de contenedores o superficies, también se calculará, y así indefinidamente.

La única excepción a esto es que un contenedor o soporte tenga peso 0, en cuyo caso no se contabilizará lo que tiene dentro (¡caja mágica!).