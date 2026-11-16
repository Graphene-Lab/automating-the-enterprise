# 29. La aritmética de no hacerlo

Gerald Pryce, el contable situado encima de la tienda de productos químicos, tenía una regla sobre las inversiones: *muéstrame el coste de la cosa por la que ya estás pagando.*

Maggie había ido a verlo en primavera, con las facturas del año y una pregunta de la que se sentía ligeramente avergonzada, porque sonaba como la pregunta de alguien que ya había decidido. "¿Había valido la pena?"

Gerald se puso las gafas, lo que significaba que se lo iba a pasar bien.

"Aún no," dijo. "Primero hacemos la aritmética de no hacerlo."

---

La mayoría de los casos de negocio para software se escriben al revés. Enumeran el coste de la cosa nueva—la licencia, el hardware, la formación, el consultor—y luego enumeran los beneficios en el lenguaje de la esperanza: eficiencia, visibilidad, agilidad. Los números del lado del coste son precisos, porque alguien los ha presupuestado. Los números del lado de los beneficios son adjetivos.

La aritmética de no hacerlo va al revés. Parte de la posición de que la empresa ya está pagando por su forma actual de trabajar, cada único día, y que ese pago no aparece en ninguna cuenta porque se hace en horas.

Así que Gerald y Maggie pasaron una mañana con una hoja de cálculo—la herramienta que sustituyó a la aritmética del contable y no sustituyó al contable—y contaron.

**La primera línea era la emisión de facturas.** Riverton producía, de promedio, cuatrocientas ochenta facturas al mes. Cada una tardaba, desde el momento en que se confirmaba la entrega hasta el momento en que el sobre estaba en el correo, entre cuatro y seis minutos del tiempo de alguien: imprimir, comprobar frente al albarán de entrega, doblar, dirigir, sellar. Llamémosle cinco minutos, lo que son sesenta horas al mes, lo que es casi una semana y media de trabajo.

Tras el cambio, la emisión tardaba once minutos en total, porque los documentos se generaban y enviaban por correo electrónico, y la comprobación se hacía mirando una lista en lugar de cada hoja de papel. Las sesenta horas no se volvieron cero; algunas se convirtieron en comprobación, y algunas en el trabajo que Doreen siempre había querido hacer. Pero cuarenta horas al mes volvían a la empresa.

**La segunda línea era la búsqueda.** Nadie había medido nunca esto, porque nadie mide la búsqueda. Doreen la estimó en una hora al día, lo que probablemente era una subestimación, porque la gente no cuenta las interrupciones. Veinte horas al mes, desaparecidas. Tras el cambio, quizás tres, gastadas en su mayor parte mirando cosas que necesitaban una decisión en lugar de una ubicación.

**La tercera línea eran los errores.** Doce notas de crédito en el año anterior, causadas por precios equivocados, cantidades equivocadas o direcciones equivocadas, a un promedio de ciento cuarenta libras cada una, más el tiempo para corregirlas y el pequeño daño a la relación. El cambio no eliminaba los errores, pero eliminaba la clase de errores causados por reescribir, porque nada se reescribía.

**La cuarta línea era el dinero que llegaba tarde.** Esta es la línea que sorprendió a Maggie, porque no es un coste en las cuentas; es un coste en el banco. El tiempo medio desde la factura hasta el pago había sido de cincuenta y tres días. Tras seis meses de facturas enviadas a tiempo, y de un recordatorio educado que la asistente producía cada lunes sin que se le pidiera, fue de cuarenta y uno. Doce días de facturación de una empresa, sentados en el banco en lugar de en las cuentas de los clientes, valen más que el coste entero del sistema, y aparecen en ningún lugar de una cuenta de pérdidas y ganancias.

---

Frente a eso, los costes.

El software era gratuito. Odoo Community, la base de datos, la asistente y el conector son todos de código abierto, y la licencia de todo ello es cero. Esto no es un truco y no es una prueba: es el modelo de negocio del código abierto, y es por lo que una empresa del tamaño de Riverton puede permitirse un sistema que habría sido impensable en 1995.

El hardware era un ordenador que la empresa ya poseía, con suficiente memoria y disco para correr tres programas a la vez. Si una empresa tiene que comprar uno, es una inversión de capital del mismo orden que el servicio anual de una furgoneta de entrega, y dura más tiempo.

