# 22. El trabajo que corre mientras duermes

El primer trabajo programado que configuró Riverton no era ingenioso. Era la lista del lunes.

Todos los lunes a las ocho, el asistente produce una página: facturas que vencieron en la semana
anterior, productos que descendieron por debajo de su punto de reorden, pedidos pendientes de entrega
en los próximos siete días, y cualquier ajuste de existencias sin motivo registrado. Se la envía a
Maggie, Priya y Tom por correo electrónico, y al asistente le toma unos cuarenta segundos.

Nadie la pidió. Fue idea de Sam, y la explicó con una frase que ha acompañado a Maggie desde entonces.

"La gracia de un horario no es que la máquina trabaje mientras duermes. Es que la *pregunta* se hace
pase lo que pase si alguien recuerda hacerla."

---

## Dos clases de trabajo programado

Hay dos mecanismos en esta pila, y valen la pena distinguirlos porque responden a preguntas distintas.

**Los propios programadores del ERP** se ejecutan dentro de Odoo. Son las cosas que un sistema de
empresa siempre ha hecho sobre un temporizador: recalcular los puntos de reorden, enviar los correos
de recordatorio, correr la depreciación, limpiar las sesiones viejas. Se configuran en el ERP, se
ejecutan pase lo que pase si el asistente está abierto, y son el lugar correcto para todo lo que forma
parte del *modelo*—cualquier cosa que tendría que ocurrir aunque a nadie de la empresa le importara.

**El programador de tareas del asistente** corre trabajos como conversaciones. Una tarea programada es,
literalmente, un prompt con una fecha adjunta: a las ocho del lunes, se le da una instrucción al
asistente, hace el trabajo, y informa. Ese es el lugar correcto para todo lo que requiere juicio sobre
*qué revisar*—un resumen, una inspección, una comparación, un empujoncito.

Riverton usa ambos, y la división entre ellos es la parte útil de este capítulo.

## Qué pertenece a un horario

La tentación, al descubrir el trabajo programado, es programarlo todo. Resístala, y usa una prueba
fácil de aplicar: **un trabajo pertenece a un horario si su ausencia solo se notaría cuando ya es tarde.**

La lista del lunes supera la prueba. Sin ella, una factura vencida se nota cuando alguien piensa en
revisarla—es decir, cuando tiene sesenta días de antigüedad.

Un respaldo nocterno supera la prueba, catastróficamente.

Un "informe de ventas" diario suele fallarla. Nadie lo lee; el número está en el panel; y un informe
que nadie lee es un pequeño impuesto diario sobre la atención que con el tiempo enseña a las personas a
ignorar los mensajes del sistema.

La prueba tiene una consecuencia: **un trabajo programado debe producir una decisión, no un documento.**
La lista del lunes produce cuatro decisiones (perseguir esta, reordenar aquella, entregar esto, explicar
aquello). Un informe produce un documento, y los documentos se acumulan.

## Los tres trabajos que mantuvo Riverton

Tras un mes de experimentación, la empresa se decidió por tres, y las ha mantenido desde entonces.

**La lista del lunes**, a las ocho. Cuatro preguntas, una página, tres destinatarios.

**La revisión de existencias del viernes**, a las cuatro. El asistente lista cada producto que descendió
por debajo de su punto de reorden durante la semana y propone pedidos de compra—en borrador, nunca
confirmados. Tom lo lee el viernes por la tarde y decide; los pedidos se colocan el lunes por la mañana,
que es cuando los proveedores contestan el teléfono.

**El resumen del día uno del mes**, a las siete. Ventas por cliente, ventas por producto, las cinco
principales y las cinco peores por margen, entradas y salidas de caja, y los tres clientes cuyo
comportamiento de pago ha cambiado. Son dos páginas, y es el documento que Maggie lee con su primer
café del mes.

Todo lo demás que se probó ese mes se eliminó, y las eliminaciones son tan instructivas como las que se
quedaron: un resumen diario (nadie lo leía), una revisión de conexión horaria (producía ruido, no
información), y un trabajo nocterno de "limpiar duplicados" que era una idea genuinamente mala—una
máquina decidiendo cuál de dos registros de cliente es el real, a las tres de la mañana, con nadie que
lo vigile.

## Qué pasa cuando un trabajo falla

La parte interesante del trabajo programado no es el horario. Es el fallo.

Un trabajo puede fallar por tres motivos, y cada uno tiene una firma distinta.

**La máquina estaba apagada.** El ERP no estaba corriendo a las ocho, así que el trabajo no se ejecutó.
Los propios programadores de Odoo resuelven esto corriendo los trabajos perdidos al arrancar el servidor;
las tareas programadas del asistente se almacenan como planes y se corren en el próximo arranque, con la
fecha para la que debían correr. De cualquier manera, el trabajo ocurre, tarde.

