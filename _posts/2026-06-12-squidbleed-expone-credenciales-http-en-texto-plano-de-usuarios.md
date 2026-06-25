---
title: "Squidbleed (CVE-2026-47729): expone credenciales HTTP en texto plano de usuarios"
date: 2026-06-12 11:00:00
categories: [VULNERABILIDAD]
tags: [ciberseguridad, vulnerabilidad, ciberataque, hacking, redes, servidores, linux, seguridadweb, tecnología, news]
description: Una vulnerabilidad en Squid Proxy podría exponer credenciales, cookies y datos sensibles de otros usuarios que comparten el mismo proxy. El fallo, presente desde 1997, afecta principalmente entornos empresariales y educativos. Se recomienda actualizar Squid y deshabilitar FTP si no es necesario.
image: /assets/266/preview1.png
---

Una sobrelectura de la pila en el proxy web Squid puede filtrar la solicitud HTTP en texto plano de otro usuario, incluyendo cualquier credencial o token de sesión que contenga, a cualquier persona que ya tenga permiso para enviar tráfico a través del mismo proxy.

El fallo se remonta a un cambio en el análisis FTP de 1997 y aún persiste en la configuración predeterminada de Squid. Investigadores de Calif.io lo revelaron en junio y lo denominaron Squidbleed (CVE-2026-47729), en referencia a Heartbleed, que filtraba memoria de la misma manera.

**Squid describe esto como un ataque por parte de un cliente de confianza: alguien que ya tiene permiso para usar el proxy, no cualquier host aleatorio en internet.** Esto coincide con el entorno habitual de Squid: redes compartidas como escuelas, oficinas y redes Wi-Fi públicas. En estos entornos, el atacante es simplemente otro usuario del mismo proxy.

Además, la filtración solo afecta al tráfico que Squid puede leer. El HTTPS normal utiliza un túnel CONNECT opaco, por lo que Squid nunca ve su contenido. El tráfico expuesto es HTTP en texto plano, además de configuraciones con terminación TLS donde Squid descifra e inspecciona.

El atacante también necesita el proxy para acceder a un servidor FTP que controla en el puerto 21. Tanto FTP como ese puerto están activados por defecto.

El fallo reside en el analizador de listados de directorios FTP de Squid. La demostración de Calif extrae una cabecera de autorización de una víctima que comparte el mismo proxy, suficiente para actuar como ese usuario. El código de prueba de concepto es público y, hasta la fecha, no se ha informado de ninguna explotación en la práctica.

### Qué hacer

Si aplicas un parche, verifica la corrección, no solo la versión. Confirma que la protección se encuentra en FtpGateway.cc o consulta la versión anterior de tu distribución, ya que las distribuciones incluyen sus propias compilaciones (Debian incluye Squid 5.7).

El hilo público sigue siendo inconsistente: el mantenedor Amos Jeffries primero dijo que Squid 7.6 incluía la corrección, luego lo corrigió a 7.7, y el 22 de junio Salvatore Bonaccorso de Debian señaló que la confirmación a la que se hace referencia parece estar ya en 7.6.

La solución es sencilla: una comprobación del terminador nulo antes de las llamadas vulnerables a `strchr`, integrada en la rama de desarrollo en abril y en la versión 7 en mayo. Squid 7.6 corrige por separado la vulnerabilidad CVE-2026-50012, un desbordamiento de búfer en el montón de `cache_digest` sin relación con esta.

La solución más eficaz es la que recomiendan los investigadores: desactivar FTP. Chromium dejó de usar FTP hace años, y la mayoría de las redes apenas lo utilizan, por lo que deshabilitarlo elimina esta vulnerabilidad automáticamente, independientemente de la compilación que se utilice.




