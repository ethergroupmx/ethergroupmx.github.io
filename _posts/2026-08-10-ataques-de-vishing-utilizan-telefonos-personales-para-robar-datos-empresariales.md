---
title: "UNC6671: ataques de vishing utilizan teléfonos personales para robar datos empresariales"
date: 2026-08-10 09:00:00
categories: [CIBERSEGURIDAD]
tags: [vishing, phishing, ciberseguridad, ciberataques, ingeniería social, seguridad informática]
description: "UNC6671 utiliza llamadas falsas de soporte TI para engañar a empleados y comprometer cuentas y servicios empresariales."
image: /assets/285/preview1.png
---

Los ciberdelincuentes están llevando las campañas de ingeniería social más allá del correo electrónico. Un grupo identificado como UNC6671 está utilizando llamadas telefónicas para hacerse pasar por personal de soporte de TI y engañar a empleados para que entreguen sus credenciales y códigos de autenticación.

La campaña resulta especialmente preocupante porque los atacantes contactan a los empleados a través de sus teléfonos móviles personales, utilizando supuestas migraciones de seguridad, problemas con las cuentas o actualizaciones urgentes como pretexto.

De acuerdo con información de Google Threat Intelligence Group (GTIG) y Mandiant, los ataques han afectado a organizaciones de servicios financieros, capital privado y servicios profesionales. Los atacantes buscan comprometer plataformas empresariales en la nube y aplicaciones SaaS, incluyendo Microsoft 365 y Okta.

### ¿Qué es el vishing?

El vishing es una modalidad de phishing que utiliza llamadas telefónicas para manipular a las víctimas.

En lugar de enviar un correo electrónico con un enlace malicioso, el atacante establece una conversación directa con el empleado y utiliza técnicas de ingeniería social para generar confianza y urgencia.

El supuesto técnico puede afirmar que:

- La cuenta presenta un problema de seguridad.
- Es necesario realizar una migración urgente.
- Debe actualizarse el sistema de autenticación.
- Hay que configurar nuevamente MFA.
- Se detectó actividad sospechosa en la cuenta.
- Es necesario acceder a un portal para resolver un supuesto incidente.

El objetivo es conseguir que la víctima actúe rápidamente sin verificar que la solicitud sea legítima

### El ataque comienza con una llamada

UNC6671 ha destacado por contactar a empleados directamente en sus números de teléfono personales.

En algunos casos, los atacantes pueden incluso falsificar el número telefónico utilizado por el verdadero servicio de soporte para hacer que la llamada parezca legítima.

Durante la conversación, el supuesto técnico puede proporcionar un enlace que lleva a una página de inicio de sesión falsa.

El sitio puede imitar la apariencia de Microsoft, Okta u otros servicios corporativos para evitar levantar sospechas.

### El objetivo: robar credenciales y sesiones

Las páginas utilizadas en estos ataques emplean infraestructura conocida como Adversary-in-the-Middle (AiTM).

Este tipo de ataque permite al ciberdelincuente situarse entre el usuario y el servicio legítimo para interceptar información de autenticación.

De esta manera, los atacantes pueden intentar obtener:

- Usuarios y contraseñas.
- Tokens de autenticación.
- Códigos relacionados con MFA.
- Sesiones autenticadas.
- Información necesaria para acceder a servicios corporativos.

Esto demuestra que activar MFA por sí solo no siempre es suficiente cuando los usuarios son engañados para autenticarse a través de una infraestructura controlada por un atacante.

## Una cuenta puede abrir la puerta a múltiples servicios

El problema aumenta cuando una organización utiliza un proveedor de identidad (IdP) conectado con múltiples aplicaciones SaaS.

Una vez comprometida una identidad, los atacantes pueden aprovechar las relaciones de confianza existentes para acceder a diferentes servicios sin necesidad de comprometer cada aplicación individualmente.

Esto puede convertir una sola cuenta comprometida en un punto de entrada a:

- Correo corporativo.
- Documentos y almacenamiento.
- Aplicaciones SaaS.
- Herramientas de colaboración.
- Información financiera.
- Datos de clientes.
- Sistemas internos.

Según CrowdStrike, los atacantes pueden utilizar una sesión autenticada para desplazarse por el ecosistema SaaS de una organización.

### Los atacantes también buscan mantener el acceso

El robo de credenciales puede ser solamente el comienzo.

UNC6671 también ha sido asociado con técnicas para mantener la persistencia en las cuentas comprometidas. Entre ellas se encuentra el registro de dispositivos MFA controlados por los atacantes y la eliminación de dispositivos MFA legítimos.

También se han observado intentos de eliminar correos de restablecimiento de contraseña y alertas de seguridad para dificultar la detección del ataque.

Por esta razón, cambiar una contraseña no siempre es suficiente después de una intrusión. Es necesario revisar sesiones activas, métodos de autenticación, dispositivos registrados y actividad reciente.

