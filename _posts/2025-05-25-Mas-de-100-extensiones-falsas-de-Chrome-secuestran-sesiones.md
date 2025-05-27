---
title: Más de 100 extensiones falsas de Chrome secuestran sesiones, roban credenciales e inyectan anuncios
date: 2025-05-25 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, hacking, malware, web, vulnerabilidad]
description: Un desconocido ha creado de varias extensiones maliciosas para el navegador Chrome desde febrero de 2024.
image: /assets/133/preview1.png
---

Un actor de amenazas desconocido ha creado de varias extensiones maliciosas para el navegador Chrome desde febrero de 2024. Estas extensiones se hacen pasar por utilidades aparentemente inofensivas, pero incorporan funciones encubiertas para exfiltrar datos, recibir comandos y ejecutar código arbitrario.

*"El actor crea sitios web que se hacen pasar por servicios legítimos, herramientas de productividad, asistentes de creación o análisis de anuncios y medios, servicios VPN, criptomonedas, servicios bancarios y más, para dirigir a los usuarios a instalar las extensiones maliciosas correspondientes en la Chrome Web Store (CWS) de Google"* , declaró el equipo de DomainTools Intelligence (DTI) en un informe.

**Si bien los complementos del navegador parecen ofrecer las funciones anunciadas, también permiten el robo de credenciales y cookies, el secuestro de sesiones, la inyección de anuncios, las redirecciones maliciosas, la manipulación del tráfico y el phishing mediante la manipulación del DOM.**

Otro factor que favorece a las extensiones es que están configuradas para otorgarse permisos excesivos a través del archivo manifest.json, lo que les permite interactuar con todos los sitios web visitados en el navegador, ejecutar código arbitrario obtenido de un dominio controlado por el atacante, realizar redirecciones maliciosas e incluso inyectar anuncios.

También se ha descubierto que las extensiones utilizan el controlador de eventos "onreset" en un elemento temporal del modelo de objetos de documento (DOM) para ejecutar código, probablemente con el objetivo de eludir la política de seguridad de contenido (CSP).

Algunos de los sitios web señuelo identificados se hacen pasar por productos y servicios legítimos como DeepSeek, Manus, DeBank, FortiVPN y Site Stats para incitar a los usuarios a descargar e instalar las extensiones. Los complementos recopilan cookies del navegador, obtienen scripts arbitrarios de un servidor remoto y configuran una conexión WebSocket que actúa como proxy de red para el enrutamiento del tráfico.

Actualmente no se sabe cómo se redirige a las víctimas a estos sitios falsos, pero DomainTools indicó que podría implicar métodos habituales como el phishing y las redes sociales. *"Dado que aparecen tanto en Chrome Web Store como en sitios web adyacentes, pueden aparecer como resultados en búsquedas web normales y en búsquedas dentro de Chrome Store. Muchos de los sitios web señuelo utilizaban identificadores de seguimiento de Facebook, lo que sugiere firmemente que están aprovechando las aplicaciones de Facebook/Meta para atraer visitantes. Posiblemente a través de páginas, grupos e incluso anuncios de Facebook".*

Al momento de escribir este artículo, se desconoce quién está detrás de la campaña, aunque los actores de amenazas han creado más de 100 sitios web falsos y extensiones maliciosas de Chrome. Google, por su parte, ha eliminado las extensiones.

Para mitigar los riesgos, se recomienda a los usuarios que utilicen desarrolladores verificados antes de descargar extensiones, revisen los permisos solicitados, revisen las reseñas y eviten usar extensiones similares. Dicho esto, también conviene tener en cuenta que las calificaciones podrían manipularse e inflarse artificialmente al filtrar las opiniones negativas de los usuarios.

DomainTools, en un análisis publicado a finales del mes pasado, encontró evidencia de extensiones que suplantaban a DeepSeek y redirigían a los usuarios con calificaciones bajas (de 1 a 3 estrellas) a un formulario de comentarios privado en el dominio ai-chat-bot[.]pro, mientras que enviaban a los usuarios con calificaciones altas (de 4 a 5 estrellas) a la página oficial de reseñas de la Chrome Web Store.


