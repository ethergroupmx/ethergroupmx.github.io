---
title: "Un ataque de navegador de tipo "Zero-Click Agentic" puede eliminar todo Google Drive mediante correos electrónicos manipulados"
date: 2025-12-08 09:00:00 
categories: [CIBERATAQUES]
tags: [seguridad web, phishing, ciberataques]
description: Un exploit en el navegador Comet permite que un correo aparentemente inocente active comandos automáticos que eliminan todo Google Drive sin que el usuario haga clic.
image: /assets/196/preview1.png
---

Un nuevo ataque de navegador agente dirigido al navegador Comet de Perplexity es capaz de convertir un correo electrónico aparentemente inocuo en una acción destructiva que borra todo el contenido de Google Drive de un usuario, según muestran los hallazgos de Straiker STAR Labs.

La técnica de borrado de Google Drive sin hacer clic se basa en conectar el navegador a servicios como Gmail y Google Drive para automatizar tareas rutinarias otorgándoles acceso para leer correos electrónicos, así como para explorar archivos y carpetas y realizar acciones como mover, renombrar o eliminar contenido.

Por ejemplo, un mensaje emitido por un usuario benigno podría ser similar a este: "Por favor, revise mi correo electrónico y complete todas mis tareas recientes de organización". Esto hará que el agente del navegador busque mensajes relevantes en la bandeja de entrada y realice las acciones necesarias.

"Este comportamiento refleja una autonomía excesiva en los asistentes con tecnología LLM, donde el LLM realiza acciones que van mucho más allá de la solicitud explícita del usuario", dijo la investigadora de seguridad Amanda Rousseau en un informe compartido con The Hacker News.

Un atacante puede utilizar este comportamiento del agente del navegador para enviar un correo electrónico especialmente diseñado que incorpora instrucciones en lenguaje natural para organizar la unidad del destinatario como parte de una tarea de limpieza regular, eliminar archivos que coincidan con ciertas extensiones o archivos que no estén dentro de ninguna carpeta y revisar los cambios.

Dado que el agente interpreta el mensaje de correo electrónico como una tarea de rutina, trata las instrucciones como legítimas y elimina los archivos de usuario reales de Google Drive sin requerir confirmación del usuario.

El resultado: un limpiador controlado por un agente del navegador que elimina contenido crítico a gran escala, activado por una sola solicitud en lenguaje natural del usuario —explicó Rousseau—. Una vez que un agente tiene acceso OAuth a Gmail y Google Drive, las instrucciones mal utilizadas pueden propagarse rápidamente entre carpetas compartidas y unidades de equipo.

![Imagen 01](/assets/196/196-01.jpg)

Lo destacable de este ataque es que no se basa en un jailbreak ni en una inyección inmediata. En cambio, logra su objetivo simplemente siendo educado, dando instrucciones secuenciales y usando frases como "encárgate de", "maneja esto" y "haz esto en mi nombre", que transfieren la propiedad al agente.

En otras palabras, el ataque resalta cómo la secuenciación y el tono pueden empujar al modelo de lenguaje grande (LLM) a cumplir con instrucciones maliciosas sin siquiera molestarse en verificar si cada uno de esos pasos es realmente seguro.

Para contrarrestar los riesgos que plantea la amenaza, se recomienda tomar medidas para proteger no solo el modelo, sino también el agente, sus conectores y las instrucciones en lenguaje natural que sigue.

"Los asistentes de navegador de Agentic convierten las indicaciones cotidianas en secuencias de acciones eficaces en Gmail y Google Drive", afirmó Rousseau. "Cuando estas acciones se basan en contenido no confiable (especialmente correos electrónicos educados y bien estructurados), las organizaciones se enfrentan a un nuevo tipo de riesgo de borrado de datos sin necesidad de hacer clic".

### HashJack explota fragmentos de URL para la inyección indirecta de mensajes

La revelación se produce después de que Cato Networks demostrara otro ataque dirigido a navegadores con inteligencia artificial (IA), que oculta mensajes fraudulentos después del símbolo "#" en URL legítimas (p. ej., "www.example[.]com/home#<prompt>") para engañar a los agentes y que los ejecuten. Esta técnica se ha denominado HashJack.

Para desencadenar el ataque del lado del cliente, un actor de amenazas puede compartir una URL especialmente diseñada por correo electrónico, redes sociales o insertándola directamente en una página web. Una vez que la víctima carga la página y le hace una pregunta relevante al navegador de IA, este ejecuta la solicitud oculta.

"HashJack es la primera inyección indirecta de mensajes conocida que puede usar cualquier sitio web legítimo para manipular los asistentes de navegación de IA", declaró el investigador de seguridad Vitaly Simonovich . "Como el fragmento malicioso está incrustado en la URL de un sitio web real, los usuarios asumen que el contenido es seguro, mientras que instrucciones ocultas manipulan en secreto el asistente de navegación de IA".

![Imagen 01](/assets/196/196-02.png)

Tras una divulgación responsable, Google lo clasificó como "no se solucionará (comportamiento previsto)" y de baja gravedad, mientras que Perplexity y Microsoft han publicado parches para sus respectivos navegadores con IA (Comet v142.0.7444.60 y Edge 142.0.3595.94). Se ha comprobado que Claude para Chrome y OpenAI Atlas son inmunes a HashJack.

Vale la pena señalar que Google no trata la generación de contenido que viola las políticas y las evasiones de las medidas de seguridad como vulnerabilidades de seguridad en el marco de su Programa de Recompensa por Vulnerabilidades de IA (AI VRP).

Credits: HackersNews
