---
title: "Vulnerabilidad crítica en PHP permite ejecución remota de código"
date: 2026-10-20 09:00:00
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, vulnerabilidad, servidores]
description: "Dos vulnerabilidades críticas en PHP podrían permitir la ejecución remota de código sin autenticación. Conoce los riesgos, las versiones afectadas y las medidas para proteger tus servidores."
image: /assets/302/preview1.png
---

El equipo de desarrollo de PHP ha anunciado una próxima actualización de seguridad crítica, programada para el miércoles 21 de octubre de 2026 a las 14:00 UTC. Esta actualización aborda dos vulnerabilidades críticas.

Los identificadores CVE asignados son CVE-2026-109618 y CVE-2026-109619. Los detalles técnicos completos se publicarán junto con la actualización. La información fue revelada inicialmente por el investigador de seguridad Florian Roth (@cyb3rops). Posteriormente, el equipo de seguridad de PHP publicó el anuncio oficial en php.net.

Florian también dice que "la vulnerabilidad de ejecución remota de código (RCE) en el núcleo de PHP, con una puntuación CVSS de 10.0, solo recibirá parches para PHP 8.x".

El equipo de PHP ha declarado que se reserva el derecho de lanzar la actualización antes de lo previsto si los detalles de alguna de las vulnerabilidades se hacen públicos, o si aparecen pruebas de que están siendo explotadas activamente.

# Versiones afectadas

- PHP 5.4.0 — 8.5.11 (todas las versiones que incluyen `session.upload_progress`)
- Corregido en: 8.2.35, 8.3.36, 8.4.27, 8.5.12 (publicados el 21 de octubre de 2026)
- Mitigaciones en: PHP 7.4, PHP 8.0 y PHP 8.1 (publicados el 21 de octubre de 2026)
- PHP 5.x, 7.1: fin de vida útil, sin corrección oficial

### El rumor inicial
La primera mención pública apareció en una publicación de la sección "Tell HN". El usuario petecooper citó una "fuente confiable" que afirmaba que, para el 22 de octubre de 2026 a las 18:00 CEST, estaba programado un anuncio sobre dos vulnerabilidades de ejecución remota de código (RCE) en PHP, ambas con una puntuación CVSS de 10.0. Capturas de pantalla y resúmenes de dicha publicación se difundieron rápidamente en X y Mastodon. Una publicación de collysucker, amplificó la información, señalando que las vulnerabilidades afectarían a todas las versiones de PHP desde la 5 en adelante, e identificando los identificadores CVE reservados.

### ¿Qué son CVE-2026-109618 y CVE-2026-109619?
CVE-2026-109618 y CVE-2026-109619 son vulnerabilidades de ejecución remota de código reportadas en PHP, un lenguaje de scripting utilizado para crear y ejecutar aplicaciones web y sitios web. Según un informe no verificado, la vulnerabilidad permitiría a un atacante ejecutar su propio código en un servidor que utilice PHP, lo que podría darle el control del mismo. El informe indica que el problema afecta a todas las versiones de PHP desde la 5 en adelante; sin embargo, no existe un aviso oficial del proveedor que confirme el alcance, la causa técnica o la disponibilidad de una versión corregida.

### ¿Cómo salieron a la luz CVE-2026-109618 y CVE-2026-109619?
Se filtró información en redes sociales que indicaba que, para el 22 de octubre, estaba programado un anuncio de seguridad sobre dos vulnerabilidades de ejecución remota de código en PHP. Quien publicó la información señaló que esta se basaba únicamente en la credibilidad de la fuente y que, en el momento de la publicación, no había sido confirmada de forma independiente.

### ¿Qué versiones de PHP están afectadas?
A confirmar: PHP 5, 6, 7, 8. El informe sostiene que la vulnerabilidad afecta a todas las versiones de PHP desde la 5 en adelante; no obstante, este alcance aún no ha sido confirmado mediante un aviso oficial del proveedor.

El informe disponible no menciona ningún requisito específico de configuración o funcionalidad.

### ¿Cómo puedo solucionar CVE-2026-109618 y CVE-2026-109619?
Aún no existe un aviso oficial del proveedor ni una versión corregida, por lo que, por el momento, no hay ningún parche o solución alternativa confirmada. Los equipos de seguridad deben permanecer atentos al anuncio oficial de seguridad de PHP y aplicar la versión corregida tan pronto como esté disponible.

