# 17. Comprar cosas

Comprar es la mitad de un negocio sobre la que nadie escribe libros.

Vender tiene algo de romántico: clientes, cotizaciones, la emoción de la orden. Comprar tiene una orden de compra, un albarán de entrega, una factura de un proveedor y un proceso de pagos. Y sin embargo, cada libra que gasta un mayorista llega por esa puerta, y la diferencia entre una empresa que compra bien y una que compra mal es la diferencia entre un margen y un hábito.

La compra en Riverton la hacía Maggie, por teléfono, de memoria, durante once años. Conocía al proveedor de papel, al proveedor de bolígrafos y al proveedor de carátulas, y sabía cuánto había pagado la última vez porque tenía una carpeta. Lo que no tenía era ninguna forma de saber si el precio se había disparado, o si la última entrega había llegado efectivamente, o si la factura que estaba a punto de pagar coincidía con la orden que había hecho.

El primer trabajo de compras del asistente fue una regla de reabastecimiento que se activaba un miércoles.

---

## La regla de reabastecimiento, y lo que propone

El capítulo once fijó dos números en cada producto: un mínimo y un máximo. Odoo vigila el existencias, y cuando un producto cae por debajo de su mínimo, propone una orden de compra.

Propuso una de carátulas con anillas el miércoles, en una lista que Tom revisó con su café.

> *Tres productos están por debajo de su punto de reabastecimiento: Carátula A4 con anillas (azul) 62 disponibles, mínimo 100; Marcadores para pizarra (surtido) 44 disponibles, mínimo 60; Papel A4 9 resmas disponibles, mínimo 40.*

Tom revisó la lista, decidió que el papel podía esperar hasta que se confirmara el precio por palet, y pidió los otros dos.

> *Cree una orden de compra de 500 carátulas A4 con anillas, azules, y 200 paquetes de marcadores para pizarra, surtidos, de nuestros proveedores habituales, al último precio pagado. No la confirme todavía.*

> *Orden de compra P00008 creada, en borrador. Dos proveedores, porque los productos provienen de distintos proveedores: 500 × Carátula A4 con anillas (azul) de Pennine Paper a £2.10; 200 × Marcadores para pizarra (paquete de 4, surtidos) de Kestrel Supplies a £6.80. Total neto £2,410.00, IVA £482.00, total £2,892.00. No se ha enviado nada; diga "confirmar" para hacer los pedidos.*

Dos cosas de esa respuesta valen la pena observarse, y ambas son el sistema haciendo algo que una persona habría tenido que hacer a mano.

La primera es *dos proveedores*. Tom pidió dos productos; el sistema sabía que provenían de distintos proveedores y generó dos órnes de compra. Una persona habría hecho lo mismo, tras revisar los registros de producto. La diferencia es que la persona podría haberse olvidado, y haber pedido carátulas al proveedor de marcadores.

La segunda es *el último precio pagado*. Eso no es una lista de precios; es un dato de la historia. El sistema miró la compra más reciente de ese producto y usó el precio. Si el proveedor ha subido sus precios, la orden será incorrecta—pero será incorrecta de una forma que se puede ver, porque el precio anterior está en el registro junto al nuevo.

## Lo que hace confirmar

Confirmar una orden de compra hace tres cosas, y la tercera es la que importa.

**Compromete** a la empresa a comprar, a un precio, para una fecha—lo cual es una promesa, y por tanto un documento que debe revisarse antes de que se emita.

**Crea una recepción esperada**: el almacén ahora sabe que van a llegar quinientos cuadernos, y cuándo. Eso es lo que hace posible responder a la pregunta *¿podemos prometer esto a un cliente la próxima semana?* con algo mejor que un conjetura.

Y **abre una puerta para la factura**: cuando llegue la cuenta del proveedor, puede cotejarse contra la orden. No porque el sistema sea sospechoso, sino porque la *triple verificación* es el control más antiguo del comercio y sigue siendo el mejor.

## La triple verificación

La idea es lo suficientemente simple como para caber en una servilleta, y ha ahorrado a empresas más dinero que cualquier función de software inventada jamás.

Pediste quinientos cuadernos a £2.10 cada uno. El almacén recibió quinientos cuadernos. La factura del proveedor dice quinientos cuadernos a £2.10 cada uno. Tres documentos, tres números, y deben coincidir antes de pagar la cuenta.

