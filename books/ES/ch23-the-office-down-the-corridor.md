# 23. La oficina al final del pasillo

El asistente tiene dos puertas delanteras, y la mayoría de las empresas usan una de ellas durante un mes antes de descubrir la otra.

La primera es la ventana de terminal: fondo negro, un indicador, y la respuesta debajo. Es la puerta que este libro ha estado usando, porque es la que muestra el trabajo—las llamadas a herramientas, los pasos intermedios, el registro. Es un taller.

La segunda es una página web, en `http://localhost:5290/OfficeManager`, y no es un taller. Es una oficina.

---

## Qué muestra la página

La página dibuja una pequeña sala. Hay escritorios, una puerta, una planta, y varias figuras pequeñas que caminan, se sientan, se levantan y, de vez en cuando, se reúnen junto al dispensador de agua. Una de ellas es tu agente. Debajo de la sala hay una caja de chat.

![La oficina: una sala, un trabajador, y una caja de chat en la parte inferior](../../assets/screens/assistant-01-office.png)

Cuando llega una instrucción, una figura aparece en la puerta y toma un escritorio, el panel de la derecha muestra qué está haciendo—*obtener contexto*, *buscar*, *crear*—y el registro de chat anota el intercambio.

![La instrucción cuando llega: el agente ha tomado un escritorio y está trabajando](../../assets/screens/assistant-02-prompt.png)

Si eso suena caprichoso, lo es—y también es la interfaz más efectiva para este tipo de trabajo que Riverton probó. La razón vale la pena entenderla, porque no se trata de ternura.

Una ventana de terminal muestra *una sola conversación a la vez*, y muestra todo: cada llamada a herramienta, cada resultado intermedio, cada línea de razonamiento. Eso es exactamente lo que quieres cuando estás construyendo o depurando un trabajo. Es exactamente lo que no quieres cuando eres un gerente de oficina con un cliente al teléfono.

La página de oficina muestra *una sola cosa*: el agente, y si está ocupado. Las figuras caminan cuando el agente está pensando y se sientan cuando está inactivo. Puedes ver, desde el otro lado de la sala, si el asistente está trabajando—lo cual suena trivial y es, de hecho, la información más útil de todo el sistema.

"Puedes saber si está ocupado sin leer nada," dijo Priya. "En la terminal tengo que mirar la última línea. Aquí simplemente miro."

## Cuándo usar cuál

Tras un mes, los hábitos de Riverton se asentaron en una división simple.

**La terminal para cualquier cosa que toque dinero o cambie un documento.** Crear una factura, publicar una cuenta, confirmar un pedido. La razón no es que la página web no pueda hacerlo—puede—sino que la terminal muestra los *pasos*, y una persona que puede ver los pasos puede detenerlos. En la terminal, observas al asistente buscar al cliente, leer el producto, crear el documento, y puedes ver el momento en que se equivoca. En la página web ves una burbuja que dice "hecho", y tienes que fiarte de ello.

**La página web para preguntas y barridos.** *¿Cuántas facturas vencidas tenemos? ¿Qué productos están bajos? ¿Qué vendimos la semana pasada?* No se cambia nada, la respuesta es corta, y la metáfora de la oficina hace que todo se sienta como preguntar a un colega en vez de operar una máquina.

**La página web para cualquiera que no sea Maggie.** Tom la usa, Priya la usa, y Doreen—tras alguna resistencia—la usa. La terminal es intimidante de una manera que no tiene nada que ver con el trabajo: parece el interior de una máquina, y a la mayoría del personal de oficina les han enseñado, durante treinta años, que el interior de una máquina no es para ellos. La página de office se parece a un lugar donde alguien trabaja.

Ese último punto no es decoración. Es la diferencia entre una herramienta que usan cuatro personas y una herramienta que una persona usa en nombre de cuatro.

## Las pequeñas figuras

Las figuras de la oficina no son avatares del personal. Son *agentes*: la instalación puede correr varias, cada una con su propio trabajo, y la página las muestra a todas. Riverton corre una, porque la máquina tiene un modelo y una tarjeta gráfica, y los agentes paraleles en una máquina no añaden velocidad—se turnan, y pueden agotar la memoria.

La página es honesta con esto si la miras: las figuras comparten la sala, y la sala tiene un solo teléfono. Dos agentes intentando contestarlo a la vez no es una característica.

