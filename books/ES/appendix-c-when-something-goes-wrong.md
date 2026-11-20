# Apéndice C — Cuando algo sale mal

Este apéndice está organizado por síntoma, porque así es como llega el problema. Cada entrada dice qué verás, qué suele significar y qué hacer. Las entradas marcadas como *vistas* son fallos que ocurrieron durante la escritura de este libro, en la instalación que produjo sus capturas de pantalla; no son hipotéticos.

Antes que nada, un hábito. Cuando algo sale mal, no reinstales. Lee las veinte últimas líneas del registro y observa cuál de las tres cajas de la servilleta está insatisfecha: la memoria (la base de datos), el modelo (el ERP) o el asistente. Nueve veces de cada diez la respuesta te dice qué hacer, y reinstalar destruye las pruebas.

---

## El instalador se detiene con "psql was not found"

**Qué verás.** El instalador informa de que PostgreSQL no está instalado, intenta `winget`, luego intenta descargar el instalador oficial directamente y finalmente se detiene con un mensaje que dice que `psql` no se encontró y que nada de lo que viene a continuación funcionaría.

**Qué significa.** PostgreSQL no está en la máquina. El instalador intentó instalarlo y no pudo: bien `winget` no pudo alcanzar su fuente, o la descarga desde el sitio del fabricante no terminó. En una conexión lenta o inestable este es el fallo más común de todo el procedimiento.

**Qué hacer.** Ejecuta el instalador de nuevo. Continúa por donde se detuvo y reutiliza lo que ya está ahí; una descarga parcial se reanuda en lugar de reiniciarse, así que cada intento avanza más que el anterior. Si estás en una conexión más lenta que medio megabit por segundo aproximadamente, descarga el instalador de PostgreSQL tú mismo, con un navegador, desde el sitio del fabricante, y colócalo en la carpeta que el instalador indica; la próxima ejecución lo encontrará y lo usará. Si prefieres instalar PostgreSQL a mano, vale cualquier versión 16.x, y el instalador lo detectará en la próxima ejecución—incluso su puerto, que lee del propio archivo de configuración del servidor.

*Visto durante la escritura de este libro:* la primera ejecución falló exactamente en este punto, después de tres intentos de descarga, en una conexión que iba a unos sesenta kilobytes por segundo. La segunda ejecución reanudó el archivo parcial y completó.

---

## "TCP port 5432 is already in use"

**Qué verás.** A principios de la ejecución, una advertencia de que el puerto 5432 está ocupado y de que PostgreSQL escuchará en el 5433 en su lugar.

**Qué significa.** Otra cosa en la máquina está usando el puerto estándar de base de datos. Muy a menudo es una base de datos dentro del Subsistema de Windows para Linux, reenviada al lado de Windows, o un contenedor de Docker.

**Qué hacer.** Nada. El instalador elige el primer puerto libre y lo lleva a lo largo de toda la pila—el rol de la base de datos, la base de datos, el ERP y el lanzador. Esto no es un error; es el instalador haciendo lo correcto en una máquina ocupada. Apunta el puerto si planeas conectarte a la base de datos con otras herramientas.

---

## `winget` no puede instalar nada

**Qué verás.** Un mensaje de que `winget` salió con un error de conexión, seguido de que el instalador recurre a una descarga directa.

**Qué significa.** No se pudo alcanzar la fuente del paquete. Las redes corporativas, las redes de hoteles y algunos productos de antivirus interfieren con el Administrador de Paquetes de Windows.

**Qué hacer.** Deja que el recurso a la descarga alternativa haga su trabajo. Si ambas rutas fallan, instala el componente a mano (PostgreSQL y Python son los únicos dos que el instalador necesita del exterior), luego ejecuta el instalador de nuevo.

---

## La página que se abre no es la de acceso

