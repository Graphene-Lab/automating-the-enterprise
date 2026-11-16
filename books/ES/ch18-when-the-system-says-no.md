# 18. Cuando el sistema dice que no

El primer rechazo llegó un jueves por la tarde, y fue el momento en que Doreen dejó de sospechar del sistema y empezó a confiar en él.

Había pedido al asistente que corrigiera un error: una factura se había registrado con la cantidad equivocada, y ella quería que se corrigiera.

> *Cambia la cantidad de la factura INV/2026/0007 de 350 a 300.*

> *No puedo cambiarla. INV/2026/0007 está registrada, y las facturas registradas son de solo lectura: las entradas de libro y el momento fiscal ya están registrados. Para corregirla, anula la factura y emite una nota de crédito, o emite una nota de crédito por la diferencia. ¿Cuál prefieres?*

Doreen lo leyó dos veces y luego llamó a Maggie.

"No lo hace", dijo.

"¿No quiere o no puede?"

"No puede. Dice que el libro ya está escrito."

Esa distinción—*no quiere* frente a *no puede*—es el tema de este capítulo, y es la razón por la que un sistema empresarial es distinto de un colega servicial.

---

## Los tres tipos de no

Un ERP rechaza por tres motivos distintos, y vale la pena aprender a distinguirlos, porque cada uno exige una respuesta diferente.

**El sistema no puede hacerlo porque el modelo lo prohíbe.** No puedes registrar una factura sin líneas, entregar mercancías que no tienes, o cambiar un documento que ya ha producido entradas de libro. Estos rechazos son estructurales: protegen la integridad del modelo, y no hay forma de anularlos, porque una anulación rompería la garantía que hace que el modelo valga la pena tenerlo.

**El sistema no puede hacerlo porque al *usuario* no se le permite.** El asistente es un usuario con un rol, y si el rol no incluye eliminar registros, la solicitud se rechaza por el sistema de permisos antes de llegar al modelo. Estos rechazos son sobre autoridad, y pueden cambiarse—alguien con derecho para cambiarlos, deliberadamente, y con constancia de haberlo hecho.

**El sistema no puede hacerlo porque los *datos* no están.** El cliente no existe, el producto no tiene precio, el stock está en una ubicación que el usuario no puede ver. Estos rechazos son sobre el estado del mundo, y suelen ser los más útiles, porque señalan algo que necesita corrección en lugar de algo que necesita ser anulado.

Un buen asistente te dice de qué tipo de no se trata. Eso es lo que ocurrió arriba: el rechazo nombró el documento, la razón, y dos alternativas válidas.

## Los rechazos que enseñaron algo a Riverton

Durante los primeros meses, el sistema dijo no de un puñado de formas que eran cada una una pequeña lección.

**"No hay suficiente stock."** Tom pidió una entrega de seiscientos archivadores cuando solo había cuatrocientos doce. El sistema rechazó, y ofreció entregar lo disponible y crear un pedido pendiente para el resto. Tom eligió el pedido pendiente, y el cliente fue telefoneado antes de que saliera la furgoneta—que es justamente el punto del rechazo: movió la conversación desde la playa de carga hasta el teléfono, donde todavía podía ser útil.

**"El período contable está cerrado."** Doreen intentó registrar una factura fechada en el mes anterior, después de que el mes hubiera sido bloqueado. El sistema rechazó y explicó que el período estaba cerrado. Movió la factura al mes actual, y luego pidió al asistente una lista de todo lo registrado después del cierre—which came back empty, which is what a closed period is for.

**"Este usuario no puede eliminar registros."** El asistente, pedido para eliminar un cliente duplicado, dijo que no podía, y ofreció archivarlo en su lugar. Archivar mantiene el registro y lo oculta de las listas, que es la respuesta correcta para un duplicado que tiene documentos adjuntos. El rechazo había sido configurado a propósito, en el capítulo doce, por alguien que pensó en ello con antelación.

**"Ese producto no tiene impuesto."** Se había creado un producto nuevo sin tasa impositiva, y la cotización rechazó calcular un total. El rechazo señaló el formulario del producto, y la corrección tomó treinta segundos. Sin el rechazo, la cotización habría salido sin IVA—and the company would have discovered it at the end of the quarter, in a return that did not add up.

## Leer el registro

Cada rechazo deja una trazabilidad, y aprender a leer la trazabilidad es la habilidad que transforma un asistente de una caja negra en un colega.

