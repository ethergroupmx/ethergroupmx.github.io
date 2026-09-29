---
title: "Microsoft SharePoint Server: vulnerabilidad crítica es explotada activamente"
date: 2026-09-29 09:00:00
categories: [VULNERABILIDAD]
tags: [vulnerabilidad, ciberseguridad, seguridad informática]
description: "Una vulnerabilidad de ejecución remota de código en Microsoft SharePoint Server está siendo explotada activamente. Conoce los sistemas afectados y la importancia de aplicar las actualizaciones de seguridad."
image: /assets/295/preview1.png
---

Una vulnerabilidad de Microsoft SharePoint Server (local), identificada como CVE-2026-65660, está siendo explotada actualmente en ataques, aproximadamente seis semanas después de que Microsoft anunciara los parches y un par de días después de que investigadores revelaran detalles técnicos.

La CVE-2026-65660 es una vulnerabilidad de ejecución remota de código que Microsoft corrigió con las actualizaciones del "Patch Tuesday" de agosto de 2026. El boletín de seguridad de la compañía la describe como un problema de inyección de código que permite a un atacante autenticado, con acceso de bajo nivel a un servidor afectado, ejecutar código arbitrario sin necesidad de interacción del usuario. "A fecha del 25 de septiembre de 2026, Microsoft disponía de pruebas fiables de ataques observados que explotaban esta vulnerabilidad", declaró Microsoft en su boletín actualizado.

Previdian (anteriormente KEVIntel), una plataforma de inteligencia de amenazas y alerta temprana, informó haber detectado intentos de explotación el 24 de septiembre. El 25 de septiembre, la empresa observó intentos de crear una puerta trasera tipo webshell.

No está claro quién está detrás de los ataques, que parecen haber comenzado poco después de que Viettel Security, cuyos investigadores notificaron la vulnerabilidad a Microsoft, revelara los detalles técnicos.
Viettel señaló que Microsoft clasificó inicialmente la vulnerabilidad como un problema de suplantación de identidad (spoofing) de gravedad media, pero posteriormente revisó su evaluación para calificarla como un fallo de ejecución remota de código de alta gravedad.

Microsoft clasifica la CVE-2026-65660 como una vulnerabilidad que requiere autenticación; exige privilegios de bajo nivel, pero no precisa interacción del usuario. Por sí misma, la vulnerabilidad consiste en eludir la comprobación de tipos, lo que permite la ejecución de código a un atacante autenticado; para lograr la ejecución remota de código (RCE) sin autenticación, es necesario encadenarla con otra vulnerabilidad distinta que permita saltarse la autenticación.

<img src="/assets/295/295-01.png" alt="Conferencias" style="width: 80%;">

Previdian observó que los intentos de explotación detectados en entornos reales parecían basarse en la información técnica compartida por Viettel.

CISA añadió la CVE-2026-65660 a su catálogo de vulnerabilidades explotadas conocidas (KEV) el 25 de septiembre, estableciendo el 28 de septiembre como fecha límite para que las agencias federales aplicaran el parche. El catálogo KEV de la CISA incluye actualmente 16 vulnerabilidades de SharePoint, incluidas ocho descubiertas y corregidas este año.