Existe una tentación, cuando ves la oficina, de poblarla—darle a cada departamento su propia pequeña figura con sus propias instrucciones. Es una mala idea para una pequeña empresa, y la razón es la misma que atraviesa todo este libro: un agente solo es tan bueno como el modelo detrás de él, y un modelo contestando cuatro conversaciones es cuatro conversaciones lentas. La oficina es una ventana a un solo trabajador, no un personal.

## La tercera puerta, que no es una puerta en absoluto

Hay una tercera forma de entrar, y no es una pantalla: el asistente responde a solicitudes HTTP.

En la misma máquina, en `http://localhost:5290/v1/chat/completions`, habla el mismo protocolo que los grandes servicios en la nube. Cualquier cosa que pueda hablar con un punto de extremo compatible con OpenAI puede hablar con él—un script, una macro de hoja de cálculo, otro programa, un sistema telefónico, el formulario de contacto de un sitio web.

Riverton no ha usado esto, y vale la pena explicar por qué, porque la tentación es fuerte y el riesgo es sutil.

La tentación es obvia: un cliente envía un correo con una consulta, el sitio web lo reenvía al asistente, el asistente crea un registro de cliente y una cotización borrador, y Priya encuentra el trabajo hecho cuando abre su pantalla. Ese es un flujo de trabajo real, y es exactamente el tipo de cosa en que esta tecnología es buena.

El riesgo es que cada puerta al sistema es una puerta, y la puerta en `localhost:5290` está abierta a cualquier cosa que corra en la máquina—incluida una pestaña de navegador que ha sido engañada para hacer una solicitud. La API no tiene autenticación por defecto, porque fue diseñada para ser alcanzada desde la misma máquina por programas que el controlador controla. Ese es un diseño razonable para un taller. No es un diseño razonable para una empresa que un día la conecte a internet.

La regla que Riverton adoptó, y la que este libro recomienda: **la API se queda en la máquina hasta que alguien tenga una necesidad específica y un plan específico.** Cuando llegue ese día, el plan tiene tres líneas—ponerlo detrás de un proxy que requiera un token, limitarlo a un solo punto de extremo, y registrar cada solicitud. Hasta entonces, dos puertas delanteras son suficientes, y ambas tienen una persona detrás.

## La tarde de Tom

El día en que la página de oficina ganó su lugar en la empresa fue un jueves de febrero, y la historia es pequeña.

Tom estaba en el almacén con una tabla de madera, haciendo el conteo trimestral, y necesitaba saber si una paleta de papel había sido recibida contra un pedido o seguía "en tránsito" en el sistema. En la terminal, esa pregunta significa caminar hasta la oficina, sentarse en la máquina que corre el asistente, y escribir. En la página de oficina, significa abrir una pestaña de navegador en la laptop del almacén—que es una máquina barata que existe para buscar códigos de producto—y escribir la pregunta allí.

*¿Se ha recibido la paleta de papel A4 de Pennine en el pedido P00008?*

*Recibido: 40 resmas el 12 de noviembre, validado por Tom Beck, movimiento de stock WH/IN/00031. El pedido está completamente recibido; la factura aún no ha sido creada.*

Tuvo su respuesta en nueve segundos, de pie junto a la paleta. La versión antigua de esa respuesta era una caminata hasta la oficina, una conversación, y una nota en la tabla de madera.

Este es el beneficio menos dramático de todo el libro y posiblemente el más importante: la distancia entre una pregunta y su respuesta, medida en pasos. Un almacén que puede preguntar al sistema algo sin salir del almacén es un almacén que verifica cosas.

## Lo que la oficina no puede hacer

Tres límites vale la pena conocer antes de que una empresa construya un alrededor de la página.

**No puede correr dos conversaciones a la vez, útilmente.** La oficina dibuja varias figuras, y la tentación es contratar una por departamento. En una máquina con un modelo, eso son cuatro conversaciones se turnando, y las figuras se sentarán en sus escritorios luciendo ocupadas mientras nada termina. La página es honesta con esto si la observas: el panel de la derecha lista las sesiones, y solo una de ellas está *trabajando* en cualquier momento.