### Cómo reconocer una llamada de vishing?

Los empleados deben prestar especial atención cuando una llamada relacionada con TI presenta alguna de estas características:

1. Te presionan para actuar inmediatamente

Frases como: 

> "Tu cuenta será bloqueada si no haces esto ahora."

La urgencia es una de las herramientas favoritas de la ingeniería social.

2. Te solicitan una contraseña

El personal legítimo de TI no debería pedirte tu contraseña.

3. Te solicitan un código MFA

Nunca compartas códigos de autenticación recibidos por SMS, aplicaciones autenticadoras o dispositivos de seguridad.

4. Te proporcionan un enlace

Especialmente si te piden iniciar sesión inmediatamente.

5. Insisten en utilizar tu teléfono personal

Una llamada inesperada a tu celular relacionada con una supuesta emergencia informática debe verificarse mediante los canales oficiales.

6. No quieren que contactes al soporte oficial

Esta es una señal de alerta especialmente importante.

### ¿Qué debe hacer un empleado?

Si recibes una llamada sospechosa:

1. No compartas información.

No proporciones contraseñas, códigos MFA, tokens ni información confidencial.

2. No abras enlaces proporcionados durante la llamada.

Aunque la página parezca idéntica al portal corporativo.

3. Finaliza la llamada.

Contacta directamente al área de TI utilizando los canales oficiales de la empresa.

4. Reporta el intento.

Informa a seguridad o TI para que puedan investigar si otros empleados recibieron llamadas similares.

5. Si proporcionaste información, avisa inmediatamente.

No esperes a comprobar si ocurrió algo. El equipo de seguridad puede necesitar revocar sesiones, cambiar credenciales y revisar la cuenta.

## ¿Cómo pueden protegerse las empresas?

Las organizaciones pueden reducir significativamente el riesgo combinando controles técnicos con capacitación continua.

### Implementar MFA resistente al phishing

Las organizaciones deberían avanzar hacia mecanismos de autenticación resistentes al phishing, como passkeys y tecnologías basadas en FIDO2/WebAuthn.

Estas soluciones dificultan que una página falsa pueda utilizar las credenciales obtenidas mediante ingeniería social.

### Proteger las identidades

También es recomendable:

- Integrar aplicaciones SaaS con SSO.
- Implementar controles de sesión.
- Restringir la autenticación desde ubicaciones o redes no confiables.
- Requerir dispositivos administrados por la empresa.
- Supervisar cambios en los métodos MFA.
- Revisar registros del proveedor de identidad.
- Detectar registros sospechosos de dispositivos MFA.
- Alertar sobre accesos anómalos.

### La capacitación también es una medida de seguridad

Los controles tecnológicos son importantes, pero los empleados siguen siendo un objetivo fundamental para los atacantes.

Una capacitación efectiva debe enseñar a los usuarios que el soporte de TI no debe solicitar contraseñas ni códigos MFA y que cualquier solicitud inesperada debe verificarse mediante un canal independiente.

Los ejercicios de simulación de phishing y vishing también pueden ayudar a identificar comportamientos de riesgo y reforzar los procedimientos de reporte.

### El teléfono personal también forma parte de la superficie de ataque

Una de las principales lecciones de esta campaña es que el perímetro de seguridad empresarial ya no termina en la oficina.

Cuando los empleados utilizan sus dispositivos personales para acceder a servicios corporativos, esos dispositivos y canales de comunicación pueden convertirse en objetivos para los ciberdelincuentes.

UNC6671 demuestra que una llamada aparentemente normal puede ser el primer paso para comprometer una identidad y, posteriormente, acceder a múltiples servicios empresariales.


## Conclusión

Los ataques de UNC6671 muestran cómo los grupos de extorsión están combinando ingeniería social, vishing y técnicas de robo de sesiones para atacar las identidades corporativas.

El atacante no necesariamente necesita explotar una vulnerabilidad en Microsoft 365, Okta u otra plataforma. Puede intentar engañar a un empleado, robar sus datos de autenticación y utilizar una sesión legítima para acceder al entorno empresarial.

Por ello, las organizaciones deben combinar:

- Capacitación continua.
- MFA resistente al phishing.
- Controles de identidad y acceso.
- Dispositivos administrados.
- Monitoreo de sesiones y actividad.
- Respuesta rápida ante incidentes.

### Recuerda

El verdadero soporte de TI nunca debería pedirte tu contraseña ni tu código MFA por teléfono.

Si recibes una llamada sospechosa, detente, verifica por un canal oficial y repórtala.

La seguridad de la empresa también depende de cada usuario.

Fuente: [https://thehackernews.com/2026/08/unc6671-vishing-attacks-target-personal.html](https://thehackernews.com/2026/08/unc6671-vishing-attacks-target-personal.html)
