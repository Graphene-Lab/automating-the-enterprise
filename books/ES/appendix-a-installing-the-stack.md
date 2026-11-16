# Apéndice A — Instalar el stack, paso a paso

Este apéndice es la instalación sin la historia: el mismo procedimiento que el capítulo siete, escrito
como una lista que puedes seguir con el libro cerrado. Asume Windows 10 u 11; el procedimiento para Linux
es el mismo script con un nombre distinto, y el instalador está diseñado para comportarse idénticamente.

## Antes de empezar

| Requisito | Por qué | Cómo comprobarlo |
|---|---|---|
| Windows 10 u 11, de 64 bits | el motor de base de datos y el asistente son programas de Windows | Configuración → Sistema → Acerca de |
| Aproximadamente 12 GB de disco libre | base de datos, fuente del ERP, paquetes de Python, asistente | Explorador de archivos → Este PC |
| Una cuenta de administrador | la base de datos instala un servicio de Windows | el instalador lo dice al final si no se dispone del adecuado |
| Una conexión a internet | las partes se descargan una sola vez | cualquier navegador |
| Un nombre de empresa | aparece en tus documentos | decídelo ahora |

No necesitas: una contraseña de base de datos, un número de puerto, .NET, Git, Docker, una instalación de
Python ni ningún conocimiento de la línea de comandos.

## Paso 1 — Conseguir el instalador

Descarga `install.bat` desde la página de versiones de OdooTool y colócalo en una carpeta vacía, por ejemplo
`C:\Users\<tú>\Downloads\odoo-install\`.

El archivo pesa unos pocos kilobytes. Descarga el resto de sí mismo si es necesario, por lo que funciona
incluso cuando llega solo.

## Paso 2 — Ejecutarlo

Haz doble clic en `install.bat`. Se abre una ventana de consola con el título *Instalador de OdooTool*.

Si Windows pide permiso para realizar cambios, permítel: la base de datos necesita registrar un servicio.

## Paso 3 — Responder las preguntas

En una ejecución normal el instalador pregunta por el **nombre de la empresa** y acepta el valor predeterminado
sugerido para todo lo demás pulsando Intro. En una ejecución no atendidas las respuestas pueden darse con
antelación mediante variables de entorno, y el instalador no pregunta nada en absoluto.

El instalador imprime un encabezado llamado *Preguntas* con las respuestas que va a usar, para que puedas
ver qué ha decidido antes de empezar a trabajar.

## Paso 4 — Vigilar las cuatro etapas

La pantalla imprime un encabezado por etapa. Cada encabezado va seguido de líneas que indican qué está
ocurriendo; no hay que escribir nada.

1. **Espacio libre.** Se niega a empezar por debajo de doce gigabytes.
2. **Comprobación de PostgreSQL, Python y Git.** Informa de lo que encuentra y de lo que va a instalar.
3. **Instalación.** La parte larga: la base de datos, el entorno de Python si es necesario, la fuente del ERP,
   los paquetes de Python, la base de datos en sí, el asistente, el conector.
4. **Resumen.** Direcciones, credenciales y lo que falta, si algo falta.

Dos mensajes durante la etapa 2 son normales y no son errores:

- *El puerto TCP 5432 ya está en uso; el nuevo PostgreSQL escuchará en 5433 en su lugar.* Otra cosa en la
  máquina ocupa el puerto estándar. El instalador elige el siguiente libre y lo usa en todas partes.
- *PostgreSQL no está instalado. Se instala ahora con la contraseña del superusuario 'postgres' establecida en
  'odoo'.* La contraseña la asigna el instalador, es local de esta PC y se imprime al final. No hay que
  recordarla ni buscarla.

## Paso 5 — Si la descarga es lenta

El instalador de la base de datos pesa unos 390 MB y procede del propio sitio del fabricante. En una línea
lenta la descarga puede tardar una hora o fallar. El instalador conserva el archivo parcial y lo reanuda en
la próxima ejecución, por lo que **volver a ejecutarlo es la respuesta correcta**: continúa por donde se detuvo
y reutiliza lo que ya está ahí.

Si la máquina no puede acceder al fabricante en absoluto, descarga tú mismo el instalador de PostgreSQL 16 para
Windows desde enterprisedb.com, déjalo en la carpeta que el instalador indica y vuelve a ejecutar `install.bat`.
Lo encontrará y comprobará su tamaño antes de usarlo.

## Paso 6 — Conservar el resumen

Al final la ventana imprime algo como esto. Escríbelo o fotografía la pantalla.

```
Odoo:          http://localhost:8069
Administrador: admin@yourcompany.example
Contraseña:      (la que generó el instalador, o la que le diste)
Base de datos:   odoo en el puerto 5433
Asistente:       AI Odoo (ícono de escritorio)
```

El navegador abre la página de primeros pasos del ERP. Esa página es el inicio de la configuración, no el fin
de la instalación.

## Paso 7 — Primer arranque del asistente

Haz doble clic en el ícono **AI Odoo** del escritorio. Ocurren dos cosas: el ERP se inicia (si no estaba
ejecutándose) y el asistente se abre en su propia ventana de terminal. El navegador abre la página del ERP.

En su primer arranque el asistente pregunta por el proveedor de IA: elige el servicio, pega la clave y este
recoge la lista de modelos de dicho servicio. No se necesita nada más—la dirección del ERP y la clave de acceso
las escribió el instalador.

## Paso 8 — Comprobar que funciona

Tres comprobaciones, en orden, y cada una te dice cuál de las tres máquinas está malcontenta si falla.

1. **El ERP.** Abre `http://localhost:8069` en un navegador y inicia sesión. Si la página no carga, el ERP o
   la base de datos no están ejecutándose; el archivo `odoo.log` en la carpeta de instalación dice por qué.
2. **El conector.** En el asistente, pregunta: *comprueba la conexión a Odoo y dime qué versión está
   ejecutándose.* Un número de versión significa que la clave y la dirección son correctas.
3. **El modelo.** Pregunta: *¿cuántos clientes tenemos?* Un número significa que el asistente puede leer los
   datos del ERP como su usuario, con los permisos de ese usuario.

Si las tres responden, la instalación está completa.

## Desinstalar

El stack vive en una sola carpeta, `%LOCALAPPDATA%\odoo-tool-stack`, más el servicio de base de datos y los
datos de usuario en `%LOCALAPPDATA%\agent`. Para eliminarlo:

1. Detén el ERP y el asistente (cierra sus ventanas).
2. Desinstala PostgreSQL desde *Aplicaciones y características* (o ejecuta su desinstalador) y elimina la carpeta
   que deja en `C:\Program Files\PostgreSQL` si queda algo.
3. Elimina `%LOCALAPPDATA%\odoo-tool-stack` y `%LOCALAPPDATA%\agent`.
4. Elimina el acceso directo **AI Odoo** del escritorio y del menú Inicio.

Eso es todo el proceso de eliminación. No se registra nada en ningún otro lugar, lo que es una de las ventajas
de un sistema que se ejecuta en tu propia máquina.