### ¿Qué otras vulnerabilidades corrige el mismo boletín?
Según se informa, el mismo anuncio también incluye la CVE-2026-109619, una segunda vulnerabilidad de ejecución remota de código en PHP que, según el informe no verificado, afecta a todas las versiones desde PHP 5 en adelante.

### ¿Qué se puede hacer mientras tanto?
Florian ha estado trabajando en una herramienta para quienes no saben qué hacer en este momento. Process-watcher muestra todos los programas que inician tus procesos de PHP, incluyendo las líneas de comando completas, lo que permite detectar actividades sospechosas.

<img src="/assets/302/302-01.jpeg" alt="Imagen 01" style="width: 100%;">

Hasta que haya un parche disponible, el aislamiento (mediante contenedores) y una monitorización estricta son las mejores opciones para limitar los daños. Además, es seguro que los modelos de lenguaje (LLM) ya están trabajando a toda marcha y hay gente intentando reproducir la vulnerabilidad.

La explotación probablemente se manifestará a través de la creación de subprocesos sospechosos. Eso es precisamente lo que esta herramienta supervisa mediante eBPF: consiste en un único binario estático para Linux (amd64, arm64), sin dependencias, que se puede poner en marcha en cuestión de minutos. También permite finalizar procesos específicos (con una opción de prueba previa), pero cabe destacar que se trata de una capa de detección, no de un parche; además, no puede observar lo que ocurre dentro de PHP si no se llega a iniciar un proceso externo.

### Recomendamos encarecidamente a los administradores que:

- Supervisen los canales oficiales para estar al tanto del próximo boletín de seguridad de PHP.
- Se preparen para actualizar a la versión más reciente de PHP (que incluirá los parches correspondientes) tan pronto como los paquetes actualizados estén disponibles.
- No confiar en cualquier tipo de información que no llegue de canales oficiales.

## Rumor (23 hs)

<img src="/assets/302/302-02.png" alt="Imagen 02" style="width: 100%;">

Se rumorea que al menos una de las vulnerabilidades está relacionada con dos primitivas de tipo use-after-free en el heap, presentes en el gestor `session.upload_progress` de PHP.

##  Posible solucióne temporal... (8 hs)

Ante la (no sorpresiva) aparición de exploits, y para prevenir ataques mientras se publica el parche, se recomienda desactivar temporalmente estas directivas en todas las versiones de PHP (5.x a 8.x) en los archivos php.ini (global) y .user.ini (por cada sitio), la siguiente configuración:

        session.upload_progress.enabled = Off⁠
        session.upload_progress.cleanup = Off

**IMPORTANTE: se trata de una mitigación y NO resuelve el problema raíz.**

Los sitios PHP que utilizan Cloudflare ya cuentan con un conjunto inicial de reglas de WAF implementadas para hacer frente a los vectores de ataque conocidos asociados a estas vulnerabilidades. Estas reglas están disponibles para todos los clientes, incluidos los de la modalidad gratuita.

VirusTotal identifica aproximadamente 5,1 millones de direcciones IP que ejecutan PHP (port_service_cpe:php); de ellas, cerca de 3,8 millones tienen al menos un puerto abierto actualmente.

## php2shell: Prueba de concepto (PoC) de vulnerabilidad

Finalmente la vulnerabilidad ya tiene nombre, PoC y exploits: PHP2shell (y sí, ya hay "sitio oficial")

El informe del investigador describe varias vías para la ejecución de código, en lugar de un exploit universal que funcione contra cualquier sitio web basado en PHP. Una de estas cadenas combina la inyección en archivos de sesión con una vulnerabilidad de inclusión de archivos locales (LFI, por sus siglas en inglés) en una aplicación.

Según el repositorio, esta vía depende de que la función de seguimiento del progreso de carga (upload progress) esté habilitada, junto con una vulnerabilidad en la aplicación que permita la inclusión de archivos locales. Un fallo de inclusión de archivos locales ocurre cuando es posible forzar a una aplicación a cargar un archivo desde su propio servidor de una manera no prevista.

El repositorio indica que el gestor de progreso de carga de PHP almacena el nombre de archivo proporcionado en los datos de sesión sin realizar ninguna validación. Asimismo, señala que un identificador de sesión enviado en el cuerpo de una petición POST puede eludir la configuración `session.use_only_cookies`, la cual está diseñada para restringir la forma en que se aceptan los identificadores de sesión.