El modelo de lenguaje era un servicio, pagado por uso. La cantidad depende del proveedor y de cuánto se le pide a la asistente, y es la única línea que una empresa debería vigilar, de la misma forma en que vigila la electricidad. Lo que importa es la relación: se le pide a la asistente que haga cosas que de otro modo tomarían a una persona minutos, y el coste de una solicitud se mide en fracciones de penique, así que la relación no es cercana.

Los costes honestos eran los dos que nadie presupueste.

El primero era *el tiempo de instalación*, que fue un día de atención de Sam Okafor y una semana de Maggie, repartidos en un mes, mayoritariamente en las noches. El segundo era *la disciplina*, que no es un coste que se paga una sola vez. Alguien tiene que mantener limpia la lista de productos, decidir qué se le permite hacer a la asistente, leer el registro, y decir que no a la solicitud de añadir una excepción más. Ese es un trabajo permanente, pequeño y poco atractivo, y es el precio de todo ello.

---

Hay una trampa en esta aritmética, y vale la pena nombrarla porque atrapa a las empresas inteligentes.

La trampa es automatizar la parte que es fácil de automatizar en lugar de la parte que cuesta más. Se puede enseñar a una asistente, en una tarde, a producir un informe semanal hermoso. El informe tarda diez minutos en producirse a mano. Mientras tanto, el proceso que cuesta cuarenta horas al mes—la emisión de facturas, la conciliación, el seguimiento de cuentas pendientes—se deja solo, porque es más desordenado y porque toca el dinero y porque alguien tendría que tomar una decisión sobre cómo debería funcionar.

Las empresas que obtienen un retorno son las que empiezan por el proceso caro, aburrido y repetitivo, y aceptan que la primera versión será imperfecta. Las empresas que obtienen una demostración son las que empiezan por el informe.

Hay una segunda trampa, que es la imagen especular: automatizar algo que no debería hacerse en absoluto. Una asistente producirá de buena gana un informe que nadie lee, a una velocidad que hace imposible argumentar que no se está produciendo. Antes de automatizar una tarea, la pregunta no es "¿puede automatizarse?" sino "si esto ocurriera automáticamente, cada día, ¿alguien estaría mejor?". Un número sorprendente de tareas de oficina fracasan en esa prueba, y la automatización correcta para ellas es la eliminación.

## Los números que son fáciles de equivocarse

Se cometen tres errores en casi cada caso de negocio para este tipo de sistemas, y cada uno de ellos vale la pena evitar porque cada uno destruye la credibilidad de todo el cálculo.

**Contar las horas ahorradas como si fueran dinero.** Una hora ahorrada no es una hora pagada. Si la empresa no reduce las horas de nadie, el ahorro es *capacidad*, no efectivo—y la capacidad solo vale dinero si alguien la usa para algo que genera ingresos. La versión honesta de Riverton para el cálculo era: cuarenta horas al mes de capacidad, de las que aproximadamente la mitad se usaron para un trabajo que de otro modo habría sido hecho por una agencia o no se habría hecho en absoluto, y la mitad era simplemente una oficina menos cansada. La segunda mitad es real y no aparece en una hoja de cálculo.

**Ignorar el coste del cambio.** La instalación, la configuración, el primer mes de correcciones, la formación, la resistencia. Un caso de negocio que supone que el nuevo sistema funciona desde el primer día es un caso de negocio que estará equivocado por una semana del tiempo de alguien. El de Riverton fueron dos meses de atención de Doreen a aproximadamente media jornada, que es la línea individual más grande de todo el cálculo y que ningún proveedor menciona nunca.

**Suponer que el beneficio es permanente.** Un sistema que no se mantiene decae: la lista de productos se llena de basura, los códigos fiscales se desplazan, los permisos de la asistente se amplían "solo esta vez". El decaimiento es lento y es invisible hasta que alguien intenta responder a una pregunta y obtiene una respuesta equivocada con seguridad. La hora a la semana en la agenda es el coste de mantenimiento, y pertenece al cálculo.

## Lo que la aritmética realmente dice

Con los errores evitados, la aritmética del primer año de Riverton se ve así.

