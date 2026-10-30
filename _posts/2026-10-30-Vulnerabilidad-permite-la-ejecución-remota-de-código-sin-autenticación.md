---
title: "Vulnerabilidad permite la ejecución remota de código sin autenticación"
date: 2026-10-29 09:00:00
categories: [VULNERABILIDADES]
tags: [ciberseguridad, vulnerabilidad, seguridad informática]
description: "Una vulnerabilidad de seguridad podría permitir a los atacantes ejecutar código de forma remota sin autenticación. Conoce los riesgos y las medidas de protección recomendadas."
image: /assets/308/preview1.png
---

Anthropic ha publicado un artículo en donde describe su modelo de investigación interno, para detectar vulnerabilidades críticas en algunas aplicaciones más utilizados a nivel mundial, como navegadores y sistemas operativos.

En su publicación, comparten detalles sobre cinco cadenas de ataque que permitieron la ejecución remota de código y otros impactos críticos, requiriendo poca o ninguna interacción por parte del usuario. Estas cadenas de ataque demuestran la capacidad del modelo para generar exploits sofisticados de varias etapas, tanto en software de código abierto como en software propietario.

Cualquier vulnerabilidad en estos productos (Linux, Chrome, Safari, Android y Windows) podría afectar a miles de millones de usuarios. Además, al tratarse de algunos de los programas más críticos para la seguridad a escala global, sirven como un excelente indicador para evaluar la eficacia de los modelos en la investigación de vulnerabilidades y sus capacidades en el ámbito de la ciberseguridad.

Como se ha notificado cada vulnerabilidad a los proveedores afectados, siguiendo el protocolo de divulgación coordinada; este proceso otorga a los desarrolladores un plazo de 90 días para aplicar parches, seguido de un periodo adicional de 45 días antes de que se divulgue detalles más allá de los ya incluidos en el aviso público correspondiente.

Con la ayuda de Claude, los investigadores también descubrieron vulnerabilidades de escalamiento de privilegios local en OpenBSD y FreeBSD; varios casos de escape de entornos aislados (sandboxes) en infraestructuras populares; y numerosas vulnerabilidades en aplicaciones web importantes.

Entre vulnerabilidades descriptas y que permiten la ejecución remota de código arbitrario sin necesidad de interacción del usuario (zero-click) se encuentra un error en la pila de red del kernel de Linux. Las vulnerabilidades ya han sido corregidas en la rama principal (upstream) y divulgadas públicamente.

Tras recibir las instrucciones iniciales, Claude generó un exploit que permite a un atacante remoto enviar paquetes a servidores Linux que cuenten con un listener de TCP multipath, logrando así ejecutar comandos arbitrarios con privilegios de root, sin necesidad de credenciales ni de interacción por parte del usuario. La vulnerabilidad subyacente es un error de tipo "use-after-free" (UAF) —uso de memoria tras su liberación— provocado por una condición de carrera en la pila de red del núcleo. El proceso de explotación consta de dos etapas clave:

En la primera etapa, el atacante elude de forma remota el mecanismo KASLR (aleatorización del espacio de direcciones del núcleo). Para ello, aprovecha la condición de carrera y logra que el núcleo lea un campo de longitud controlado por el atacante, lo que provoca la copia de bytes adicionales que son enviados de vuelta al atacante. Si una de estas lecturas excesivas incluye un puntero del núcleo, el atacante obtiene información sobre la distribución del espacio de direcciones del mismo.

En la segunda etapa, el atacante secuestra el flujo de control. Utiliza el mismo error UAF para desbordar un búfer y sobrescribir un puntero de callback (llamada de retorno) con la dirección del payload que el atacante ha preparado previamente en la memoria del núcleo mediante una funcionalidad estándar del protocolo. Cuando el núcleo invoca dicho callback, la carga útil desencadena una serie de llamadas a funciones existentes en el núcleo, culminando en la ejecución de un comando de consola (shell) elegido por el atacante con privilegios de root.

Una característica que facilita esta condición de carrera es que, si el atacante pierde la "carrera", el único resultado es el fallo del handshake sin provocar el bloqueo o colapso de todo el sistema; por tanto, un atacante persistente puede reintentar la operación indefinidamente hasta lograr su objetivo. En la prueba de concepto de Anthropic, el proceso requirió 48 minutos para filtrar un puntero del núcleo y otros cinco minutos adicionales para llegar a la ejecución del comando en la consola.

### Distros está afectadas

Esta vulnerabilidad, identificada como CVE-2026-98432 y corregida el 15 de octubre en la rama principal y aplicada también a todas las ramas estables del núcleo que reciben mantenimiento, ha generado controversia porque Ubuntu (22.04 y posteriores), la ha catalogado con un CVSS de 9,8 porque el protocolo MPTCP está activo por defecto en esta distribución.

En cambio Amazon (CVSS 7), Oracle (8,1), Red Hat y Debian y otras distribuciones solo le dan un score de 5.9 porque puede generar un DoS y es de difícil explotación tal y como han probado los investigadores.

Si no es posible actualizar inmediatamente, se recomienda desactivar MPTCP:

        sudo sysctl -w net.ipv4.tcp_migrate_req=0
        sudo sysctl -w net.mptcp.enabled=0
        sysctl en /etc/sysctl.d/ #no se necesario reboot.

Impacto:

MPTCP solo afecta a aplicaciones que crean sockets MPTCP explícitamente y casi ninguna usa IPPROTO_MPTCP por defecto.
