# 9. El primer acceso

El navegador se abrió solo, que es el tipo de pequeño detalle que hace que un sistema parezca terminado. La dirección era `http://localhost:8069`—`localhost` siendo la forma de la máquina de decir *esta computadora*, y 8069 siendo la puerta tras la cual escucha el ERP.

La página que apareció estaba casi vacía: una tarjeta blanca, un logo formado por dos formas púrpuras, y dos campos.

![La página de acceso del ERP, en la máquina que lo está ejecutando](../../assets/screens/odoo-01-login.png)

Maggie escribió la dirección de administrador que había impreso el instalador, y la contraseña, y pulsó Intro.

No pasó nada dramático. Esa es la primera cosa digna de decir sobre el ERP: no te saluda. No te felicita. Abre una página con un menú en la parte superior y algunas tarjetas de colores, y espera a que se le diga qué es.

![La primera pantalla tras el acceso: la empresa aún no tiene datos](../../assets/screens/odoo-02-dashboard.png)

Este es el momento en que una pequeña empresa suele perder el valor. El sistema parece vacío, las tarjetas son insignificantes, y existe la tentación de concluir que algo ha salido mal—o, peor aún, de empezar a hacer clic, que es como una empresa termina con cuatro almacenes, tres monedas y un cliente llamado "prueba".

La página vacía no es una falta. Es la verdad. El sistema aún no sabe nada sobre Riverton: ni su nombre, ni su dinero, ni lo que vende. Lo que sabe es cómo *ser* una empresa. La próxima hora es la hora en que aprende qué empresa es.

---

## La primera cosa que hay que cambiar: el idioma de la máquina

Odoo habla muchos idiomas, y el instalador tomó el de la máquina, que en este PC era el italiano. Una empresa en un pueblo de mercado en Inglaterra quiere sus facturas en inglés, sus nombres de impuestos en inglés, y sus mensajes de error en inglés, así que el idioma es el primer ajuste que hay que cambiar, antes de que se haya nombrado nada.

El ajuste reside en las preferencias del usuario—el pequeño círculo en la esquina superior derecha, *Mi Perfil*, *Preferencias*—y es por usuario, no por empresa. Esa distinción es digna de entender desde temprano: Odoo está lleno de ajustes que pertenecen *a ti* (idioma, zona horaria, qué notificaciones quieres) y ajustes que pertenecen *a la empresa* (moneda, impuestos, el plan de cuentas). Cambiar tu idioma no cambia nada para nadie más; cambiar la moneda lo cambia todo para todos.

## La segunda cosa: la empresa misma

Bajo *Ajustes*, la primera entrada es la empresa. Es un formulario con un nombre, una dirección, un número de impuestos, una moneda, un país y un logo, y es el formulario más importante de todo el sistema, porque cada documento que sale del edificio se sella con lo que dice.

![El formulario de la empresa: nombre, dirección, moneda, país](../../assets/screens/odoo-03-company.png)

Tres campos de ese formulario merecen un párrafo cada uno.

**El nombre** es lo que aparece en las facturas. No es necesariamente el nombre que la empresa usa en la conversación; es el nombre que el departamento de cuentas del cliente verá y el nombre contra el que la oficina de impuestos hará coincidir un registro. Si difieren, usa el registrado.

**El país** decide una cantidad sorprendente: cuál plan de cuentas ofrece el sistema, qué impuestos existen, el formato de las direcciones, la forma en que se imprimen las fechas. Es posible elegirlo tarde, y es doloroso; elegirlo primero es gratis.

**La moneda** es la en que la empresa lleva sus libros. No la moneda de cada transacción—Odoo maneja moneda extranjera, con tasas de cambio y ganancias y pérdidas— sino la moneda del libro mayor. Para Riverton, esa es la libra.

Existe una advertencia unida al cambiar la moneda después de que existan documentos, y no es una formalidad: el libro mayor está denomin en ella, y cambiarla retroactivamente es como cambiar la unidad de medida de un almacén después de que las estanterías estén llenas. Hazlo ahora, en un sistema vacío, y será un menú desplegable.

## La tercera cosa: las personas

Odoo viene con un usuario—el administrador—y la tentación es seguir usándolo para todo, porque es el único que existe.

