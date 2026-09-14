---
title: "La policía alemana accede a datos WhatsApp, Telegram, Signal en sus investigaciones"
date: 2026-09-13 09:00:00
categories: [CIBERSEGURIDAD]
tags: [android, vulnerabilidades, ciberseguridad, móviles]
description: "Investigadores descubren una cadena de exploits que puede llevar desde una videollamada VoLTE hasta el acceso completo al kernel de Android en dispositivos con módem Unisoc."
image: /assets/292/preview1.png
---

Un artículo publicado por Netzpolitik investiga una técnica utilizada por organismos policiales alemanes  (BKA) para interceptar comunicaciones de WhatsApp, Telegram, Signal y otros mensajeros sin instalar un "Staatstrojaner" (software espía estatal) en el dispositivo.

La motivación de la unidad es operativa: la generalización del cifrado de extremo a extremo (E2EE) impide que una intervención telefónica tradicional obtenga el contenido en claro. En lugar de romper el cifrado, **los investigadores vinculan un nuevo cliente Web/Desktop a la cuenta de la persona investigada, de modo similar a agregar un segundo dispositivo autorizado.**

Las principales instancias que reconstruye la investigación son:

- 1. **Caso WhatsApp, 2020.** Un matrimonio entregó voluntariamente sus teléfonos durante una declaración para que la policía examinara mensajes intercambiados con su hija. Mientras tenía acceso físico a los dispositivos, la policía activó de forma encubierta WhatsApp Web, escaneando el QR correspondiente y obteniendo así acceso persistente a comunicaciones futuras. El problema es que el consentimiento había sido otorgado para consultar determinados mensajes, no para crear un acceso permanente a las cuentas.

- 2. **Caso Telegram, 2022.** En una investigación por comercialización ilegal de sustancias, el BKA consiguió vincularse secretamente a la cuenta Telegram del sospechoso. Antes de que éste detectara y desconectara el dispositivo policial unas horas después, el BKA había descargado aproximadamente cuatro meses de conversaciones anteriores. Esos chats fueron utilizados en una condena a tres años y nueve meses de prisión. El caso llegó al Bundesgerichtshof (BGH - Tribunal Federal de Justicia), que el 20 de enero de 2026 consideró que ese tipo de acceso constituye una Quellen-TKÜ, es decir, interceptación de telecomunicaciones directamente en la fuente. La ley sólo permite recoger comunicaciones producidas desde la autorización judicial; no habilita a descargar indiscriminadamente conversaciones anteriores. Por esta irregularidad, el BGH anuló parcialmente la sentencia y ordenó volver a juzgar parte del caso.

- 3. **Uso sistemático por la Aduana alemana (Zollkriminalamt, ZKA).** Un documento interno obtenido por Netzpolitik revela que el ZKA comenzó a probar esta técnica a fines de 2023. Según el propio organismo, el piloto produjo "éxitos investigativos significativos" contra la delincuencia grave y organizada, por lo que desde el 1 de agosto de 2025 se incorporó como capacidad operativa permanente, con asistencia técnica de otros organismos federales. Sin embargo, el ZKA no publicó casos concretos, cifras ni métricas que permitan verificar independientemente esos resultados.

El punto jurídico central es que los clientes Web/Desktop comerciales presentan un problema adicional: al vincular una cuenta pueden sincronizar mensajes anteriores, contactos y otras informaciones, e incluso técnicamente permitir el envío de mensajes desde la identidad intervenida. La ley alemana exige que la evidencia esté técnicamente limitada a los datos autorizados. Para acceder a información histórica se necesitaría, en principio, una autorización que exige delitos especialmente graves y condiciones más estrictas.

En síntesis, el hallazgo relevante no es que Alemania haya "roto" el cifrado de WhatsApp o Signal, sino que sus investigadores están evitando el cifrado mediante la vinculación encubierta de dispositivos, una técnica eficaz pero jurídicamente muy sensible porque puede otorgar técnicamente más acceso del que autoriza una orden judicial.
