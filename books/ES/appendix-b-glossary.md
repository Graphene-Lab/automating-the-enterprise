# Apéndice B — Un glosario para quienes no programan

Cada palabra que sigue es una que este libro ha usado, o que alguien usará contigo mientras instalas el sistema. Las definiciones son deliberadamente sencillas y a veces imprecisas; donde una definición precisa ayudaría a un programador y confundiría a un gerente de oficina, ha ganado la sencilla.

**Agent.** Un programa que puede recibir una instrucción en lenguaje ordinario y actuar sobre ella—buscar datos, crear registros, ejecutar un proceso—en lugar de limitarse a responder con texto. En este libro, el agente es AgentBridge, el programa con el que hablas en una ventana de terminal.

**API.** Application Programming Interface (Interfaz de Programación de Aplicaciones). Una forma documentada de que un programa le pida a otro que haga algo. Piensa en ella como la trampilla de servicio de un restaurante: la cocina no quiere que entres a la cocina, pero hay una forma correcta de entregar un pedido y recibir un plato.

**API key.** La contraseña que un programa utiliza en lugar de un ser humano. Es una cadena larga de caracteres, se muestra una sola vez, y debe tratarse como la llave de la caja fuerte: guardada en un gestor de contraseñas, nunca en un correo electrónico, nunca en un documento que se reenvíe.

**Backup.** Una copia de los datos tomada en un momento determinado, guardada en un lugar distinto de la máquina que contiene el original. Un respaldo no verificado es un deseo; un respaldo que has abierto y leído es un respaldo.

**Database.** Un programa cuya función es guardar hechos y devolverlos con precisión, incluso cuando se corta la corriente en medio de un cambio. En este libro, PostgreSQL.

**Document (in an ERP).** No una hoja de papel: un registro de algo que ocurrió o va a ocurrir—un pedido, una entrega, una factura, un pago—con una fecha, una parte, una lista de líneas y un estado. Los documentos conservan su propia copia de los hechos con los que se crearon, de modo que la factura de mes pasado sigue mostrando el precio de mes pasado.

**ERP.** Enterprise Resource Planning (Planificación de Recursos Empresariales). Software que mantiene al cliente, el producto, el pedido, el existo, la factura y el libro mayor en un único modelo conectado, de modo que un hecho introducido una sola vez es visible en todas partes. El nombre fue acuñado por la firma de análisis Gartner en 1990.

**Field.** Una pieza de información en un registro: el número de teléfono del cliente, el precio de un producto, la fecha de una factura.

**Journal entry.** El registro contable de doble entrada que produce todo evento financiero: un importe en una cuenta y el mismo importe, opuesto, en otra. Inventada mucho antes que el software; codificada por Luca Pacioli en 1494; sigue siendo la razón por la que las cuentas pueden verificarse.

**JSON.** Una forma de escribir datos como texto, de modo que un programa pueda enviárselos a otro. Solo la verás en un archivo de registro, donde se parece a un párrafo de signos de puntuación.

**Language model (LLM).** Un programa entrenado sobre una cantidad enorme de texto, capaz de producir texto plausible en respuesta a una instrucción. Es bueno con el lenguaje y poco fiable con los hechos, salvo que esté *fundado*—es decir, salvo que se le obligue a buscar los hechos en lugar de recordarlos.

**MCP.** Model Context Protocol (Protocolo de Contexto del Modelo). Un estándar abierto, publicado por Anthropic en noviembre de 2024, que permite a un programa describir las herramientas que ofrece a un asistente de forma uniforme. Es la razón por la que una herramienta escrita para un asistente puede ser usada por otro.

**Model (in this book, two meanings).** 1. La representación de una empresa dentro de un ERP: partes, productos, documentos, dinero. 2. El artefacto entrenado tras un asistente: el "modelo de lenguaje." El contexto aclara cuál; cuando no lo hace, el primer significado suele ser el que importa.

**Module.** Un paquete que añade una capacidad a un ERP—contabilidad, existos, fabricación, compras. Instalar un módulo añade pantallas, registros y reglas; no cambia los datos subyacentes.

**Odoo.** Un ERP de código abierto, iniciado en 2005 con el nombre TinyERP, renombrado OpenERP en 2008 y Odoo en 2014. La edición Community es gratuita; la edición Enterprise está licenciada. La versión 20, usada en este libro, se publicó en septiembre de 2026.

**PostgreSQL.** La base de datos de código abierto usada por Odoo. Comenzó como un proyecto de investigación en la Universidad de California en Berkeley en la década de 1980 y es hoy una de las bases de datos más usadas del mundo.

**Prompt.** La instrucción que escribes para el asistente, en lenguaje ordinario. Un buen prompt dice qué quieres, para quién y hasta cuándo; un mal prompt dice "haz las facturas" y espera lo mejor.

**Record.** Una fila en una tabla: un cliente, un producto, una factura.

**Schema.** La lista de tablas y campos que contiene una base de datos, y las reglas sobre lo que puede ir en ellos. Cuando alguien dice "el esquema dice que un cliente debe tener un nombre," significa que la base de datos rechazará guardar un cliente sin uno.

**Stock move.** El registro de bienes que se mueven de un lugar a otro: de un proveedor a un almacén, de una estantería a una furgoneta, de una furgoneta de vuelta a una estantería porque la puerta de la escuela estaba cerrada. El nivel de existos de un producto es la suma de sus movimientos; nunca se escribe directamente.

**Token.** La unidad en que se mide el trabajo de un modelo de lenguaje. Aproximadamente, un token son tres cuartos de una palabra. Los proveedores cobran por token, que es por lo que un documento muy largo cuesta más procesar que una pregunta corta.

**Tool (in the context of an assistant).** Una acción que el asistente está autorizado a realizar, con un nombre y una descripción: *buscar clientes*, *crear una factura*, *asentar un pago*. Un asistente sin herramientas solo puede hablar. Un asistente con herramientas puede trabajar.

**Transaction.** Un cambio que ocurre por completo o no ocurre en absoluto. Es la promesa que hace confiable a una base de datos: no hay ningún estado en que exista a medias una factura.

**Variant.** Una versión de un producto que difiere en un atributo—tamaño, color, voltaje. Un producto con doce variantes no es doce productos, y modelarlo correctamente marca la diferencia entre un informe útil y uno inútil.

**Web interface (or web UI).** Las pantallas que ves en un navegador. La interfaz web de Odoo es donde configuras la empresa, miras registros y imprimes documentos; el asistente es una segunda forma de alcanzar los mismos registros.

**Workflow.** La secuencia de estados por los que pasa un documento—borrador, confirmado, entregado, facturado, pagado—y las reglas sobre quién puede moverlo de uno al siguiente. En un ERP bueno, el flujo de trabajo es la política de la empresa, escrita y hecha cumplir.