| Línea | Cantidad |
|---|---|
| Licencias de software | £0 |
| Hardware (una máquina que la empresa ya poseía) | £0 |
| Uso del modelo de lenguaje para el año | unas £90 |
| Instalación y configuración (tiempo de Sam) | £1,200 |
| Tiempo interno para configurar y corregir (dos meses, a media jornada) | unas £4,000 |
| **Coste total** | **unas £5,300** |
| Horas devueltas al trabajo productivo | unas 480 |
| Valor de esas horas a las tarifas salariales de Riverton | unas £9,600 |
| Cobro anterior de deudas (doce días de facturación) | unas £14,000 de capital circulante |
| Errores evitados (notas de crédito, precios equivocados, recargos perdidos) | unas £3,400 |
| **Beneficio total, primer año** | **unas £27,000, de las que £13,000 son efectivo** |

La línea de capital circulante es la que sorprende a la gente, y vale la pena explicarla porque no es beneficio. Doce días de facturación que llegan antes no hacen a la empresa más rica; hacen a la empresa *más segura*, porque el dinero está en el banco cuando llega la factura del proveedor. Para un negocio con liquidez ajustada, eso vale más que la línea de beneficio, y es invisible en una cuenta de pérdidas y ganancias.

El cálculo del segundo año es mucho mejor, porque el coste de instalación ha desaparecido y solo queda el mantenimiento: unas £500 de coste frente a los mismos beneficios. Esa es la forma de toda buena inversión en software: cara en el primer año, barata después, y que no vale nada en absoluto si nadie la mantiene.

## La comparación que importa

La comparación que una empresa debería hacer no es entre este sistema y no tener sistema. Es entre este sistema *y la forma en que la empresa trabaja ahora*, con todos sus costes contados—incluidos los que no aparecen en las cuentas.

La forma antigua de Riverton costaba, por año: sesenta horas al mes de facturación y archivo (unas £18,000 a las salarializadas), una cantidad desconocida de búsqueda y de preguntas (probablemente £6,000), doce notas de crédito por errores de reescripción (£1,700), y doce días de deudas permanentemente en las cuentas de los clientes (lo que es un préstamo permanente de unas £14,000 de capital circulante, a cualquier coste que tenga el sobregiro).

Frente a eso, la nueva forma cuesta £500 al año después de la primera, más una hora a la semana de atención.

La comparación no es cercana, y nunca lo es—para cualquier empresa que produce documentos y quiere saber qué es verdad. Lo que frena a las empresas no es la aritmética. Es el cambio, y el miedo a él, y ninguna hoja de cálculo aborda eso.

---

Gerald sumó las columnas, se quitó las gafas, y dio a Maggie la respuesta de la forma en que lo hacen los contables: no un número, sino una frase con un número dentro.

"Las horas que recuperaste vale alrededor de treinta y una mil libras al año a los salarios que pagas," dijo. "El dinero que llegó doce días antes vale más que eso, y no es ingreso, es oxígeno. Los errores valen cuatro mil. Frente a eso, tus costes son la máquina, el modelo y tu propio tiempo, que no has cobrado y deberías."

"Así que había valido la pena."

"Había valido la pena *si sigues haciendo la disciplina*," dijo. "Si paras, el sistema se desplazará de vuelta a ser un archivador muy caro en un año. He visto que ocurra. El software no falla. Los hábitos sí."

Esa es la frase que recordar de este capítulo, y es la frase menos comercial de todo el libro. La aritmética de no hacerlo es favorable, decisivamente así, para casi cada empresa que produce documentos y quiere saber qué es verdad. Pero la aritmética solo se mantiene mientras alguien mantiene el modelo honesto, y ese alguien es una persona, y esa persona tiene que recibir el tiempo.

---

Maggie escribió los números en una tarjeta y la puso en el cajón con la servilleta. Luego hizo algo que Gerald no había sugerido, y que aprobó cuando ella se lo dijo.

Le dio a Doreen un título.

No era un título grandioso—*sistemas de oficina y excepciones*—y no venía con más dinero, porque Riverton es una pequeña empresa y el dinero es real. Pero venía con una hora al día que estaba protegida, en la agenda, para el trabajo de notar: comprobar precios, leer el registro, hacer preguntas a la asistente cuyas respuestas podrían ser incómodas.

La tarjeta en el cajón decía cuánto valía el sistema. La hora en la agenda era lo que hacía verdadera la tarjeta.