El repositorio de verificación del proyecto ofrece una visión general de la investigación y archivos de laboratorio; su propósito declarado es facilitar pruebas controladas, no su uso contra sistemas sin la debida autorización.

Dado que PHP sustenta una gran variedad de sitios web y aplicaciones, un fallo en su mecanismo central de gestión de sesiones podría afectar a múltiples tipos de implementaciones. El riesgo puede ser mayor cuando una aplicación ya presenta una vulnerabilidad de inclusión de archivos o un comportamiento de deserialización inseguro.

Un informe de Mallory pone de relieve la magnitud de las implementaciones de PHP obsoletas, justo cuando los administradores se preparan para las actualizaciones de seguridad que aparecerán hoy.

**Por ahora, lo más adecuado es considerar esta prueba de concepto pública como una señal para prepararse y realizar validaciones de forma segura. El siguiente paso fundamental consiste en comparar las afirmaciones de la investigación con los detalles de las versiones oficiales de PHP y, posteriormente, aplicar parches en los sistemas afectados tan pronto como el proyecto publique versiones corregidas confirmadas.**

### Parches publicados (11 hs)

Las versiones PHP 8.5.12, 8.4.27, 8.3.36 y 8.2.35 corrigen dos vulnerabilidades críticas que podrían permitir la ejecución remota de código sin necesidad de autenticación. Se recomienda encarecidamente a todos los usuarios de PHP que actualicen sus sistemas de inmediato.

### ¿Quiénes están en riesgo?

Todas las instalaciones de PHP que procesan solicitudes web, incluyendo PHP-FPM, Apache con mod_php, php-cgi, FrankenPHP y LiteSpeed. Consideramos que el riesgo es mayor en el caso de mod_php, donde existe un exploit demostrado en el que una solicitud sin autenticar puede desencadenar el ataque antes de que se ejecute cualquier código de la aplicación.

### Las vulnerabilidades
- Ejecución remota de código (RCE) mediante corrupción por falta de memoria (OOM), CVE-2026-109618 (GHSA-w8hw-w9fx-j79w): el manejo de situaciones de falta de memoria puede interrumpir PHP mientras los datos internos de la solicitud solo están parcialmente inicializados. Posteriormente, el proceso de limpieza de la solicitud podría interpretar estos datos no válidos como válidos.
- Ejecución remota de código (RCE) mediante estado global obsoleto, CVE-2026-109619 (GHSA-6wmf-4rv5-p3rp): un estado interno asociado a una solicitud puede persistir incluso después de que la memoria que lo albergaba haya sido liberada. Una solicitud posterior, gestionada por el mismo proceso de trabajo (worker), podría utilizar este estado obsoleto antes de que la inicialización estándar lo restablezca.

## PHP <8.2

PHP 8.1 y versiones anteriores ya no reciben actualizaciones por parte del proyecto PHP. Algunas distribuciones y proveedores de versiones LTS ofrecen correcciones adaptadas. Dada la gravedad de estas vulnerabilidades, el equipo de seguridad de PHP ha proporcionado backports mínimos del código fuente para PHP 7.4, PHP 8.0 y PHP 8.1, destinados a quienes compilan desde el código fuente o no tienen acceso a un proveedor que ofrezca soporte a largo plazo (LTS).

Si no puede actualizar de inmediato: aunque solo una actualización constituye una solución completa, las siguientes medidas reducen la exposición a vectores de ataque específicos, si bien no garantizan la seguridad de la instalación.

### Ejecución remota de código (RCE) mediante corrupción por falta de memoria (OOM) (CVE-2026-109618):

- Establecer `memory_limit=-1`, preferiblemente de una forma que las aplicaciones no puedan sobrescribir —por ejemplo, mediante `php_admin_value` en el pool de FPM o en la configuración de Apache— y asegúrese de que ninguna configuración de pool, directorio o aplicación restablezca un límite finito. Esto elimina el fallo provocado por el límite de memoria de PHP, aunque un fallo de asignación subyacente aún podría alcanzar la ruta vulnerable.
- Establecer un valor bajo para `post_max_size`. Para aplicaciones que no requieran la carga de archivos, configure `post_max_size = 8M`. Si es necesario permitir la carga de archivos, establezca `post_max_size = 32M`.
- Asegurar que `upload_max_filesize` sea siempre inferior a `post_max_size`. Considere aplicar límites a nivel de servidor web o proxy para parámetros como el tamaño de la solicitud decodificada, el número de campos de entrada, la cantidad de partes en una solicitud multipart, el número de encabezados y la profundidad de anidamiento. Estos límites deben aplicarse también a las solicitudes que carezcan de un encabezado `Content-Length` válido.
- Utilizar un contenedor o un límite de `cgroup` como medida de control de disponibilidad; lo ideal es aplicar una política que finalice únicamente el worker afectado. No utilizar `RLIMIT_AS` ni `RLIMIT_DATA`, ya que pueden provocar el mismo fallo de asignación que hace vulnerable al sistema.

