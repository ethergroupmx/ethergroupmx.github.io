---
title: "La nube se apaga: una interrupción en AWS afecta a servicios clave en línea"
date: 2025-10-20 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [cloud, servidores, internet, news, tecnología]
description: Una interrupción de AWS ha paralizado millones de sitios web, incluyendo Amazon.com, Prime Video, Perplexity AI, Canva y más.
image: /assets/181/preview1.png
---

La caída comenzó durante la madrugada del lunes y se concentró en servidores de la región de Virginia del Norte (Estados Unidos), una de las más críticas dentro del ecosistema de AWS. El suministro se restableció en horas de la tarde.

La interrupción ha afectado a consumidores de todas las regiones, incluyendo Estados Unidos y Europa y Latinoamérica y, en la página de AWS Health, Amazon está informando sobre el estado de situación que afecta a múltiples servicios. "Podemos confirmar un aumento en las tasas de error y latencia para múltiples servicios de AWS en la región US-EAST-1. Este problema también podría estar afectando la creación de casos a través del Centro de Soporte de AWS o la API de Soporte. Estamos trabajando activamente para mitigar el problema y comprender la causa raíz", señaló AWS.

Si bien Amazon (aún) no ha compartido la causa específica de la interrupción, las actualizaciones de estado indican que está relacionada con un problema de resolución de DNS para el punto final de la API de DynamoDB en la región US-EAST-1 de AWS.

Según investigaciones en curso, el fallo se originó en la red interna de Elastic Compute Cloud (EC2), que permite a los usuarios crear aplicaciones basadas en la nube y gestionar los recursos informáticos pertinentes para hacerlas funcionar.

La interrupción tuvo un alcance global. Servicios como Netflix, Microsoft 365, YouTube, Facebook, Snapchat y Fortnite registraron fallas generalizadas. En algunos casos, los usuarios no podían iniciar sesión; en otros, se interrumpía la reproducción de videos o el funcionamiento de videollamadas.

En una publicación en X, Fortnite de Epic Games confirmó una importante interrupción del servicio, así como Perplexity cuya aplicación de chat está fuera de línea debido. La empresa de diseño gráfico Canva reconoció una interrupción del servicio que afectó la edición de imágenes y otras funciones.

Según Downdetector, 15 servicios importantes, incluyendo plataformas de entretenimiento como Roblox y Hulu, están o estuvieron fuera de línea debido a problemas con AWS.

El impacto también se sintió en América Latina, donde miles de usuarios reportaron dificultades para realizar pagos electrónicos o acceder a apps de uso cotidiano. 

Tras casi 12 horas en la interrupción del servicio, el problema "fue mitigado por completo y la mayoría de las operaciones del servicio AWS funcionan con normalidad ahora en todo el mundo" indicó en una actualización la página web de mantenimiento y añadió que algunas operaciones, aún tienen inconvenientes que se irán recuperando en el transcurso de la jornada.