El asistente escribe un registro: lo que se le pidió, qué herramientas eligió, con qué argumentos, qué regresó, y cuánto tiempo tomó. No es un documento bonito—it is a file, in a folder, with timestamps—y es el primer lugar a donde mirar cuando algo ha salido mal.

Tres patrones vale la pena reconocerlos.

**Un bucle.** La misma herramienta llamada con los mismos argumentos, tres o cuatro veces. Es el asistente intentando que algo funcione y fallando de la misma manera cada vez—usualmente porque un documento está en un estado que no esperaba. El rechazo está en el registro, tres veces, y leerlo una vez es suficiente.

**Una herramienta equivocada.** El asistente eligió *crear* cuando debería haber elegido *actualizar*, y el ERP rechazó porque el registro ya existía. El registro muestra la elección; la corrección está en la instrucción, que no decía *actualizar*.

**Un éxito silencioso que no era lo deseado.** Sin error, sin rechazo, y un resultado que es técnicamente correcto y prácticamente inútil. Este es el patrón más difícil, porque nada en el registro parece mal. La defensa es la verificación: pedir al asistente qué hizo, y comparar eso con lo que se pretendía.

Doreen lee el registro cada viernes, por la misma razón por la que antes leía el extracto bancario: no porque espere un problema, sino porque leerlo es cómo aprendes qué parece normal—and therefore how you notice when it is not.

## El rechazo que salvó a un cliente

Un rechazo en el primer año de Riverton valió más que cualquiera de los éxitos, y ocurrió en medio de una discusión.

Un cliente—uno grande, y difícil—había recibido una factura por una entrega que afirmaban nunca haber llegado. La nota de entrega estaba firmada, pero la firma era ilegible, y el gerente de compras del cliente insistía en que las mercancías habían sido rechazadas en la puerta.

Priya pidió al asistente emitir una nota de crédito, porque el cliente amenazaba con llevar su negocio a otro lugar y la factura era de £640.

El sistema rechazó, y la razón que dio es la razón por la que esta historia está en el libro.

> *Puedo crear una nota de crédito, pero debes saber cómo se verá en las cuentas: una nota de crédito sin devolución detrás registra que las mercancías nunca se suministraron. La entrega se validó el 3 de septiembre por Tom Beck, y el movimiento de stock muestra 40 artículos saliendo del Estante A. Si el cliente rechazó la entrega, las mercancías deberían haber regresado y no hay ninguna devolución registrada. Si no la rechazaron, la nota de crédito estaría pagando por mercancías que se entregaron. ¿Cuál de las dos?*

Priya telefoneó al cliente, hizo la pregunta que el asistente había hecho, y descubrió que la entrega había sido aceptada por un guardia de seguridad temporal que había puesto la paleta en una sala de almacenamiento y no le había dicho a nadie. La factura se pagó en su totalidad, y el cliente se disculpó.

El rechazo no salvó los £640. Salvó una relación, y lo hizo rehusando permitir que una persona saltara una pregunta—which is what a good bookkeeper has always done, and what this system does because somebody configured it to.

## Los rechazos que una empresa debería diseñar a propósito

La mayoría de los rechazos vienen con el software. Algunos deben añadirse, deliberadamente, y son los que transforman un ERP de un sistema de registro en un sistema de control.

Cuatro valen la pena considerarlas en cualquier empresa que permita a un asistente escribir.

**Un límite de crédito para clientes.** Cuando un pedido llevaría a un cliente por encima de su límite, el sistema puede rehusar confirmarlo, o requerir aprobación. El asistente entonces reportará el rechazo y el número, que es exactamente la conversación que un vendedor debe tener con el dueño—antes de que salgan las mercancías, no después.

**Un descuento máximo.** Odoo puede configurarse de modo que un descuento por encima de un umbral necesita una segunda persona. El asistente no puede concederlo, porque el asistente es un usuario con un rol; solo puede decir quién sí podría.

**Un período cerrado.** Una vez que un mes está bloqueado, nada se registra en él, por nadie, incluyendo al asistente. Esa es la única medida de control más efectiva en todo el sistema, y cuesta una sola configuración.

**Una regla de cuatro ojos en los pagos.** En Odoo esto es una configuración del proceso de pago, no una función del asistente, pero el efecto es el mismo: el asistente prepara la corrida de pagos, una persona la libera.

Ninguna de estas es una formalidad. Cada una codifica una decisión que la empresa ya ha tomado sobre cómo quiere ser gestionada, y cada una convierte esa decisión en algo que no puede olvidarse un viernes ocupado.

## Lo que cuesta un rechazo

Hay un costo en la rigidez, y vale la pena nombrarlo porque las empresas que lo ignoran terminan apagando las reglas.

