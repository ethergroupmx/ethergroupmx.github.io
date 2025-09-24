---
title: "Robo de credenciales por phishing a través de redes sociales y mensajería (y sí, correo)"
date: 2025-09-24 09:00:00 
categories: [CIBERATAQUES]
tags: [phishing, hacking, malware]
description: Los atacantes envían cada vez más enlaces de phishing a través de medios distintos al correo electrónico, como redes sociales, aplicaciones de mensajería instantánea y anuncios maliciosos en buscadores.
image: /assets/172/preview1.png
---

En este artículo, exploraremos por qué los ataques de phishing están dejando de basarse exclusivamente en el correo electrónico y qué significa esto para los equipos de seguridad.

**Debido a los cambios en las prácticas laborales, los empleados son más vulnerables que nunca a los atacantes externos.** Antaño, el correo electrónico era el principal canal de comunicación con el resto del mundo, y el trabajo se realizaba localmente: en el dispositivo y dentro de un entorno de red protegido. Esto convertía el correo electrónico y el endpoint en la máxima prioridad desde el punto de vista de la seguridad.

Pero ahora, con el trabajo moderno que se realiza a través de una red de aplicaciones de internet descentralizadas y una mayor variedad de canales de comunicación fuera del correo electrónico, es más difícil impedir que los usuarios interactúen con contenido malicioso.

Los atacantes pueden enviar enlaces a través de aplicaciones de mensajería instantánea, redes sociales, SMS, anuncios maliciosos y mediante la funcionalidad de mensajería integrada en la aplicación, así como enviar correos electrónicos directamente desde servicios SaaS para eludir las comprobaciones basadas en correo electrónico. Asimismo, ahora hay cientos de aplicaciones por empresa a las que apuntar, con distintos niveles de configuración de seguridad de cuenta.

Los ataques de phishing fuera del correo electrónico suelen pasar desapercibidos. Esto es de esperar, ya que la mayoría de los datos del sector sobre ataques de phishing provienen de proveedores y herramientas de seguridad de correo electrónico.

Esto ya es bastante difícil al analizar una aplicación SaaS típica. Pero la última generación de kits de phishing Attacker-in-the-Middle (AitM) totalmente personalizados están haciendo todo lo posible para que esto sea lo más desafiante posible, utilizando técnicas como ofuscación de DOM, de páginas web y de código fuente, de modo que todo lo que se ve en una capa de red es un "lío" confuso y ofuscado de código JS.

![Imagen 01](/assets/172/172-01.jpg)

Así pues, el phishing no relacionado con el correo electrónico pasa prácticamente desapercibido a través de los controles técnicos. E incluso cuando un usuario lo detecta y lo denuncia, ¿qué se puede hacer realmente al respecto?

Tomemos como ejemplo un phishing en redes sociales. No se puede ver qué otras cuentas de su base de usuarios fueron atacadas. A diferencia del correo electrónico, no hay forma de recuperar o poner en cuarentena el mismo mensaje que afecta a varios usuarios. No hay ninguna regla que se pueda modificar ni remitentes que se puedan bloquear. Se puede denunciar la cuenta, y quizá ocurra algo cuando el propietario del sitio web lo haga, pero es probable que para entonces el atacante ya haya conseguido lo que necesitaba y haya seguido adelante.

**La mayoría de las organizaciones simplemente bloquean las URL implicadas. Pero esto no ayuda mucho cuando los atacantes rotan rápidamente sus dominios de phishing: para cuando se bloquea un sitio, otros tres ya lo han reemplazado.**

Los usuarios inician sesión en aplicaciones como LinkedIn, X, WhatsApp, Signal e incluso en foros como Reddit desde sus portátiles o dispositivos móviles del trabajo. Y, dado que se encuentran enlaces maliciosos en buscadores (también conocidos como malvertising), pueden incluso encontrarlos mientras navegan por la web con normalidad.

**En resumen: cualquier lugar donde alguien externo a la organización pueda contactar a sus usuarios representa una oportunidad para el phishing. De hecho, en la mayoría de estos casos, las personas esperan ser contactadas por desconocidos.**

También es un mito que las campañas no se puedan dirigir de la misma manera en estas plataformas, que sean más aleatorias y, por lo tanto, menos peligrosas. Por ejemplo, las cuentas de redes sociales son de las más fáciles de crear en masa o de tomar el control para los atacantes.

