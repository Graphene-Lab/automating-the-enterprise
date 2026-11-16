# 16. El almacén responde

La pregunta que cambió el trabajo de Tom Beck se hizo un martes, y no era una pregunta sobre ordenadores.

> *¿Cuántos archivadores de anillas A4 tenemos, y dónde están?*

La había hecho mil veces en diecinueve años, y la respuesta siempre había venido de una persona: de él mismo, o de quien estuviera en la línea de preparación, o de un cuaderno que a veces acertaba. Ahora lo escribía en una ventana y obten esto:

> *Archivador de anillas A4: 412 en total en existencias. 350 reservados para el pedido S00012 (Academia Ashfield). 62 disponibles. Ubicaciones: Existencia/Estantería A — 380, Existencia/Devoluciones — 24, Existencia/Cuarentena — 8.*

Lo leyó tres veces. Luego salió hasta la estantería A y contó, lo que le onze minutos y demostró que el sistema tenía razón en los tres números.

"Vale", dijo, al volver. "Ahora le creo."

---

## Qué es un movimiento de existencias

El número 412 no está almacenado en ningún sitio. Esa es la primera cosa que hay que entender, y es lo que separa un sistema de inventario real de una hoja de cálculo con una columna de cantidades.

Lo que se almacena es una lista de *movimientos*: doscientos recibidos del proveedor en marzo, trescientos cincuenta preparados para Ashfield en junio, veinte devueltos en julio, ocho trasladados a cuarentena en agosto. El nivel de existencias es la suma de esos movimientos, calculada cuando preguntas. Si vuelves a preguntar dentro de un minuto, y nada se ha movido, obtienes la misma respuesta. Si algo se ha movido, obtienes una distinta, y la diferencia es *el propio movimiento*—que tiene una fecha, un usuario, una razón y un documento.

Esto tiene tres consecuencias que una hoja de cálculo no puede reproducir.

**Siempre puedes saber por qué.** Cuando un número parece incorrecto, los movimientos lo explican. No "alguien cambió la cantidad" sino "veinte pasaron a cuarentena el 3 de agosto porque la paleta estaba aplastada".

**Dos personas no pueden discrepar en silencio.** Si Tom cuenta 380 y el sistema dice 412, la diferencia es un documento: un ajuste, con una razón, aprobado por alguien. El conteo no sobreescribe el sistema; produce un movimiento que los reconcilia.

**El sobrevive un cambio de unidad, precio o proveedor.** Los movimientos conservan las cantidades en que se hicieron. Reorganizar el catálogo no reescribe el pasado.

## Reservado, disponible y la diferencia que importa

La segunda cosa que aprendió Tom es la diferencia entre *en existencias* y *disponible*, y es la diferencia entre un almacén que promete y un almacén que cumple sus promesas.

**En existencias** es lo que hay físicamente en el edificio: 412 archivadores.

**Reservado** es lo que se ha prometido a un pedido concreto: 350 archivadores, para Ashfield, esperando la furgoneta.

**Disponible** es en existencias menos reservado: 62 archivadores que se pueden prometer a otra persona.

Una empresa que solo sigue *en existencias* prometará las mismas 350 archivadores dos veces—una para Ashfield y otra para Northgate—y descubrirá el problema la mañana de la entrega, cuando solo hay una paleta. Una empresa que sigue las reservas la descubre en el momento de la segunda promesa, cuando el sistema dice *62 disponibles* y el vendedor tiene que tomar una decisión.

Esa decisión—entregamos a Northgate tarde, o compramos más, o dividimos el pedido—es una decisión comercial, y el punto del sistema no es tomarla. El punto es situarla delante de una persona *antes* de que se convierta en una disculpa.

## La entrega

La entrega en sí es el documento más simple de todo el sistema y el que más consecuencias tiene.

> *Entrega el pedido S00012 y muéstrame los movimientos de existencias que creó.*

> *Entrega WH/OUT/00004 validada para el pedido S00012. Movimientos: 350 × Archivador de anillas A4 (azul) de Existencia/Estantería A a Clientes; 20 × Marcadores de pizarra (paquete de 4) de Existencia/Estantería A a Clientes. Existencias tras el movimiento: 62 archivadores en existencias, 0 reservados; marcadores 44 en existencias.*

Pasaron tres cosas a la vez, y valen la pena separarlas.

El **stock** se movió: 350 archivadores salieron de la estantería A. La **reserva** desapareció, porque se había cumplido. Y el **pedido** cambió de estado: ahora está *entregado*, lo que significa que se puede crear la factura contra él.

