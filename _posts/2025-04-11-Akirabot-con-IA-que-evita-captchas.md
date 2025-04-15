---
title: AkiraBot - Bot con IA que evita CAPTCHAs y envía spam a sitios web a gran escala
date: 2025-04-11 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, malware, IA]
description: Investigadores han revelado detalles de una plataforma impulsada por inteligencia artificial (IA) llamada AkiraBot, que se utiliza para enviar spam a chats.
image: /assets/125/preview1.png
---

Investigadores han revelado detalles de una plataforma impulsada por inteligencia artificial (IA) llamada AkiraBot, que se utiliza para enviar spam a chats, secciones de comentarios y formularios de contacto de sitios web con el fin de promocionar servicios de optimización para motores de búsqueda (SEO) dudosos como Akira y ServicewrapGO.

*"AkiraBot ha atacado más de 400.000 sitios web y ha enviado spam con éxito a al menos 80.000 desde septiembre de 2024"*, declararon los investigadores de SentinelOne, Alex Delamotte y Jim Walter, en un informe. *"El bot utiliza OpenAI para generar mensajes de contacto personalizados según el propósito del sitio web"*.

![Imagen 01](/assets/125/125-01.png)

Los objetivos de esta actividad incluyen formularios de contacto y widgets de chat presentes en sitios web de pequeñas y medianas empresas, y el framework comparte contenido spam generado mediante los modelos de lenguaje (LLM) de OpenAI. Lo que distingue a esta extensa herramienta basada en Python es su capacidad para crear contenido que permite eludir los filtros de spam.

Se cree que la herramienta de mensajería masiva se ha utilizado al menos desde septiembre de 2024, comenzando con el nombre "Shopbot", en lo que parece ser una referencia a los sitios web que utilizan Shopify.

Con el tiempo, AkiraBot ha ampliado su alcance de segmentación para incluir sitios desarrollados con GoDaddy, Wix y Squarespace, así como aquellos con formularios de contacto genéricos y widgets de chat en vivo creados con Reamaze.

La clave de la operación, que consiste en generar el contenido de spam, se facilita mediante el uso de la API de OpenAI. La herramienta también ofrece una interfaz gráfica de usuario (GUI) para seleccionar la lista de sitios web objetivo y personalizar cuántos de ellos se pueden atacar simultáneamente.

*"AkiraBot crea mensajes de spam personalizados para los sitios web objetivo procesando una plantilla que contiene un esquema genérico del tipo de mensaje que debe enviar el bot"*, explicaron los investigadores. *"La plantilla se procesa mediante una solicitud enviada a la API de chat de OpenAI para generar un mensaje de contacto personalizado basado en el contenido del sitio web".*

Un análisis del código fuente revela que el cliente OpenAI utiliza el modelo gpt-4o-mini y se le asigna la función de "asistente útil que genera mensajes de marketing".

Otro aspecto destacable del servicio es que puede sortear las barreras CAPTCHA para enviar spam a sitios web a gran escala y evadir las detecciones basadas en la red mediante un servicio de proxy que se suele ofrecer a los anunciantes. Los servicios CAPTCHA objetivo son hCAPTCHA, reCAPTCHA y Cloudflare Turnstile.

Para lograrlo, el tráfico web del bot está diseñado para simular un usuario final legítimo y utiliza diferentes servidores proxy de SmartProxy para ocultar el origen del tráfico.

AkiraBot también está configurado para registrar sus actividades en un archivo llamado "submissions.csv", que registra tanto los intentos de spam exitosos como los fallidos. Un análisis de estos archivos ha revelado que más de 420.000 dominios únicos han sido atacados hasta la fecha. Además, las métricas de éxito relacionadas con la evasión de CAPTCHA y la rotación de proxy se recopilan y se publican en un canal de Telegram a través de la API.

En respuesta a los hallazgos, OpenAI ha desactivado la clave API y otros recursos asociados utilizados  por los actores de amenazas. *"El autor o los autores han invertido un esfuerzo considerable en la capacidad de este bot para evadir las tecnologías CAPTCHA de uso común, lo que demuestra que los operadores están motivados a violar las protecciones de los proveedores de servicios. El uso por parte de AkiraBot del contenido de mensajes de spam generados por LLM demuestra los nuevos desafíos que la IA plantea para la defensa de los sitios web contra los ataques de spam".*

