---
title: "Enlace compartido de ChatGPT podía exponer conversaciones privadas"
date: 2026-11-02 09:00:00
categories: [CIBERSEGURIDAD]
tags: [IA, vulnerabilidades, ciberseguridad, ciberataques]
description: "Una vulnerabilidad en los enlaces compartidos de ChatGPT permitía ejecutar código en la sesión de una víctima y acceder a conversaciones privadas. OpenAI ya corrigió el fallo."
image: /assets/309/preview1.png
---

Una vulnerabilidad de seguridad en ChatGPT permitió que un enlace compartido especialmente diseñado ejecutara código dentro de la sesión de un usuario y accediera a conversaciones privadas. El fallo fue descubierto por investigadores de la empresa de seguridad Parameter y reportado a OpenAI mediante su programa de recompensas por errores.

El caso demuestra que incluso los enlaces que parecen legítimos pueden convertirse en una vía de ataque cuando existen fallas en los componentes de una aplicación web.

## ¿Cómo funcionaba el ataque?

Los atacantes podían preparar una conversación de ChatGPT con contenido diseñado para aprovechar una vulnerabilidad en la función de vista previa (*Preview*).

En la versión más confiable del ataque, la víctima solo tenía que abrir el enlace y pulsar el botón de vista previa. En otra variante desarrollada por los investigadores, la vista previa se abría automáticamente, por lo que bastaba con visitar el enlace.

No era necesario instalar programas, descargar archivos ni iniciar sesión en una cuenta controlada por el atacante.

El problema permitía que código malicioso se ejecutara dentro de la sesión autenticada de la víctima, utilizando los permisos disponibles en su cuenta.

## ¿Qué información podía quedar expuesta?

Durante las pruebas controladas, los investigadores demostraron que era posible:

- Consultar la lista de conversaciones recientes del usuario.
- Abrir conversaciones privadas que no habían sido compartidas con el atacante.
- Extraer fragmentos de esas conversaciones y enviarlos a un servidor externo.

Debido al acceso obtenido, los investigadores señalaron que el alcance potencial podía ir más allá de la lectura de mensajes.

Sin embargo, Parameter no reportó explotación de esta vulnerabilidad contra usuarios reales. Las pruebas se realizaron de manera controlada entre cuentas independientes.

## ¿Cuál fue la causa de la vulnerabilidad?

El ataque combinó varias debilidades en componentes de la aplicación web.

ChatGPT utiliza una función de vista previa que permite representar contenido HTML en un entorno aislado. Este aislamiento estaba diseñado para impedir que el contenido accediera directamente a la página principal.

Sin embargo, los investigadores identificaron un problema en la comunicación entre los elementos de la página y una biblioteca matemática llamada MathLive, utilizada para mostrar contenido interactivo.

El componente aceptaba determinados mensajes sin verificar adecuadamente su origen y permitía introducir contenido HTML sin la validación necesaria. Esto hizo posible que el contenido de la vista previa cruzara los límites de seguridad previstos y consiguiera ejecutar código con acceso a la sesión de ChatGPT.

La vulnerabilidad surgió de la combinación de estos errores, no simplemente del uso de enlaces compartidos.

## ¿Qué hizo OpenAI para corregir el problema?

OpenAI recibió el reporte el 18 de octubre de 2026 y, tras reproducir el fallo, implementó una corrección en dos versiones de la interfaz web de ChatGPT.

De acuerdo con la información publicada por The Hacker News, para el 26 de octubre ambas versiones ya rechazaban los mensajes utilizados en el ataque. La empresa clasificó el problema como P1, su categoría de mayor gravedad dentro del reporte mencionado.

Los investigadores publicaron los detalles técnicos el 28 de octubre, una vez aplicada la corrección.

**Los usuarios no necesitan instalar una actualización ni realizar cambios específicos en su cuenta para corregir esta vulnerabilidad**, ya que la solución se implementó del lado de OpenAI.

## ¿Qué lecciones deja este incidente?

Este caso recuerda que las herramientas de inteligencia artificial también pueden presentar riesgos de seguridad relacionados con la privacidad y el manejo de información.

Para las empresas, es importante considerar las siguientes medidas:

- **Verificar los enlaces recibidos:** incluso si parecen provenir de una plataforma conocida, especialmente cuando llegan de forma inesperada.
- **Mantener las aplicaciones actualizadas:** las correcciones de seguridad ayudan a reducir la exposición a vulnerabilidades conocidas.
- **Proteger la información confidencial:** evitar compartir datos sensibles en herramientas digitales sin evaluar previamente sus condiciones de uso y protección.
- **Revisar las herramientas de inteligencia artificial:** identificar qué aplicaciones utilizan los colaboradores y qué información empresarial pueden procesar.
- **Evaluar los controles de seguridad:** comprobar que las aplicaciones y sus componentes validen correctamente los datos recibidos y mantengan el aislamiento entre contenidos.

## Conclusión

La vulnerabilidad de ChatGPT demuestra que una función aparentemente cotidiana, como compartir una conversación, puede convertirse en un vector de ataque cuando se combina con fallas en los controles de seguridad.

Aunque OpenAI corrigió el problema y no se reportó explotación real, el incidente subraya la importancia de evaluar las herramientas de inteligencia artificial como parte de la estrategia de ciberseguridad de las organizaciones.

**En Ethergroup ayudamos a las empresas a identificar riesgos, fortalecer sus controles de seguridad y utilizar la tecnología de forma más segura.**

Fuente: [The Hacker News — A Shared ChatGPT Link Could Run Attacker Code in Your Session and Read Private Chats](https://thehackernews.com/2026/10/a-shared-chatgpt-link-could-run.html)
