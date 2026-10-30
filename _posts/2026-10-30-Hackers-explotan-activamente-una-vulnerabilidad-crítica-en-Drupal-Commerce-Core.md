---
title: "Hackers explotan activamente una vulnerabilidad crítica en Drupal Commerce Core"
date: 2026-10-30 09:00:00
categories: [VULNERABILIDADES]
tags: [ciberseguridad, control de acceso, explotación activa, vulnerabilidades]
description: "Ciberdelincuentes explotan una vulnerabilidad crítica en Drupal Commerce Core que permite eludir controles de autorización y acceder a funciones o datos protegidos. Se recomienda actualizar a las versiones corregidas."
image: /assets/306/preview1.png
---

Drupal ha advertido que agentes maliciosos están explotando una vulnerabilidad de seguridad "altamente crítica" en su componente Commerce Core.

La vulnerabilidad, identificada como CVE-2026-118539 (puntuación CVSS: N/A), es un caso de autorización faltante que afecta a las versiones de Commerce Core desde la 0.0.0 hasta la 2.41 y desde la 3.0.0 hasta la 3.3.13.

"Este módulo le permite vender bienes y servicios a los clientes a través de un carrito de compras y un formulario de pago incluidos, o a través de aplicaciones independientes mediante API", indicó Drupal en un comunicado.

"El módulo no protege suficientemente ciertas rutas y campos de entidad, lo que provoca una vulnerabilidad de acceso que puede tener un impacto financiero en el proveedor."

El marco de gestión de contenido de código abierto reconoció que la vulnerabilidad está siendo "explotada activamente en la práctica", pero no proporcionó detalles sobre la naturaleza de la actividad ni el alcance de la campaña.

Se recomienda a los usuarios que actualicen a la última versión.

- Versión 3.x - Actualización a Commerce Core 3.3.13
- Versiones anteriores: Actualice a Commerce Core 8.x-2.41.

Drupal ha reconocido a los investigadores Dan Puccetti (dpuccetti), Marcus Johansson (marcus_johansson) y Robert Snyder (rsnyd) por haber informado sobre el fallo.

Este desarrollo se produce en un momento en que dos vulnerabilidades críticas en PHP, identificadas como CVE-2026-109618 y CVE-2026-109619 (puntuaciones CVSS: 9,2), y denominadas colectivamente PHP2Shell , están siendo objeto de intentos de explotación activos.

Según datos de Wiz, empresa propiedad de Google, a fecha de 25 de octubre, el porcentaje de organizaciones afectadas significativamente por PHP2Shell ha disminuido al 52,1%.

La empresa de seguridad en la nube afirmó haber observado hasta el momento dos tipos de actividades, incluidos intentos de utilizar el mecanismo de explotación PHP2Shell que coinciden con las pruebas de concepto (PoC) públicas.

La otra categoría se refiere a "herramientas de la marca PHP2Shell no relacionadas con las vulnerabilidades que, en cambio, se basaban en el envenenamiento de sesiones y una vulnerabilidad de inclusión de archivos locales (LFI) separada en la aplicación", dijeron los investigadores de Wiz Yaara Shriki, Shahar Dorfman, Alma Blachsan y Yaron Samuel .

Nuestras observaciones demuestran que provocar el agotamiento de la memoria por sí solo no basta para completar la cadena de explotación. Las diferencias en las compilaciones de PHP, los límites de memoria y el comportamiento de los procesos de trabajo pueden impedir que las etapas posteriores funcionen. El reto para los atacantes oportunistas reside en convertir las pruebas de concepto públicas disponibles actualmente en herramientas operativas igualmente fiables o desarrollarlas por su cuenta.

