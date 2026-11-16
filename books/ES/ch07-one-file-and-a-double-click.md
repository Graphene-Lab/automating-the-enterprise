# 7. Un archivo y un doble clic

El escritorio auxiliar de Riverton daba a una ventana que miraba al patio donde cargaban las furgonetas.
Maggie lo había preparado ella misma, es decir, que había movido cuatro cajas de catálogos al
suelo y había limpiado el escritorio con un trapo que no estaba del todo limpio. Sobre él colocó un
portátil, una taza y una hoja de papel con tres líneas escritas en él.

Sam Okafor miró la hoja de papel.

"—¿Eso es todo?"

"—Eso es todo."

Las tres líneas eran: *nombre de la empresa, correo de administración, contraseña de administración*. Todo lo demás, ella había decidido, la máquina podía resolverlo por sí misma.

---

Antes del doble clic, hay cuatro cosas que una empresa debe comprobar, y ninguna de ellas es
técnica.

**Un ordenador que no esté haciendo otra cosa.** La pila ejecuta tres programas a la vez—la
base de datos, el ERP y el asistente—y en un portátil ocupado competirán con cualquier otra cosa
abierta. Riverton usó una máquina que se había comprado para la tienda web y que nunca se usó para
ello. Ocho gigabytes de memoria son suficientes; dieciséis son holgados; el disco necesita unos
doce gigabytes libres antes de que el instalador comience, y lo comprueba.

**Una conexión a internet, una sola vez.** El instalador descarga las partes que necesita. A partir
de entonces, el sistema funciona sin conexión, salvo el modelo de lenguaje, que es un servicio en
otro edificio (o en otra máquina propia, si se prefiere).

**Permiso para instalar.** En Windows el motor de la base de datos instala un servicio, y eso necesita
derechos de administrador. Si la cuenta que se usa no los tiene, el instalador lo dice al final en
lugar de fallar en silencio, y una segunda ejecución con la cuenta adecuada termina el trabajo.

**Un nombre de empresa.** No necesariamente el nombre legal—el nombre que quieres ver en la parte
superior de tus facturas. Riverton usó "Riverton Office Supply", que es como la llaman sus clientes.

Esa es la lista entera. No hay que inventar una contraseña de base de datos, no hay que elegir un
puerto, no hay que editar un archivo de configuración. El instalador asigna él mismo la contraseña de
superusuario de la base de datos, la imprime al final, y elige un puerto libre si el estándar está
ocupado. Se pide el proveedor de IA más tarde, por parte del asistente, en su primer arranque—donde
una clave de verdad puede contrastarse contra el servicio que la emitió.

---

El archivo se llama `install.bat`, y es uno de los pocos ideas genuinamente buenas en la historia
de la distribución de software empresarial: un único archivo de texto, lo suficientemente pequeño
como para por correo electrónico, que sabe cómo obtener todo lo demás.

Maggie hizo doble clic en él. Se abrió una ventana negra, con una barra de título que decía *OdooTool installer*,
y lo primero que hizo fue hacer una pregunta.

No una pregunta técnica. Imprimió cuatro encabezados—*Preguntas*, *Espacio libre*, *Comprobando
PostgreSQL, Python y Git*—y bajo *Preguntas* listó lo que se iba a preguntar. En una ejecución sin
intervención no había nada que escribir, porque las tres respuestas estaban en el entorno; en una
ejecución normal habría pedido el nombre de la empresa y nada más.

Hay una decisión de diseño oculta en ese orden, y vale la pena observarla porque es la diferencia
entre un instalador en el que confía la gente y uno que abandonan. Los encabezados vienen *antes* del
trabajo: el instalador te dice qué se va a preguntar, luego qué ha encontrado, luego qué se va a
hacer. Nada se descubre a medias, cuando ya es tarde para cambiar de opinión. Una persona que lee la
primera pantalla conoce la forma de los próximos cuarenta minutos.

La ventana en sí es deliberadamente sencilla—texto blanco sobre negro, sin barras de progreso, sin
logotipo, sin animación. Eso no es pereza. Una ventana de consola que imprime una línea por evento
real es una ventana cuya salida puede ser *leída*, copiada en un correo electrónico, y comparada con
la ejecución de otra persona. Los instaladores que ocultan su salida tras un círculo giratorio son
los que no se pueden diagnosticar cuando se detienen.

