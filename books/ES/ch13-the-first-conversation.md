# 13. La primera conversación

La primera vez que se inició el asistente, pidió una clave.

No la clave del ERP—esa se había creado durante la instalación y se había escrito en la
configuración del conector. Era la otra: la clave que permite al asistente hablar con un modelo de
lenguaje, es decir, la clave que le permite pensar.

La ventana era propia del asistente, abierta mediante el icono de Odoo IA, y tenía el aspecto de un
terminal de 1995: una barra de menú en la parte superior, una amplia zona vacía y una línea en la
parte inferior con un cursor. Antes del primer inicio, hubo además una breve serie de preguntas.

*Elija un proveedor.*

La lista era la habitual: los grandes servicios en la nube, un par de agregadores, y la opción de un
modelo que se ejecuta en la propia máquina. Maggie eligió DeepSeek, porque era el que Sam había
recomendado por su coste, y porque la empresa ya tenía una cuenta para él.

*Pegue la clave.*

La pegó. La ventana se detuvo un segundo y luego imprimió una lista de nombres de modelos—que es el
momento digno de ser señalado, porque es el momento en que el asistente *demuestra* que la clave
funciona. No se había limitado a aceptar lo que ella había escrito; la había usado para preguntar al
proveedor qué podía hacer, y el proveedor había respondido. Una clave que está mal produce un error
en ese momento, no tres días después en medio de una factura.

Ella escogió el modelo, y la ventana se limpió.

---

## La primera pregunta

Ella escribió: *¿Qué puedes hacer?*

La respuesta era una lista, y era más larga de lo que ella esperaba. Podía buscar clientes,
productos, pedidos, facturas y existencias; podía leer y crear registros; podía invocar las acciones
que mueven un documento desde borrador hasta confirmado; podía agrupar, sumar y contar. No podía
cambiar la configuración de la empresa, gestionar usuarios, ni eliminar nada.

La leyó dos veces. Luego escribió la pregunta que venía arrastrando desde noviembre.

*¿Cuántos clientes tenemos?*

La respuesta llegó en unos segundo: *Cero. La base de datos aún no tiene registros de clientes.*

![El asistente en su terminal: la misma pregunta, respondida desde el ERP, con el criterio y los
registros detrás del número](../../assets/screens/assistant-04-tui-answer.png)

Un modelo que adivinara habría dicho algo como "tiene aproximadamente 40 clientes" o habría
producido una tabla de nombres plausibles, porque eso es lo que hace un modelo de lenguaje cuando no
tiene datos: produce el texto más probable. Este había sido construido para *mirar*, y mirar una
tabla vacía produce la única respuesta honesta que existe.

La figura de arriba es de la misma instalación, unos días después, cuando ya existían los cuatro
clientes de demostración. Dos cosas en ella vale la pena leerlas dos veces: la respuesta nombra el
criterio (*res.partner con customer_rank > 0*) y dice que fue confirmada por un segundo conteo
independiente; y ofrece tres observaciones que nadie pidió—que los cuatro clientes están guardados
como personas físicas en lugar de empresas, que ninguna de ellas tiene dirección de correo
electrónico, y qué registros se excluyeron del conteo y por qué. Eso no es un informe. Es lo que
dice un colega cuidadoso cuando te entrega un número.

---

## Lo que ocurre entre la pregunta y la respuesta

Vale la pena ralentizar el segundo, porque la velocidad oculta algo que vale la pena entender.

Cuando Maggie escribió *¿cuántos clientes tenemos?*, ocurrieron cuatro cosas.

**El asistente leyó la instrucción** y decidió qué tipo de cosa era: una pregunta sobre el número
de registros de un tipo, no una acción. Esa decisión la toma el modelo de lenguaje, y es la parte
que es genuinamente nueva: nadie escribió una regla que diga "si la frase comienza con cuántos,
cuenta algo".

**Elegió una herramienta.** El conector ofrece una docena de operaciones, cada una con un nombre y
una descripción. El asistente escogió *buscar*, sobre el modelo *clientes*, con un filtro vacío y un
conteo.

**La herramienta se ejecutó, en Odoo, como el usuario Agent.** Odoo verificó la clave, verificó los
permisos, ejecutó la consulta contra la base de datos, y devolvió un número.

**El asistente escribió la frase.** Podría haber escrito un párrafo sobre gestión de clientes; en
lugar de eso escribió una sola línea, porque la instrucción pedía un número y el número era cero.

Toda la secuencia tomó aproximadamente un segundo, de los cuales la mayor parte fue el modelo de
lenguaje pensando. La consulta a la base de datos tomó microsegundos.

## El bucle, y por qué no es un chatbot

Un chatbot toma una pregunta y produce texto. Esta cosa toma una instrucción y produce *trabajo*,
y la diferencia es un bucle.

El bucle es: pensar, elegir una herramienta, ejecutarla, leer el resultado, pensar de nuevo, y
bien detenerse o elegir otra herramienta. Una pregunta sencilla es una vuelta del bucle. Una
instrucción complicada—*crear una cotización, confirmarla, entregarla y facturarla*—es ocho o nueve
vueltas, decidida cada una por el modelo en función de lo que devolvió la anterior.

