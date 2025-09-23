---
title: "EDR-Freeze: herramienta para congelar el AV/EDR para siempre"
date: 2025-09-23 09:00:00 
categories: [CIBERATAQUES]
tags: [tools, hacking, malware]
description: Se ha desarrollado una nueva herramienta de prueba de concepto llamada EDR-Freeze, capaz de suspender los sistemas de Detección y Respuesta de Endpoints (EDR) y las soluciones antivirus.
image: /assets/170/preview1.png
---

Según Zero Salarium, la técnica aprovecha una función integrada de Windows, ofreciendo una alternativa más discreta a los cada vez más populares ataques de "Traiga su propio controlador vulnerable" (BYOVD), utilizados por los actores de amenazas para desactivar el software de seguridad.

A diferencia de los métodos BYOVD, que requieren la introducción de un controlador vulnerable en el sistema objetivo, EDR-Freeze explota componentes legítimos del sistema operativo Windows.

Este enfoque evita la necesidad de instalar controladores de terceros, lo que reduce el riesgo de inestabilidad y detección del sistema. Todo el proceso se ejecuta desde código en modo usuario, lo que lo convierte en una forma sutil y eficaz de neutralizar temporalmente la monitorización de seguridad.

### El exploit MiniDumpWriteDump

El núcleo de la técnica EDR-Freeze reside en la manipulación de la función MiniDumpWriteDump. Esta función, parte de la biblioteca DbgHelp de Windows, está diseñada para crear un minivolcado, una instantánea de la memoria de un proceso para fines de depuración.

Para garantizar una instantánea consistente e intacta, la función suspende todos los subprocesos del proceso de destino mientras se crea el volcado. Normalmente, esta suspensión es breve. Sin embargo, el desarrollador de EDR-Freeze ideó un método para prolongar este estado de suspensión indefinidamente.

Los principales desafíos fueron dos: extender el breve tiempo de ejecución de la función MiniDumpWriteDump y eludir la función de seguridad Protected Process Light (PPL), que protege los procesos de EDR y antivirus contra manipulaciones.

Para superar la protección de PPL, la técnica utiliza WerFaultSecure.exe, un componente del servicio Informe de errores de Windows (WER) y que puede ejecutarse con protección de nivel WinTCB, uno de los niveles de privilegio más altos, lo que le permite interactuar con procesos protegidos.

Al configurar los parámetros correctos, se puede indicar a WerFaultSecure.exe que inicie la función MiniDumpWriteDump en cualquier proceso objetivo, incluidos los agentes de EDR y antivirus protegidos.

La última pieza del rompecabezas es un ataque de condición de carrera que convierte una suspensión momentánea en una congelación prolongada. El ataque se desarrolla en una secuencia rápida y precisa:

- *WerFaultSecure.exe* se ejecuta con parámetros que le indican que cree un volcado de memoria del proceso de EDR o antivirus objetivo. La herramienta EDR-Freeze monitoriza continuamente el proceso objetivo.
- En el momento en que el proceso objetivo entra en estado suspendido (mientras *MiniDumpWriteDump* comienza a funcionar), la herramienta EDR-Freeze suspende inmediatamente el proceso *WerFaultSecure.exe.*
- Dado que *WerFaultSecure.exe* está suspendido, nunca podrá completar la operación de volcado de memoria y, fundamentalmente, nunca podrá reanudar los subprocesos del proceso EDR objetivo.

**Como resultado, el software de seguridad queda en un estado de suspensión permanente, prácticamente bloqueado, hasta que finalice el proceso WerFaultSecure.exe.**

![Imagen 01](/assets/170/170-01.jpg)

### Eliminación del proceso mediante la herramienta EDR-Freeze

El desarrollador ha lanzado la herramienta EDR-Freeze para demostrar esta técnica. Requiere dos parámetros simples: el ID de proceso (PID) del objetivo que se congelará y la duración de la suspensión en milisegundos.

Esto permite a un atacante desactivar las herramientas de seguridad, realizar acciones maliciosas y, posteriormente, permitir que el software de seguridad reanude sus operaciones normales como si nada hubiera sucedido.

Una prueba en Windows 11 24H2 suspendió con éxito el proceso MsMpEng.exe de Windows Defender.

Para los defensores, detectar esta técnica implica monitorear ejecuciones inusuales de WerFaultSecure.exe.

Si se observa que el programa ataca los PID de procesos sensibles como lsass.exe o agentes EDR, debe considerarse una alerta de seguridad de alta prioridad que requiere investigación inmediata.

De acuerdo a [Florian Roth](https://x.com/cyb3rops/status/1970441497292992581):

- Los primeros envíos de VirusTotal tuvieron una detección de AV muy baja (5/73).
- El binario de la versión precompilada se cargó varias veces en VT y finalmente alcanzó 22/73 detecciones.
- Otras compilaciones de la herramienta aún obtienen solo entre 8 y 10 detecciones.
- Los antivirus aún tardan en reaccionar a las herramientas lanzadas públicamente.
- Existen reglas de bloqueo para esta herramienta en la configuración de Sysmon, usando Imphash.
- Esto significa que si usa Sysmon y una versión lo suficientemente reciente, EDR-Freeze es bloqueada al escribir mediante FileBlockExecutable.





