---
title: "Un investigador detalla la cadena de ataques de WhatsApp a host utilizando tres vulnerabilidades de OpenClaw"
date: 2026-07-10 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [IA, vulnerabilidades, malware, ciberseguridad]
description: Tres vulnerabilidades ya corregidas en el asistente de IA OpenClaw podrían haber permitido el robo de credenciales, la escalada de privilegios y la ejecución de código en los sistemas afectados. Actualizar a la versión más reciente es esencial para mitigar estos riesgos.
image: /assets/273/preview1.png
---

A continuación se presenta una breve descripción de las vulnerabilidades de alta gravedad:

- **GHSA-hjr6-g723-hmfm** (puntuación CVSS: 8.8) - Una vulnerabilidad de inyección de comandos del sistema operativo y una lista incompleta de entradas no permitidas que afecta al mecanismo de filtrado del entorno de ejecución del host y que podría permitir la ejecución o persistencia de acciones más allá de la autorización prevista por quien realiza la llamada.
- **GHSA-9969-8g9h-rxwm** (puntuación CVSS: 8.8) - Una vulnerabilidad de inyección de comandos del sistema operativo y una lista incompleta de entradas no permitidas que afecta al mecanismo de filtrado del entorno de ejecución del host y que podría permitir la ejecución o persistencia de acciones más allá de la autorización prevista por quien realiza la llamada.
- **GHSA-575v-8hfq-m3mc** (puntuación CVSS: 8,4): una vulnerabilidad de recorrido de ruta y seguimiento de enlaces que podría permitir que los montajes de enlace de sandbox eludan las comprobaciones de la lista de denegación del directorio padre y realicen acciones que deberían haber estado protegidas con comprobaciones de autorización o políticas más estrictas.

Las tres deficiencias se han solucionado en la versión 2026.6.6 de OpenClaw.

![Imagen 01](/assets/273/273-01.jpg)

En una serie de comunicados publicados la semana pasada, los responsables del mantenimiento de OpenClaw afirmaron que "el impacto práctico depende de la configuración del operador y de si la información de menor confianza puede llegar a esa ruta".

Sin embargo, el investigador de seguridad Chinmohan Nayak, a quien se le atribuye el descubrimiento y la denuncia de estos problemas, afirmó en un informe compartido con The Hacker News que pueden utilizarse para activar la ejecución de código del sistema desde un mensaje externo enviado a través de WhatsApp.

![Imagen 02](/assets/273/273-02.jpg)

A diferencia de las vulnerabilidades de Claw Chain reveladas por Cyera en mayo, los fallos recientemente identificados no requieren que un atacante establezca un punto de acceso previo para extraer datos confidenciales, instalar una puerta trasera persistente, obtener la ejecución remota de código arbitrario y facilitar el acceso al sistema anfitrión.

"La función **getBlockedReasonForSourcePath()** comprueba si la ruta de origen se encuentra dentro de una ruta bloqueada", explicó el investigador sobre GHSA-575v-8hfq-m3mc. "Pero nunca comprueba lo contrario: si una ruta bloqueada se encuentra dentro de la ruta de origen (omisión del directorio padre)".

En concreto, la lista de bloqueo de montaje de enlace bloquea directorios como "~/.ssh", "~/.aws" y "~/.gnupg", pero permite montar el directorio padre "/home" o "/var", lo que en la práctica anula los bloqueos individuales.

"Si montas /home en tu contenedor, puedes leer las claves SSH, las credenciales de AWS y los secretos GPG de todos los usuarios", dijo Nayak. "Si montas /var, obtienes el socket de Docker, lo que significa una fuga completa del host desde dentro del 'sandbox'".

Además de actualizar OpenClaw a la última versión, se recomienda habilitar el modo sandbox para todas las sesiones que no sean la principal, eliminar "exec" de la lista de herramientas permitidas para los agentes que interactúan con el canal y supervisar los comandos git clone que contengan el auxiliar de protocolo externo "ext::", que podría utilizarse indebidamente para ejecutar comandos del sistema arbitrarios.

«Antes de actualizar, restrinja la función afectada a operadores de confianza o desactívela cuando no sea necesaria», indicó OpenClaw. «Como medida general de seguridad, mantenga las listas de canales y herramientas permitidas reducidas, evite compartir una puerta de enlace entre usuarios que no confían entre sí y desactive la función afectada cuando no sea necesaria».