Ese bucle es lo que permite al asistente hacer cosas que nadie programó para que hiciera, y también
es lo que le permite equivocarse de formas que un programa no puede. Un programa hace lo que fue
escrito para hacer, cada vez. Un bucle decide qué hacer a continuación, cada vez, y una decisión
puede estar mal.

La defensa es la que este libro ha descrito desde el principio: las herramientas son estrechas, los
permisos son los del ERP, y el resultado es visible. El asistente no puede hacer nada que un usuario
no pudiera hacer, y todo lo que hace queda anotado.

---

## La primera acción

Lo primero que el asistente *hizo*—en lugar de responder—fue crear un cliente, y Maggie lo hizo
ella misma, en el terminal, con la apertura manual.

*Cree un cliente llamado Ashfield Academy, en Mill Lane, Ashfield, con términos de pago de treinta
días, y haga de Carol Whitfield el contacto de facturación.*

El asistente pensó un momento—dos segundos, que es más que una consulta—y luego:

*Cliente "Ashfield Academy" creado (ID 7), dirección Mill Lane, Ashfield, términos de pago 30 días.
Contacto Carol Whitfield añadido como contacto de facturación. ¿Quiere que compruebe si hay
duplicados antes de añadir el resto?*

La última frase no está en ningún manual. Es el modelo decidiendo, por su cuenta, que lo siguiente
que haría una persona cuidadosa era comprobar si hay duplicados—porque la instrucción decía
*crear*, y crear sin comprobar es como las empresas terminan con cuatro versiones de la misma
escuela.

Maggie escribió *sí*, y el asistente buscó cualquier cosa similar. No había nada, porque la base
de datos estaba vacía. Pero el hábito se había establecido desde el primer día: la máquina propone
una comprobación, la persona la acepta, y tras una semana la persona empieza a proponerlo también.

## El primer error

Tres días después, el asistente cometió su primer error, y vale la pena registrarlo porque no fue
del tipo que nadie esperaba.

Maggie preguntó: *¿Qué productos nunca hemos vendido?*

El asistente respondió con una lista de cuatro productos, y Maggie, que conocía el catálogo, notó
que uno de ellos—el papel A4—había vendido cuatrocientos resmas la semana anterior.

La causa fue una definición. El asistente había interpretado *nunca vendido* como "sin línea de
pedido de venta confirmado", y el papel se había vendido a través de una entrega que se creó
directamente, sin pedido, porque Tom había atendido una solicitud urgente de un cliente que llamó
por teléfono.

Ambos hechos eran verdaderos. La pregunta era ambigua, y el asistente había elegido una de las
lecturas.

El veredicto de Doreen, cuando se enteró, fue la frase que dio forma a todo el enfoque de la
empresa respecto a la tecnología.

*"Respondió a la pregunta que hice. Yo hice la pregunta equivocada."*

Eso no es una defensa de la máquina; es una descripción del trabajo. La habilidad de usar un
asistente es, en gran medida, la habilidad de preguntar con precisión—y la habilidad de comprobar,
cuando la respuesta importa, haciendo una segunda pregunta que tendría que coincidir.

*¿Qué productos no tienen línea de pedido de venta ni entrega directa en el último año?*

Esa versión produjo la lista correcta, y tardó cuatro segundos.

---

## La primera pregunta de Doreen

Dore había observado la primera semana desde la distancia, de la forma en que alguien con treinta y
un años de experiencia observa a un nuevo colega: con cortesía, y con una lista de cosas que
probablemente saldrían mal.

El sábado se sentó y escribió una sola cosa.

*¿Facturas del último mes que no han sido pagadas?*

La respuesta fue una lista de cuatro, con importes y días de retraso, y un total. La miró un rato,
luego abrió el viejo programa de contabilidad, ejecutó el mismo informe a mano, y comparó.

Coincidían.

"Vale," dijo. "Es el mismo informe. A mí me llevó veinte minutos y a esa cosa le llevó un segundo,
y es el mismo informe."

Luego hizo la pregunta que de verdad importaba.

*¿Por qué está atrasado Marchmont Hotel?*

El asistente no lo sabía, y lo dijo: no tenía registro de ninguna llamada telefónica, ni nota de
ninguna consulta, ni razón. Lo que tenía era la factura, la fecha de vencimiento, y el hecho de que
Marchmont había pagado cada factura anterior dentro de los diez días.

*Han pagado a tiempo todos los meses durante dos años,* añadió. *Esta es la primera factura atrasada.*

Esa frase no está en la base de datos. Es una conclusión extraída de la base de datos—un patrón,
notado y expresado—y es lo que hizo que Dore dejara de ser sospechosa. Llamó a Marchmont, y descubrió
que la factura se había enviado a una dirección de contabilidad que se había cerrado cuando el hotel
cambió de dueño en octubre, y que nadie había informado a Riverton.

