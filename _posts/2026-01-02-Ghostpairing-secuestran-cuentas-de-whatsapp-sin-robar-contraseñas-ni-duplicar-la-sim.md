---
title: "GhostPairing: secuestran cuentas de WhatsApp sin robar contraseñas ni duplicar la SIM"
date: 2026-01-02 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, redes, hacking, vulnerabilidad, móviles]
description: La campaña de fraude denominada GhostPairing permite a los atacantes tomar el control de cuentas de WhatsApp sin necesidad de robar contraseñas, interceptar códigos SMS ni clonar la tarjeta SIM. 
image: /assets/208/preview1.png
---

El ataque se basa en ingeniería social y en el abuso de la funcionalidad legítima de vinculación de dispositivos de la propia aplicación.

A diferencia de otros ataques habituales contra servicios de mensajería, GhostPairing no requiere vulnerabilidades técnicas, malware ni acceso previo al dispositivo de la víctima. El éxito del ataque depende exclusivamente de engañar al usuario para que autorice, sin ser consciente de ello, la vinculación de su cuenta a un dispositivo controlado por el atacante.

El ataque suele comenzar con un mensaje aparentemente legítimo, a menudo enviado desde una cuenta previamente comprometida de un contacto conocido, que incluye un enlace con algún pretexto ("mira esta foto", "¿eres tú en este vídeo?"). Dicho enlace dirige a una página fraudulenta que simula ser un servicio de Meta o un visor de contenidos.

Al acceder al enlace, la víctima es redirigida a una página que imita la apariencia de una pantalla de inicio de sesión de Facebook. Allí se le solicita que introduzca su número de teléfono. Tras este paso, el sitio pide confirmar el acceso escaneando un código QR con WhatsApp o ingresando un código numérico enviado al dispositivo. Aunque ambas opciones existen de forma legítima, los investigadores señalan que el método del código numérico es el más utilizado en esta campaña.

![Imagen 01](/assets/208/208-01.jpeg)

Lo que el usuario no percibe es que, al completar estos pasos, está siguiendo exactamente el proceso de vinculación de dispositivos de WhatsApp. **De manera involuntaria, está autorizando que su cuenta se conecte a un nuevo navegador, que en realidad pertenece al ciberdelincuente.** Para WhatsApp, la acción es completamente válida: el sistema interpreta que el propietario de la cuenta ha añadido un nuevo dispositivo de forma consciente.

### Una vez vinculada la cuenta, el atacante puede:

- Leer conversaciones y acceder a archivos compartidos.
- Enviar mensajes en nombre de la víctima, facilitando la propagación del fraude.
- Mantener el acceso de forma persistente mientras el dispositivo malicioso siga vinculado.

Este tipo de ataques pone de relieve los riesgos derivados del abuso de funcionalidades legítimas y la dificultad de mitigarlos únicamente con controles técnicos. La principal defensa sigue siendo la concienciación del usuario.

### Como medidas de protección, se recomienda:

- Revisar periódicamente el apartado "Dispositivos vinculados" en WhatsApp y eliminar accesos sospechosos.
- Desconfiar de enlaces inesperados, incluso si proceden de contactos conocidos.
- Activar la verificación en dos pasos en la cuenta de WhatsApp.
- Cerrar inmediatamente todas las sesiones vinculadas si se sospecha un compromiso.