**El trabajo se ejecutó y la respuesta era incorrecta.** Este es el peligroso, porque nada parece roto.
La lista del lunes llega, y una de sus cuatro secciones está vacía porque se dejó un filtro activado. La
defensa es la misma que en todo lo demás de este libro: la lista dice *qué revisó*, no solo qué encontró.
Una sección vacía que dice "no hubo facturas vencidas en la semana hasta el 14 de noviembre" es
información; una sección vacía sin explicación es una pregunta.

**El trabajo se ejecutó y nadie lo leyó.** Este es el fallo más común y el menos discutido. Un trabajo
programado que llega a una bandeja de entrada que nadie abre es peor que no haber trabajo alguno, porque
crea la *impresión* de control. La respuesta de Riverton fue hacer de la lista del lunes una reunión—quince
minutos, tres personas, la lista en la pantalla—que suena a burocracia y es en realidad la forma más barata
posible de hacer real la automatización.

## Una breve historia del trabajo por lotes

El trabajo programado es más antiguo que el ordenador personal, y su vocabulario procede del mainframe.

En los años sesenta, un ordenador era demasiado caro como para dejar a una persona sentada ante él, así que
el trabajo se preparaba en tarjetas y se corría en *lotes* durante la noche: nómina el día 25, facturas el
día 1, el libro mayor al fin de mes. El lote era una cola, y el trabajo del operador era mantener la cola
en movimiento. Cuando llegaron los minicomputadores en los años setenta, el lote sobrevivió como `cron`—un
programa de Unix, escrito en 1975 por Ken Thompson, cuyo nombre procede de *chronos*, el tiempo—y `cron`
sigue siendo lo que corre los servidores del mundo, incluido, indirectamente, el programador dentro de tu
ERP.

Lo nuevo no es el temporizador. Es *qué* corre sobre él. Un trabajo de lotes de 1975 era un programa escrito
por un programador para hacer exactamente una cosa. Una tarea programada de 2026 es una frase en inglés, y
la máquina saca los pasos cada vez que corre. Es una clase distinta de automatización, y necesita una clase
distinta de supervisión: el programa hacía lo para lo que fue escrito, toda vez; la frase puede interpretarse
diferente a medida que cambian los datos.

Por eso la primera regla del trabajo programado en este libro es: **programa preguntas, no acciones.** La
lista del lunes pregunta. La revisión de existencias del viernes propone. El resumen del día uno del mes
informa. Ninguno publica una factura, envía una carta a un cliente, o coloca un pedido, porque esas son
decisiones con consecuencias, y una decisión tomada a las tres de la mañana por una máquina que nadie vigila
no es una decisión—es una apuesta.

## La única excepción

Hay un trabajo programado en Riverton que sí actúa, y vale la pena describirlo porque muestra dónde está la
línea.

Toda la noche a las dos, el sistema toma un respaldo: un volcado de la base de datos, una copia de la
configuración, y una línea en un registro. Actúa. Cambia el mundo, en el sentido de que aparecen archivos.
Y se le permite actuar porque la acción es *reversible por diseño*: un respaldo incorrecto se puede eliminar
y volver a tomar, y nada en la empresa depende de que haya ocurrido, hasta el día en que algo lo haga.

Esa es la prueba para cualquier acción programada: si esto corre mal a las tres de la mañana, ¿puedo deshacerlo
antes de que nadie lo note? Si sí, se puede programar. Si no, se puede proponer, y una persona puede decidir.

## El coste de un horario que nadie posee

Un trabajo programado es una pequeña promesa, y las promesas necesitan un dueño.

El fallo es silencioso y es común: un trabajo se configura por alguien que luego se va, o cambia de rol, o
simplemente olvida. Sigue corriendo. Seis meses después está produciendo un informe con un filtro que estaba
bien en marzo, o proponiendo pedidos de una línea de productos que la empresa discontinuyó, y nadie lo nota
porque nadie lo lee—hasta que alguien lo hace, y le cree.

El remedio es una lista, guardada en el mismo archivo que los prompts: cada trabajo programado, qué hace, a
quién le toca leerlo, y cuándo se revisó por última vez. Cuatro columnas, una página, revisada dos veces al
año. Un trabajo para el que nadie puede nombrar un dueño es un trabajo a eliminar.

La lista de Riverton tiene tres entradas y una cuarta que es un recordatorio para revisar la lista. Es el
documento menos impresionante de la empresa, y ha impedido dos decisiones malas, ambas las que habrían tomado
una máquina haciendo exactamente lo que le dijeron.