## Ejecución remota de código (RCE) mediante estado global obsoleto (CVE-2026-109619):

- Establecer `session.upload_progress.enabled=0` y reiniciar todos los procesos. Realizar este cambio en `php.ini`, en el pool de FPM o en la configuración del servidor, de modo que se aplique antes del procesamiento de la solicitud. No depender de `ini_set()` ni de archivos `.user.ini` de FPM. Esto bloquea las rutas de sesión confirmadas, pero no otras variantes.
- En PHP 8.5, establece `fatal_error_backtraces=0` y reiniciar todos los procesos trabajadores. Esto bloquea únicamente la ruta confirmada de los backtraces en caso de error fatal.
- Eliminar las configuraciones no válidas u obsoletas aplicadas por solicitud que generen mensajes de diagnóstico antes de la inicialización. Ocultar dichos mensajes mediante `error_reporting`, `display_errors` o el operador `@` no resulta eficaz.
- Corrigir los errores fatales y los tiempos de espera de ejecución (timeouts) a los que pueda acceder un atacante; esto incluye fallos en callbacks, procesos de carga o importación de archivos, y tareas de limpieza.

### Parches para versiones 5.x y 7.2.x
Sury.org (de Ondřej Surý) acaba de publicar una protección contra PHP2Shell en todas las ramas de PHP para Debian/Ubuntu, desde la versión 5.6 en adelante. Para muchos que aún utilizan versiones antiguas de PHP, las actualizaciones (backports) de hoy podrían ahorrarles una migración. Desde esta tarde, el repositorio de Debian y Ubuntu de Ondřej Surý incluye un backport de protección contra PHP2Shell en todas las ramas, llegando incluso hasta PHP 5.6.

Esto le da un giro completo al habitual mensaje de "actualízate o muere". Ya no es necesario eliminar una instalación de PHP con una década de antigüedad para sobrevivir a esta vulnerabilidad en particular.

Sury se ha asegurado de que todas las ramas que mantiene incluyan la protección necesaria frente a ellas. Cuatro de estas ramas incorporan la corrección de forma nativa, al haber sido reconstruidas a partir de la versión original (upstream). Las otras siete ya han llegado al final de su vida útil; por ello, sury.org ha aplicado la corrección en los paquetes que mantiene. En cualquier caso, el resultado es el mismo: un sistema vulnerable que utiliza PHP 5.6 ya no representa una presa fácil para un atacante.

El modelo de Sury es "sencillo". Para una rama que ya no recibe soporte oficial, toma su última versión publicada por los desarrolladores originales —aquella que ya incluye todas las correcciones de seguridad que PHP lanzó para dicha rama— y la reempaqueta continuamente para adaptarla a las bibliotecas del sistema, garantizando así que siga siendo instalable. El contador de revisión "-N" indica simplemente cuántas veces se ha reempaquetado una rama; en el caso de PHP 5.6, se han acumulado 104 revisiones.

Ahora, esa lista incluye la corrección para PHP2Shell. Por tanto, si utilizas PHP 5.6.40 o 7.2.34, ya no tienes por qué alarmarte: obtienes protección sin necesidad de reescribir tu código.

**IMPORTANTE:** Dicho esto, OJO, estas versiones tienen parches retroactivos que son anteriores a la publicación de este CVE por parte de los desarrolladores originales; por tanto, **se trata de una adaptación deliberada realizada por terceros, no de un parche oficial del proyecto original.** Vale la pena dedicar cinco minutos a leer el registro de cambios del paquete antes de implementarlo, ya que un backport podría modificar el comportamiento del software de forma inesperada, por ejemplo, desactivando alguna funcionalidad de la que dependas.

*Noticia en desarrollo...*
