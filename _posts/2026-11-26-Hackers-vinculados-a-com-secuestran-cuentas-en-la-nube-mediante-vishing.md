---
title: "Hackers vinculados a Com secuestran cuentas en la nube mediante llamadas fraudulentas"
date: 2026-11-26 12:00:00
categories: [CIBERATAQUES]
tags: [vishing, phishing, ransomware, ciberataques, ciberseguridad, cloud]
description: "Ciberdelincuentes vinculados a Com utilizan llamadas fraudulentas para robar credenciales, secuestrar cuentas corporativas en la nube y extraer información confidencial para extorsionar a las organizaciones."
image: /assets/321/preview1.png
---

Grupos de ciberdelincuentes vinculados a Com están utilizando llamadas telefónicas fraudulentas para obtener acceso a cuentas corporativas en la nube, robar información confidencial y extorsionar a las organizaciones afectadas.

De acuerdo con una investigación de Palo Alto Networks Unit 42, desde agosto de 2026 se han identificado múltiples campañas de *vishing* (phishing por voz) que han comprometido entornos empresariales. Los ataques han afectado principalmente a organizaciones de servicios financieros, atención médica y servicios legales en Estados Unidos, Reino Unido y Australia, aunque también se han identificado objetivos en sectores como tecnología, transporte, manufactura, construcción, seguros y farmacéutica.

Las organizaciones atacadas comparten una característica: administran grandes volúmenes de información corporativa sensible, cuya exposición puede generar consecuencias legales, regulatorias y económicas.

## Suplantación del personal de TI para obtener acceso

Los ataques comienzan generalmente con llamadas telefónicas en las que los delincuentes se hacen pasar por integrantes del departamento de soporte técnico o personal de TI. Bajo el argumento de resolver supuestos problemas de autenticación, convencen a los empleados de acceder a páginas fraudulentas diseñadas para imitar los portales legítimos de sus organizaciones.

Estas páginas utilizan técnicas de intermediario (*Adversary-in-the-Middle*, AiTM), que permiten capturar credenciales de acceso y tokens de sesión, incluso cuando la víctima completa los procesos de autenticación multifactor (MFA).

Una vez obtenida la información, los atacantes registran sus propios dispositivos como métodos de autenticación, consiguiendo mantener el acceso a las cuentas comprometidas. También recurren a redes de proxies residenciales y servicios VPN comerciales para dificultar la identificación de sus conexiones.

## Robo de información en plataformas empresariales

Después de comprometer las cuentas, los ciberdelincuentes aprovechan herramientas y servicios legítimos de la infraestructura cloud para desplazarse dentro de los entornos corporativos y extraer información.

Entre las plataformas afectadas se encuentran Microsoft 365, OneDrive y SharePoint. En algunos incidentes, los atacantes utilizaron scripts desarrollados en Python para automatizar la recopilación de correos electrónicos y archivos almacenados en estos servicios.

También se identificaron actividades relacionadas con aplicaciones de terceros autorizadas mediante OAuth, generación de credenciales temporales y modificaciones de reglas de correo electrónico para ocultar actividades sospechosas o dificultar la detección.

En determinados casos, los delincuentes enviaron mensajes internos mediante Microsoft Teams para informar a los empleados sobre el supuesto robo de información y dirigirlos a sitios alojados en la red Tor, donde iniciaban los procesos de extorsión.

## Extensiones maliciosas amplían el alcance del ataque

La investigación también identificó una extensión maliciosa para navegadores basada en Chromium, distribuida bajo el nombre de "Google Chrome".

Esta extensión, instalada mediante la activación del modo desarrollador, podía realizar diversas acciones para obtener información de los dispositivos comprometidos, entre ellas:

- Registrar las pulsaciones del teclado mediante funciones de *keylogging*.
- Robar cookies de autenticación y datos almacenados en el navegador.
- Capturar códigos QR relacionados con procesos de inicio de sesión y autenticación multifactor.
- Transmitir imágenes de la cámara web.
- Capturar pantallas, acceder al portapapeles y controlar la navegación mediante mecanismos de acceso remoto.

Estas capacidades representan un riesgo adicional, ya que permiten obtener información más allá de las cuentas corporativas directamente comprometidas.

## La evolución de las campañas de extorsión

Los investigadores identificaron varios grupos relacionados con estas actividades, entre ellos Bling Libra, también conocido como ShinyHunters, y distintos clústeres identificados como CL-CRI-1116, CL-CRI-1147, CL-CRI-1182, CL-CRI-1192, CL-CRI-1264 y CL-CRI-1274.

Además, se documentó el uso de herramientas de phishing como Doko's Panel, diseñadas para interceptar sesiones autenticadas y facilitar el acceso a plataformas empresariales como SharePoint, Salesforce, DocuSign y Slack.

Según Unit 42, estos grupos están evolucionando sus métodos de operación y reduciendo su dependencia del cifrado de archivos característico del ransomware tradicional. En su lugar, priorizan el acceso a cuentas legítimas, la extracción de información y la extorsión, lo que les permite avanzar con mayor rapidez y aprovechar herramientas que ya forman parte de los entornos empresariales.

## ¿Cómo pueden protegerse las organizaciones?

Este tipo de campañas demuestra que las amenazas actuales no dependen exclusivamente de vulnerabilidades técnicas. La ingeniería social y el robo de sesiones pueden comprometer incluso entornos que cuentan con mecanismos de autenticación adicionales.

Para reducir estos riesgos, las organizaciones deben fortalecer sus controles de identidad y acceso mediante medidas como:

- **Autenticación multifactor resistente al phishing:** implementar métodos como FIDO2 o passkeys y evitar depender exclusivamente de códigos de verificación.
- **Verificación de solicitudes de soporte:** establecer procedimientos para confirmar la identidad del personal de TI antes de autorizar cambios de acceso o autenticación.
- **Monitoreo de cuentas cloud:** identificar inicios de sesión inusuales, nuevos dispositivos MFA, aplicaciones OAuth no autorizadas y descargas masivas de información.
- **Control de extensiones:** restringir la instalación de complementos de navegador y permitir únicamente aquellos aprobados por la organización.
- **Capacitación de usuarios:** preparar al personal para reconocer llamadas sospechosas, páginas de inicio de sesión fraudulentas y solicitudes inesperadas de autenticación.

La protección de los entornos cloud requiere una estrategia que combine tecnología, monitoreo y concientización. Una llamada aparentemente legítima puede convertirse en el punto de entrada para comprometer información crítica, por lo que verificar cada solicitud de acceso es fundamental para mantener la seguridad de una organización.