Si la factura dice £2.30, alguien pregunta por qué. Si el almacén recibió cuatrocientos ochenta, alguien pregunta a dónde fueron los veinte. Si la orden era de quinientos y la factura de seiscientos, alguien pregunta quién autorizó los cien extra—y la respuesta suele ser *nadie*, que es exactamente el punto.

El control es viejo. Los libros de contabilidad de costos lo describieron en los años 20, y se formalizó en los manuales de compra de los años 50, cuando los grandes fabricantes descubrieron que la diferencia entre lo que pedían y lo que pagaban era una fracción significativa de su beneficio. Sobrevive porque es barato: tres documentos que ya existen, comparados por una máquina que no se aburre.

Lo nuevo es que la comparación tarda un segundo y puede ser *explicada*.

> *Cree la factura del proveedor para la orden de compra P00008 y verifíquela contra la orden y la recepción.*

> *Factura de proveedor BILL/2026/0031 creada desde P00008 para Pennine Paper: 500 × Carátula A4 con anillas (azul) a £2.10, neto £1,050.00, IVA £210.00, total £1,260.00. Cotejada: pedido 500, recibido 500, facturado 500. Sin diferencia. La factura está en borrador.*

Sin diferencia. En un buen día, eso es todo el trabajo: tres números que coinciden, en una frase, en un segundo.

En un mal día dice algo como: *pedido 500, recibido 480, facturado 500 — una diferencia de 20 unidades a £2.10.* Y entonces una persona tiene que decidir: ¿el proveedor entregó menos, ¿el almacén contó mal, o alguien aceptó una entrega parcial y olvidó registrarla? El sistema no puede responder a eso. Solo puede hacer que la pregunta sea imposible de evitar.

---

## Pagar

Pagar a un proveedor es la imagen especular de ser pagado, y tiene la misma forma: un documento (la factura), un pago, y una coincidencia entre ambos.

> *Registre un pago del monto completo de BILL/2026/0031, con fecha de hoy, por transferencia bancaria.*

> *Pago registrado para BILL/2026/0031: £1,260.00 a Pennine Paper, desde el diario bancario, con fecha 14 de noviembre de 2026. La factura está ahora completamente pagada; el saldo del proveedor es cero.*

El diario bancario no es el banco. Es el *registro* de la empresa de lo que hizo el banco, y ambos tienen que conciliarse—lo cual es el ritual mensual descrito en el próximo capítulo, pero uno. La distinción importa porque es donde una empresa descubre que un pago que registró nunca se hizo, o un pago que hizo el banco nunca se registró.

## Una breve historia de la orden de compra

La orden de compra como documento es hija de la era del ferrocarril. Antes de los ferrocarriles, un comerciante compraba a personas que podía ver, y un apretón de manos más una entrada de libro era suficiente. Los ferrocarriles crearon distancia: un comprador en Manchester pidiendo a un molino en Leeds necesitaba un documento que dijera qué se pedía, a qué precio, y cuándo, porque las mercancías llegarían días después y el hombre que las había pedido quizás no estuviera allí.

La forma de la orden de compra moderna—número, fecha, proveedor, líneas, cantidades, precios, condiciones—se fijó a principios del siglo XX y no ha cambiado desde entonces, porque codifica la información mínima necesaria para resolver un litigio. El software no cambió el documento. Cambió el costo de producir, enviar, cotejar y encontrarlo.

Lo cual es, en una frase, el argumento de todo este libro.

## El registro de proveedor, y para qué sirve

Un proveedor en un ERP no es una entrada de directorio telefónico. Es un conjunto de condiciones, y son las condiciones las que hacen que el papeleo funcione.

Los registros de proveedor de Riverton se construyeron en una tarde, y cada uno contiene cinco cosas que importan: las **condiciones de pago** (treinta días desde la fecha de factura, o fin de mes siguiente, que son cosas muy distintas), la **moneda**, el **tratamiento fiscal** (si el proveedor cobra IVA y bajo qué régimen), el **plazo de entrega** que espera el comprador, y el **contacto** que responde cuando algo va mal.

