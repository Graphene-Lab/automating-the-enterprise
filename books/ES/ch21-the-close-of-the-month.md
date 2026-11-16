# 21. El cierre del mes

Cerrar un mes es lo más parecido a un ritual religioso que tiene una pequeña empresa, y como la mayoría de los rituales, se cumple porque la alternativa es peor.

El objetivo es simple: declarar que un período ha terminado, que sus números son definitivos y que no se añadirá nada a ellos después. Todo lo que una empresa hace con sus cuentas—pagar impuestos, informar a un banco, valorar la empresa, pagar un dividendo—depende de que existan períodos con bordes.

Doreen solía cerrar un mes en cuatro noches, con una calculadora, un extracto bancario impreso y una lista de cosas que no quería mirar. El primer cierre con el sistema tardó una tarde, y el segundo noventa minutos. Este capítulo es lo que ocurrió entre medias.

---

## Los siete controles

El capítulo diecinueve listó las preguntas. Aquí está cómo se ven como trabajo.

**Uno: cada entrega tiene una factura, y cada factura tiene una entrega.** El asistente produce la lista de órdenes entregadas aún no facturadas, y la lista de facturas sin entrega detrás. La primera debe estar vacía al final del mes; la segunda debe estar vacía siempre, porque una factura sin entrega es o un servicio (bien) o un error (no bien).

**Dos: cada factura de proveedor que llegó está en el sistema.** Este es el control que requiere un acto físico—vaciar la bandeja de correo, abrir los correos—and ningún sistema puede hacerlo por ti. Lo que el sistema puede hacer es decirte qué espera: la lista de pedidos de compra que han sido recibidos pero no facturados.

**Tres: el banco coincide.** El diario bancario se compara con el extracto, línea por línea. Odoo puede importar un archivo de extracto y proponer coincidencias; las proposiciones se aceptan o rechazan por una persona. Este es el control que solía tardar Doreen tres horas y ahora noventa minutos, y los noventa minutos se dedican a las seis líneas que no coincidieron automáticamente—que son, por supuesto, las interesantes.

**Cuatro: deudores y acreedores coinciden.** La lista de quién debe qué, por antigüedad, frente a la cuenta del libro mayor. Si difieren, hay una entrada sin socio en ella, y encontrarla es una búsqueda más que una investigación.

**Cinco: el existe está correcto.** La valuación de existe en las cuentas frente al almacén. Una diferencia aquí suele ser una entrega que nunca se validó, o un coste que no se recalculó.

**Seis: los devengamientos son correctos.** Un gasto que pertenece a este mes y aún no se ha facturado—la electricidad, el alquiler trimestral, la cuota del contador—tiene que registrarse, o el profit del mes se adultera y el del siguiente mes se castiga.

**Siete: el IVA es correcto.** El impuesto sobre ventas y compras, frente al devoluto. Este es el control que lleva adjunta una fecha límite, y el en el que un error es más costoso.

Siete controles, y la contribución del sistema no es realizarlos. Es que hace que cada uno sea una *lista* más que una *excavación*.

## El devoluto del IVA, que es el cierre con fecha límite

Todo en este capítulo hasta ahora es voluntario: una empresa cierra su mes porque quiere saber dónde está. El devoluto del IVA no es voluntario, y es la única parte del cierre en la que un error lleva adjunto un precio.

El devoluto es, en esencia, un resumen de dos números: el impuesto cobrado en ventas, y el impuesto pagado en compras, con la diferencia yendo hacia o saliendo del oficina de impuestos. Un niño podría hacer la aritmética; la dificultad está enteramente en la *clasificación*—qué ventas son de tipo general, cuáles son de tipo cero, cuáles están fuera del alcance, y qué compras son recuperables.

Odoo produce el devoluto de los códigos fiscales en los documentos, por eso el capítulo diez insistió en que el impuesto se configura en el producto y no se escribe en la factura. Un único producto con el código equivocado produce un devoluto que es incorrecto de una manera invisible: el total es plausible, la aritmética es correcta, y la clasificación es falsa.

El hábito de Doreen, conservado de la era del papel, es reconciliar el devoluto con el libro mayor antes de presentarlo: la cifra de ventas en el devoluto debe igualar el saldo acreedor en las cuentas de ventas para el período, y la cifra de compras debe igualar el saldo deudor en las de compras. Si coinciden, la clasificación es al menos internamente coherente. Si no, la diferencia es un documento con el código equivocado, y encontrarlo es una búsqueda más que un adivinar.

