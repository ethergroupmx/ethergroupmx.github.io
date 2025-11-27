---
title: "Matrix Push C2: utiliza notificaciones del navegador para ataques de phishing multiplataforma sin archivos"
date: 2025-11-27 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, phishin, redes]
description: Los delincuentes están aprovechando las notificaciones del navegador como vector de ataques de phishing para distribuir enlaces maliciosos mediante una nueva plataforma de comando y control (C2) llamada Matrix Push C2.
image: /assets/190/preview1.png
---

*"Este marco nativo del navegador y sin archivos aprovecha las notificaciones automáticas, las alertas falsas y los redireccionamientos de enlaces para apuntar a las víctimas en todos los sistemas operativos"*, dijo la investigadora de Blackfog, Brenda Robb, en un informe. En estos ataques, se engaña a los posibles objetivos para que permitan notificaciones del navegador mediante ingeniería social en sitios web maliciosos o legítimos pero comprometidos.

![Imagen 01](/assets/190/190-01.png)

Una vez que un usuario acepta recibir notificaciones del sitio, los atacantes aprovechan el mecanismo de notificación push web integrado en el navegador web para enviar alertas que parecen haber sido enviadas por el sistema operativo o el propio navegador, aprovechando marcas confiables, logotipos familiares y un lenguaje convincente para mantener la engaño.

Estos incluyen alertas sobre, por ejemplo, inicios de sesión sospechosos o actualizaciones del navegador, junto con un útil botón "Verificar" o "Actualizar" que, cuando se hace clic, lleva a la víctima a un sitio falso.

Lo que hace que esta técnica sea inteligente es que todo el proceso se lleva a cabo a través del navegador sin necesidad de infectar primero el sistema de la víctima por algún otro medio. En cierto modo, el ataque es como ClickFix en el sentido de que los usuarios son atraídos a seguir ciertas instrucciones para comprometer sus propios sistemas, evitando así de manera efectiva los controles de seguridad tradicionales.

![Imagen 01](/assets/190/190-02.png)

Eso no es todo. Dado que el ataque se realiza a través del navegador web, también es una amenaza multiplataforma. Básicamente, esto convierte cualquier aplicación de navegador en cualquier plataforma que se suscriba a notificaciones maliciosas para que se inscriba en el grupo de clientes, brindando a los adversarios un canal de comunicación persistente.

Matrix Push C2 se ofrece como un kit de malware como servicio (MaaS) a otros actores de amenazas. Se vende directamente a través de canales de crimeware, generalmente a través de Telegram y foros de cibercrimen, bajo un modelo de suscripción escalonada: alrededor de $150 por un mes, $405 por tres meses, $765 por seis meses y $1.500 por un año completo.

"Los pagos se aceptan en criptomonedas y los compradores se comunican directamente con el operador para obtener acceso", dijo el Dr. Darren Williams, fundador y director ejecutivo de BlackFog. "Matrix Push se observó por primera vez a principios de octubre y ha estado activo desde entonces. No hay evidencia de versiones anteriores, marcas anteriores o infraestructura de larga data. Todo indica que se trata de un kit recién lanzado".

Se puede acceder a la herramienta como un panel basado en web, lo que permite a los usuarios enviar notificaciones, rastrear a cada víctima en tiempo real, determinar con qué notificaciones interactuaron las víctimas, crear enlaces acortados utilizando un servicio de acortamiento de URL incorporado e incluso registrar extensiones de navegador instaladas, incluidas carteras de criptomonedas.

*"El núcleo del ataque es la ingeniería social, y Matrix Push C2 viene cargado con plantillas configurables para maximizar la credibilidad de sus mensajes falsos"*, explicó Robb. *"Los atacantes pueden personalizar fácilmente sus notificaciones de phishing y sus páginas de destino para hacerse pasar por empresas y servicios conocidos"*

Algunas de las plantillas de verificación de notificaciones admitidas están asociadas con marcas conocidas como MetaMask, Netflix, Cloudflare, PayPal y TikTok. La plataforma también incluye una sección de "Análisis e informes" que permite a sus clientes medir la efectividad de sus campañas y perfeccionarlas según sea necesario.

Matrix Push C2 nos muestra un cambio en la forma en que los atacantes obtienen acceso inicial e intentan explotar a los usuarios. Una vez que el punto final de un usuario (computadora o dispositivo móvil) está bajo este tipo de influencia, el atacante puede intensificar gradualmente el ataque. "Podrían enviar mensajes de phishing adicionales para robar credenciales, engañar al usuario para que instale un malware más persistente o incluso aprovechar los exploits del navegador para obtener un control más profundo del sistema. En última instancia, el objetivo final suele ser robar datos o monetizar el acceso, por ejemplo, vaciando carteras de criptomonedas o filtrando información personal".