Un rechazo detiene el trabajo. Alguien tiene que dejar lo que está haciendo, descubrir por qué, y o corregir los datos o pedir una excepción. En una pequeña empresa, ese alguien suele ser el dueño, y el dueño suele ser la persona más ocupada del edificio.

El costo es real, y la forma de mantenerlo pequeño no es debilitar la regla sino hacer que el rechazo *informativo*. Un mensaje que diga *límite de crédito excedido: £2,310 de £2,000, cliente Calder e Hijos, revisado por última vez en marzo* le dice a la persona qué hacer. Un mensaje que diga *acceso denegado* no lo hace.

Ese es el argumento a favor de un asistente delante de un ERP en una sola frase: las reglas son del ERP, y la *explicación* es del asistente.

## Por qué la rigidez es la función

Hay una tentación, cuando un sistema rechaza algo, en buscar la configuración que apaga el rechazo. La mayoría de los ERPs tienen tales configuraciones, y la mayoría de ellas son un error.

Considera qué protegen los rechazos.

El rechazo a editar una factura registrada protege la **huella de auditoría**: el registro de lo que se envió al cliente, y cuándo. Una empresa que puede editar su propia historia no puede probar nada sobre ella.

El rechazo a entregar stock que no está protege la **promesa**: se le dijo al cliente una fecha, y la fecha depende de mercancías que existen.

El rechazo a registrar en un período cerrado protege las **cuentas**: un período está cerrado porque alguien ha reportado sobre él—to the bank, to the tax office, to the owners—and reopening it silently would make the report a lie.

El rechazo a permitir que un usuario eliminate protege la **responsabilidad**: si un documento puede desaparecer, entonces la ausencia de un documento no significa nada.

Ninguna de estas es sobre orden. Cada una es sobre la única propiedad que hace que un ERP valga su costo: que lo que dice es verdadero, y puede mostrarse que es verdadero.

## La parte del asistente en esto

Un asistente hace los rechazos *mejores*, de una forma que es fácil pasar por alto.

Una persona que se encuentra con un rechazo en una pantalla ve una caja roja con un código y una frase. Un asistente que se encuentra con el mismo rechazo puede explicarlo en el lenguaje de los negocios, ofrecer las alternativas, y hacer la válida si estás de acuerdo. Esa es la diferencia entre *Error: no se puede modificar un asiento registrado* y *la factura está registrada, así que no se puede editar; puedo emitir una nota de crédito por la diferencia, o anular y reemitir—which do you want?*

Hay un riesgo en esa fluidez, y vale la pena nombrarlo: un asistente que explica los rechazos de forma servicial puede hacerlos sentir negociables. No lo son. La explicación es una cortesía; la regla es la regla. El asistente no puede anular el ERP, porque el asistente no es la autoridad—and any assistant that claims otherwise has been given too much power, which is a fault in the installation, not a feature of the model.

## El único rechazo que no es un rechazo

Hay un cuarto tipo de no, y es el más peligroso porque parece un sí.

El asistente, pedido una pregunta cuya respuesta no está en el sistema, puede responder *plausiblemente*. No porque esté mintiendo, sino porque eso es lo que hace un modelo de lenguaje cuando no tiene datos: produce la frase más probable. Este es el problema de la alucinación, y la defensa es arquitectónica, no moral: el asistente debe hacerse obtener sus datos del ERP, a través de herramientas, y decirlo cuando la herramienta devuelve nada.

La regla de Riverton, en la pared junto al servilleta, es una sola frase: *si no puede mostrarte de dónde viene el número, no uses el número.*

Esa regla es por qué cada respuesta en este libro incluye los documentos detrás de ella—the invoice number, the order, the list of moves. No es decoración. Es la diferencia entre un sistema que puedes auditar y un sistema que tienes que creer.

---

Doreen emitió la nota de crédito, y la factura se mantuvo.

Esa noche dijo algo a Maggie que ninguna de las dos esperaba.

"Me gusta que dispute conmigo."

"¿Por qué?"

"Porque mi viejo sistema hacía lo que escribía. Si escribía el número equivocado, tomaba el número equivocado, y nunca me lo decía. Este me hace decir lo que quiero decir."

Pensó por un momento.

"Es como tener un contable que lleva haciéndolo seiscientos años y no tiene modales."

Que es, más o menos, exactamente lo que son las reglas de Pacioli: sin modales, sin memoria de tus excusas, y sin interés en si vas con prisa. Solo los dos lados de la página, y el rechazo a permitir que disagree.
