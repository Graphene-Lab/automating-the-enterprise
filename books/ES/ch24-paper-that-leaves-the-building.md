# 24. El papel que sale del edificio

Hay una estantería en la oficina de Riverton que contiene cuatro archivadores, y son el último papel que la empresa conserva.

No son facturas. Las facturas están en el sistema y en los buzones de los clientes. Los archivadores contienen las cosas que tienen que firmarse: las notas de entrega que volvieron con las iniciales de un cuidador, las notas de crédito que un cliente consultó, y los dos contratos que importan. Todo lo demás es un PDF.

Este capítulo trata sobre el momento en que un documento sale del edificio, que es el momento en que el software se encuentra con el mundo físico—y en que un número sorprendente de sistemas de lo bien fallan.

---

## Qué hace imprimible un documento

Un documento imprimible no es una pantalla que ha sido reducida. Es un objeto distinto, con reglas distintas, y el motor de informes de Odoo vale la pena entenderlo porque las hace cumplir.

**Tiene un diseño fijo.** Una pantalla se reorganiza; una página no. La plantilla de la factura decide adónde va el logo, cuán ancha es la columna de descripción, y qué ocurre cuando el nombre de un producto es más largo que la columna. (La respuesta, en una buena plantilla, es que se ajusta—y la fila crece. En una mala, se superpone al precio, y el cliente ve un número que pertenece a otra línea.)

**Tiene un encabezado y un pie que se repiten.** La página uno de una factura de cinco páginas debe decir de quién es la factura, y la página cinco debe decir que es la página cinco de cinco. Esto no es vanidad: una página que llega sola, sin encabezado, es una página que puede ser disputada.

**Lleva la identidad de la empresa.** Nombre, dirección, número fiscal, registro, datos bancarios. No son decoración; son los campos que hacen del documento una reclamación legal, y provienen del registro de la empresa configurado en el capítulo nueve.

**Es reproducible.** La misma factura, impresa un año después, debe parecer idéntica. Por eso la plantilla es una plantilla y no un documento que alguien editó: una factura que puede editarse después de los hechos es una factura que no prueba nada.

## Los tres documentos que un mayorista realmente imprime

Riverton imprime tres cosas, y cada una tiene un trabajo distinto.

**La factura**, como PDF adjunto a un correo. Es la solicitud de pago y el documento fiscal, y es la que el departamento de cuentas del cliente archivará.

**La nota de entrega**, impresa en la impresora de la furgoneta y firmada en la puerta. No es un documento financiero; es la evidencia de que las mercancías llegaron, y es la cosa que resuelve el debate tres semanas después sobre si se firmó por el palé.

**El extracto**, enviado mensualmente a los clientes con varias facturas abiertas. Es una lista, no una exigencia, y es la herramienta de cobro más eficaz que existe—porque pone cada partida abierta delante de la persona que paga, en una sola página, sin acusación.

Hay una cuarta, menos obvia: el **informe de existencias**. No se envía a nadie. Se imprime porque Tom lo lee en la furgoneta, y leer una cosa en papel es distinto de leerla en una pantalla—más lento, y por tanto más propenso a ser reflexionado.

## El flujo de trabajo que reemplazó al sobre

El viejo flujo de Doreen era: imprimir, doblar, direccionar, sellar, enviar, archivar la copia. Cinco pasos, y el último era el que fallaba, porque archivar es el paso que no tiene fecha límite.

El nuevo flujo es: generar, comprobar, enviar, y dejar que el sistema lo archive. Tres pasos, y el archivado es automático—lo que significa que ocurre, lo que significa que cuando un cliente telefonea en noviembre por una factura de junio, la respuesta es una búsqueda y no una expedición a la sala de facturas.

La comprobación es el paso que importa, y es el que las empresas saltan. Un documento generado por una máquina no es automáticamente correcto: es correcto si lo es los datos que lo sustentan, y los datos que lo sustentaban los introdujo alguien. El hábito de Doreen, que conservó de la era del papel, es leer la primera factura de cada tanda—no todas, la primera—y fijarse en el nombre del cliente, la dirección, el total y el impuesto. Si esos cuatro están bien, el resto casi con certeza lo están.

## Qué hace el asistente, y qué no hace

El asistente puede producir el PDF y adjuntarlo a un correo. En Riverton no lo hace, y la decisión vale la pena registrarla porque es una elección, no una limitación.

