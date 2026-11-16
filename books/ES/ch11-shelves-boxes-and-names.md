# 11. Estantes, Cajas y Nombres

Tom Beck había trabajado en el almacén de Riverton durante diecinueve años, y tenía una regla sobre
las computadoras, la cual anunció la mañana del cuarto día, de pie en el umbral de la
pequeña habitación con los brazos cruzados.

"No voy a escribir mil cien productos."

"Nadie te lo está pidiendo," dijo Maggie. "Vamos a escribir cuarenta."

Tom descruzó los brazos, lo cual era lo más cercano al entusiasmo que llegaba antes del almuerzo.

---

## Por qué cuarenta y no mil cien

El catálogo de un mayorista no es lo mismo que su *amplitud*. Riverton listaba mil cien
referencias porque, en más de treinta años, había comprado lo que los clientes le pedían, y la lista
había crecido como crece un seto. De esos mil cien, cuatrocientos habían vendido más de diez unidades
en el último año. Cuatrocientos sigue siendo demasiados para escribirlos en una semana, y la mayoría
comparten una forma: una marca, un tamaño, un color, una cantidad de empaque.

Así que el plan no era copiar el catálogo. El plan era modelar correctamente las *familias* y dejar
que las variantes hagan el trabajo.

La pizarra en la oficina del almacén terminó con cuatro líneas:

| Familia | Variantes | Unidad de venta | Unidad de compra |
|---|---|---|---|
| Carpetas con anillas | 2 tamaños × 3 colores | unidad | caja de 20 |
| Marcadores para pizarra | 4 colores | paquete de 4 | caja de 12 paquetes |
| Papel A4 | 1 | resma | palet de 40 resmas |
| Bolígrafos | 2 colores | caja de 50 | caja de 50 |

Cuatro familias, y entre todas un par de docenas de variantes. Eso es lo que un ERP moderno llama una
lista de productos: no una lista de todo lo que has comprado nunca, sino un modelo de las cosas que
vendes, con las diferencias expresadas como variantes en lugar de como entradas separadas.

La diferencia no es cosmética. Si "Carpeta con anillas A4 azul" y "Carpeta con anillas A4 roja" son dos
productos, entonces el sistema no puede responder "¿cuántas carpetas A4 vendimos?" sin que alguien
sepa que las dos están relacionadas. Si son un solo producto con una variante de color, la pregunta es
trivial—y la pregunta es todo el punto.

## Categorías, y por qué un informe las necesita

La categoría de un producto es una carpeta, y las carpetas son aburridas hasta que alguien hace una
pregunta.

En Odoo una categoría hace tres cosas: agrupa productos para informes, puede contar con cuentas por
defecto (de modo que cada producto de la categoría registre sus ventas en la misma cuenta de ingresos),
y puede contar con una unidad de medida y un método de coste por defecto.

Las categorías de Riverton terminaron siendo seis: *Papel*, *Carpetas y archivado*, *Instrumentos de
escritura*, *Tinta y tóner*, *Mobiliario* y *Servicios*. Seis es suficiente para responder a la pregunta
*¿qué parte del negocio ganó dinero este mes?* y pocas como para que nadie discuta sobre dónde
pertenece un producto.

La alternativa—una sola llamada *Todos los productos*—es lo que una empresa obtiene si no decide, y
significa que cada informe de margen es un informe sobre la empresa en su conjunto. Ese es un buen
informe, pero no es el que necesita un mayorista, porque el profit de un mayorista se gana y se pierde
en la mezcla entre categorías, no en el total.

Hay una segunda razón para preocuparse, y es contable. Si la categoría contiene la cuenta de ingresos,
entonces un producto nuevo se registra correctamente por defecto, y la persona que lo crea no tiene que
saber nada sobre el plan general de cuentas. Si no, cada producto nuevo es una pequeña decisión
contable tomada por alguien que está pensando en material de oficina.

## Unidades de medida, y la aritmética del almacén

La segunda cosa que hay que hacer bien es la unidad.

Riverton compra carpetas con anillas en cajas de veinte y las vende de una en una. Si el sistema no
sabe que una caja es de veinte, entonces cada recepción, cada conteo y cada entrega es un argumento, y
alguien terminará convirtiendo en su cabeza en el momento equivocado.

Odoo resuelve esto con dos unidades por producto: la unidad de medida usada para comprar y almacenar
(la caja), y la unidad de venta (la unidad), con un factor de conversión. El almacén cuenta cajas; el
cliente ordena unidades; la factura es en unidades; el stock está en cajas. Un número, tres vistas.

