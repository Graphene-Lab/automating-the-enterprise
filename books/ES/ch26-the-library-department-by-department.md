# 26. La biblioteca, departamento por departamento

Este capítulo es una lista, y está pensado para usarse más que para leerse.

Cada instrucción de abajo se ejecutó en la instalación descrita en este libro, contra una empresa
con clientes, productos, existencias, pedidos e facturas. El resultado se anota donde no es obvio,
y las que fallaron en el primer intento se marcan, con lo que hubo que cambiar—porque una
biblioteca de instrucciones que solo contiene las que funcionaron es una biblioteca de mentiras.

Adapta los nombres. Los productos de Riverton son carpetas con anillas y papel; los tuyos no. Lo que
vale la pena copiar es la *forma* de cada instrucción: un verbo, un objeto, un alcance y una
restricción.

---

## Clientes

**1.** *¿Cuántos clientes tenemos, y cuántos de ellos han hecho un pedido en los últimos noventa
días?* — Dos números, y el segundo es el que importa. Una lista de clientes que solo crece es una
lista de personas que han dejado de comprar.

**2.** *Busca el cliente llamado Ashfield Academy y muéname su dirección, número de teléfono y
condiciones de pago.* — La primera cosa que hace cualquiera por teléfono. Reemplazó tres pantallas y
una búsqueda.

**3.** *Crea un nuevo cliente llamado Northgate Library Service, en Mill Lane 14, Northgate, con las
mismas condiciones de pago que Ashfield Academy.* — *Las mismas que* es la parte útil: copia una
configuración real en lugar de una adivinada.

**4.** *¿Qué clientes no han pedido nada en los últimos seis meses, y cuál fue su último pedido?* —
La lista que salvó al centro de jardinería en el capítulo veinte.

**5.** *Añade un segundo contacto a Ashfield Academy: Carol Whitfield, oficina de finanzas, y hazla
el contacto para facturación.* — Una instrucción pequeña que antes requería saber dónde viven los
contactos en el menú.

**6.** *Muéname los diez clientes con el importe total facturado más alto de este año.* — Un
clasificatorio, con los números detrás.

## Ventas

**7.** *Crea una cotización para Ashfield Academy de 400 carpetas con anillas y 20 cajas de rotuladores
para pizarra, a los precios estándar.* — La primera pieza de trabajo de verdad, en el capítulo
catorce.

**8.** *Muéname la cotización que creé para Ashfield Academy hoy, con sus líneas y el total.* — El
comprobar. Pregunta siempre por el comprobar.

**9.** *Confirma la cotización de Ashfield Academy y dime el número de pedido de ventas.* — La
transición de la propuesta a la promesa.

**10.** *Crea una cotización para Northgate Library Service de 12 cajas de papel A4 y 6 paquetes de
bolígrafos, entrega el próximo lunes.* — *El próximo lunes* se interpreta y se devuelve como una
fecha, que es cómo te das cuenta de que la máquina y tú discrepan sobre qué lunes.

**11.** *¿Cuál es el valor total de todas las cotizaciones que siguen abiertas, y para quién son?* —
El pipeline, sin un módulo de CRM.

**12.** *¿Qué productos vendimos más el último mes, por cantidad?* — El informe útil más simple en
cualquier negocio mayorista.

**13.** *Cambia la fecha de entrega del pedido abierto de Ashfield Academy al final del mes.* — Un
cambio en un documento confirmado, que el ERP solo permite mientras no se ha entregado todavía.

**14.** *Cancela la cotización de Northgate Library Service y dime en qué estado está ahora.* — *En
qué estado está ahora* es la verificación, y es lo que hace que cancelar sea seguro.

## Facturación

**15.** *Crea una factura desde el pedido de ventas confirmado de Ashfield Academy.* — El enlace entre
el pedido y la factura, que es toda la razón por la que existe un ERP.

**16.** *Registra la factura de Ashfield Academy y dime su número y el total.* — El registrar, el
momento en que el libro mayor cambia.

**17.** *¿Qué facturas están sin pagar y tienen más de treinta días? Muéname el cliente, el número de
factura, la fecha y el importe pendiente.* — El informe de antigüedad, en una frase.

**18.** *Registra un pago del importe total contra la factura de Ashfield Academy, fechado hoy, por
transferencia bancaria.*

**19.** *Muéname el estado de pago de cada factura de Northgate Library Service.* — Un extracto para
el cliente, sin generar uno.

**20.** *Crea un abono para Ashfield Academy de 20 carpetas con anillas que se devolvieron dañadas, y
regístralo.* — La corrección que no reescribe la historia.

**21.** *¿Cuánto dinero se nos debe en total, y cuánto de eso está vencido?* — Los dos números que un
propietario de empresa mira primero.

