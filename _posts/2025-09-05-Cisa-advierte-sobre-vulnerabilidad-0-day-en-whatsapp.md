---
title: "CISA advierte sobre vulnerabilidad 0-Day en WhatsApp explotada en ataques"
date: 2025-09-05 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, ciberseguridad, redes, vulnerabilidad]
description: CISA ha emitido un aviso urgente sobre una vulnerabilidad de día cero recientemente revelada en el servicio de mensajería WhatsApp de Meta Platforms ( CVE-2025-55177 ). 
image: /assets/164/preview1.png
---

Esta falla, categorizada bajo CWE-863: Autorización incorrecta, permite que un actor no autorizado manipule mensajes de sincronización de dispositivos vinculados y fuerce a un dispositivo de destino a buscar y procesar contenido de una URL controlada por el atacante. 

### Conclusiones clave

  - CVE-2025-55177 explota una falla de autenticación en la sincronización de dispositivos de WhatsApp para obtener URL maliciosas.
  - El error CWE-863 habilita RCE y ha aparecido en phishing. 
  - CISA exige el parche del 2 de septiembre o la suspensión de WhatsApp.

Se insta encarecidamente a las organizaciones y usuarios individuales a aplicar las mitigaciones proporcionadas por el proveedor antes del 23 de septiembre de 2025 o a interrumpir su uso hasta que haya parches seguros disponibles.

## Vulnerabilidad de autorización de WhatsApp (CVE-2025-55177)

CVE-2025-55177 surge de una verificación de autorización incompleta en el manejo de mensajes de sincronización de dispositivos vinculados por parte de WhatsApp. 

Cuando un usuario vincula su cliente de WhatsApp en un nuevo dispositivo, los mensajes de sincronización propagan los historiales de chat y los medios en múltiples puntos finales. 

Debido a la verificación incorrecta del origen y la integridad del mensaje, un usuario no relacionado puede crear una carga útil de sincronización maliciosa que haga referencia a una URL arbitraria. El cliente vulnerable:

- Analizar el mensaje de sincronización sin verificar el token de autorización del remitente.
- Inicie una solicitud GET a la URL controlada por el atacante para recuperar datos de carga útil adicionales.
- Ejecutar o mostrar contenido como una página web impulsada por JavaScript en el contexto del cliente de WhatsApp.

Esta cadena de eventos permite efectivamente la ejecución remota de código (RCE) o la suplantación de contenido, que podrían aprovecharse para lanzar cargas útiles que van desde scripts de robo de credenciales hasta ransomware. 

Si bien aún no está confirmado si CVE-2025-55177 se ha integrado en campañas de ransomware activas, ya se ha observado su explotación en operaciones de phishing dirigidas.

![Tabla](/assets/164/164-01.png)

## Mitigaciones

El aviso de CISA instruye a todas las entidades que utilizan WhatsApp, particularmente aquellas en sectores de infraestructura crítica, a implementar los siguientes pasos de inmediato:

Aplique el parche lanzado el 2 de septiembre de 2025 por Meta Platforms, como se describe en su Aviso de seguridad .

Hacer cumplir las instrucciones de configuración del proveedor, garantizando que los mensajes de sincronización de dispositivos vinculados solo se permitan desde puntos finales autenticados.

Siga los requisitos de la Directiva Operacional Vinculante (BOD) 22-01 de la Agencia de Seguridad de Infraestructura y Ciberseguridad para la seguridad del servicio en la nube, incluida la autenticación multifactor y el registro sólido de todos los eventos de sincronización.

CISA recomienda suspender el uso de WhatsApp hasta que se implemente una versión segura. Las organizaciones también deben supervisar el tráfico de red para detectar solicitudes HTTP salientes inusuales provenientes de clientes de WhatsApp, lo que podría indicar intentos de explotación.

Como precaución, los equipos de seguridad deben validar la instalación del parche y verificar que la versión corregida rechace correctamente las cargas de sincronización no autorizadas.