Ninguna de esas es decoración. Las condiciones de pago deciden la fecha de vencimiento en cada factura, y un proveedor cuyas condiciones se registran como "30 días" cuando en realidad son "60 días neto" se pagará temprano cada mes durante un año—lo que suena inofensivo y es en realidad un pequeño préstamo permanente a un proveedor que no lo pidió. La moneda decide si una factura en euros se convierte al tipo de cambio de la fecha de factura o de la fecha de pago, lo cual es una diferencia que aparece como ganancia o pérdida. El plazo de entrega decide cuándo el sistema espera las mercancías, lo que hace que el informe de "órnes de compra tardías" tenga algún sentido.

El sistema antiguo no tenía nada de esto. Tenía una carpeta de facturas y un número de teléfono escrito en el interior de la carpeta.

## Lo que no hace una orden de compra

Vale la pena ser claro sobre los límites, porque una empresa que espera demasiado de un documento quedará decepcionada por el software que lo produce.

Una orden de compra no **negocia**. Registra el precio que se acordó, y el asistente puede mostrarte lo que pagaste la última vez, y lo que pagaste la vez anterior—lo cual es la munición para una negociación, no la negociación.

No **garantiza** la entrega. Crea una expectativa, y la expectativa es lo que mide el informe de órnes tardías.

No **verifica las mercancías**. Eso es la recepción, y la recepción es una persona con una tabla de madera.

Y no **paga**. El pago es una decisión aparte, tomada después, normalmente por alguien que primero mira el saldo bancario.

Lo que hace es hacer que esas cuatro cosas sean *visibles*, y la visibilidad es lo que convierte una relación conducida por teléfono en una relación que puede examinarse.

## El precio que se disparó

El cargo por palet que Doreen encontró en el capítulo十九 tenía una contraparte en el lado de compra, y se encontró con el mismo tipo de pregunta.

> *¿Qué proveedores han subido sus precios en los últimos seis meses, y en cuánto?*

La respuesta listaba cuatro proveedores y once productos, y uno de ellos era el papel: el precio de compra había pasado de £2.05 a £2.18 por reama en julio, lo que es un seis por ciento, en un producto que Riverton compra por palet.

Seis por ciento en papel era, a los volúmenes de Riverton, unas £1,900 al año. Nadie lo había notado, porque nadie tenía una lista de lo que pagaba antes. La compradora—Maggie, en este caso—había notado que la factura "se veía un poco más cara" y había supuesto que era su imaginación.

Ese es el patrón al que todo este libro sigue volviendo: el dinero no se pierde en errores grandes y dramáticos. Se pierde en cambios demasiado pequeños para notarse de uno en uno y demasiado grandes para ignorarse cuando se suman. Un sistema que recuerda el precio anterior los hace *notables*, y notar es la mayor parte del trabajo.

## La única cosa que hay que hacer bien el primer día

Si una empresa se lleva una sola cosa de este capítulo, debe ser esta: **registrar las condiciones de pago en el proveedor, no en la factura.**

Una factura con condiciones escritas en ella es un documento que se pagará con esas condiciones una sola vez. Un proveedor con condiciones en su registro es un proveedor cuya cada factura vence en el día correcto, para siempre, sin que nadie tenga que pensar en ello. La diferencia es treinta segundos de configuración y un año de no tener esta conversación:

"¿Por qué estamos pagando a Pennine temprano?"
"No sé, el sistema dice que la factura está vencida."
"La factura vence en sesenta días, no en treinta."
"Entonces el registro de proveedor está mal."
"¿Desde cuándo?"

Desde el primer día, normalmente, y nadie lo notó porque pagar temprano no es un error del que nadie se queje—excepto la persona que mira el flujo de caja en febrero.

---

El veredicto de Tom, al final del primer mes comprando a través del sistema, era característicamente práctico.

"Solía pensar que una orden de compra era papeleo," dijo. "No lo es. Es lo único que me evita pagar por algo que no recibí."

Maggie le preguntó si el sistema había detectado algo.

"Dos veces. Una vez la factura era por veinte más de lo que recibimos, y una vez el precio había subido sin que nadie nos lo dijera. Ambas veces lo habría pagado, porque habría mirado la factura y pensado, sí, eso parece correcto."

*Correcto* es la frase que hay que recordar. La mayor parte del dinero perdido en una pequeña empresa se pierde en la brecha entre *correcto* y *correcto*, y la brecha no se cierra siendo más cuidadoso. Se cierra teniendo tres números que comparar, y una máquina que los compara cada vez.
