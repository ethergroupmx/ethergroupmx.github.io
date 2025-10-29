---
title: "Microsoft caído — Múltiples servicios sufren daños"
date: 2025-10-29 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, news, tecnología, web]
description: Aproximadamente a las 9 de la mañana, hora del Pacífico, varios servicios de Microsoft dejaron de funcionar simultáneamente, incluyendo la plataforma en la nube Azure, Microsoft 365, Xbox y otros.
image: /assets/182/preview1.png
---

Se observaron picos de casi 10 000 reportes en [DownDetector](https://downdetector.mx/), el sitio web que monitorea interrupciones de servicio, en varias plataformas de Microsoft. Actualmente, estos picos han comenzado a disminuir en Microsoft Azure, Microsoft Teams y Microsoft 365.

Según la página de estado de Azure, la interrupción se debió a problemas relacionados con DNS, aunque no se ha precisado si se trató de un ataque externo o de un error interno. Microsoft informó que su equipo está trabajando para revertir el servicio a una versión anterior y restaurar la normalidad.

Entre los servicios afectados se encuentran Starbucks.com y otros que dependen de la infraestructura de Azure. Al mismo tiempo, Amazon Web Services (AWS) también presenta inconvenientes, lo que genera preocupaciones sobre la disponibilidad de una gran parte de internet si ambas plataformas presentan fallas simultáneas.

### Declaración de Microsoft

> "Estamos trabajando para solucionar un problema que afecta a Azure Front Door y que repercute en la disponibilidad de algunos servicios. Los clientes deben seguir consultando sus alertas de estado del servicio; la última actualización sobre este problema se puede encontrar en la [página de estado de Azure](https://azure.status.microsoft/en-us/status)."

![Imagen 01](/assets/182/182-01.png)

### Servicios de Microsoft afectados

Estos son los servicios propiedad de Microsoft que hemos visto hasta ahora que presentan problemas. Estamos seguros de que hay más empresas que utilizan Azure, como Starbucks, pero esto es lo que hemos visto aumentar específicamente en este momento.

- Microsoft 365 (incluyendo el portal de administración y conectividad a servicios de productividad)
- Microsoft Azure (la plataforma en sí misma, incluyendo el portal de gestión)
- Minecraft (reportes indican que los usuarios experimentaron fallos)
- Xbox / Xbox Live (problemas de acceso reportados)
- Microsoft Copilot (aparecen en reportes como servicio con reportes de fallo)

![Imagen 01](/assets/182/182-02.png)

### Actualización

Según la página de estado de Azure, el equipo de Microsoft ha implementado su solución, que debería estar lista en unos 30 minutos.

> "Hemos iniciado el despliegue de nuestra última configuración operativa conocida. Se prevé que esté completamente desplegada en unos 30 minutos, momento en el que los clientes comenzarán a observar los primeros indicios de recuperación. Una vez finalizado este proceso, la siguiente fase consistirá en recuperar los nodos mientras redirigimos el tráfico a través de estos nodos operativos."

> "Los cambios en la configuración de los clientes permanecerán bloqueados durante este período mientras trabajamos para mitigar el problema. Les comunicaremos a los clientes cuando se levante este bloqueo."