**Qué ves.** Haces doble clic en **AI Odoo**, o abres `http://localhost:8069`, y el navegador muestra
algo que no es la tarjeta blanca de acceso: una página sobre Odoo, un sitio web con un logo de relleno,
o una lista de bases de datos.

**Qué significa.** La dirección que pediste no es la de tu ERP, o es una dirección a la que pueden
responder varias cosas. Hay exactamente tres casos, y cada uno tiene su causa.

*Es la documentación de Odoo, en odoo.com, en el idioma de tu navegador.* Es una página sobre el
producto, no sobre tu máquina: nada de lo que hay es un dato tuyo y no forma parte de la instalación.
Es lo que una versión anterior del instalador abría al final, y todavía se imprime al final como
enlace para leer después. Ciérrala y abre la página inicial desde el icono.

*Es un sitio web con un logo que no elegiste, un menú y un enlace «Iniciar sesión» en una esquina.* Es
la aplicación **website** de Odoo: un módulo que sirve un sitio público en la dirección raíz. Una vez
instalado, `http://localhost:8069` muestra el sitio en lugar de la página de acceso, y el ERP se
esconde detrás del pequeño enlace de acceso. No hay nada roto y no se ha perdido ningún dato. La
página de acceso tiene su propia dirección, y funciona siempre:
`http://localhost:8069/web/login?db=odoo_agent`. La página inicial y el icono usan esa dirección por
este motivo.

*Es una lista de bases de datos, o un formulario que pregunta qué base quieres decir.* La máquina tiene
más de una base Odoo—una copia de prueba, una instalación vieja—y la dirección no nombraba ninguna.
Añade `?db=odoo_agent` a la dirección, o usa la página inicial, que la nombra.

---

## El usuario y la contraseña impresos al final no funcionan

**Qué ves.** Las credenciales del resumen del instalador son rechazadas, y la página de acceso dice
que el nombre de usuario o la contraseña son incorrectos.

**Qué significa.** En una primera instalación el instalador crea el administrador e imprime lo que ha
creado, así que las dos cosas coinciden. En una segunda ejecución la cuenta ya existe y conserva su
usuario y su contraseña: imprimir ahí una contraseña recién inventada sería imprimir una contraseña
que nunca se aplicó. Ahora el instalador vuelve a leer la cuenta de la base de datos y dice o la
contraseña que ha puesto, o que la contraseña no ha cambiado desde la primera instalación.

**Qué hacer.** Si el resumen dice *sin cambios*, usa la contraseña de la primera instalación. Si se ha
perdido, pon una nueva a propósito: ejecuta otra vez el instalador con `ADMIN_PASS` en el entorno, y
aplicará e imprimirá esa contraseña. Nada más en la base de datos se toca.

---

## La ventana negra ha desaparecido

**Qué ves.** Odoo sigue respondiendo en el navegador, pero no hay ninguna ventana donde escribir.

**Qué significa.** La ventana negra *es* el asistente: cerrarla detiene el asistente, y solo al
asistente. El ERP se ejecuta como un programa separado, y por eso el navegador sigue funcionando.

**Qué hacer.** Haz doble clic otra vez en **AI Odoo**. Arranca lo que falta y no arranca una segunda
copia de lo que ya está en marcha.

---

## El ERP no responde en su puerto

**Qué verás.** Tras la instalación, el navegador no alcanza la dirección impresa al final (el valor por defecto es `http://localhost:8069`), o el lanzador abre una página en blanco.

**Qué significa.** El proceso del ERP no está corriendo, o se inició y luego se detuvo a causa de un error en su propio registro.

**Qué hacer.** Abre el archivo llamado `odoo.log` en la carpeta que el instalador creó (por defecto bajo tus datos de aplicación locales, en `odoo-tool-stack`). Las últimas líneas dicen por qué. Las tres causas comunes son: el servicio de la base de datos no está corriendo; la contraseña de la base de datos en la configuración ya no coincide con la base de datos; y el puerto está ocupado por otro programa. Las tres son corregibles sin reinstalar.