El papel del asistente es *preparar*: crear la factura, registrarla, producir el documento, y decirle a Doreen que está lista. El envío lo hace una persona, en el cliente de correo, porque el envío es el paso en que un error llega a un cliente—y un error que llega a un cliente cuesta más que el minuto que toma prevenirlo.

Eso es una elección conservadora, y una empresa con cien facturas al día no puede hacerla. Riverton tiene quince, y quince minutos de atención humana son asequibles. El principio que escala, sin embargo, es el mismo a cualquier volumen: **el paso que sale del edificio es el paso en que debe haber una persona, hasta que hayas visto a la máquina hacerlo correctamente cien veces.**

## Una breve historia de la factura impresa

La factura impresa es hija del siglo XIX, y su forma fue fijada por los ferrocarriles y el telégrafo.

Antes de que imprimir fuera barato, una factura era una nota manuscrita. Cuando las empresas crecieron, y cuando el mismo cliente empezó a comprar de varios departamentos del mismo proveedor, la nota se convirtió en un formulario: impreso con el nombre de la empresa, con líneas numeradas, con columnas para cantidad, descripción, precio y importe. Las columnas no son arbitrarias—reflejan la secuencia en que un dependiente comprueba el documento, de izquierda a derecha, terminando con el total.

El formulario ha sobrevivido a toda tecnología desde entonces, incluida esta, porque codifica la información mínima necesaria para resolver un litigio: quién, qué, cuántos, a qué precio, cuánt tax, en total, para cuándo. El software no cambió el formulario. Cambió el costo de producirlo, y—más importante—el costo de *buscarlo* después.

Ese último cambio es el que nadie nota. En 1975, una copia de una factura vivía en un archivador, en una carpeta, bajo el nombre de un cliente, y buscarla tomaba a una persona que conocía el sistema. En 2026, vive en una base de datos y puede ser encontrada por cualquiera quepa escribir el nombre de un cliente—lo que significa que puede ser encontrada por la persona que está realmente al teléfono, en lugar de la que por casualidad sabe dónde está la carpeta.

## El archivo

Todo documento que sale del edificio debe ser localizable después, y aquí es donde el hábito de una pequeña empresa y la capacidad de un sistema suelen divergir.

Odoo conserva todo documento registrado y puede regenerar su PDF en cualquier momento, lo que significa que el *archivo* no necesita archivarse por separado: el documento es los datos, y el PDF es una vista de ellos. Eso es elegante, y también es ligeramente alarmante la primera vez que lo oyes—¿qué pasa si la plantilla cambia y la factura se imprime distinto dentro de un año?

La respuesta es que lo hará, y que eso es aceptable, porque lo que importa es el *contenido* y el contenido está almacenado. Si tu jurisdicción exige el PDF exacto tal como se emitió, Odoo puede adjuntar el PDF generado al registro cuando se registra, y el archivo queda fijo. Riverton hace eso con las facturas que se envían al extranjero, donde la autoridad fiscal es más exigente, y no con las nacionales.

## La impresora, y todo lo que puede salir mal con ella

Un capítulo sobre impresión que no mencionara la impresora sería un capítulo escrito por alguien que nunca ha trabajado en una oficina.

La impresora es el componente menos fiable de toda la pila, y es la que falla en el momento de máxima urgencia—que es la naturaleza de las impresoras. Tres cosas vale la pena conocer.

**Imprimir a PDF no es imprimir.** Todo documento descrito en este capítulo puede producirse como un PDF sin que intervenga una impresora, y para facturas y extractos es lo que una empresa debe hacer: generar el PDF, adjuntarlo a un correo, y guardar el papel para las cosas que necesitan firma. La impresora de Riverton se usa para notas de entrega y el informe de existencias del viernes, y para nada más.

**Un documento que ha sido impreso no es un documento que ha sido enviado.** Esto suena obvio y es la fuente de la factura de Ashfield al principio de este libro. El sistema sabe que el PDF se generó; no sabe si el correo se envió. Si el envío importa, el envío tiene que registrarse—que es una razón por que las empresas eventualmente automatizan todo el paso, para que el registro exista.

**El atasco de papel es un riesgo empresarial.** Una nota de entrega que no se puede imprimir es una entrega que no puede salir, porque el conductor no irá sin el papel que firma el cliente. Toda empresa que depende de una impresora en la zona de carga debe tener una segunda, o una forma de imprimir la nota en la dirección del cliente. Riverton aprendió esto un sábado, y ahora guarda una de reserva en un armario.