Hay aquí una trampa que ha costado a empresas más dinero que cualquier otro ajuste único: **la unidad
de medida de un producto existente no puede cambiarse después de que haya movido.** Una vez que se han
registrado cien recepciones en "unidad", decirle al sistema que el producto en realidad se compra en
"cajas de veinte" no convierte el historico; lo corrompe. El momento de hacer esto bien es antes de la
primera recepción, lo cual es por qué Tom dedicó una hora a ello y por qué esa hora valió más que los
dos días que habría gastado luego en reconciliar un conteo de stock.

## El almacén en sí

Un ERP no tiene "el almacén". Tiene *ubicaciones*, y una ubicación es cualquier lugar donde el stock
puede estar.

Odoo instala dos por defecto: una ubicación virtual llamada *Socios* (de donde vienen las mercancías y
adónde van, porque un proveedor no es una estantería) y *Stock*, el almacén físico. Desde ahí una
empresa añade lo que realmente tiene: *Stock/Estante A*, *Stock/Estante B*, *Stock/Devoluciones*,
*Stock/Dañado*.

![Las ubicaciones del almacén: un lugar para todo, incluidas las lugares donde las mercancías no están](../../assets/screens/odoo-06-locations.png)

Riverton añadió cuatro: dos estanterías, una zona de devoluciones y una zona de cuarentena para
mercancías dañadas. La última importa más de lo que suena. Sin ella, el stock dañado se queda en la
ubicación principal y se cuenta como vendible, y la empresa descubre el problema cuando un cliente abre
una caja de carpetas aplastadas. Con ella, el daño es un *movimiento*—un documento, con una fecha y un
motivo—y el informe de stock dice la verdad.

## Los primeros productos

Los productos se introdujeron en una tarde, por Priya y Tom juntos, que es la única forma en que se
hace: el vendedor sabe cómo lo llama el cliente, el almacén sabe cómo lo llama el proveedor, y el
registro de producto necesita ambos.

Seis campos en ese formulario deciden casi todo lo que ocurre después.

**Tipo de producto.** *Mercancía* para lo que se puede poner en una estantería; *Servicio* para lo que
no. Un servicio no tiene stock ni entrega; una mercancía tiene ambas. Cometer un error aquí hace que un
producto sea permanentemente no entregable o permanentemente no contable.

**Precio de venta y precio de compra.** Los valores por defecto. El precio real para un cliente dado
puede ser diferente—para eso son las listas de precios—pero el valor por defecto es el que ve el
vendedor cuando va aprisa.

**Impuesto.** La tasa que aplica a este producto. Como dijo el capítulo diez: configurada aquí, una
vez, y heredada por cada documento.

**Unidad de medida.** Como arriba.

**Referencia interna.** El código que usa el almacén. Es el campo que marca la diferencia entre un
sistema que los humanos pueden usar y uno que no, porque es lo que la gente dice en voz alta cuando está
de pie frente a una estantería.

**Código de barras.** Opcional, y transformador si tienes un escáner: una entrega puede verificarse
emitiendo un pitido por cada caja en lugar de leer una lista.

## El primer stock

Un sistema que cree que el almacén está vacío reusará entregar algo, lo cual es correcto y
molestoso. Así que el primer stock hay que introducirlo, y hay dos formas honestas de hacerlo.

La primera es una *inventario inicial*: le dices al sistema cuántas unidades de cada producto tienes, en
una fecha dada, y crea el correspondiente stock. Ese es el que hizo Riverton, en dos noches, con una
tabla de madera y una linterna.

La segunda es un *conteo de stock*: el sistema te pide que cuentes, y introduces lo que encuentras, y
registra la diferencia entre lo que creía y lo que es real. Ese es el que hace Riverton ahora cada
trimestre, y es una operación diferente con un propósito diferente.

Ambas son documentos. Ninguna es un número escrito en un campo. Esta es la disciplina que hace que todo
el sistema funcione: **el stock nunca es un número que estableces; es la suma de los movimientos que has
registrado.** Si eso suena pedante, considera lo que ocurre cuando un número puede establecerse:
alguien lo establece, alguien más lo vuelve a establecer, y el almacén y las cuentas disagreeán para
siempre.

## Las cosas que no son cosas

Hay una categoría de producto que causa más confusión que cualquier otra, y vale una página para sí
misma: los productos que no son físicos.

Riverton tiene tres de ellos, y todo mayorista tiene los mismos tres.

**El flete.** El cargo que paga el cliente por la entrega. No tiene stock, nunca se recibe, y debe
facturarse. En Odoo es un producto de tipo *Servicio*, con una tasa de impuesto y un precio, y lo único
que lo distingue de una caja de bolígrafos es que nunca aparece en una entrega.

