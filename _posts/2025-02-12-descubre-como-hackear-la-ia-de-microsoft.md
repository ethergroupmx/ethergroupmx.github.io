---
title: Descubren cómo hackear la IA de Microsoft para que filtre datos personales de los usuarios con un simple email
date: 2025-06-12 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, news, ciberataques]
description: Un agente de IA revela información confidencial de los usuarios a los que asiste.
image: /assets/142/preview1.png
---

Cualquier herramienta digital es susceptible de ser hackeada, los expertos en ciberseguridad no se cansan de recordar esto, la seguridad 100% no existe en informática. Con la inteligencia artificial, la nueva revolución tecnológica ocurre lo mismo, ya se han visto casos en los que los usuarios conseguían manipular a ChatGPT para que se saltara las normas de OpenAI. Ahora se ha descubierto una técnica para que un agente de IA revele información confidencial de los usuarios a los que asiste.

Investigadores de ciberseguridad han descubierto una nueva vulnerabilidad en Microsoft 365 Copilot, la herramienta basada en inteligencia artificial que se integra en todas las plataformas y aplicaciones para profesionales de la compañía, Microsoft Office.

Para redactar documentos de Word, crear hojas de cálculo en Excel, presentaciones en PowerPoint o transcribir videoreuniones en Teams, incluso resumir correos de Outlook. Copilot se impulsó con la colaboración de OpenAI tras la presentación de los grandes modelos de lenguaje que revolucionaron esta industria tras la presentación de ChatGPT hace un par de años.

### Ataque de cero clics

La empresa de seguridad Aim Security ha descubierto esta brecha de la que Fortune informa en exclusiva. Se trataría del primer ataque sin clics conocido en un agente de IA, esto significa que el usuario no tiene que realizar ninguna acción para ser atacado. O dicho de otra forma, no se necesita que la víctima cometa el error de hacer clic en ningún enlace para atacarle.

*El hacker puede manipular al agente de IA para que acceda a información confidencial dentro de las aplicaciones y herramientas que utiliza este usuario, sin que la persona se entere.*

Los investigadores detallan que el atacante puede hacker Microsoft 365 Copilot enviando un correo electrónico al usuario, en el que ocultan las instrucciones para Copilot. No se trata de la conocida técnica phishing con malware en un archivo o enlace. En cambio, este exploit utiliza una serie de técnicas para sugestionar al agente de IA en vez de a la persona.

Al escanear los correos electrónicos que llegan al usuario, el agente artificial recibe esas instrucciones ocultas, cuyo objetivo es volver al asistente de IA contra sí mismo

El ataque evade las protecciones integradas de Copilot, las cuales la empresa diseñó para garantizar que solo los usuarios puedan acceder a sus propios archivos, evitando exponer datos personales, confidenciales o relacionados con el cumplimiento normativo.

Igual que Copilot trabaja siguiendo las instrucciones del usuario dentro de las aplicaciones de Office, analizando documentos o generando sugerencias, la IA podría volverse un infiltrado a favor de los hackers para aportarles información confidencial.

### Microsoft corrige el fallo

Esta vez, quienes han descubierto esta vulnerabilidad antes, han sido investigadores que han trabajado de la mano con Microsoft para solucionar el problema antes de que los usuarios se vieran afectados, según ha informado el gigante tecnológico a Fortune.

Los investigadores de esta empresa de ciberseguridad dedicaron tres meses a aplicar ingeniería inversa a Microsoft 365 Copilot. La brecha se ha denominado "EchoLeak". “Encontramos esta cadena de vulnerabilidades que nos permitió implementar el equivalente al 'clic cero' para teléfonos móviles, pero para agentes de IA”, explica Aim Security.

<img src="/assets/142/142-01.png"  alt="Imagen01" width="500" height="500">

*“Ya hemos actualizado nuestros productos para mitigar este problema y no se requiere ninguna acción por parte del cliente. También estamos implementando medidas adicionales de defensa en profundidad para fortalecer aún más nuestra seguridad”,* ha dicho Microsoft.

Por suerte, los ciberdelincuentes no han encontrado esta puerta trasera para poder explotarla, pero AimSecurity advierte que este fallo no es exclusivo de Copilot, sino que tiene implicaciones en el diseño de los agentes de IA basados en LLM.

Si dirigiera una empresa que implementa agentes de IA ahora mismo, "me aterraría", dijo el investigador principal. La brecha se descubrió en enero, pero Microsoft no habría comenzado a parchear el fallo hasta cinco meses después, por lo que el equipo esperó a hacer público su descubrimiento.




