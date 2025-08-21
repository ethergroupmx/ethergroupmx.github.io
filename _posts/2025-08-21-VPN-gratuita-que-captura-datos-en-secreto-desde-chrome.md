---
title: "VPN gratuita que captura datos en secreto desde Chrome"
date: 2025-08-21 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [vulnerabilidad, hacking, ciberseguridad, navegador]
description: La extensión, una vez instalada en Chrome, activa un disparador en segundo plano que realiza capturas de pantalla de lo que están haciendo los usuarios.
image: /assets/157/preview1.png
---

La firma de ciberseguridad KOI Security ha advertido del comportamiento malicioso de FreeVPN[.]One, una extensión para Chrome verificada que promete proteger la privacidad de los usuarios en internet, pero que espía su actividad con capturas de pantalla.

FreeVPN es una extensión para Chrome que ofrece una red privada virtual (VPN) para navegar de forma "segura". En la tienda del navegador de Google muestra una insignia de verificación, ocupa una posición destacada y está respaldada por más de 100.000 instalaciones.

A ello se suma que en su descripción, sus creadores aseguran que la extensión no recopila ni utiliza los datos de los usuarios. Sin embargo, en KOI Security han descubierto que su actividad real es todo lo contrario a lo que promete.

**La extensión, una vez instalada en Chrome, activa un disparador en segundo plano que realiza capturas de pantalla de lo que están haciendo los usuarios,** ya sea ver una pagina web, abrir una hoja de cálculo o ingresar en su cuenta bancaria. Desde KOI Security señalan que estas capturas de pantalla pueden acceder a contraseñas, datos bancarios, mensajes personales, fotografías privadas y, en general, *"cualquier dato confidencial que aparezca en pantalla".*

![Imagen 01](/assets/157/157-01.png)

Lo particular de esta extensión es que el disparador tiene un retardo de 1,1 segundos para garantizar que realiza una captura cuando la página se ha renderizado por completo, para asegurar que recoge la mayor cantidad de información posible. Todas las capturas se envían a un servidor externo junto con con la URL de la página abierta, el ID de la pestaña y un identificador único de usuario.

Este comportamiento, sin embargo, no ha acompañado a la VPN desde el principio. Según la firma de ciberseguridad, comenzó en abril de este año, con la actualización v3.0.3, que introdujo los permisos que posteriormente permitirían a sus desarrolladores realizar la actividad de espionaje, activa desde julio (v3.1.3). Ese mismo mes, también introdujeron (v3.1.4) una encriptación para tratar de de ocultar su rastro.

*"FreeVPN.One muestra cómo una marca de privacidad puede convertirse en una trampa"*, apuntan desde KOI Security.