Resístale, y resístale por una razón que no tiene nada que ver con el teatro de seguridad. Cada registro en el ERP recuerda quién lo creó y quién lo cambió. Si todos trabajan como administrador, esa memoria se vuelve inútil: el sistema dirá que *admin* creó la factura, *admin* aprobó el descuento y *admin* eliminó al cliente, y la pregunta "¿quién hizo esto?" no tendrá respuesta. La pista de auditoría solo vale algo si las personas son separadas.

Para Riverton, cuatro usuarios fueron suficientes para empezar:

| Usuario | Rol | Por qué |
|---|---|---|
| Administrador | derechos completos | configuración, y nada más |
| Doreen | contabilidad, facturación | su trabajo, y su firma en el libro mayor |
| Priya | ventas | cotizaciones, pedidos, clientes |
| Tom | inventario | recibos, entregas, ajustes de existencias |

Cada uno tiene un acceso, una contraseña y un rol. Cada uno aparece en la pista de auditoría por nombre. Y cada uno puede recibir más o menos derechos sin tocar los de nadie más.

Existe un quinto usuario, como nadie en el que inicia sesión: el asistente. Lo creó el instalador, tiene su propia clave, y tiene exactamente los derechos que necesita para hacer el trabajo descrito en este libro. Lo conoceremos de verdad en el capítulo doce.

## La cuarta cosa: lo que la empresa hace

La última pregunta de la primera hora es la que decide qué partes del ERP se encienden. Odoo es modular: puede ser un programa de facturación, o un almacén, o una fábrica, o una tienda, y la diferencia está en qué aplicaciones están instaladas.

Para un mayorista, la respuesta es corta: *Ventas*, *Compras*, *Inventario*, *Facturación* y *Contabilidad*. No *Fabricación* (Riverton no fabrica nada), no *Punto de Venta* (no hay tienda), no *Sitio Web* (la tienda en línea es una cosa aparte y puede conectarse más tarde). Cada aplicación que se instala añade menús, y cada menú es una invitación a la confusión si nadie lo necesita.

Maggie instaló cinco aplicaciones en la primera hora y resistió las otras veinte. Esa contención vale más que cualquier configuración: un sistema con cinco aplicaciones que todos usan vale más que un sistema con veinte que nadie confía.

## El panel, y por qué está vacío a propósito

Las tarjetas de colores en la primera pantalla son el intento de Odoo de responder a la pregunta *¿qué debería mirar?* antes de que sepas suficiente como para preguntar. Hay una tarjeta para ventas, una para facturas, una para existencias, y cada una muestra un número y un pequeño gráfico.

En una empresa nueva cada tarjeta muestra cero, y los gráficos son líneas planas. Eso no es un error y no es una primera mala impresión; es lo único honesto que el sistema podía mostrar. Un panel que inventara un número plausible para una empresa vacía sería un panel que nunca más podrías confiar.

Las tarjetas se vuelven útiles en distintos momentos, y saber cuáles ignorar es parte del primer mes.

**Ventas** es útil desde la primera cotización. Muestra el pipeline en dinero: cotizaciones enviadas, pedidos confirmados, facturas por emitir.

**Facturación** es útil desde la primera factura publicada, y es la tarjeta que Maggie miraba cada mañana: cuánto se debe, cuánto está atrasado.

**Inventario** es inútil hasta que existen productos y se ha contado el stock, que es por qué el capítulo once viene antes que el asistente.

**Contabilidad** es inútil hasta que el plan de cuentas está configurado y se publican las primeras entradas.

Una empresa que intenta hacer que las cuatro tarjetas sean significativas en la primera semana pasará una quincena en configuración y perderá el valor. Una empresa que ignora tres de ellas y hace que una funcione tendrá un sistema que será útil el viernes.

## La primera persona que no es la dueña

Priya inició sesión en el segundo afternoon, desde su propio escritorio, con la cuenta que Maggie había creado para ella, y lo primero que dijo fue: "¿Dónde está todo?"

La pantalla que vio no era la pantalla en la que Maggie había estado mirando. Los menús eran más cortos. No había *Ajustes*, no *Usuarios*, no *Contabilidad* más allá de las facturas que se permitía ver. Había *Ventas*, con cotizaciones y pedidos, y *Clientes*, y una caja de búsqueda.