**El descuento.** No un producto en absoluto, en la mayoría de los sistemas: una línea negativa en el
pedido, o una regla de lista de precios. Pero una empresa que emite notas de crédito por devoluciones
por volumen necesita un producto para poner en la nota de crédito, y suele llamarse algo como *Devolución
por volumen* y escribirse como un servicio.

**La muestra.** Un producto que se regala. Tiene stock, sale del almacén, y no debe facturarse. Si se
modela como un producto normal con precio cero, los informes de margen mostrarán una pérdida del cien
por ciento sobre cien unidades; si se modela como un servicio, el stock nunca saldrá. La forma limpia es
una *entrega* del producto sin un pedido detrás, con un motivo, lo cual es también la única forma en
que el coste termina en el lugar correcto.

Ninguna de estas es difícil. Todas son invisibles el primer día y producen números extraños el
trigesimo, lo cual es por qué la persona que configura el sistema debería sentarse con la persona que
factura y hacer una pregunta simple: *¿qué ponemos en una factura que no está en una estantería?*

## Los cuatrocientos productos que nadie compra

Todo mayorista los tiene: el catálogo de cosas que se compraron una vez para un cliente que pidió, y
luego nunca más. Los mil cien referencias de Riverton contenían, según la estimación de Tom, unas
cuatrocientas de esas.

La tentación es limpiarlas en la primera semana, y es el primer movimiento equivocado por dos razones.
La limpieza toma semanas, y le enseña a la oficina que el nuevo sistema es una carga antes de haberles
enseñado que el nuevo sistema es útil.

El movimiento correcto es traer las cuatrocientas líneas que importan—las que tienen actividad en el
último año—y dejar el resto en el viejo sistema, archivado, tanto como exige la ley. Un producto que no
ha movido desde 2019 no necesita un registro en el nuevo sistema el primer día; necesita una decisión,
y la decisión puede esperar hasta que alguien tenga tiempo.

Hay un segundo beneficio en esperar. Después de tres meses del nuevo sistema, el informe *productos sin
movimiento en el último año* es una lista de exactamente los candidatos a jubilación, producida en un
segundo, con el valor de stock adjunto. La limpieza se convierte en una decisión con números, en lugar
de una semana de escritura.

## La regla de reabastecimiento

La última cosa que Tom configuró fue la regla de reabastecimiento, y es el primer lugar donde el
sistema empieza a ser útil en lugar de meramente preciso.

Para cada producto estableció dos números: un *mínimo* (por debajo de esto, estamos en riesgo) y un
*máximo* (pedir hasta esto). Odoo vigila el stock, y cuando un producto cae por debajo del mínimo propone
un pedido de compra para la diferencia. No lo envía. Lo propone, en una lista, y una persona decide.

Esa distinción—proponer, no actuar—es la misma distinción que importará enormemente cuando llegue el
asistente en la Parte III. Una máquina que propone es un colega. Una máquina que actúa sin preguntar es
un riesgo con un enchufe.

---

El viernes de esa semana, Tom hizo algo que no había hecho en diecinueve años: imprimió un informe de
stock y lo leyó en la furgoneta, en camino a una entrega.

"Cuatrocientos doce líneas," dijo, cuando volvió. "Las conozco todas. Pero nunca las he visto en una
solo página antes. Las he visto en mi cabeza, de una en una, cuando alguien preguntaba."

Puso el informe sobre el escritorio de Maggie.

"Mira el papel," dijo. "Tenemos mil cien remesas y vendemos unas noventa a la semana. Son tres meses
de papel. No es incorrecto, exactamente, pero es mucho dinero sentado en una estantería."

Lo era, y fue la primera vez que alguien en Riverton pudo decirlo con un número adjunto. El stock
siempre había estado ahí; el *hecho* sobre el stock estaba en la cabeza de Tom, y la cabeza de Tom
estaba en una furgoneta.

Eso es lo que se convierte en un almacén cuando se modela correctamente: no un lugar donde las cosas
están, sino un lugar donde las cosas son *conocidas*. Y el conocimiento, una vez que existe, empieza
inmediatamente a hacer preguntas que nadie había pensado en hacer—sobre el papel, sobre el efectivo,
sobre las mil cien remesas que podrían haber sido cuatrocientas.

Maggie escribió el número en el reverso del informe de stock y lo puso en el cajón con la servilleta
y la tarjeta de Gerald. El cajón se estaba llenando. Eso, decidió, era un buen signo.
