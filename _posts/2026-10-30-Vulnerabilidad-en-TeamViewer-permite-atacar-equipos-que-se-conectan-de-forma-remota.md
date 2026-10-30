---
title: "Vulnerabilidad en TeamViewer permite atacar equipos que se conectan de forma remota"
date: 2026-10-30 09:00:00
categories: [VULNERABILIDADES]
tags: [acceso remoto, seguridad informática, vulnerabilidades, ciberseguridad]
description: "Una vulnerabilidad de alta gravedad en TeamViewer permite que un equipo remoto comprometido provoque fallos o ejecute código en el dispositivo que se conecta. Se recomienda actualizar a la versión 15.83 o posterior."
image: /assets/305/preview1.png
---

TeamViewer ha corregido una vulnerabilidad que permitía que la máquina controlada en una sesión remota atacara al ordenador que se conectó para controlarla. En una sesión de TeamViewer, el ordenador que se conecta y toma el control es el visor, y la máquina que controla es el anfitrión.

Un host malicioso o comprometido puede explotar la vulnerabilidad para bloquear la aplicación TeamViewer del usuario y, según la plataforma, también puede ejecutar código en su equipo. Esto solo funciona después de que el usuario inicie una sesión de control remoto con dicho host. La solución se encuentra en la versión 15.83 de TeamViewer.

La vulnerabilidad se identifica como CVE-2026-111585 y obtuvo una puntuación de 8,8 sobre 10, lo que la sitúa en el rango alto. Afecta al cliente completo de TeamViewer para Windows, Linux y macOS, a la edición portátil para Windows y a la aplicación de control remoto para Android, en todas las versiones anteriores a la 15.83.

En cuanto a este fallo, el boletín de TeamViewer menciona el cliente completo, la aplicación portátil y la aplicación para Android, pero no el host. La misma actualización 15.83 corrige otros dos fallos mencionados en ese boletín que sí afectan al host, por lo que quienes utilicen el host también deberían actualizar.

Omri Dar, investigador de la empresa de seguridad Remedio, publicó un informe técnico sobre la vulnerabilidad el 29 de octubre. En este fallo, escribió, "el atacante es el anfitrión y la víctima es el espectador".

En una sesión remota, el anfitrión le indica al espectador el tamaño de su imagen en pantalla. El espectador utiliza ese tamaño para reservar memoria, pero el cálculo puede desbordarse y reservar muy poca. Los datos de pantalla que llegan posteriormente se escriben más allá del límite de ese espacio.

Como mínimo, esto provoca el cierre inesperado de la sesión de TeamViewer del usuario, y el anfitrión puede volver a provocar el cierre cuando quiera.

En Windows, Remedio afirma haber aprovechado aún más la vulnerabilidad, eludiendo las defensas integradas del sistema operativo contra exploits y ejecutando código de su elección en el visor. La demostración utilizó un servidor virtual en el host para proporcionar parte de los datos del ataque, por lo que aún no se trata de un ataque realizado completamente a través de la red.

Ese resultado solo se mostró en Windows. En el artículo no se especifica si funciona igual en macOS, Linux o Android. TeamViewer solo indica que la ejecución de código es posible, dependiendo de la plataforma.

El ataque no requiere contraseña ni clics adicionales más allá de aceptar la sesión, y funciona con la configuración predeterminada de TeamViewer, escribió Dar. La vulnerabilidad afecta a todas las versiones anteriores a la 15.83, incluida la 15.82, la actualización de seguridad que TeamViewer lanzó en septiembre . La actualización del mes pasado no la eliminó.

### Qué hacer

La única solución que ofrece TeamViewer es actualizar, y no incluye ninguna alternativa. Los usuarios actuales deben actualizar a la versión 15.83 o posterior. Las versiones corregidas para las ramas compatibles más antiguas se encuentran en la tabla anterior.

La misma actualización 15.83 también corrige otras dos vulnerabilidades graves descritas en el mismo boletín, incluyendo una vulnerabilidad de ejecución de código que afectaba a Linux y macOS. Un boletín complementario del mismo día, TV-2026-1012, corrige seis vulnerabilidades más en los complementos de administración remota de TeamViewer, que se distribuyen mediante actualización automática.

TeamViewer afirmó que, al publicar la solución, desconocía la existencia de ataques que explotaran la vulnerabilidad. Esta no figura en el catálogo de Vulnerabilidades Explotadas Conocidas de CISA, según su publicación del 29 de octubre. Remedio no reportó ataques activos ni publicó el código de explotación.
