---
title: iShutdown - scripts claves para identificar software espía en iPhone
date: 2024-05-08 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [tools, ciberseguridad, hacking]
description: Investigadores de seguridad han descubierto que es posible detectar infecciones de los conocidos softwares espía Pegasus, Reign y Predator en dispositivos Apple. Esto se logra examinando el archivo Shutdown.log, que registra los eventos de reinicio del sistema.
image: /assets/71/preview1.png
---


Para facilitar este análisis, Kaspersky ha desarrollado tres scripts en Python. Estos scripts automatizan la revisión del archivo Shutdown.log, buscando indicios de infección por malware de una manera sencilla.

El archivo Shutdown.log se crea al reiniciar el dispositivo y anota el tiempo que tarda en terminarse un proceso, así como su identificador (PID).

Los scripts, denominados iShutdown, ayudan a identificar cambios provocados por malware en el proceso de reinicio. Estos cambios dejan huellas digitales que pueden confirmar una infección. Estos scripts ofrecen una alternativa más sencilla a métodos tradicionales, como el análisis de copias de seguridad cifradas de iOS o el tráfico de red.

Los tres scripts iShutdown publicados por Kaspersky son:

* iShutdown_detect.py: Analiza el archivo Sysdiagnose que contiene el log.
* iShutdown_parse.py: Extrae los datos de Shutdown.log del archivo tar.
* iShutdown_stats.py: Recopila estadísticas de reinicio del log.

Kaspersky aconseja reiniciar frecuentemente el dispositivo para que el archivo Shutdown.log registre posibles infecciones. La frecuencia recomendada depende del nivel de riesgo del usuario.

El repositorio de GitHub de Kaspersky incluye instrucciones y ejemplos sobre cómo utilizar estos scripts. Sin embargo, se requiere cierto conocimiento en Python, iOS y análisis de malware para interpretar correctamente los resultados.

![Imagen 01](/assets/71/071.png)

Estos archivos Sysdiagnose, que son archivos comprimidos de entre 200 y 400 MB, se usan para diagnosticar problemas en dispositivos iOS y iPadOS. Incluyen datos sobre el comportamiento del software y las comunicaciones de red, entre otros.

Kaspersky usó esta metodología inicialmente para analizar iPhones infectados con el spyware Pegasus, confirmado luego con la herramienta MVT de Amnistía Internacional.

“Esta consistencia en el comportamiento observado en otras infecciones por Pegasus nos hace creer que estos hallazgos pueden ser un indicador fiable para el análisis de infecciones”, afirma Kaspersky.

Sin embargo, este método tiene limitaciones. Si el usuario no reinicia su dispositivo el día de la infección, el análisis podría no ser efectivo. Además, el log registra retrasos en el reinicio, que pueden ser indicativos de procesos maliciosos, como los relacionados con Pegasus.

Aunque los retrasos pueden darse en dispositivos no infectados, los investigadores consideran que más de cuatro retrasos son una anomalía que merece investigación.

En pruebas con iPhones infectados con el spyware Reign, se observó que la ejecución del malware se originaba en la misma ruta que con Pegasus. Rutas similares en el archivo Shutdown.log también se han asociado con el spyware Predator, dirigido a jueces, abogados y periodistas.

Los investigadores de Kaspersky concluyen que el análisis del archivo Shutdown.log podría ser útil para identificar infecciones de estas familias de malware, siempre que los usuarios reinicien sus dispositivos con la frecuencia necesaria.

