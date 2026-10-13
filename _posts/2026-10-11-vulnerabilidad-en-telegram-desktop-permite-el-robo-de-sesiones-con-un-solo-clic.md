---
title: "Vulnerabilidad en Telegram Desktop permite el robo de sesiones con un solo clic"
date: 2026-10-11 09:00:00
categories: [CIBERSEGURIDA]
tags: [ciberseguridad, vulnerabilidad, phishing]
description: "Una vulnerabilidad en Telegram Desktop permitía a atacantes robar sesiones mediante un enlace malicioso. Conoce el riesgo y cómo proteger tu cuenta."
image: /assets/300/preview1.png
---

El 3 de octubre de 2026, el investigador de seguridad beaksec publicó un informe técnico que describe una vulnerabilidad de toma de control de cuenta mediante un solo clic en Telegram Desktop; dicho informe se actualizó el 7 de octubre.

La vulnerabilidad, identificada como CVE-2026-107181 es una neutralización inadecuada de delimitadores de registro. Telegram Desktop gestiona los enlaces abiertos desde fuera de la aplicación enviándolos a la instancia que ya se está ejecutando a través de un canal local de instancia única; dicho canal no escapaba correctamente el carácter separador de registros. Por consiguiente, un enlace manipulado podía inyectar un comando adicional.

Telegram solucionó el problema el 16 de septiembre de 2026 y publicó Telegram Desktop 7.2.9 el 17 de septiembre de 2026.

Según el informe, ese comando llegaba a un componente auxiliar interno heredado (utilizado originalmente para la publicación de versiones) que lee un archivo local y lo envía a un chat sin realizar ninguna comprobación de autorización ni solicitar confirmación.

El resultado es la lectura y exfiltración arbitraria de archivos locales hacia un chat controlado por el atacante. Dado que entre los archivos que pueden extraerse se incluyen los datos de sesión local de Telegram, el investigador demuestra que esto conduce a la toma de control de la cuenta cuando el usuario no ha establecido un código de acceso local.

Las versiones de Telegram Desktop anteriores a la 7.2.9 están afectadas. El investigador afirma que el problema persiste hasta la versión 7.2.8 y confirmó la cadena de ataque en Windows, probando la versión 6.9.3. El CVE afecta únicamente a Telegram Desktop y los enlaces en los que se hace clic dentro de la propia aplicación de Telegram se procesan internamente y no se ven afectados.

El ataque requiere hacer clic en un enlace abierto fuera de Telegram (por ejemplo, en un navegador web), el cual podría mostrar un aviso de confirmación antes de iniciar la aplicación de escritorio. La cadena de ataque del investigador también depende de dos configuraciones predeterminadas: la descarga automática de archivos en grupos y la posibilidad de que cualquier persona añada al usuario a un grupo. 

<img src="/assets/300/300-01.png" alt="Imagen 01" style="width: 50%;">

La corrección elimina el componente auxiliar heredado (*legacy helper*), escapa el separador IPC y añade medidas de seguridad adicionales cuando llegan diferentes tipos de registros a través de la misma conexión.

El informe detallado incluye una prueba de concepto paso a paso. Afirma que existe una cadena de ataque de un solo clic que permite la lectura arbitraria de archivos locales y la toma de control de la cuenta de Telegram en Windows.

