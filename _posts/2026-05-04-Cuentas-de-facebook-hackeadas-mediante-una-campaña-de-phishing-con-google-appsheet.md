---
title: "30.000 cuentas de Facebook hackeadas mediante una campaña de phishing con Google AppSheet"
date: 2026-05-04 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, ciberseguridad, hacking, phishing, fraude, redes, internet]
description: Se ha detectado una operación reciente que utiliza Google AppSheet como plataforma para distribuir correos electrónicos de phishing con el objetivo de comprometer cuentas de Facebook.
image: /assets/250/preview1.png
---

Guardio ha denominado a esta actividad AccountDumpling y el esquema consiste en la venta de las cuentas robadas a través de una plataforma ilícita gestionada por los ciberdelincuentes. Se estima que aproximadamente 30.000 cuentas de Facebook fueron hackeadas como parte de esta campaña.

![Imagen 01](/assets/250/250-01.png)

*"Lo que encontramos no fue un solo kit de phishing", escribió el investigador de seguridad Shaked Chen en el informe. "Se trataba de una operación en constante evolución, con paneles de control en tiempo real, sistemas avanzados de evasión, un ciclo criminal-comercial que se nutría silenciosamente de las mismas cuentas que ayudaba a recuperar."*

Estos hallazgos son solo el ejemplo más reciente de cómo los ciberdelincuentes vietnamitas siguen empleando diversas tácticas para obtener acceso no autorizado a las cuentas de Facebook de las víctimas, que luego venden en mercados clandestinos para obtener beneficios económicos.

El punto de partida de los ataques más recientes es un correo electrónico de phishing dirigido a los propietarios de cuentas de Facebook Business, que se hace pasar por el Soporte de Meta y les insta a presentar una apelación o arriesgarse a que su cuenta sea eliminada permanentemente. Los correos se envían desde una dirección de Google AppSheet ("noreply@appsheet.com"), lo que les permite eludir los filtros de spam.

![Imagen 01](/assets/250/250-02.png)

Esta falsa sensación de urgencia se utiliza para redirigir a los usuarios a una página web falsa diseñada para robar sus credenciales. Cabe destacar que KnowBe4 informó de una campaña similar en mayo de 2025.

En las últimas semanas, estas campañas han adoptado diversos tipos de señuelos diseñados para generar pánico relacionado con Meta. Estos incluyen desde la desactivación de cuentas y denuncias de derechos de autor hasta la revisión de la verificación, la contratación de ejecutivos y alertas de inicio de sesión de Facebook. Los cuatro grupos principales identificados por Guardio se enumeran a continuación:

- **Páginas del centro de ayuda de Facebook alojadas en Netlify** que permiten ataques de robo de cuentas, además de recopilar fechas de nacimiento, números de teléfono y fotos de documentos de identidad emitidos por el gobierno. Los datos se envían finalmente a un canal de Telegram controlado por el atacante.
- **Señuelos de evaluación con insignia azul** que guían a las víctimas a páginas de "Verificación de seguridad" o "Meta | Centro de privacidad" alojadas en Vercel, las cuales requieren una verificación CAPTCHA falsa antes de redirigir a los usuarios a una página de phishing para recopilar datos de contacto, información comercial, credenciales (tras un reintento forzado) y códigos de autenticación de dos factores (2FA), para luego extraerlos a un canal de Telegram.
- **PDFs alojados en Google Drive** que simulan instrucciones para completar la verificación de la cuenta, con el fin de que los usuarios recopilen contraseñas, códigos 2FA, fotos de documentos de identidad oficiales y capturas de pantalla del navegador mediante html2canvas. Los documentos PDF se generan utilizando una cuenta gratuita de Canva.
- **Ofertas de trabajo falsas** que suplantan la identidad de empresas como WhatsApp, Meta, Adobe, Pinterest, Apple y Coca-Cola para ganarse la confianza de los destinatarios y pedirles que se unan a una llamada o continúen la conversación en sitios controlados por el atacante. En conjunto, se ha descubierto que los canales de Telegram asociados con los tres primeros grupos contienen alrededor de 30.000 registros de víctimas, la mayoría de las cuales se encuentran en Estados Unidos, Italia, Canadá, Filipinas, India, España, Australia, Reino Unido, Brasil y México, y han sido bloqueadas para acceder a sus propias cuentas.

En cuanto a quién está detrás de la operación, la prueba irrefutable proviene de los archivos PDF generados como parte del tercer grupo utilizando la cuenta gratuita de Canva, cuyos metadatos identifican al autor vietnamita "PHẠM TÀI TÂN". Además, la información de fuentes abiertas ha permitido descubrir un sitio web ("phamtaitan[.]vn") donde ofrecen servicios de marketing digital.

En una publicación compartida en X en febrero de 2023, el sitio web indicaba que se especializaba en brindar servicios de marketing digital, recursos de marketing y consultoría sobre estrategias efectivas de marketing digital.

![Imagen 01](/assets/250/250-03.png)

*"En conjunto, conforman una imagen coherente de una megaoperación a gran escala con sede en Vietnam. Esta campaña va más allá de un simple abuso de AppSheet. Es una ventana al mercado negro que rodea a los activos robados de Facebook, donde el acceso, la identidad comercial, la reputación publicitaria e incluso la recuperación de cuentas se han convertido en mercancías comercializables. Un nuevo ejemplo del patrón que seguimos observando: plataformas de confianza reconvertidas en capas de entrega, alojamiento y monetización", afirmó Chen.*