El asistente hace esa comparación en una frase, y es la cosa más valiosa que hace en todo el ciclo contable, porque convierte una reconciliación de dos horas en un control.

## Cierre del año

El cierre de año es el cierre de mes con más ceremonia y mayores apuestas, y los mismos siete controles aplican, con tres adiciones.

**La valuación de existe** tiene que ser correcta, porque es el número más grande en el balance de un mayorista. Un conteo de existe en la última semana del año no es una formalidad; es la diferencia entre un profit y una pérdida.

**Los devengamientos y pagos anticipados** tienen que ser completos: una prima de seguro pagada en noviembre para el año siguiente pertenece en parte al año siguiente, y una empresa que ignora esto reporta un profit que no existe.

**Las cuentas de los administradores o propietarios** tienen que estar ordenadas, porque el oficina de impuestos las mira primero.

Y luego el año se bloquea, y las cuentas se archivan, y durante once nadie vuelve a mirarlas—which is why the *monthly* close matters more than the annual one. A company that only looks once a year is driving with the windscreen painted over and a annual glance in the mirror.

## El cierre en una empresa de uno

La mayor parte de este libro asume una empresa con oficina: varias personas, una división de trabajo, alguien que puede comprobar el trabajo de otro. El cierre se ve distinto en una empresa de uno, y vale una sección porque un montón de negocios son exactamente eso.

En una empresa de uno, no hay separación de funciones. La persona que emite la factura la registra, la paga, la reconcilia y cierra el mes. Los controles que protegen a una empresa mayor—límites de aprobación, cuatro ojos, una persona distinta la que libera el pago—no existen, y no pueden inventarse por software.

Lo que el sistema puede hacer en su lugar es hacer que el *registro* sea completo, para que la ausencia de un control sea al menos visible. Tres hábitos valen más que cualquier configuración.

**Haz el cierre de una sola vez, en un tiempo fijo.** Un cierre de mes repartido en tres noches es un cierre de mes con tres posibilidades de perder el hilo. El sistema hace posible la sesión: dos horas, una vez al mes, con las siete listas delante de ti.

**Escribe el razonamiento.** Cuando un gasto es inusual, cuando el saldo de un cliente se ve incorrecto, cuando la factura de un proveedor no coincide: una línea en un archivo diciendo qué decidiste y por qué. Seis meses después, esa línea es lo único que te recordará.

**Mantén la reconciliación bancaria actualizada.** En una empresa de uno, el extracto bancario es el único testigo independiente. Reconciliarlo semanalmente en lugar de mensalmente convierte una investigación de dos horas en cuatro de diez minutos, y capta el error mientras todavía recuerdas haberlo cometido.

El asistente ayuda aquí de una manera fácil de subestimar: se le puede preguntar *¿algo se ve incorrecto este mes?* y producirá las excepciones—la cantidad rara, la referencia perdida, el cliente que pagó dos veces. En una empresa con departamento de finanzas, esa pregunta la hace el departamento de finanzas. En una empresa de uno, nadie la hace a menos que el sistema la haga.

## El cierre como conversación

La cosa más útil que el asistente hizo durante el primer cierre de Riverton no fue producir un informe. Respondió una pregunta en medio de una.

> *La reconciliación bancaria tiene seis líneas sin coincidir. ¿Cuáles son?*

> *Seis líneas sin coincidir, total £3,412.60:*
> *1. 2 nov, £1,200.00 acreedor — pago de Calder & Sons, sin referencia de factura.*
> *2. 3 nov, £14.50 deudor — cargo bancario, sin entrada en los libros.*
> *3. 7 nov, £2,000.00 deudor — transferencia a la cuenta de ahorros, no registrada.*
> *4. 9 nov, £88.10 deudor — pago con tarjeta a un proveedor de papelería, sin factura.*
> *5. 11 nov, £60.00 acreedor — devolución del mensajero, no registrada.*
> *6. 12 nov, £50.00 acreedor — pagador desconocido, referencia "INV 2025".*

Seis líneas, seis historias. Un cliente pagó sin referencia; el banco cobró una comisión; Maggie movió dinero a ahorros; alguien compró algo con la tarjeta de la empresa; un mensajero devolvió un cargo; y alguien pagó cincuenta libras contra una factura de 2025, que es o un pago muy tardío o un error.

