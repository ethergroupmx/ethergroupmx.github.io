---
title: "Fallos en Microsoft Teams permiten a los atacantes suplantar la identidad de compañeros y editar mensajes sin ser detectados."
date: 2025-11-04 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, news, tecnología, web, vulnerabilidad]
description: Investigadores de ciberseguridad han revelado detalles de cuatro fallos de seguridad en Microsoft Teams que podrían haber expuesto a los usuarios a graves ataques de suplantación de identidad e ingeniería social.
image: /assets/185/preview1.png
---

Las vulnerabilidades "permitían a los atacantes manipular conversaciones, suplantar la identidad de compañeros de trabajo y aprovechar las notificaciones", según indicó Check Point en un informe compartido con The Hacker News.

Tras la divulgación responsable en marzo de 2024, algunos de los problemas fueron abordados por Microsoft en agosto de 2024 bajo el identificador CVE-2024-38197, con parches posteriores lanzados en septiembre de 2024 y octubre de 2025.

En resumen, estas deficiencias permiten alterar el contenido de los mensajes sin dejar la etiqueta "Editado" ni la identidad del remitente, y modificar las notificaciones entrantes para cambiar el remitente aparente del mensaje, lo que permite a un atacante engañar a las víctimas para que abran mensajes maliciosos haciéndolos parecer que provienen de una fuente confiable, incluidos altos ejecutivos de la alta dirección.

El ataque, que afecta tanto a usuarios invitados externos como a actores maliciosos internos, plantea graves riesgos, ya que socava los límites de seguridad y permite a los posibles objetivos realizar acciones no deseadas, como hacer clic en enlaces maliciosos enviados en los mensajes o compartir datos confidenciales.

Además, las vulnerabilidades también permitían cambiar los nombres que se mostraban en las conversaciones de chat privadas modificando el tema de la conversación, así como modificar arbitrariamente los nombres que se mostraban en las notificaciones de llamadas y durante la llamada, lo que permitía a un atacante falsificar las identidades de las personas que llamaban en el proceso.

"En conjunto, estas vulnerabilidades demuestran cómo los atacantes pueden erosionar la confianza fundamental que hace que las herramientas de espacio de trabajo colaborativo sean efectivas, convirtiendo a Teams de un facilitador de negocios en un vector de engaño", dijo la compañía de ciberseguridad .

![Imagen 01](/assets/185/185-01.jpg)

Microsoft ha descrito CVE-2024-38197 (puntuación CVSS: 6,5) como un problema de suplantación de identidad de gravedad media que afecta a Teams para iOS, que podría permitir a un atacante alterar el nombre del remitente de un mensaje de Teams y potencialmente engañarlo para que revele información confidencial a través de tácticas de ingeniería social.

Estos hallazgos se producen en un momento en que los ciberdelincuentes están abusando de la plataforma de comunicación empresarial de Microsoft de diversas maneras, incluyendo el acercamiento a los objetivos y la persuasión para que otorguen acceso remoto o ejecuten una carga útil maliciosa haciéndose pasar por personal de soporte.

Microsoft, en un comunicado publicado el mes pasado, afirmó que "las amplias funciones de colaboración y la adopción global de Microsoft Teams lo convierten en un objetivo de alto valor tanto para los ciberdelincuentes como para los actores patrocinados por estados" y que sus funciones de mensajería (chat), llamadas, reuniones y compartición de pantalla basada en vídeo se utilizan como armas en diferentes etapas de la cadena de ataque.

«Estas vulnerabilidades atentan contra la esencia misma de la confianza digital», declaró Oded Vanunu, jefe de investigación de vulnerabilidades de productos en Check Point, a The Hacker News. «Las plataformas de colaboración como Teams son ahora tan cruciales como el correo electrónico e igual de expuestas».

Nuestra investigación demuestra que los ciberdelincuentes ya no necesitan infiltrarse; basta con quebrantar la confianza. Las organizaciones ahora deben proteger las creencias de las personas, no solo los procesos de los sistemas. Ver ya no es creer, ahora lo es verificar.