*"La máquina no sabía por qué,"* dijo después. "Pero sabía que era extraño. Esa es la parte que no
esperaba. Sabía que era extraño."

## La regla de la primera semana

A finales de la primera semana, la oficina tenía una regla, y estaba escrita en la pizarra en letras
lo suficientemente grandes como para leerse desde la puerta.

*Pídale algo que ya sabe que la respuesta.*

La regla parece una pérdida de tiempo, y es todo lo contrario. Una pregunta cuya respuesta se sabe es
una prueba de la máquina: si coincide, has aprendido que la conexión, la clave, las definiciones y el
modelo están funcionando todos, y cada respuesta posterior puede confiarse un poco más. Si no
coincide, has encontrado un problema mientras las apuestas valen cero.

Dore la usó durante una quincena. Pidió el conteo de clientes, el total de las facturas de una
semana, el saldo de la cuenta bancaria—todas cosas que podía comprobar en el viejo sistema en diez
minutos. Dos veces las respuestas difirieron, y ambas veces la diferencia fue una definición: una
vez un cliente se contaba como dos porque tenía dos contactos, una vez una factura se excluyó porque
era una nota de crédito.

Esas dos correcciones valieron más que cualquier sesión de formación, porque enseñaron a la oficina
cómo *piensa* la máquina—y enseñaron a la máquina, en pequeña escala, lo que la oficina significa. Las
definiciones se fijaron en las instrucciones y en los datos, y no han estado mal desde entonces.

## Qué esperar de la primera semana

Tres cosas sorprenden a la gente en la primera semana, y las tres vale la pena conocerlas con
anticipación.

**Es más lenta de lo que uno quiere, y más rápida de lo que uno espera.** Una pregunta tarda de dos
a ocho segundos, dependiendo del modelo y del número de pasos. Eso parece lento junto a una caja de
búsqueda e instantáneo junto a abrir cuatro pantallas. La tentación es preguntar varias a la vez, lo
que hace todo más lento y produce respuestas entrelazadas—la forma más común de hacer que un buen
sistema parezca malo.

**Es literal de una forma que parece pedantería.** *Muéstrame los pedidos* producirá una pregunta
sobre qué pedidos. Eso no es un fallo; es la misma conducta que tiene un nuevo empleado cuidadoso, y
es la conducta que hace que el sistema sea seguro. La cura es una instrucción mejor, no un sistema
más indulgente.

**Es mejor en barridos que en conversaciones.** Pídale cada factura con más de treinta días y le
dará una lista completa y precisa. Pídale qué debe hacer al respecto y le dará un párrafo cuidadoso
y genérico, porque la respuesta depende de cosas que no conoce. La primera vale la pena pagarla; la
segunda no.

## Las cuatro preguntas que el asistente se hace

Cuando llega una instrucción, el asistente recorre cuatro preguntas, y entenderlas es la forma más
rápida de escribir instrucciones mejores.

**¿Qué tipo de cosa se está pidiendo?** Una pregunta, una acción, o una conversación. Esto lo decide
el modelo, a partir de la forma de la frase, y es por eso que *¿cuántos clientes tenemos?* y *crear
un cliente* producen conductas tan distintas.

**¿Qué herramientas podrían hacerlo?** El conector describe cada operación en una frase, y el
asistente escoge las que coinciden. Una solicitud que no coincide con ninguna herramienta producirá
una negativa cortés, que es mejor que una adivinación.

**¿Cuáles son los argumentos?** El nombre del cliente, el producto, la fecha. Aquí es donde muerde la
ambigüedad: *los binders azules* no coinciden con un producto, y el asistente preguntará en lugar de
inventar.

**¿Es el resultado lo que se pidió?** Tras devolver la herramienta, el asistente lee el resultado y
decide si la instrucción se ha cumplido o si se necesita otro paso. Ese bucle es lo que hace posible
una cadena de operaciones, y también es lo que hace posible un error—el bucle puede conformarse con
algo que no es lo que uno quiso decir.

## Cómo se sintió la primera semana

La nota de Maggie, escrita el sábado de la primera semana, es el mejor resumen de este capítulo que
existe, y tiene cuatro líneas.

*Día 1: me dijo que no teníamos clientes. Correcto, y un poco grosero.*
*Día 2: creó un cliente y preguntó si quería comprobar si había duplicados. Lo hice.*
*Día 3: respondió a una pregunta que hice mal, y Dore tenía razón sobre por qué.*
*Día 4: dejé de estar impresionada y empecé a molestarme cuando era lenta, lo que creo que significa
que está funcionando.*

Esa última línea es la que hay que conservar. La medida de una herramienta que se ha convertido en
parte de un negocio no es la admiración; es la impaciencia. Nadie está impresionado por el teléfono.
La gente se molesta cuando no funciona.

A finales de la primera semana, el asistente había dejado de ser una demostración y se había
convertido en un colega con un hábito irritante de ser literal—lo cual, como sabe cualquiera que haya
gestionada a un junior muy concienzudo, es un problema con el que se puede trabajar.
