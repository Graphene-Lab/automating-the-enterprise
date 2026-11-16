# 8. Qué pasó mientras la barra avanzaba

La instalación tardó cuarenta minutos, la mayor parte de los cuales se dedicó a mirar una pantalla que no cambiaba.

Este capítulo es lo que pasó durante esos cuarenta minutos, explicado para alguien que nunca tendrá que hacerlo a mano pero que merece saber qué es lo que ahora se ejecuta en la máquina—porque un sistema que no comprendes es un sistema que no puedes confiar, y un sistema que no puedes confiar es un sistema que abandonarás en marzo.

Hay cinco cosas que explicar: la base de datos, el entorno de Python, el ERP, el conector y el asistente. Viven en una carpeta, y conocer esa carpeta es conocer la instalación.

---

## La carpeta

Todo lo que crea el instalador va a un mismo lugar:

```
%LOCALAPPDATA%\odoo-tool-stack
```

En una máquina Windows típica eso es `C:\Users\<tu>\AppData\Local\odoo-tool-stack`. Dentro, cuatro subcarpetas, una por componente, más los archivos de registro. Nada está disperso por el disco, ningún archivo se coloca en `Windows`, y nada se registra salvo el servicio de la base de datos y dos accesos directos.

Es una decisión de diseño deliberada y tiene una consecuencia práctica enorme: **desinstalar es eliminar una carpeta.** Una empresa que prueba el sistema en enero y lo abandona en febrero no deja un fósil en la máquina para los próximos cinco años. Elimina un directorio y desinstala la base de datos.

Los datos propios del usuario—la configuración del asistente, sus conversaciones, la configuración del conector—viven por separado, en `%LOCALAPPDATA%\agent`, de modo que actualizar o reinstalar la pila no los destruya.

## La base de datos

PostgreSQL se instala de la forma en que PostgreSQL está destinado a instalarse en Windows: como un servicio, con un directorio de datos propio, escuchando en un puerto. El servicio significa que arranca con la máquina y corre sin que nadie inicie sesión; el directorio de datos significa que la memoria de la empresa es un conjunto de archivos en un lugar conocido, que es lo que hace posible una copia de seguridad.

El instalador eligió el puerto. Quería el 5432, lo encontró ocupado por la base de datos dentro del Subsistema de Windows para Linux, y tomó el 5433. Luego hizo tres cosas que una persona de otro modo tendría que hacer a mano:

1. Creó un usuario de base de datos llamado `odoo`, con una contraseña, de modo que el ERP nunca se conecte como superusuario. Esta es la diferencia entre darle a la contable la llave de la oficina y darle la llave maestra del edificio.
2. Creó una base de datos llamada `odoo`, de propiedad de ese usuario.
3. Escribió el puerto y las credenciales en el archivo de configuración del ERP.

La contraseña del superusuario es `odoo` a menos que la persona instaladora haya elegido otra, y el instalador la imprime en el resumen. Es una cuenta local. No tiene nada que ver con ninguna cuenta de internet, y es la contraseña que necesitarás si alguna vez tienes que restaurar una copia de seguridad a mano.

## El entorno de Python

Odoo está escrito en Python, y los programas en Python necesitan bibliotecas. El instalador crea un entorno aislado—una *entorno virtual*—dentro de la carpeta de la pila, e instala en él exactamente las bibliotecas que Odoo necesita, en las versiones que Odoo espera.

La palabra "aislado" está haciendo un trabajo real aquí. Sin él, instalar Odoo cambiaría el Python que usan otros programas en la máquina, y un día algo sin relación dejaría de funcionar. Con él, la pila lleva su propio Python y no puede romper nada fuera de su carpeta.

Si la máquina no tuviera ningún Python útil en absoluto, el instalador instaló uno primero—y lo comprobó ejecutándolo, no buscándolo, porque en una máquina Windows moderna el comando `python` suele ser un anuncio de la Microsoft Store en lugar de un programa.

## El ERP