Si la entrega hubiera sido parcial—doscientos archivadores en lugar de trescientos cincuenta—Odoo habría creado un *pedido pendiente*: un segundo documento de entrega para el resto, vinculado al primero. Ese único mecanismo es la razón por la que una empresa puede prometer *enviaremos el resto el viernes* sin que nadie tenga que recordar cuál era el resto.

## Las ubicaciones, en la práctica

Una ubicación suena a tecnicismo hasta la primera vez que algo se pierde, y entonces es lo único que importa.

Las cuatro ubicaciones de Riverton—dos estanterías, devoluciones, cuarentena—se configuraron en una hora y se usaron correctamente durante unos meses antes de que nadie las valorara.

La ubicación de devoluciones fue la primera en ganarse el sustento. Un cliente devuelve veinte archivadores porque son del color equivocado; la furgoneta los trae hasta el muelle de carga; Tom tiene que decidir si vuelven a la estantería A (son, después de todo, vendibles) o a la cuarentena (no lo son). En el sistema viejo, la decisión la tomaba dónde se ponía la caja, y la caja se ponía donde había sitio. En el sistema nuevo, la decisión es un movimiento de existencias, y el movimiento lleva una razón adjunta.

La consecuencia apareció en el informe de margen tres meses después: la ubicación de devoluciones contenía cuarenta y cinco artículos que habían sido "devueltos" y nunca comprobados, algunos dañados, otros de hecho un producto distinto. Cada uno de ellos había sido contado como stock vendible. Eso es cuarenta y cinco artículos de stock que la empresa creía tener y no podía vender—un número pequeño, y una ilustración perfecta del principio general: **el valor de una ubicación es que obliga a registrar una decisión.**

## La triple verificación, desde el lado del almacén

El capítulo diecisiete describe la triple verificación desde el punto de vista del contable. Desde el lado de Tom, se ve distinto y vale un párrafo.

Cuando llega una entrega, el trabajo del almacén es registrar lo que realmente ha venido: cuántos, de qué producto, en qué estado, en qué fecha. Ese registro es la *recpción*, y es la pata intermedia de la verificación. Si es incorrecta—si Tom registra cuarenta paletas en lugar de cuarenta resmas, o si valida la recpción antes de contar—entonces la verificación "tendrá éxito" contra un número incorrecto, y el error sobrevivirá hasta el final en las cuentas.

Por eso la recpción es un documento con un usuario y una marca de tiempo, y por qué al asistente no se le permite validar una recpción por iniciativa propia. Puede crear una desde un pedido de compra, que es una propuesta; validarla significa *he contado esto*, y eso es una afirmación sobre el mundo físico que solo alguien parado delante de la paleta puede hacer.

La regla de Tom, escrita en la pizarra: *el sistema puede adivinar qué debería haber. Solo yo puedo decir qué hay.*

## El costo de un conteo erróneo

Vale la pena poner un número al conteo trimestral, porque "deberíamos hacerlo más a menudo" es el tipo de consejo que muere en un mes ajetreado.

El stock de Riverton valía unas £180.000 al coste. El primer conteo encontró una diferencia neta del 1,8 por ciento—unas £3.200—repartidas en once productos. Eso no es robo; es el efecto acumulado de cuarenta errores pequeños: una paleta registrada como cuarenta paletas, una devolución devuelta sin comprobar, una entrega validada antes de que se contara.

Un conteo cuesta a dos personas un día, dos veces al año, lo que son unas £1.200 de salarios. Encontró £3.200 de error la primera vez y £900 la segunda. La aritmética no es sutil: una empresa que cuenta dos veces al año está comprando una póliza de seguro de £1.200 contra un error de £3.000, y el error que previene es el que deja las cuentas erróneas al final del año.

Lo que cambió con el sistema no fue la aritmética sino la *forma* del conteo. En lugar de contar todo y reconciliar una lista, el sistema propone lo que cree y el contador confirma o corrige. Las correcciones se investigan luego, una a una, y cada investigación corrige un hábito más que un número. Esa es la diferencia entre contar existencias y gestionarlas.

## El albarán de entrega, y las tres firmas

Una entrega en un mayorista tiene tres momentos, y cada uno tiene una firma de su tipo.

**La preparación:** alguien saca las mercancías de la estantería y las pone en una paleta. La firma es la lista de preparación, firmada línea por línea, y es el almacén que dice *esto es lo que he montado*.

**La carga:** las mercancías suben a la furgoneta. La firma es la del conductor, y es la empresa que dice *esto salió del edificio*.

**La entrega:** el cuidador del cliente firma el albarán. La firma es la suya, y es el cliente que dice *esto llegó*.