**No puede mostrarte el razonamiento.** La terminal muestra las llamadas a herramientas a medida que ocurren; la oficina muestra una etiqueta (*buscar*, *crear*, *obtener contexto*) y luego una respuesta. Ese es el nivel de detalle correcto para un gerente de oficina y el nivel incorrecto para alguien que depura un trabajo. Las dos entradas no son intercambiables, y una empresa que use solo la página web eventualmente necesitará la terminal—usualmente el día que algo se equivoca.

**No puede dejarse abierta en una pantalla en una habitación pública.** El chat muestra los datos de la empresa: nombres, montos, facturas. Una laptop sobre un escritorio en una tienda es una ventana al libro mayor. La página no tiene inicio de sesión propio, porque es servida por el asistente en `localhost` y asume que la máquina es tuya. Esa suposición es correcta en un escritorio y incorrecta en una sala de recepción.

## El sonido, y el interruptor que lo apaga

La página emite ruidos pequeños: un teclado cuando el agente está escribiendo, una campana cuando un trabajo está hecho. Es encantador por una semana y exasperante por un mes, y el interruptor está en la esquina inferior derecha de la página, etiquetado *SONIDO: ON*.

El hecho de que esto merezca un párrafo es en sí mismo una lección sobre el software de oficina. Las funciones que deciden si una herramienta sobrevive rara vez son las de la folleto. Son las que tocan los nervios de la oficina: si hace ruido, si puede dejarse abierta, si la cosa que muestra es verdadera.

## Una breve historia de la metáfora de la oficina

Poner personas en una imagen para representar el trabajo es una idea vieja en informática, y tiene un buen registro.

En 1984, el Macintosh de Apple introdujo la metáfora del escritorio—archivos, carpetas, una papelera—y funcionó porque permitía a las personas usar conocimiento que ya tenían. En 1987, el proyecto Information Visualizer en Xerox PARC fue más allá y dibujó oficinas, con salas y documentos, como una forma de navegar espacios grandes de información. En 1993, el juego *Doom* enseñó a una generación que una vista en primera persona de un espacio es más legible que un diagrama de él.

Lo que los tres descubrieron es la misma cosa: **una metáfora espacial lleva el estado.** No tienes que leer una línea de estado para saber que una sala está ocupada; puedes verla. La página de oficina en Riverton es un descendiente directo de esa idea, y existe para la misma razón—no para ser encantadora, sino para responder a la pregunta *¿qué está pasando?* sin requerir que el usuario lea.

## El chat, y la misma disciplina

La caja de chat en la parte inferior de la página toma las mismas instrucciones que la terminal, y produce el mismo trabajo. Todo en el capítulo veinticinco sobre las instrucciones se aplica sin cambios.

Dos cosas son diferentes, y ambas son consecuencias de la interfaz.

**Las respuestas son más cortas.** La página web muestra una conversación, no un registro, así que el asistente resume. Eso es bueno para leer y malo para verificar: el número de factura puede estar en el resumen, pero la lista de pasos que lo produjeron no. Cuando un resultado importa, pregunta una continuación—*muéstrame los documentos detrás de ese número*—y la respuesta será una lista.

**La tentación de hacer múltiples tareas es más fuerte.** Una ventana de chat invita a una segunda pregunta mientras la primera sigue corriendo, y una segunda pregunta mientras la primera está corriendo es lo que hace sentir rota a una instalación de un solo modelo. La página no lo impide. El hábito sí.

---

El uso propio de Maggie se asentó en algo que ella no esperaba: usa la página web por la mañana y la terminal por la tarde.

"Por la mañana quiero saber cosas," dice. "Quiero la lista de lo que está tarde, lo que está bajo, lo que llegó durante la noche. Eso es una conversación, y la oficina es donde la tengo. Por la tarde quiero *hacer* cosas—publicar las facturas, perseguir las tres cuentas, arreglar la cosa que encontró Tom—y para eso quiero ver dar las ruedas."

Pensó en ello por un momento.

"Es como la diferencia entre preguntar a alguien una pregunta en el pasillo y sentarse con ellos en un escritorio. Misma persona. Diferente sala."

Ese es tan buena descripción de las dos interfaces como este libro puede ofrecer, y sugiere el principio detrás de ellas: la interfaz debe coincidir con el *tipo de atención* que el trabajo requiere, no con el tipo de tecnología detrás de él. Una pregunta necesita una conversación. Una publicación necesita un testigo.