Odoo en sí es una carpeta de fuente en Python y un gran conjunto de módulos. El instalador descargó la versión que se instalaba, creó el esquema de la base de datos, y cargó los módulos base—los que proporcionan el modelo de una empresa: socios, productos, documentos, el libro mayor, la interfaz web.

Este es el paso que más tarda y que más se parece a que no pase nada. Se está construyendo una base de datos: cientos de tablas, miles de reglas, la tabla de cuentas de una empresa genérica, los impuestos de un país genérico, los menús de un usuario genérico. Cuando termina, el ERP es un programa funcional que sabe cómo ser una empresa pero que aún no sabe qué empresa es. Para eso sirve la página de primeros pasos.

## El conector

El conector es el pequeño programa que traduce entre el asistente y el ERP. Se instala como un plugin—una carpeta de archivos que el asistente carga al arrancarse—y se configura con dos datos: la dirección del ERP (`http://localhost:8069`) y una clave.

La clave se genera durante la instalación y se escribe en la configuración del conector. Es una clave de API de Odoo: una credencial que pertenece a un usuario, que puede revocarse sin cambiar la contraseña de ese usuario, y que lleva los permisos de ese usuario. Cuando el asistente pide a Odoo que cree una factura, es esa clave la que viaja con la solicitud, y Odoo la comprueba tal como comprobaría el inicio de sesión de una persona.

Esta es la parte de la arquitectura sobre la que el auditor de una empresa hará preguntas, y la respuesta es tranquilizadora: el asistente es un *usuario*. Aparece en la lista de usuarios del ERP. Tiene un rol. Cada registro que crea lleva estampado su nombre. Se puede desactivar con un clic, y la pista de auditoría seguirá mostrando qué hizo.

## El asistente

El asistente llega como una publicación pública: un ejecutable, una carpeta de herramientas, y el cliente de chat de escritorio. El instalador lo descomprime, instala el conector en él, y crea el acceso directo **AI Odoo**.

El acceso directo es la pieza que hace que el sistema se sienta como un producto en lugar de un proyecto de ciencias. Al hacer doble clic en él se arranca el ERP si no está corriendo, se abre la página del ERP en el navegador, y se abre el asistente en una ventana de terminal. Un ícono, tres ventanas, y el trabajo puede comenzar.

La propia configuración del asistente—qué proveedor de IA, qué modelo, qué clave—se pregunta en su primer arranque, por el propio asistente, en la misma ventana de terminal donde escribirás tus instrucciones. Ese es un buen lugar para preguntar, porque es el único lugar donde la clave puede realmente probarse: el asistente obtiene la lista de modelos del proveedor con la clave que pegaste, y si la lista vuelve, la clave funciona.

---

## Lo que podría haber salido mal

Todo lo anterior funcionó en el segundo intento. Vale la pena listar lo que salió mal en el primero, porque cada elemento es un punto donde una empresa que instale esto de verdad perderá una tarde, y cada uno se resolció en lugar de documentarse como un problema conocido.

**La descarga que empezaba de nuevo.** Descrita en el capítulo anterior: el instalador eliminaba su descarga parcial antes de cada reintento, de modo que una línea lenta significaba tres fracasos en lugar de un éxito lento. Se resolvió conservando el archivo parcial, nombrándolo según su versión, y reanudándolo.

**Una lista de versiones que se vuelve obsoleta.** El instalador conocía los nombres de archivo de tres versiones recientes de PostgreSQL. El fabricante había publicado una cuarta, que no estaba en la lista. Un lector que instale dentro de seis meses se habría topado con una lista de archivos que ya no existen. Se resolvió añadiendo la versión actual y haciendo que el mensaje de falla diga exactamente qué archivo descargar a mano.

**El mensaje del gestor de paquetes en el idioma de la máquina.** Cuando `winget` falla, explica por qué en el idioma de Windows. El instalador repetía los últimos doscientos caracteres de esa explicación, y en una consola cuya página de códigos no es UTF-8 las letras acentuadas llegaban como basura—así que la pantalla mostraba un fragmento de italiano, destrozado, en medio de una instalación en inglés. Se resolvió dos veces: la consola ahora está configurada en UTF-8, y el instalador ya no repite en absoluto el texto del gestor de paquetes. El código de salida es el hecho; la línea siguiente dice qué ocurre en su lugar.