Ese es el punto entero de un usuario, y vale la pena observar a alguien que lo conoce por primera vez. Durante treinta años Priya había trabajado en un sistema donde todos podían hacer todo, porque el sistema era una carpeta compartida y un conjunto de archivos. La idea de que un programa le mostraría *menos*, a propósito, tomó unos diez minutos para dejar de sentirse como un insulto y empezar a sentirse como un alivio.

"No puedo romper nada," dijo, al final de la tarde.

"Puedes romper una cotización," dijo Maggie. "No puedes romper el libro mayor."

Existe un punto más profundo en ese intercambio, y es la razón por la que los usuarios se configuraron antes de que se ingresara cualquier dato. En un sistema donde todos pueden hacer todo, nadie es responsable de nada: cuando un precio está mal, está mal porque alguien, en algún lugar, lo escribió. En un sistema donde cada persona tiene un rol, el precio está mal porque Priya lo escribió—que suena más severo y es de hecho más amable, porque significa que el precio puede corregirse, y la persona que lo corrigió puede ser agradecida.

El asistente, cuando llegó, recibió exactamente el mismo tratamiento. Es un usuario en esa lista, con un rol, y aparece en la pista de auditoría como todos los demás.

## La página que te dice qué hacer a continuación

La primera pantalla tras el acceso no es el panel. Es una página llamada *Primeros pasos*, y es la cosa más considerada de toda la aplicación.

Lista cinco cosas: elegir el país de tu empresa, configurar tu plan de cuentas, añadir tus productos, añadir tus clientes, e invitar a tus colegas. Cada una es un enlace, y cada una desaparece cuando se hace. Cuando las cinco están hechas, la página también desaparece.

Existe un principio de diseño en eso, y vale la pena nombrarlo porque la mayoría del software lo hace mal: **el sistema debe saber lo que aún no conoce.** Un panel que muestra ceros es un panel que no te dice nada. Una lista de verificación que dice *no tienes clientes* es una lista de verificación que te dice exactamente qué hacer a continuación, en el orden que tiene sentido.

El orden también importa. País primero, porque decide el plan de cuentas; plan de cuentas antes que los productos, porque los productos necesitan cuentas de ingresos; productos antes que los clientes, porque una cotización necesita ambos. Una empresa que empieza con clientes—which es el instinto natural, porque los clientes son lo que un negocio es—descubrirá en una hora que no puede cotizar nada.

Maggie hizo las cinco pasos en una tarde, en el orden dado, y la única que saltó fue *invitar a tus colegas*, porque quería un día para hacer sus propios errores antes de que nadie la observara.

Eso fue una buena decisión, y es la única pieza de consejo en este capítulo que no está en el software.

---

Para el final de la tarde la página se veía diferente. Había menús: *Ventas*, *Compras*, *Inventario*, *Contabilidad*. Había cuatro usuarios. Había una empresa con un nombre, una moneda y un país. Aún no había datos—no clientes, no productos, no facturas—pero el sistema ahora sabía para qué tipo de empresa estaba trabajando, que es la diferencia entre una página en blanco y un libro mayor vacío.

Doreen entró a las cuatro y media, como se concertó, y se sentó frente a ella.

Miró la pantalla por un rato sin decir nada. Luego dijo: "Está muy vacío."

"Lo está."

"Y esto va a saber más sobre esta empresa de lo que yo."

Maggie había estado esperando la pregunta en una forma u otra, y había decidido responderla honestamente.

"Va a *recordar* más que tú," dijo. "No va a saber más. No sabe que el oficial de finanzas de Ashfield se llama Carol, o que la puerta de la escuela se cierra antes de las ocho, o que el gerente allá prefiere una llamada de teléfono a un correo electrónico. No sabe que los cuadernos azules son los que se venden, o que el proveedor de papel es poco confiable en agosto. Sabe lo que le decimos, y nunca olvida lo que se le ha dicho."

Doreen consideró esto.

"Así que soy yo quien se lo dice," dijo.

"Soy tú quien decide qué es verdadero. Ese es un trabajo diferente al que tenías el lunes."

Lo era, y le tomó algunas semanas dejar de sentir que el sistema la estaba observando. Pero fue la primera en admitir, para la primavera, que el libro mayor se había convertido en un lugar donde podía *preguntar*—y que preguntar es una mejor manera de pasar una mañana que buscar.

A la mañana siguiente empezaron con el dinero, porque el dinero es donde comienzan los argumentos de toda empresa.