En Odoo los tres momentos colapsan en dos documentos—el pedido de entrega y su validación—y eso es una simplificación que vale la pena entender, porque es donde nace la mayoría de las discrepancias. Una paleta que se prepara, se carga y nunca se entrega ha salido del stock del sistema pero no del patio de la empresa; una paleta que se entrega y nunca se valida ha salido del patio pero no del sistema.

El hábito de Tom, tras el primer año, era tratar la validación como el momento de la verdad: la entrega se valida cuando vuelve el albarán firmado, no cuando sale la furgoneta. Hace que el informe de existencias sea un día más tarde y lo hace correcto, y preferiría tener un número correcto el miércoles a uno erróneoe el martes.

## Lo que el almacén sabe y el sistema no

Hay un límite para todo esto, y Tom es el primero en describirlo.

El sistema sabe cantidades, ubicaciones y fechas. No sabe que la esquina de la estantería B es por donde entra la humedad, que la paleta de papel de la entrega de agosto pesa más que la de febrero porque el proveedor cambió el peso de la remesa, o que el conductor que entrega los viernes no esperará mientras cuentas.

Un gestor de almacén lleva ese conocimiento, y el valor del sistema no es reemplazarlo sino *liberarlo*: una persona que no tiene que recordar dónde están cuatrocientos cincuenta archivadores puede dedicar la atención a por qué la paleta de agosto se siente incorrecta.

"Es lo mismo que la oficina", dice Tom. "El sistema cuenta. Yo me fijo."

## El conteo

Una vez al trimestre, Riverton cuenta.

No es una tarde agradable. Implica una tabla de montar, dos personas, una linterna y un almacén más frío de lo que parece. Pero ahora es distinto, de una forma que le tomó a Tom un rato articular.

"La primera vez conté todo y lo escribí, y el sistema me dijo dónde me equivocaba", dijo. "La segunda vez solo conté las cosas que el sistema decía que debía tener, y me dijo dónde se equivocaba *ello*. Es un trabajo distinto. El primero es una tarea. El segundo es una conversación."

Lo que quiere decir es esto: con un conteo de existencias, el sistema propone una lista de productos y las cantidades que cree que hay en la estantería, y el contador confirma o corrige. Las correcciones se revisan luego, y cada una es una pequeña investigación: ¿fue un error de preparación, una entrega firmada pero no registrada, una devolución que nunca volvió a la estantería?

Esa investigación es donde está el dinero. En el primer año de Riverton, el conteo trimestral encontró tres problemas recurrentes, y ninguno era robo:

- Un producto cuya unidad de medida se había configurado mal en 2022, de modo que cada recpción se registraba como una paleta en lugar de cuarenta remesas. El sistema había estado "perdiendo" papel durante tres años.
- Un albarán de entrega firmado en la escuela pero nunca validado en el sistema, de modo que las mercancías estaban en la estantería y también en el armario del cliente.
- Un proceso de devoluciones que devolvía las mercancías a existencias sin comprobarlas, de modo que los artículos dañados se vendían dos veces.

Cada uno de ellos se encontró comparando lo que el sistema creía con lo que era verdadero, y cada uno se corrigió cambiando un hábito, no comprando algo.

---

## Una nota sobre la palabra "almacén"

El almacén de Tom es una con estanterías, un muelle de carga y una esquina donde van las cosas dañadas. En Odoo es una *ubicación*, y las ubicaciones pueden anidarse: un almacén contiene una zona de existencias, que contiene estanterías, que contienen huecos.

Una empresa con una sola habitación no necesita la anidación, y Riverton no la usó al principio. Pero la estructura estaba ahí, y en el segundo año, cuando la empresa alquiló la unidad contigua, añadir un segundo almacén fue cosa de crear una ubicación y mover existencias—no de comprar un segundo sistema ni de empezar un segundo hoja de cálculo.

Ese es el ventaja silenciosa de modelar la realidad en vez de registrarla. Una hoja de cálculo que dice "412 archivadores" no puede crecer una segunda estantería sin reconstruirse. Un sistema que dice "412 archivadores, aquí están los movimientos que los pusieron ahí" puede crecer un segundo edificio en una tarde.

---

El informe de Tom, al final de ese primer trimestre, tenía cuatro páginas y lo leyó en la furgoneta.

"Lo que sigo retomando", dijo, al devolverlo, "es que solía *saber* cosas y no podía *mostrarlas*. Ahora puedo mostrarlas. Es el mostrar lo que cambia la conversación."

Maggie le preguntó qué quería decir.

"Antes, si decía que teníamos demasiado papel, era la opinión de Tom. Ahora es un número en una hoja con una fecha. Nadie discute con un número en una hoja. Discuten con Tom."

Sonrió. "Es muy descansado."