El tercer encabezado produjo dos líneas que vale la pena entender, porque son el tipo de cosas que
hacen pensar a la gente que un ordenador está roto.

```
! El puerto TCP 5432 ya está en uso en este PC; el nuevo PostgreSQL escuchará en 5433 en su lugar.
PostgreSQL no está instalado. Se instala ahora con la contraseña de superusuario 'postgres' establecida como 'odoo'.
```

La primera línea no es un error. Es un informe de algo ordinario: otro programa en la
máquina—en este caso una base de datos dentro del Subsistema de Windows para Linux, reenviado al lado
de Windows por un pequeño auxiliar llamado `wslrelay`—ya estaba usando el puerto estándar de
PostgreSQL. Los puertos son puertas numeradas, y solo un programa puede escuchar detrás de cada
puerta. El instalador buscó la primera puerta libre después de 5432, encontró la 5433, y decidió
usarla para todo: la base de datos, el ERP y el lanzador. Nadie tiene que recordar el número; el
instalador lo escribe donde necesita ser escrito.

La segunda línea es el instalador diciendo lo que está a punto de hacer, y—esta es la parte que importa
a una pequeña empresa—que va a elegir la contraseña de la base de datos por sí misma. La contraseña es
`odoo`, es una cuenta local en este PC, y no tiene nada que ver con ninguna cuenta en el
internet. El instalador la imprime al final para que el dueño de la máquina pueda encontrarla más tarde.

---

Luego comenzó la espera, y la espera es donde este capítulo gana su lugar en el libro,
porque el primer intento falló.

El instalador probó primero el gestor de paquetes de Windows, que es la forma educada de instalar software
en Windows. El gestor de paquetes no pudo alcanzar su fuente—una red corporativa, una red de hotel o un
producto de antivirus harán ese trabajo—y devolvió un error. El instalador lo dijo, en una línea, y
recurrió a descargar el instalador oficial de la base de datos directamente. Esa es la conducta correcta,
y por eso lo siguiente en la pantalla fue una descarga.

La descarga era lenta. No "un poco lenta": sixty kilobytes por segundo, en una línea que había sido
medida en cuatrocientos. El instalador de la base de datos tiene trescientos ochenta y seis megabytes, lo que
a esa velocidad es una hora y tres cuartos, y la conexión se cortó tres veces antes de que el archivo
estuviera completo. Cada corte reinició la transferencia desde cero, porque eso es lo que hacía el código en
ese momento, y después del tercer intento el instalador se rindió e imprimió la frase que manda a la gente
a un foro de soporte:

> No se pudo descargar PostgreSQL (winget y la descarga directa fallaron). Instálalo tú mismo desde enterprisedb.com y vuelve a ejecutar este instalador.

Este es el primer fallo genuino de este libro, y vale la pena ser preciso sobre qué era lo que estaba mal,
porque no era la red.

El instalador ya usaba `curl`, que puede reanudar una transferencia parcial. Pero borraba el archivo
parcial antes de cada intento, así que el reanudado no tenía nada que reanudar. En una conexión rápida nadie
notaría nunca nada. En una lenta, convirtió una descarga de treinta minutos en tres fracasos de media hora.

La solución son tres líneas de pensamiento y una docena de líneas de código: mantener el archivo
parcial, nombrarlo según la versión a la que pertenece para que nunca pueda confundirse con otro, y pedirle a `curl` que continúe desde donde se detuvo (`-C -`). Un archivo que ya tiene el tamaño correcto se reutiliza sin una
transferencia en absoluto, y un archivo que es *más grande* que el tamaño declarado se descarta, porque
no puede ser un prefijo del real.

Con ese cambio, la segunda ejecución del instalador imprimió una sola línea y siguió adelante:

```
==> reutilizando la descarga verificada de 16.16-1
```

Esa línea es toda la diferencia entre un producto y un prototipo. La primera versión le pedía al
usuario resolver un problema de red. La segunda versión lo resolvía y lo decía en siete palabras.

Mientras la base de datos se instalaba—trescientos noventa megabytes que desempacar, lo que toma unas cuantas
minutos en un disco normal—el instalador no imprimió nada, porque no había nada que imprimir. Estaba
esperando a que terminara el propio instalador de la base de datos, y el instalador de la base de datos es
silencioso por diseño. Una barra de progreso habría sido más agradable. El silencio, al menos, era honesto.

