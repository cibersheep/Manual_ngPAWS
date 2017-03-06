Cada objeto en ngPAWS puede tener una serie de atributos, que marcan como la librería lo trata por defecto para determinadas acciones:

**Los atributos básicos de los objetos (heredados de PAWS) son:**

* aLight (el objeto es una fuente de luz)
* aWear (el objeto es una prenda)
* aContainer (el objeto es un contenedor)

**Superglús introdujo el atirbuto aNPC:**

* aNPC (el objeto es en realidad un NPC, non player character --> personaje no jugador)

**ngPAWS añade varios atributos más**:

* aFemale (el objeto es femenino. Ej: llave)
* aMale (el objeto es masculino. Ej: libro)
* aNeuter (el objeto es neutro. De poco uso en castellano, pero importante en inglés)
* aPlural (el objeto es plural. Ej: llaves)

* aConcealed (el objeto está oculto, por lo que no será listado por LISTAT, LISTOBJ o LISTNPC, pero cualquier otro condacto como PRESENT o ABSENT lo detectará). Tampoco será tenido en cuanta por los bucles  [DOALL](DOALL_ES).
* aScenery (en este momento no hay diferencia entre aScenery y aConcealed)
* aStatic (el objeto es parte de la habitación y no puede ser tomado o llevado. Ej: chimenea)

* aEdible (el objeto es comestible).
* aDrinkable (el objeto es bebible)

* aEnterable (se puede entrar en el objeto, por ejemplo un armario)

* aOpenable (el objeto se puede abrir o cerrar, por ejemplo una caja)
* aOpen (el objeto está abierto, usado junto con aOpenable)
* aLockable (el objeto se puede cerrar con llave, por ejemplo una puerta, un candado)
* aLocked (el objeto está cerrado con llave)

* aTransparent (se puede ver a través del objeto, si es un contenedor, los contenido se verán sin tener qu examinarlo.)

* aSwitchable (el objeto se puede encender/apagar)
* aOn (el objeto está encendido)

* aSupporter (el objeto es una superficie, puede tener objetos sobre ella)

Notese que es importante definir el género y número de los objetos, para evitar mensajes extraños. En español se usa para reemplazar propiamente los artículos, de modo que si un objeto está definido como "una antorcha" y es femenino al cogerlo aparecerá "coges la antorcha". Si estuviera marcada como masculino pondría "coges el antorcha".

Notese que un objeto NO puede ser aSupporter y aContaniner al mismo tiempo.

