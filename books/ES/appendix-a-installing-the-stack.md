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

Al final la ventana imprime algo como esto. Escríbelo, o haz una foto de la pantalla.

```
  Odoo (el ERP, en el navegador):  http://localhost:8069
  Usuario: admin@yourcompany.example
  Contraseña: (la que generó el instalador, o la que le diste)
  Asistente (háblale aquí):  http://localhost:5290/OfficeManager
```

Si la cuenta de administrador ya existía de una ejecución anterior, el instalador imprime el usuario
que realmente está en la base de datos y dice que la contraseña no ha cambiado, en lugar de inventar
una nueva que no funcionaría.

El navegador abre la **página inicial**: un archivo en esta computadora con la dirección, la cuenta y
un enlace. Esa página es el principio de la configuración, no el final de la instalación.

## Paso 7 — El icono, y las tres ventanas

Haz doble clic en el icono **AI Odoo** del escritorio. Ocurren tres cosas:

1. el ERP arranca, si no estaba en ejecución;
2. la página inicial se abre en el navegador;
3. el asistente se abre en su propia ventana negra.

*Abrir Odoo* en la página inicial lleva a la página de acceso en
`http://localhost:8069/web/login?db=odoo_agent`. El asistente es la ventana negra, y es allí donde se
escribe; hay que dejarla abierta mientras trabajas, porque cerrarla detiene el asistente, mientras
Odoo sigue funcionando.

En su primer arranque el asistente pregunta el proveedor de IA: elige el servicio, pega la clave, y
obtiene la lista de modelos de ese servicio. No hace falta nada más—la dirección del ERP y la clave
de acceso las escribió el instalador.

## Paso 8 — Comprobar que funciona

Tres comprobaciones, en orden, y cada una te dice cuál de las tres máquinas está descontenta si
falla.

1. **El ERP.** Haz clic en *Abrir Odoo* en la página inicial, o abre
   `http://localhost:8069/web/login?db=odoo_agent` en un navegador, y entra. Si la página no se
   carga, el ERP o la base de datos no están en ejecución; el archivo `odoo.log` en la carpeta de
   instalación dice por qué.
2. **El conector.** En el asistente, pregunta: *comprueba la conexión con Odoo y dime qué versión está
   en ejecución.* Un número de versión significa que la clave y la dirección son correctas.
3. **El modelo.** Pregunta: *¿cuántos clientes tenemos?* Un número significa que el asistente puede
   leer los datos del ERP como su usuario, con los permisos de ese usuario.

Si las tres responden, la instalación está completa.

## Desinstalar

Dos scripts deshacen la instalación, y son la forma admitida: `uninstall.bat` en Windows y
`uninstall.sh` en Linux. Están junto al instalador en la misma versión, y cada uno puede descargarse y
ejecutarse solo.

Qué eliminan:

- la base de datos de Odoo, con cada cliente, producto, pedido, factura y movimiento de existencias;
- la carpeta de instalación (`%LOCALAPPDATA%\odoo-tool-stack`, o `~/odoo-tool-stack`);
- los accesos directos **AI Odoo** y la regla del firewall.

Preguntan dos veces, y la segunda pregunta no es una formalidad. La primera es un sí/no que enumera
lo que desaparece. La segunda exige la frase **DESTROY ALL**, escrita en mayúsculas. Si la frase no
es exacta, no se toca nada—ni un archivo, ni una fila. El borrado es irreversible y el desinstalador
no hace ninguna copia de seguridad, así que una copia de la base tomada antes es el único camino de
vuelta.

AgentBridge se pregunta aparte, porque puede alojar otras herramientas y guarda sus propios ajustes y
claves de API: responder *no* lo conserva y quita solo la mitad Odoo.

PostgreSQL queda instalado. Es un servicio que otros programas pueden compartir, y se quita en
*Aplicaciones y características* como cualquier otro programa, cuando nada más lo necesita. El rol de
base de datos `odoo` queda y es inofensivo: una futura instalación lo reutiliza.