---

La base de datos terminó. El instalador comprobó que podía alcanzarla, con la contraseña que había
asignado, e imprimió una línea para decirlo. Luego se volvió hacia Python.

Python es el lenguaje en el que está escrito Odoo, y el enfoque del instalador hacia él es el enfoque de un
buen compañero de trabajo: si ya hay una versión utilizable presente, úsala; si no, instálala. En Windows esto
es más delicado de lo que suena, porque el comando `python` en una máquina moderna a menudo no es
Python en absoluto sino un anuncio de la Tienda de Microsoft—un pequeño adaptador que abre la Tienda cuando escribes
`python`. Un instalador que confía en el comando no instalará nada y luego fallará misteriosamente
más tarde. Este lo ejecuta y comprueba la respuesta, que es la única prueba fiable.

Luego obtuvo a Odoo en sí—una copia del fuente de la versión que se instala—y los paquetes de Python que
necesita, y creó la base de datos, y cargó los módulos base. Cada uno de esos pasos imprime una línea, y cada línea es una pequeña pieza de tranquilidad: *esto sigue adelante, y va en la dirección correcta.*

El último paso fue el asistente: descargar la versión pública, desempacarla, instalar el conector que
le permite hablar con el ERP, escribir la dirección del ERP y una clave recién generada en la
configuración del conector, y arrancar el ERP.

Luego la ventana imprimió un resumen. Vale la pena citarlo, porque es la única parte de la
instalación que un usuario debe conservar.

```
==> Hecho

Odoo:          http://localhost:8069
Administrador: admin@riverton.example
Contraseña:      OdooDemo2026
Base de datos:      odoo en el puerto 5433
Asistente:     AI Odoo (ícono de escritorio)
```

Tres de esas líneas son las que Maggie escribió en la hoja de papel y puso en el cajón con la servilleta: la dirección, el usuario, la contraseña. La cuarta es el puerto, que ella no necesitaba saber, y la quinta es el ícono en el que haría doble clic cada mañana durante el próximo año.

## Lo que el instalador no hará

Vale la pena decir claramente qué deja el script para ti, porque una empresa que espera que el
instalador produzca un negocio funcional será desilusionada en una hora.

No **elegirá tu plan de cuentas**, más allá de instalar el que usa tu país. Las cuentas que tu empresa
necesita realmente—transporte cobrado, transporte pagado, las dos o tres gastos que
importan—son una conversación con tu contable.

No **introducirás tus productos, clientes o existencias**. Esos son los hechos de tu negocio, y nadie más los tiene.

No **decidirá quién puede hacer qué**. Crea el administrador y el usuario del asistente; el resto es un juicio sobre tu gente.

No **configurará el proveedor de IA por ti** más allá de escribir la dirección y la clave que le diste
con antelación; en una ejecución normal, el asistente pregunta en su primer arranque.

Y no **hará copias de seguridad de tus datos**, porque en el momento en que se ejecuta no hay datos que
copiar. Esa es la primera cosa que configurar después, y el capítulo ocho explica cómo.

El trabajo del instalador es estrecho y lo hace bien: pone las tres máquinas en la habitación, las
cablea juntas, e imprime las tres cosas que necesitas para iniciar sesión. Todo lo demás es el trabajo de este libro.

---

Hay una pequeña pieza de teatro al final que es fácil de pasar por alto y que te dice algo sobre
las personas que escribieron el instalador. Habiendo terminado, abre la página de primeros pasos del
ERP en el navegador. No el asistente, no una página de marketing: la página donde se le pregunta a una nueva empresa qué moneda usa, cómo debería ser su plan de cuentas, y qué vende.

El mensaje es: no has terminado, acabas de llegar. La próxima hora es de configuración, y es la hora que decide si el sistema se convierte en la verdad o se convierte en otro programa abandonado. El instalador no puede hacer esa parte por ti, y no finge hacerlo.

Maggie se sentó frente a la página de primeros pasos durante un largo momento. Luego llamó a Doreen, porque el plan de cuentas se iba a convertir en un argumento, y era mejor tener el argumento con la persona que había llevado las contabilidad durante treinta y un años que tenerlo con un consultor.

Esa conversación es el próximo capítulo.