La versión vieja de esta conversación ocurría tres semanas después, por teléfono, con un banco, y se llamaba "una consulta". La versión nueva ocurre el segundo día laboral del mes, en una ventana, y se llama "martes".

## Bloquear el período

Cuando los siete controles están hechos, el período se bloquea. En Odoo esto es una configuración en el período contable—una *fecha de fin* más allá de la cual no se pueden registrar entradas—and es lo más parecido que tiene el sistema a un sello.

Bloquear es una promesa al futuro: cualesquiera que digan los números, seguirán diciéndolo el año que viene. También es una promesa al pasado: nadie puede mejorar en silencio los resultados del trimestre pasado moviendo un gasto hacia él.

Las empresas resisten el bloqueo, y la resistencia es comprensible. Bloquear significa que un error encontrado en marzo no se puede arreglar en enero; tiene que arreglarse en marzo, con una explicación. Eso es incómodo, y es todo el punto: una cuenta que se puede reescribir no es una cuenta.

## El primer cierre, y cómo se sintió

La descripción de Doreen del primer cierre vale la pena citar a longitud, porque es la descripción más honesta de este tipo de cambio que tiene este libro.

"Me senté a las nueve esperando estar ahí hasta las siete. Tenía la calculadora, tenía los extractos impresos, tenía un sándwich. Y luego le pedí las siete listas y vinieron, una tras otra, en unos diez minutos, y pensé: bien, ahora empieza el trabajo.

"Pero el trabajo era solo... mirar las listas. El banco tenía seis líneas y sabía cuáles cuatro de ellas eran. La lista de entregado-no-facturado tenía dos órdenes, y una de ellas era una muestra que habíamos enviado al centro de jardín, que no debería haberse facturado en absoluto, así que arreglé la entrega en su lugar. El existe estaba desviado por cuarenta resmas, que era la paleta que entró el jueves y se registró como cuarenta paletas—ese fue mi error, de la unidad de medida, y lo encontré en cuatro minutos porque el sistema me mostró el movimiento.

"A las dos y media había hecho todo excepto el IVA, y el IVA tardó una hora porque siempre lo compruebo dos veces. Y luego bloqueé el mes, y me senté allí, y no sabía qué hacer conmigo misma."

Se detuvo.

"Treinta y un años, y nunca he terminado un cierre en un día. Nunca he terminado uno sin un error que encontré a la mañana siguiente. Los errores siempre estaban en las últimas tres horas, cuando estaba cansada."

## Para qué era el tiempo

La pregunta interesante no es cómo se hizo el cierre más rápido. Es en qué se gastó el tiempo en su lugar.

En el caso de Riverton, tres cosas.

**La paleta que se registró como cuarenta paletas** se encontró y corrigió en el mismo mes, en lugar de ser descubida por un conteo de existe en diciembre. Eso es una diferencia de dinero real.

**Dos órdenes que habían sido entregadas y no facturadas** se facturaron en el mes al que pertenecían, lo que movió £3,400 de ingresos al período correcto—and, más importante, al devoluto fiscal correcto.

**Y las seis líneas bancarias** produjeron una conversación con el mensajero sobre una devolución que nadie había notado, y una decisión de dejar de usar la tarjeta de la empresa para compras pequeñas, porque los recibos eran un desorden.

Ninguna de esas es dramática. Juntas son la diferencia entre un conjunto de cuentas que es un registro y un conjunto de cuentas que es una *herramienta*—algo que puedes usar para tomar una decisión, porque le confías y porque no está desactualizado tres semanas.

---

El ritual de cierre de mes tiene una función más que rara vez se habla, y vale la pena decirlo claramente.

Es el momento en que alguien mira el negocio entero. No las ventas, no el existe, no el banco—lo entero, a la vez, con una fecha límite. Una empresa que cierra su mes correctamente tiene, doce veces al año, un momento en que alguien competente se sienta y pregunta *¿esto tiene sentido?*

La mayoría de las pequeñas empresas no tienen ese momento. Tienen un devoluto fiscal, preparado con prisa, por un contador que ve los números dos veces al año. La diferencia entre esas dos empresas no es el software. Es si alguien alguna vez mira.

La contribución del software es hacer que mirar sea lo suficientemente barato como para que ocurra.
