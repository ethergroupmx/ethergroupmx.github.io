---
title: "Los hackers explotan el plugin Post SMTP de WordPress para secuestrar cuentas de administrador"
date: 2025-11-04 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, news, tecnología, web, vulnerabilidad]
description: Los ciberdelincuentes están explotando activamente una vulnerabilidad crítica en el plugin Post SMTP instalado en más de 400.000 sitios de WordPress, para tomar el control total secuestrando cuentas de administrador.
image: /assets/186/preview1.png
---

El problema, identificado como CVE-2025-11833, recibió una puntuación de gravedad crítica de 9,8 y afecta a todas las versiones de Post SMTP desde la 3.6.0 en adelante. Post SMTP es una popular solución de envío de correo electrónico que se comercializa como una alternativa más completa y fiable a la función predeterminada "wp_mail()".

El 11 de octubre, la empresa de seguridad de WordPress, Wordfence, recibió un informe del investigador "netranger" sobre un problema de divulgación de registros de correo electrónico que podría aprovecharse para ataques de suplantación de identidad.

La vulnerabilidad se debe a la falta de comprobaciones de autorización en la función "_construct" del flujo "PostmanEmailLogs" del plugin. Ese constructor muestra directamente el contenido de los correos electrónicos registrados cuando se solicita, sin realizar comprobaciones de capacidades, lo que permite a atacantes no autenticados leer correos electrónicos registrados arbitrarios.

![Imagen 01](/assets/186/186-01.png)

La vulnerabilidad incluye mensajes de restablecimiento de contraseña con enlaces que permiten cambiar la contraseña de administrador sin necesidad de un titular legítimo, lo que podría resultar en la toma de control de la cuenta y la vulneración total del sitio web.

Wordfence validó la vulnerabilidad descrita por el investigador el 15 de octubre y la comunicó al proveedor, Saad Iqbal, ese mismo día. El 29 de octubre se lanzó un parche con la versión 3.6.1 de Post SMTP. Según datos de WordPress.org, aproximadamente la mitad de los usuarios del plugin lo han descargado desde el lanzamiento del parche, dejando al menos 210 000 sitios web vulnerables a ataques de toma de control de administrador.

Según Wordfence, los atacantes comenzaron a explotar la vulnerabilidad CVE-2025-11833 el 1 de noviembre. Desde entonces, la empresa de seguridad ha bloqueado más de 4.500 intentos de explotación en sus clientes.

Dado el estado activo de la explotación, se recomienda a los propietarios de sitios web que utilizan Post SMTP que actualicen a la versión 3.6.1 de inmediato o que desactiven el plugin.

En julio, PatchStack reveló que Post SMTP era vulnerable a una falla que permitía acceder a los registros de correo electrónico con el contenido completo de los mensajes, incluso a nivel de suscriptor. Esta falla, identificada como CVE-2025-24000, tenía las mismas repercusiones que CVE-2025-11833, permitiendo a usuarios no autorizados restablecer contraseñas, interceptar mensajes y tomar el control de cuentas de administrador.