---

## El asistente responde, pero no encuentra el ERP

**Qué verás.** Pides "lista los clientes" y el asistente responde que no puede conectarse, o que falta la configuración.

**Qué significa.** El conector del asistente no tiene dirección, no tiene clave, o tiene una clave que el ERP ya no acepta. El conector lee su configuración del entorno o de un pequeño archivo en la carpeta de datos del asistente.

**Qué hacer.** Comprueba primero que el ERP está corriendo y alcanzable en un navegador. Luego comprueba la clave: en el ERP, abre el menú de usuario, ve a la página de seguridad de la cuenta y crea una nueva clave API. Pégala en la configuración del conector. Si cambiaste la contraseña del usuario del ERP, las claves existentes suelen sobrevivir; si eliminaste y recreaste al usuario, no.

---

## El asistente crea un cliente duplicado

**Qué verás.** Dos clientes llamados casi igual: "Ashfield Academy" y "Ashfield Academy Ltd."

**Qué significa.** Se pidió al asistente que creara un cliente y hizo lo que se le ordenó. No decide automáticamente que un nombre similar es la misma empresa, y no debería: dos ramas de la misma organización pueden legítimamente ser dos registros.

**Qué hacer.** Formula la instrucción para buscar primero—"busca el cliente Ashfield y añade un contacto"—o pide al asistente que te muestre las coincidencias antes de crear algo. Cuando aparece un duplicado, fusiona o archívalo en el ERP en lugar de eliminarlo, para que la historia de las facturas se mantenga intacta.

---

## Un documento no puede publicarse

**Qué verás.** El ERP se niega a publicar una factura, o una entrega, y muestra un mensaje sobre una cuenta faltante, un impuesto faltante, o un período que está cerrado.

**Qué significa.** El modelo es incompleto. Un producto no tiene cuenta de ingresos, o la empresa no tiene un impuesto configurado, o el período contable ha sido bloqueado.

**Qué hacer.** Lee el mensaje; nombra el campo. Corrige la configuración en los ajustes del ERP, luego publícalo de nuevo. Esto es el ERP haciendo su trabajo: se niega a escribir una entrada que Pacioli no reconocería.

---

## Todo es lento

**Qué verás.** Las pantallas tardan segundos en cargar; el asistente tarda mucho en responder.

**Qué significa.** Dos cosas distintas, usualmente confundidas. Si las pantallas del ERP son lentas, el problema es local: la base de datos, el disco, o la memoria de la máquina. Si solo el asistente es lento, el problema es el modelo de lenguaje—bien el servicio remoto, o el modelo local si corres uno.

**Qué hacer.** Mira primero la memoria y el disco de la máquina. Luego mira el registro del asistente: anota cuánto tardó cada solicitud y qué herramientas se llamaron. Una sola solicitud que tarda treinta segundos porque hizo doce llamadas de herramientas no es una falta; es una solicitud que debería haberse formulado de forma más estrecha.

---

## Has perdido la contraseña de administrador

**Qué significa.** La contraseña impresa al final de la instalación no se apuntó.

**Qué hacer.** En una instalación autohospedada tú eres el dueño de la máquina, así que puedes resetearla desde la base de datos. Detén el ERP, conéctate a la base de datos con la propia cuenta de administrador de la base de datos, y establece un nuevo hash de contraseña para el usuario administrador. El procedimiento está documentado en la propia documentación del ERP bajo "resetear la contraseña de administrador", y toma dos minutos. No elimines la base de datos para resolver un problema de contraseña.

---

## La única regla

Cualquier cosa que ocurra, conserva dos cosas: el archivo de registro, y una copia de la base de datos anterior al cambio. Con esas dos, casi cualquier problema puede diagnosticarse y la mayoría puede deshacerse. Sin ellas, cada problema se convierte en un argumento sobre lo que solía ser cierto.