**Según el último informe DBIR de Verizon, más del 60% de las credenciales encontradas en los registros de robo de información provenían de redes sociales.**  También es probable que utilicen inicios de sesión de un solo factor. Si un atacante logra tomar el control de una cuenta y usarla para comunicarse de forma fiable con uno de sus empleados, tiene muchas más probabilidades de éxito que con un correo electrónico no solicitado común.

Los anuncios maliciosos también pueden estar dirigidos. Por ejemplo, Google Ads puede orientarse a búsquedas procedentes de ubicaciones geográficas específicas, adaptarse a coincidencias de dominios de correo electrónico específicos o a tipos de dispositivos específicos (por ejemplo, ordenador, móvil, etc.).

Si conoce la ubicación de su organización objetivo, puede adaptar el anuncio a esa ubicación. Los sitios de phishing también suelen incluir parámetros de carga condicional para entregar la carga maliciosa solo en condiciones específicas; por ejemplo, solo si el visitante proviene de un enlace de campaña de correo electrónico específico, o solo si pertenece a una organización específica, usa un navegador específico, utiliza un rango de IP específico, etc.

**Incluso si el atacante solo logra contactar a su empleado en su dispositivo personal, esto puede utilizarse para comprometer su cuenta corporativa.**  Basta con observar la brecha de seguridad de Okta de 2023, donde un atacante aprovechó que un empleado de Okta había iniciado sesión en un perfil personal de Google en su dispositivo de trabajo.

**Esto significó que todas las credenciales guardadas en su navegador se sincronizaron con su dispositivo personal, incluida una cuenta de servicio del sistema de atención al cliente que proporcionaba acceso a 134 clientes.** Cuando su dispositivo personal fue hackeado, también lo fueron todas sus credenciales de trabajo.

Por lo tanto, existe un amplio margen para que el phishing no basado en correo electrónico resulte en campañas de phishing dirigidas. En todo caso, podría decirse que es menos trabajo para el atacante lanzar estas campañas que no son de correo electrónico que realizar el trabajo preliminar necesario para crear y consolidar la reputación del remitente.

### Caso práctico 1: Spear-phishing en LinkedIn

Recientemente, los atacantes lanzaron una campaña de Spear-phishing en LinkedIn dirigida a ejecutivos de empresas tecnológicas. Las víctimas fueron atacadas a través de un mensaje directo de LinkedIn de otro ejecutivo sobre una falsa oportunidad de inversión. La cuenta del remitente había sido comprometida y utilizada para contactar con objetivos de alto valor.

El ataque condujo a la víctima a través de una cadena de páginas personalizadas alojadas en sitios legítimos (una conocida técnica de evasión de detección) como Google Sites, Google Search y Microsoft Dynamics, antes de mostrar una página de phishing de intermediario que suplantaba la identidad de Google Workspace, y posteriormente una página de phishing de AitM que robaba sesiones.

### Caso práctico 2: Publicidad maliciosa en la Búsqueda de Google

Una empresa fue atacada con un anuncio de Google dirigido, diseñado para parecer muy convincente y posicionado encima del anuncio legítimo. Esto aprovechó que muchos usuarios buscan páginas de inicio de sesión en lugar de acceder al sitio web a través de marcadores. En lugar del inicio de sesión real, el enlace dirigía a la víctima a una página AITM que robaba sesiones.

Posteriormente, se rastreó el origen de esto a una campaña de Scattered Spider.

![Imagen 01](/assets/172/172-02.jpg)

### ¿Qué puede hacer un atacante con una cuenta comprometida?

Es importante considerar el panorama general cuando se trata de una vulnerabilidad de phishing moderna.

**La mayoría de los ataques de phishing se centran en plataformas empresariales en la nube como Microsoft y Google, o en proveedores de identidad especializados como Okta.** Tomar el control de una de estas cuentas no solo otorga acceso a las aplicaciones y datos principales de la aplicación respectiva, sino que también permite al atacante usar el inicio de sesión único (SSO) para iniciar sesión en cualquier aplicación conectada en la que el empleado inicie sesión con su cuenta.

Esto le da acceso a prácticamente todas las funciones y conjuntos de datos empresariales esenciales de su organización. A partir de este punto, es mucho más fácil atacar a otros usuarios de estas aplicaciones internas, utilizando aplicaciones de mensajería interna como Slack o Teams, o técnicas como el SAMLjacking para convertir una aplicación en un lugar de encuentro para otros usuarios que intentan iniciar sesión.

**El compromiso de una sola cuenta puede convertirse rápidamente en una brecha de seguridad multimillonaria que afecta a toda la empresa.**