**El silencio durante la instalación de la base de datos.** El propio instalador de la base de datos corre sin salida, así que la pantalla se queda quieta durante varios minutos. Este no se resuelve, porque la resolución sería inventar una barra de progreso que miente. Se documenta en su lugar, aquí y en el apéndice: si la pantalla no ha cambiado durante cinco minutos, mira la carpeta `C:\Program Files\PostgreSQL`—si está creciendo, la instalación está funcionando.

Ninguno de estos es dramático. Juntos son la diferencia entre un procedimiento que una no técnica puede completar en una conexión mala y uno que termina con un ticket de soporte.

---

## Los dos archivos que vale la pena entender

Dentro de la carpeta del conector hay dos archivos pequeños, y son la única configuración que es probable que una empresa toque.

**`odoo.json`** contiene la dirección del ERP, el nombre de la base de datos y la clave. Son cuatro líneas de texto. Si el ERP pasa a otro puerto, este es el archivo que cambia; si la clave se revoca, este es el archivo que recibe la nueva.

**`toolset.json`** contiene la lista de herramientas que el asistente tiene permitido usar. Este es el archivo que decide si el asistente puede tocar un archivo, navegar por internet, o solo hablar con el ERP. Es la configuración de seguridad más importante de toda la instalación, y es una línea de texto.

La primera semana de Riverton produjo una lección sobre ese segundo archivo que vale la pena contar, porque es el tipo de cosa que ningún manual prevé.

El instalador había habilitado cuatro herramientas: el conector del ERP, una herramienta de archivos, una herramienta web y una herramienta de control de versiones. Es un valor por defecto razonable para un asistente de propósito general. Pero la primera instrucción que dio la empresa—*crear un cliente llamado Ashfield Academy, Mill Lane, Ashfield*—fue respondida por el asistente yendo a buscar la dirección en internet, porque había una herramienta web disponible y una dirección es algo que se busca.

No estaba equivocado, exactamente. Era inútil, era lento, y usaba una herramienta que la empresa no había considerado. La resolución tomó una línea: la herramienta se recortó al conector y a la herramienta de archivos, y el asistente dejó de navegar y empezó a preguntar al ERP.

Eso es una decisión de diseño que toda empresa tiene que tomar, y el valor por defecto debe ser el estrecho. Un asistente con una herramienta que no necesita es un asistente que eventualmente la usará, en el peor momento posible, por una razón que pareció sensata a un modelo de lenguaje.

Hay una mejor respuesta que recortar la lista, aunque, y es la que este libro recomienda.

Un modelo de lenguaje elige una herramienta leyendo qué dice la herramienta de que sirve. Si el conector del ERP se describe como *consultar y gestionar datos del ERP Odoo* y nada más, entonces una instrucción que contiene las palabras "cliente" y "dirección" es una coincidencia justa para una búsqueda web—una dirección es, después de todo, algo que se busca. El modelo no está siendo tonto; está siendo literal sobre dos descripciones igual de plausibles.

La resolución es una sola frase en la propia descripción de la herramienta, en el lugar que el modelo realmente lee: *esta herramienta es el sistema de registro de la empresa: para cualquier pregunta o acción sobre clientes, proveedores, productos, precios, ventas, compras, facturas, pagos o existencias, usa estos métodos en lugar de una búsqueda web, un archivo o conocimiento general; busca primero aquí un registro con nombre, y dilo cuando no esté aquí.*

Esa frase se añadió, las cuatro herramientas se volvieron a habilitar, y la conducta cambió: la misma instalación, con la herramienta de archivos, la herramienta web y la herramienta de control de versiones todas habilitadas, ahora responde "cuántos clientes tenemos" desde el ERP, en un segundo, con el criterio que usó y los registros detrás del número.

Dos lecciones, y apuntan en direcciones opuestas.

**Para la empresa:** no resuelves un problema de enrutamiento quitando herramientas. Una oficina real necesita la web, los archivos y el ERP a la vez; un asistente que ha sido mutilado para comportarse es un asistente que fracasará el día que el trabajo necesite la herramienta que quitaste.