## Las tres cosas que salen mal en una tirada de impresión

Toda empresa que imprime documentos se ha topado con estas tres, y cada una tiene una solución barata.

**La plantilla cambia y nadie lo nota.** Un logo actualizado, una dirección cambiada, un dato bancario corregido—y la plantilla sigue mostrando la antigua porque el cambio se hizo en el registro de la empresa y la plantilla lee una copia. Las plantillas de Odoo leen el registro de la empresa directamente, así que esto es más raro que en sistemas que copian; pero una plantilla a medida todavía puede codificar un valor fijo, y la forma de saberlo es imprimir un documento tras cualquier cambio y leerlo.

**El papel es del tamaño equivocado.** Una nota de entrega diseñada para A4 impresa en la impresora A5 de la furgoneta pierde su columna derecha—que es donde están las cantidades. La solución es una segunda plantilla para el formato pequeño, o una impresora que acepte A4, y vale la pena decidirlo antes de la primera entrega que después.

**La copia del cliente y la copia de archivo divergen.** Alguien escribe sobre la copia impresa—una nota, una corrección, una firma—y el archivo conserva la versión intacta. Eso es correcto para la factura y incorrecto para la nota de entrega: la nota firmada *es* el registro, y debe escanearse o archivarse, no tirarse porque "está en el sistema".

## Qué significa una firma

La nota de entrega vuelve con un garabato en ella, y el garabato es la cosa jurídicamente más interesante de toda la pila.

Una firma en una nota de entrega es un reconocimiento: *he recibido estas mercancías, en esta cantidad*. No es un contrato—el contrato fue el pedido—y no es un recibo de pago. Es evidencia, y su valor es que se hizo en el momento de la entrega por alguien que estaba allí.

Por eso sigue imprimiéndose la nota de entrega, y por qué no se permite que el asistente marque una entrega como firmada. La firma es un acto físico de una tercera parte, y ninguna cantidad de software puede realizarlo. Lo que el software puede hacer es asegurarse de que la nota que se firma es la correcta: el cliente correcto, el pedido correcto, las cantidades correctas, y una página que el conductor pueda realmente leer en una furgoneta.

El día que se firma la nota y vuelve, alguien valida la entrega en el sistema—y el papel entra en una carpeta durante seis años, porque así de largo puede necesitar una empresa probar que las mercancías llegaron.

## El archivo de los documentos enviados

Hay una pregunta que una empresa se hace la primera vez que un cliente disputa una factura de hace dos años: *¿podemos probar lo que enviamos?*

La respuesta depende de una decisión tomada mucho antes, y vale la pena tomarla deliberadamente: ¿conserva el sistema el *documento* o los *datos*?

Conservar los datos—el registro de la factura y sus líneas—significa que el PDF puede regenerarse en cualquier momento, y parecerá la plantilla de hoy en lugar de la que se usó en aquel momento. Para la mayoría de los fines eso es suficiente, y es lo que Odoo hace por defecto.

Conservar el documento significa adjuntar el PDF generado al registro cuando se registra, para que el archivo quede fijo. Eso cuesta unas pocas cientos de kilobytes por factura y resuelve todo debate sobre lo que se envió, en la forma en que se envió.

Riverton adjunta el PDF de las facturas a los clientes extranjeros, donde la autoridad fiscal es más exigente, y para los dos contratos que importan. Para las facturas nacionales se apoya en los datos, que es una decisión que Doreen tomó después de preguntar a su contable, y que revisa cada año.

---

Los archivadores de la estantería son la excepción que confirma la regla: las cosas que deben firmarse siguen siendo papel, porque una firma sigue siendo un acto físico en la mayor parte del mundo. Todo lo demás se ha convertido en un archivo, y la estantería no ha crecido en un año.

Doreen lo notó antes que nadie.

"La estantería solía llenarse a junio," dijo. "Tendría que empezar una nueva. Este año he usado unas cuatro pulgadas."

La miró por un momento.

"Es extraño. Gasté treinta años haciendo papel, y no lo echo de menos. Lo que echo de menos es saber dónde están las cosas—y eso lo he recuperado, de otra manera."

Ese es el trueque de todo el libro ha estado describiendo, dicho por la persona que lo hizo: no la desaparición del papel, sino el retorno de saber dónde están las cosas, sin necesidad de ser la persona que las archivó.