## Dónde vive el horario, y qué pasa cuando la máquina está apagada

Una tarea programada es un archivo, y saber dónde vive es la diferencia entre un horario que posees y un
horario del que eres prisionero.

El asistente almacena sus planes como JSON, en su propia carpeta de datos, y sobreviven a un reinicio. Cada
plan es una frase, un tiempo, una recurrencia, y una lista de qué hacer con el resultado. Esto vale la pena
conocerlo por dos motivos: se puede respaldar con el resto de la configuración, y se puede inspeccionar—es
decir, una empresa puede responder a la pregunta *¿qué hace esta máquina a las ocho del lunes?* leyendo un
archivo en vez de recordar.

Los propios programadores del ERP viven en la base de datos, en una tabla de acciones programadas, y son
visibles en la interfaz bajo *Ajustes → Técnicos → Acciones programadas*. Cada uno tiene un nombre, un intervalo,
y un conteo de cuántas veces ha corrido. Ese conteo es un pequeño pero excelente diagnóstico: un trabajo que ha
corrido cuatrocientas veces y uno que ha corrido cero veces te dicen cosas distintas, y ambos valen la pena
revisarlos una vez al trimestre.

Cuando la máquina está apagada, pueden pasar tres cosas, y el comportamiento del ERP es el sensato.

**Los programadores de Odoo** corren los trabajos perdidos en el próximo arranque, en orden, y registran el
hecho. Un recordatorio que vencía a las ocho saldrá a las nueve, y el registro lo dirá.

**Las tareas del asistente** se comprueban al arrancar: si el próximo corrida de un plan está en el pasado, se
corre al instante y se reprograma a sí misma. Una lista del lunes que se perdió porque la máquina estaba
apagada llegará el martes, con los datos tal como son el martes—que es una diferencia sutil e importante. La
lista no es "lo que pasó el lunes"; es "lo que es cierto ahora, preguntado en el horario que se destinaba al
lunes".

**Un respaldo** que se perdió se pierde simplemente, y el siguiente cubre el hueco. Eso es aceptable para un
respaldo nocterno; no lo es para uno semanal en una máquina que suele estar apagada, que es por lo que el
script de respaldo escribe una línea en un registro y el registro se revisa mensualmente.

## Cuando un trabajo produce ruido

El modo de fallo que mata el trabajo programado no es un crash. Es el ruido.

Un trabajo que produce un mensaje que nadie lee entrena a las personas a ignorar los mensajes del sistema, y
entonces el que importa también se ignora. Riverton probó cuatro horarios en el primer mes y eliminó tres, y
las eliminaciones fueron tan instructivas como las que se quedaron.

**El resumen diario** se eliminó porque duplicaba el panel y llegaba a un momento en que nadie estaba en un
escritorio. La información no era incorrecta; la entrega sí.

**La revisión de conexión horaria** se eliminó porque reportaba éxito cada hora. Un mensaje que dice *todo está
bien* no es información; es un hábito, y los hábitos son los que hacen que las personas dejen de leer.

**La revisión de duplicados nocterna** se eliminó porque era una acción que nadie había autorizado, corriendo
a un momento que nadie vigilaba, sobre datos que nadie había limpiado. No encontró nada durante tres semanas
y luego propuso fusionar a dos clientes que eran, de hecho, dos ramas de la misma organización.

Las tres que sobrevivieron comparten todas una propiedad: producen una *decisión* que una persona nombrada hace
a una hora nombrada. La lista del lunes se lee en la reunión del lunes. La revisión de existencias del viernes se
lee por Tom antes de que se vaya. El resumen mensual se lee con el primer café del mes.

Un horario sin lector es un trabajo cron con un hobby.

---

La lista del lunes lleva corriendo ocho meses, y Maggie se la ha saltado dos veces—ambas veces porque estaba de
viaje, y ambas veces la leyó el martes y desició que habría preferido leerla el lunes.

"No es la información," dice. "Podría conseguir la información. Es que el lunes por la mañana, antes de que ocurra
cualquier otra cosa, alguien pone cuatro preguntas delante de mí. Y son las cuatro preguntas correctas. Nunca
pensaría en hacerlas a las ocho del lunes. Las pensaría a las cuatro del viernes, cuando ya es tarde para hacer
cualquier cosa."

Ese es el verdadero valor del trabajo programado, y no tiene nada que ver con las máquinas trabajando mientras
duermes. Es que la *pregunta* tiene un tiempo, y el tiempo lo elige alguien que pensó en él una vez, con
cuidado, en vez de quienquiera que por casualidad esté preocupado en el momento.
