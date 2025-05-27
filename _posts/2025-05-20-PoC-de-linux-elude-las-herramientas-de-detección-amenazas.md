---
title: El rootkit PoC io_uring de Linux elude las herramientas de detección de amenazas basadas en llamadas del sistema
date: 2025-05-20 09:00:00 
categories: [LINUX]
tags: [linux, ciberataque, vulnerabilidad]
description: Los investigadores de ciberseguridad han demostrado un rootkit de prueba de concepto (PoC) denominado Curing...
image: /assets/137/preview1.png
---

Los investigadores de ciberseguridad han demostrado un rootkit de prueba de concepto (PoC) denominado Curing que aprovecha un mecanismo de E/S asincrónico de Linux llamado io_uring para eludir la monitorización de llamadas del sistema tradicional.

Esto provoca un "punto ciego importante en las herramientas de seguridad del entorno de ejecución de Linux", afirmó ARMO.

"Este mecanismo permite que una aplicación de usuario realice diversas acciones sin usar llamadas al sistema", declaró la compañía en un informe compartido con The Hacker News. "Como resultado, las herramientas de seguridad que dependen de la monitorización de llamadas al sistema no detectan los rootkits que se basan únicamente en io_uring".

io_uring, introducido por primera vez en la versión 5.1 del kernel de Linux en marzo de 2019, es una interfaz de llamada al sistema del kernel de Linux que emplea dos buffers circulares llamados cola de envío (SQ) y una cola de finalización (CQ) entre el kernel y una aplicación (es decir, espacio de usuario) para rastrear el envío y la finalización de las solicitudes de E/S de manera asincrónica.

El rootkit ideado por ARMO facilita la comunicación entre un servidor de comando y control (C2) y un host infectado para obtener comandos y ejecutarlos sin realizar ninguna llamada al sistema relevante para sus operaciones, sino que utiliza io_uring para lograr los mismos objetivos.

El análisis de ARMO de las herramientas de seguridad en tiempo de ejecución de Linux disponibles actualmente ha revelado que tanto Falco como Tetragon son ciegos a las operaciones basadas en io_uring debido al hecho de que dependen en gran medida del enganche de llamadas del sistema.

Los riesgos de seguridad que plantea io_uring se conocen desde hace tiempo. En junio de 2023, Google reveló que decidió limitar el uso de la interfaz del kernel de Linux en Android, ChromeOS y sus servidores de producción, ya que proporciona potentes primitivas de explotación.

*"Por un lado, se necesita visibilidad de las llamadas del sistema; por otro, se necesita acceso a las estructuras del kernel y suficiente contexto para detectar amenazas de manera efectiva",* dijo Amit Schendel, jefe de investigación de seguridad en ARMO.

Muchos proveedores optan por la vía más sencilla: conectarse directamente a las llamadas del sistema. Si bien este enfoque ofrece una visibilidad rápida, presenta limitaciones. En particular, no siempre se garantiza la invocación de las llamadas del sistema. io_uring, que puede omitirlas por completo, es un ejemplo positivo y excelente.