**22.** *Envía un recordatorio de pago educado a cada cliente con una factura con más de quince días
de retraso en el pago.* — En Riverton esto produce borradores, no correos: el envío es decisión de
una persona. La instrucción funciona de ambos modos; la configuración decide cuál.

## Almacén

**23.** *¿Cuántas carpetas con anillas tenemos en existencias ahora mismo, y dónde están?* — La
pregunta que hizo que Tom creyera en el sistema.

**24.** *¿Qué productos están por debajo de su punto de reorden?* — La lista que se convierte en un
pedido de compra.

**25.** *Confirma la entrega del pedido de Ashfield Academy y dime qué movimientos de existencias ha
creado.* — Los movimientos son la evidencia de que la existencia salió.

**26.** *Registra un ajuste de existencias de menos 5 cajas de rotuladores para pizarra, motivo:
estropizados por la lluvia.* — El motivo no es opcional; es lo que hace que el ajuste sea
revisable.

**27.** *¿Cuál es el valor total de la existencia en el almacén al coste?* — Un número que la mayoría
de las empresas pequeñas no puede producir, y que cambia la forma en que compran.

**28.** *Muéname cada movimiento de existencias de las carpetas con anillas en los últimos treinta
días.* — La auditoría de un único producto, que es cómo se explica una discrepancia.

**29.** *¿Qué productos no se han movido en absoluto en el último año?* — Existencia muerta, que es
dinero dormido.

## Compras

**30.** *Crea un pedido de compra de 500 carpetas con anillas a nuestro proveedor habitual, al último
precio que pagamos.* — *El último precio que pagamos* es un dato de la historia, no una lista.

**31.** *Confirma el pedido de compra y dime cuándo se esperan las mercancías.* — Confirmar crea la
recibida esperada, que es lo que hace que la próxima entrega sea responsable.

**32.** *Recibe las mercancías del pedido de compra y muéname la existencia que ha añadido.*

**33.** *Crea la factura de proveedor de ese pedido de compra y regístrala.* — La tercera pata de la
triple verificación.

**34.** *¿Qué proveedores han subido sus precios en los últimos seis meses, y en cuánto?* — La
pregunta que encontró el cargo por paleta en el capítulo diecinueve.

**35.** *¿Cuánto se les debe a cada proveedor ahora mismo?* — El espejo del informe de antigüedad.

**36.** *¿Qué pedidos de compra van tarde, y con cuántos días de retraso?* — Los proveedores que van
tarde son un problema de compras, no de almacén, y la distinción importa.

## Contabilidad

**37.** *Muéname el balance de comprobación de este mes.* — El informe más antiguo en contabilidad,
producido en un segundo.

**38.** *¿Cuál es el saldo de la cuenta bancaria hoy, según los libros?* — *Según los libros* es el
calificador honesto: el banco y los libros coinciden tras la conciliación, no antes.

**39.** *Muéname cada asiento contable registrado en los últimos siete días, con el documento del que
vienen.* — El rastro desde un número de vuelta a un documento.

**40.** *¿Cuál es nuestros ingresos para este mes hasta ahora, y cómo se comparan con el último mes?*

**41.** *Lista los impuestos configurados para esta empresa y la tarifa de cada uno.* — El comprobar
que evita que se invente una cuarta tasa de IVA en el mostrador.

**42.** *¿Qué cuentas de gastos no tienen actividad este año?* — O un plan general de contabilidad
demasiado grande, o un gasto que se ha registrado en otro sitio. Ambos valen la pena conocerlos.

## Informes

**43.** *Dame un resumen de una página del negocio esta semana: ventas, facturas, dinero vencido,
alertas de existencias.* — La lista del lunes, bajo demanda.

**44.** *¿Quin productos tienen el mejor margen, y cuáles cinco tienen el peor?* — El informe que
cambia una lista de precios.

**45.** *Muéname las ventas por mes de este año, como tabla.*

**46.** *¿Qué comercial ha facturado más este trimestre?* — Solo significativo si las facturas llevan
un comercial, que es una decisión de configuración tomada en la semana uno.

**47.** *¿Qué porcentaje de nuestras facturas se pagan tarde, y cuál es el retraso promedio?* — La
medición que convirtió el "nos pagan eventualmente" de Riverton en doce días de facturación.

**48.** *Compara el número de pedidos de este mes con el mismo mes del último año.*

**49.** *¿Qué clientes se nos deben dinero y también han dejado de pedir? Ese es el lista de riesgo.* —
La instrucción que salvó al centro de jardinería. Nombrar la lista en la instrucción—*ese es el
lista de riesgo*—le dice al asistente para qué sirve la lista, y la respuesta vuelve anotada.

## Mantenimiento

