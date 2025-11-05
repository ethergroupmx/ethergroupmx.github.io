---
title: "CoPhish: nuevo ataque que roba tokens OAuth a través de agentes de Copilot Studio"
date: 2025-11-04 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, news, tecnología, web, vulnerabilidad]
description: Una nueva técnica de phishing, denominada "CoPhish", utiliza agentes de Microsoft Copilot Studio para enviar solicitudes de consentimiento OAuth fraudulentas a través de dominios legítimos y de confianza de Microsoft.
image: /assets/184/preview1.png
---

El abuso de los servicios de Microsoft para distribuir contenido malicioso no es nuevo, pero esta técnica de ataque adopta nuevas formas a medida que los servicios evolucionan. Michael Bargury ha presentado una introducción a la explotación de Copilot en sus charlas Black Hat, "Living off Microsoft Copilot" y "15 Ways to Break Your Copilot".

Esta técnica fue desarrollada por investigadores de Datadog Security Labs, quienes advirtieron en un informe a principios de esta semana que la flexibilidad de Copilot Studio introduce nuevos riesgos de phishing no documentados.

Aunque CoPhish se basa en ingeniería social, Microsoft ha confirmado que planea corregir las causas subyacentes en una futura actualización. *"Hemos investigado este informe y estamos tomando medidas para abordarlo mediante futuras actualizaciones de producto"*, declaró un portavoz de Microsoft. *"Si bien esta técnica se basa en ingeniería social, mantenemos nuestro compromiso de fortalecer nuestras experiencias de gobernanza y consentimiento, y estamos evaluando medidas de seguridad adicionales para ayudar a las organizaciones a prevenir el uso indebido"*.

### Agentes de Copilot y phishing de OAuth

Los agentes de Copilot Studio son chatbots alojados en copilotstudio.microsoft.com que los usuarios pueden crear y personalizar mediante "temas", que son flujos de trabajo que automatizan tareas específicas. Los agentes se pueden compartir en el dominio de Microsoft habilitando la función "sitio web de demostración". Dado que la URL es legítima, es más fácil que un usuario caiga en la trampa e inicie sesión.

![Imagen 01](/assets/184/184-01.png)

El tema de inicio de sesión, que autentica al usuario al iniciar una conversación con el chatbot, se puede configurar para acciones específicas, como solicitar un código de verificación o redirigir a otra ubicación o servicio.

Katie Knowles, investigadora sénior de seguridad en Datadog, afirma que un atacante puede personalizar el botón de inicio de sesión con una aplicación maliciosa, ya sea interna o externa al entorno objetivo, y podría atacar a un administrador de la aplicación incluso si no tiene acceso al entorno.

Actualmente, atacar a un usuario sin privilegios en el inquilino es posible si el atacante ya está presente en el entorno. Sin embargo, cuando cambie la política predeterminada de Microsoft, el ataque se limitará únicamente a los permisos de lectura y escritura de OneNote y cerrará la brecha para los servicios de correo electrónico, chat y calendario.

Knowles afirma que, incluso después de la actualización de Microsoft, un atacante externo aún puede atacar a un administrador de aplicaciones con una aplicación registrada externamente, ya que los cambios no se aplican a los roles con privilegios elevados.

Los usuarios con privilegios de administrador en el inquilino pueden aprobar los permisos solicitados por aplicaciones internas o externas, incluso si no están verificados (por ejemplo, si están marcados como no publicados por Microsoft o su organización).

El investigador de Datadog afirma que un ataque CoPhish comienza cuando el atacante crea una aplicación multiusuario maliciosa con el tema de inicio de sesión configurado para dirigir al proveedor de autenticación y recopilar el token de sesión.

Para obtener el token de sesión, se configura una solicitud HTTP a una URL de Burp Collaborator y se entrega la variable del token de acceso en un encabezado "token". "El ID de la aplicación (o ID del cliente), el secreto y las URL del proveedor de autenticación se utilizan para configurar los ajustes de inicio de sesión del agente", afirma Knowles en un informe publicado esta semana.

![Imagen 01](/assets/184/184-02.jpg)

Cabe destacar que la acción de redirección cuando el usuario víctima hace clic en el botón Iniciar sesión puede configurarse para redirigir a cualquier URL maliciosa, y la URL del flujo de trabajo de consentimiento de la aplicación es solo una posibilidad para el atacante.

### Ataque de CoPhish a administradores

Tras activar el sitio web de demostración del agente malicioso, un atacante puede distribuirlo a sus objetivos en campañas de phishing por correo electrónico o a través de mensajes de Teams.

Dado que la URL es legítima y el diseño de la página hacen que los usuarios puedan pensar que se trata de otro servicio de Microsoft Copilot. Knowles afirma que una pista que podría levantar sospechas es el icono de "Microsoft Power Platform", que es fácil de pasar por alto.

Un administrador que cae en la trampa y acepta los permisos de la aplicación maliciosa es redirigido a la URL de redirección OAuth [token.botframework.com] para validar la conexión del bot.

![Imagen 01](/assets/184/184-03.jpg)

*"Esto puede parecer atípico, pero es una parte estándar del proceso de autenticación de Copilot Studio que utiliza un dominio válido"*, afirman los investigadores de Datadog.

Tras completar el proceso de autenticación, el usuario no recibirá ninguna notificación sobre el reenvío de su token de sesión a Burp Collaborator ni sobre el secuestro de su sesión, pero podrá chatear con el agente.

Además, dado que el token se envió desde Copilot utilizando las direcciones IP de Microsoft, la conexión con el atacante no se mostrará en el tráfico web del usuario.

A continuación, se muestra un resumen visual de cómo funciona el ataque CoPhish y los pasos desde que la víctima accede a la aplicación maliciosa hasta que el atacante recibe el token.

![Imagen 01](/assets/184/184-04.jpg)

Microsoft informó que los clientes pueden protegerse contra ataques CoPhish limitando los privilegios administrativos, reduciendo los permisos de las aplicaciones y aplicando políticas de gobernanza.

Datadog ofrece un conjunto de consideraciones de seguridad que incluyen la implementación de una política sólida de consentimiento de aplicaciones que cubra cualquier deficiencia en la configuración básica predeterminada de Microsoft.

La empresa de monitorización y seguridad en la nube también recomienda a las organizaciones que desactiven los valores predeterminados de creación de aplicaciones de usuario y supervisen de cerca el consentimiento de las aplicaciones mediante Entra ID y los eventos de creación del agente Copilot Studio.

