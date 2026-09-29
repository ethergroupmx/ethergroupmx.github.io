---
title: "Herramientas de IA utilizadas para ciberataques"
date: 2026-09-28 09:00:00
categories: [CIBERSEGURIDAD]
tags: [inteligencia artificial, IA, ciberseguridad, ciberataques, amenazas, hacking, seguridad informática]
description: "La inteligencia artificial también está siendo utilizada para facilitar y potenciar diferentes tipos de ciberataques. Conoce cómo estas herramientas pueden ser aprovechadas por los ciberdelincuentes."
image: /assets/297/preview1.png
---

Gambit Security, una firma especializada en inteligencia de amenazas, detectó una campaña casi por accidente: un ciberdelincuente había dejado expuestos en internet los servidores que utilizaba para coordinar los ataques mediante IA, lo que permitió a los investigadores reconstruir parte de la operación.

Un solo ciberdelincuente logró dirigir agentes de inteligencia artificial contra más de 100 empresas en apenas cinco días. Al menos 27 fueron vulneradas y, desde julio, la campaña le permitió robar más de 600.000 registros de tarjetas de crédito. Para hacerlo, el atacante gastó apenas unos US$25 en servicios de IA por cada empresa que puso en la mira.

Los más de 600.000 registros de tarjetas de crédito robados procedían de apenas dos de las empresas afectadas. De ese total, 488.000 —cerca del 79%— pertenecían a titulares de Estados Unidos. Overwatch Data, una firma especializada en prevención del fraude, analizó la información y confirmó que se trataba de registros únicos y auténticos.

<img src="/assets/297/297-01.png" alt="Cairn attack status" style="width: 80%;">

De acuerdo a Gambit, la operación mostró hasta qué punto la inteligencia artificial ya está siendo utilizada para automatizar ataques informáticos a gran escala y reducir drásticamente sus costos. También dejó en evidencia la velocidad con la que estas herramientas pasaron de los ensayos y las pruebas controladas a convertirse en instrumentos concretos de la ciberdelincuencia.

Para llevar adelante los ataques se utilizaron tres herramientas comerciales de inteligencia artificial y distintos modelos de acceso público. La mayoría eran de origen chino, aunque también se recurrió a una versión anterior de Claude, desarrollada por Anthropic. El operador apenas ingresaba instrucciones breves en chino y luego delegaba en los agentes gran parte de la ejecución de las tareas.

Entre el 10 y el 15 de septiembre, los agentes de IA lanzaron 105 ataques y lograron comprometer al menos 27 empresas, con distintos niveles de impacto. En 19 sitios web se confirmó la instalación de código malicioso diseñado para robar datos de tarjetas de crédito. Además, un investigador que colabora con Gambit identificó ese mismo código en más de 100 tiendas online adicionales, lo que sugiere que el alcance de la campaña fue todavía mayor.

### Hermes
Hermes es un agente de IA autónomo de código abierto que cuenta con memoria persistente, habilidades que el propio agente escribe y edita, un archivo de sesiones anteriores con función de búsqueda, tareas programadas y una consola web. En este servidor, cargó una personalidad de sistema en chino denominada «SOUL - Red Team Operator» y 121 habilidades, de las cuales 78 eran de ataque.

El operador también añadió una habilidad destinada a eliminar los filtros de seguridad de contenido del propio Hermes. Hermes sirve como consola para que el operador coordine la actividad y lleve a cabo acciones de hackeo directo. Se utilizó el modelo opus-4.6 de Anthropic (tras el rechazo de modelos más recientes a procesar sus solicitudes), empleando 1.951 instrucciones introducidas por el humano a lo largo de 260 sesiones; es decir, apenas unas pocas instrucciones por objetivo.

Dichas instrucciones humanas son breves y están redactadas en chino; por lo general, sirven para lanzar un ataque, asignar al agente el siguiente paso general o determinar qué hacer tras lograr el acceso. Por ejemplo:

看漏洞报告 开干 (“read the vulnerability report and start”)
看看报告里的文件上传能不能rce (“see whether the file upload in the report can give code execution”)
看漏洞报告 先测sudo密码 (“read the vulnerability report, test the sudo password first”)
看一下漏洞报告 有搞头吗 (“read the report, is there anything worth doing here?”)
看看进web后台 (“get into the web backend”)
能rce吗 (“can it get code execution?”)
目标导向 围绕getshell或后台访问权限 (“goal oriented, centred on getshell or backend access”)
深挖api (“dig deeper into the API”)
你用php验证一下 (“verify it with PHP”)
你去搜一下wp2shell (“go and search for wp2shell”)
还能写js？ (“can you still write the js?”)
confirmation.php代码不扎眼吧 (“the confirmation.php code does not stand out, right?”)
script标签在html标签后面不合适 (“a script tag after the html tag is not right”)
容器里的不用动目标痕迹清 (“leave the ones in the container, clear the traces on the target”)
先把传的js删了 清临时文件 (“first delete the js we uploaded, clear the temporary files”)

### Strix

Strix es una herramienta de código abierto de pruebas de penetración basada en IA. Entre el 23 y el 31 de agosto de 2026, Strix se ejecutó 146 veces en "modo profundo" contra 138 hosts, lo que supuso 633 horas de tiempo de escaneo en un periodo de 195 horas de tiempo real. Algunos de estos informes marcaron el inicio de la siguiente fase de la explotación y fueron transferidos a Cairn. Strix operó a través de OpenRouter utilizando GLM 5.2 y, posteriormente, DeepSeek v4 Pro.

### Cairn

Cairn es un motor autónomo de pruebas de penetración. Recibe dominios objetivo y una meta —como obtener una shell o acceso de administrador— y opera durante horas hasta lograr el objetivo, agotar el tiempo límite o ser detenido. En los ataques realizados por Cairn se utilizó DeepSeek v4.1 Flash.

Entre el 10 y el 15 de septiembre se lanzaron 105 proyectos de ataque. El gráfico siguiente muestra el estado de 48 de ellos; los otros 57 fueron eliminados y no están disponibles para su análisis.

El problema no está únicamente en el bajo costo. La inteligencia artificial permite acelerar las tareas, multiplicar la cantidad de objetivos y repetir los intentos con mucha menos intervención humana, una combinación que eleva el riesgo para cualquier empresa o comercio que procese pagos a través de internet.

Ese escenario obliga a revisar las estrategias de protección y a destinar más recursos a detectar amenazas en tiempo real, controlar la actividad automatizada y garantizar la integridad de los sistemas de pago. A medida que los ataques se vuelven más baratos y escalables, también aumenta la necesidad de identificar y bloquear una intrusión antes de que llegue a comprometer información sensible.

Cloudflare confirmó a Forbes que desactivó infraestructura vinculada con esta campaña en colaboración con la Fundación Shadowserver, una organización sin fines de lucro dedicada a identificar amenazas y alertar a las posibles víctimas. Sin embargo, el ciberdelincuente volvió a poner en funcionamiento los servidores en varias oportunidades, mientras que Gambit sostiene que la actividad maliciosa todavía continúa.