**50.** *Busca cualquier cliente duplicado con el mismo nombre y muéname a los dos.* — Mostrar, no
fusionar. Una máquina no debe decidir cuál de dos registros es real.

**51.** *¿Qué productos no tienen precio establecido?* — El error que frena una cotización.

**52.** *Lista los productos cuyo nombre no coincide con su referencia interna.* — Un pequeño chequeo
de consistencia que atrapa años de descuido acumulado.

**53.** *¿Hay alguna cotización con más de noventa días que siga abierta? Archívala.*

**54.** *Comprueba la conexión con Odoo y dime qué versión está en ejecución.* — La primera instrucción
que cualquiera debería escribir, en cualquier instalación, en la vida.

## Trabajo fijo

**55.** *Cada lunes a las ocho, envíame una lista de facturas que se hicieron vencidas en la semana
anterior.*

**56.** *Cada viernes por la tarde, dime qué productos caíron por debajo de su punto de reorden durante
la semana, y propone los pedidos de compra en borrador.*

**57.** *El primer día laborable del mes, produce el resumen de ventas del último mes por cliente.*

**58.** *Cada mañana, comprueba la conexión con Odoo y dime si hay algo mal.* — Útil solo si la
respuesta es silenciosa cuando todo está bien; un "todo está bien" diario entrena a la gente a ignorar
los mensajes.

**59.** *Cada jueves, lista los pedidos de compra que van tarde y los proveedores que son
responsables.*

---

## Cómo usar esta lista en la primera semana

Un lector que intente trabajar este capítulo en orden fracasará, y vale la pena decir por qué.

Las instrucciones asumen una empresa con datos dentro: clientes, productos, existencias, pedidos. En
una instalación nueva la mayoría de ellas devuelven nada, lo que es correcto y desalentador. El orden
que funciona es el orden que siguió el libro: crea un cliente, crea un producto, pon existencias en
una estantería, haz una cotización, confírmala, entrega, factura, registra, paga. Después de eso, cada
instrucción de este capítulo tiene algo en lo que trabajar.

La segunda semana es cuando la lista se vuelve útil: elige un departamento, lee sus instrucciones, y
prueba las cuatro que describen el trabajo que haces cada semana. Descarta el resto. Una empresa no
necesita una biblioteca de cincuenta y nueve instrucciones; necesita las ocho que usa de verdad,
escritas, con sus propias palabras.

La tercera semana es cuando la empresa escribe la suya. Ese es el momento en que la tecnología deja de
ser algo que se instaló y se convierte en algo que se usa—y la prueba es simple: ¿contiene la lista una
instrucción que no esté en este capítulo? Si la contiene, la oficina ha empezado a pensar en el idioma
del sistema, que es el único resultado duradero de todo esto.

## Las que necesitaron un segundo intento

Cuatro instrucciones fallaron en el primer intento durante las pruebas tras este libro, y cada falla
vale la pena registrar porque es el mismo tipo de falla.

**"Muéname los productos que nunca vendimos."** — Ambigua, como describe el capítulo trece: ¿sin línea
de pedido de venta, o sin movimiento de ningún tipo? La versión corregida nombra el test: *productos
sin línea de pedido de venta y sin entrega directa en el último año.*

**"Envía la factura al cliente."** — En Riverton el asistente no tiene herramienta de correo, por
diseño. La instrucción se rechazó, correctamente, y la versión que funciona es *produce el PDF de la
factura y dime que está lista.*

**"Elimina el cliente duplicado."** — Rechazada: el usuario Agent no puede eliminar. La versión que
funciona es *archiva el cliente duplicado*, que también es la respuesta correcta.

**"¿Cuánto ganamos el último mes?"** — Ambigua entre ingresos, margen bruto y beneficio. La versión
corregida es *cuál fue nuestro beneficio neto el último mes, y de qué está hecho?* — y la respuesta
vuelve con los componentes, que es más útil que el número.

El patrón en los cuatro: el asistente era literal, la persona era vaga, y la corrección era decir lo
que se quería decir. Eso no es una limitación de la tecnología. Es el mismo requisito que la gestión
siempre ha tenido de la gente a la que delega, y es la razón por la que este capítulo está organizado
de la forma en que está—por departamento, en el idioma del trabajo, con los chequeos adjuntos.

---

Una última nota, sobre la biblioteca como *documento*.

Riverton guarda su propia versión de esta lista en un archivo compartido, y crece sobre una instrucción
al mes. Cada instrucción en él se probó, y las que no funcionaron se eliminaron en lugar de guardarlas
"por si acaso". El archivo tiene cuatro páginas, y es el documento más leído de la empresa después de
la lista de precios.

Eso es lo que debería ser una biblioteca de instrucciones: no un manual, no una lista de trucos, sino
el vocabulario acumulado de una empresa que ha aprendido a decir lo que significa.
