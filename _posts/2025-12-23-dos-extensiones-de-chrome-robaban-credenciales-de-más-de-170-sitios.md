---
title: "Dos extensiones de Chrome robaban credenciales de más de 170 sitios"
date: 2025-12-23 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, hacking, navegador, seguridad web, web]
description: Investigadores de seguridad han descubierto dos extensiones maliciosas para Google Chrome, ambas con el mismo nombre y creadas por el mismo autor, que interceptaban tráfico y capturaban credenciales de usuario de cientos de sitios web.
image: /assets/202/preview1.png
---

### Qué eran y cómo se distribuían

Las extensiones se anunciaban como un “plugin de prueba de velocidad de red para múltiples ubicaciones” dirigido a desarrolladores y profesionales de comercio internacional. A pesar de eso, su función real era maliciosa.

Los detalles principales:

- Phantom Shuttle (ID: fbfldogmkadejddihifklefknmikncaj) — Instalado por unas 2 000 personas desde noviembre de 2017.
- Phantom Shuttle (ID: ocpcmfmiidofonkbodpdhgddhlcmcofd) — Unos 180 usuarios desde abril de 2023.

Los usuarios pagaban una suscripción (de ¥9.9 a ¥95.9 CNY ≈ $1.40–$13.50 USD) pensando que obtendrían un servicio VPN legítimo, pero en realidad activaban funciones maliciosas ocultas.

### Qué hacían realmente

Las extensiones funcionaban como proxies de intermediario (man-in-the-middle), redirigiendo tráfico de usuarios a través de servidores controlados por los atacantes, lo que les permitía:

- Interceptar tráfico y credenciales. 
- Registrar un “latido” (heartbeat) cada 60 s hacia el servidor de control, transmitiendo correo, contraseña en texto plano y versión de extensión. 
- Manipular tráfico y respuestas de sitios web.

Para lograr esto, las extensiones inyectaban credenciales de proxy codificadas directamente en el código que se aplicaban automáticamente cada vez que un sitio solicitaba autenticación HTTP.

### Qué dominios afectaban

El proxy “VIP” dirigía tráfico a través de la infraestructura de control para más de 170 sitios importantes, incluyendo plataformas para desarrolladores (como GitHub), servicios en la nube (AWS, Azure), soluciones empresariales (Cisco, IBM) y redes sociales (Facebook, Instagram, Twitter).

También incluían sitios para adultos, probablemente para intentar extorsionar o presionar a las víctimas.

### Cómo funcionaba la ilusión de legitimidad

Las extensiones sí realizaban algunas funciones legítimas —como test de latencia y mostrar el estado de conexión— para parecer un producto real y ocultar su comportamiento malicioso.

Además, el uso de métodos de pago populares en China como Alipay y WeChat Pay, y servidores en Alibaba Cloud, sugiere que la operación podría tener origen en dicha región, aunque esto no está confirmado.

### Recomendaciones

Si tienes estas extensiones instaladas:

-  Elimínalas inmediatamente de Chrome.
-  Para empresas: implementa políticas de allowlist de extensiones y monitoreo de autenticaciones sospechosas.

Este caso demuestra cómo las extensiones de navegador pueden convertirse en una importante amenaza para la seguridad y la privacidad si no se controlan adecuadamente.

- 