**Para quien escribe la herramienta:** la descripción es la interfaz. Se lee por el modelo en cada turno, no cuesta nada, y una sola frase sobre *cuándo usar esto y cuándo no* vale más que cualquier cantidad de ingeniería de instrucciones en la orden. Las reglas que importan pertenecen al resumen de la herramienta, en líneas imperativas cortas—no en un manual, y no en un comentario que el modelo nunca ve.

## La forma de la cosa

Cuando el instalador terminó, Riverton tenía cinco programas donde antes tenía un archivador.

Una base de datos, que recuerda. Un ERP, que sabe qué significan los datos. Un entorno de Python, que ejecuta el ERP. Un conector, que traduce. Un asistente, que actúa. Y una carpeta, que contiene todo y que puede eliminarse.

Maggie escribió la ruta de la carpeta en la hoja de papel, debajo de la contraseña, y la miró por un momento. Era una sensación extraña, haber reemplazado treinta y un años de papel por un directorio en su perfil de usuario—como si la memoria de la empresa se hubiera convertido en algo que podía copiarse a un dispositivo de memoria en cuarenta minutos.

De hecho, podía copiarse a un dispositivo de memoria en cuarenta minutos. Eso es lo que es una copia de seguridad, y es el tema de una conversación que tendría con Sam tres semanas después, tras el primer susto.

Pero antes de las copias de seguridad, antes de las facturas, antes de cualquiera de los trabajos, había una página en el navegador que preguntaba qué moneda usaba la empresa.

---

## El primer susto, y qué es realmente una copia de seguridad

El susto llegó un jueves, tres semanas después, y no era un fallo del sistema.

Maggie había preguntado al asistente una pregunta—cuánto habíamos facturado el mes pasado?—y la respuesta era menor de lo que esperaba. No equivocada, exactamente: menor. Comprobó la lista de facturas, y había menos facturas de las que recordaba aprobar.

La causa, cuando Sam lo encontró, era inocente: Doreen había estado experimentando con un filtro en la lista de facturas, y el filtro se había quedado activado. El asistente respondió a la pregunta que se le hizo, contra la lista que se le dio, y la lista estaba filtrada. Nada se había eliminado. Nada se había perdido.

Pero durante veinte minutos, Maggie creyó que tres semanas de facturación habían desaparecido, y la sensación de esos veinte minutos es de lo que trata esta sección. Porque la segunda pregunta que hizo, antes de preguntar nada a Sam, fue: *¿tenemos una copia de seguridad?*

La respuesta, ese día, era: en realidad no. Había una copia de la carpeta del día de la instalación, hecha por el propio instalador, y nada desde entonces.

Qué es una copia de seguridad, en un sistema como este, son tres cosas y no una.

**La base de datos.** Un volcado de todo lo que sabe el ERP, tomado con la propia herramienta de la base de datos, según un horario. Es un único archivo, puede restaurarse en una instalación vacía, y es la única copia que importa para el libro mayor.

**La carpeta.** La fuente del ERP, la configuración, la configuración del asistente, la clave del conector. Pequeña, y tediosa de recrear a mano, que es exactamente por lo que vale la pena copiarla.

**La comprobación.** Una vez al mes, restaurar la copia de seguridad en una instalación de pruebas y mirarla. Una copia de seguridad que nunca se ha restaurado es un archivo con un nombre esperanzador. La regla de Sam—*una copia de seguridad no verificada es un deseo*—vino de haber observado a una empresa descubrir, en el peor momento posible, que su trabajo nocturno había estado escribiendo en un disco que estaba lleno.

Las herramientas para las tres están en la carpeta de la pila: un script que volca la base de datos, una carpeta para copiar, y un documento con las cuatro comandos para restaurar. La versión de Riverton corre a las dos de la mañana, conserva treinta días, y escribe en una carpeta que OneDrive sincroniza. Le tomó a Sam una hora configurarla y es, con diferencia, el seguro más barato que la empresa ha comprado nunca.
