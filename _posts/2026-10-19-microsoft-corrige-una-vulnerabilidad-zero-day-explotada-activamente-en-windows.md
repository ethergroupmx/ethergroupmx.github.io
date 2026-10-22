---
title: "Microsoft corrige una vulnerabilidad Zero-Day explotada activamente en Windows"
date: 2026-10-19 09:00:00
categories: [CIBERSEGURIDAD]
tags: [Zero-Day, vulnerabilidades, ciberseguridad]
description: "Microsoft corrige una vulnerabilidad Zero-Day en Windows Shell que estaba siendo explotada activamente para evadir protecciones de seguridad. Conoce los riesgos y las recomendaciones para proteger tus sistemas."
image: /assets/304/preview1.png
---

# Microsoft corrige una vulnerabilidad Zero-Day explotada activamente en Windows

Microsoft publicó una actualización de seguridad para corregir una vulnerabilidad Zero-Day en Windows Shell que estaba siendo explotada activamente por ciberdelincuentes. Identificada como **CVE-2026-96951**, la falla tiene una puntuación de **8.8 sobre 10 en la escala CVSS** y permite eludir mecanismos de protección diseñados para advertir sobre archivos potencialmente peligrosos. <Cite refs={["turn100241search0","turn100241search10"]}/>

## ¿En qué consiste la vulnerabilidad?

El fallo afecta a Windows Shell y permite evadir las protecciones asociadas con *Mark of the Web* (MotW), una función que identifica archivos descargados de Internet para que Windows y otras aplicaciones apliquen medidas de seguridad adicionales.

Cuando esta protección funciona correctamente, puede activar advertencias de Microsoft Defender SmartScreen y las restricciones de Vista protegida de Office. Sin embargo, un archivo manipulado para aprovechar la vulnerabilidad podría eludir estas medidas y abrirse sin las advertencias habituales. <Cite refs={["turn100241search10","turn100241search14"]}/>

Para explotar el fallo, el atacante puede intentar convencer a la víctima de abrir un archivo especialmente diseñado, distribuido mediante correo electrónico, mensajería u otros medios. Por ello, la interacción del usuario representa un factor importante en el ataque.

## ¿Qué riesgos representa?

La explotación de CVE-2026-96951 puede reducir la eficacia de las defensas que ayudan a identificar archivos sospechosos antes de su ejecución. Esto aumenta el riesgo de que los usuarios interactúen con contenido malicioso sin recibir las advertencias esperadas.

Entre los principales riesgos se encuentran:

- **Evasión de controles de seguridad:** los archivos maliciosos pueden eludir determinadas advertencias de Windows.
- **Mayor exposición a ataques de phishing:** los ciberdelincuentes pueden distribuir archivos diseñados para aprovechar la vulnerabilidad.
- **Compromiso potencial de equipos:** la evasión de estas protecciones puede facilitar otras etapas de un ataque, dependiendo del contenido malicioso y de las condiciones del sistema.

La vulnerabilidad no implica por sí sola que cualquier archivo pueda tomar el control del equipo; su impacto depende de las acciones de la víctima y de las demás protecciones presentes.

## Sistemas afectados y actualización

La vulnerabilidad afecta a distintas versiones de Windows 10, Windows 11 y Windows Server. Microsoft incluyó la corrección en sus actualizaciones de seguridad de octubre de 2026. <Cite refs={["turn100241search0","turn100241search1"]}/>

Se recomienda a las organizaciones identificar los equipos que utilizan versiones afectadas y verificar que tengan instalados los parches correspondientes.

Consulta los detalles técnicos y las versiones afectadas en el [aviso oficial de Microsoft](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-96951).

## Recomendaciones de seguridad

Para reducir el riesgo de explotación, se recomienda:

1. **Instalar las actualizaciones:** aplicar los parches de seguridad de octubre de 2026 correspondientes a cada versión de Windows.
2. **Verificar los equipos:** comprobar el estado de actualización de estaciones de trabajo y servidores mediante las herramientas de administración de TI.
3. **Evitar archivos sospechosos:** no abrir archivos inesperados recibidos por correo electrónico, mensajería o sitios web.
4. **Mantener las protecciones activas:** no deshabilitar Microsoft Defender SmartScreen ni otras funciones de seguridad para evitar advertencias.
5. **Revisar la actividad sospechosa:** investigar archivos descargados o ejecutados que pudieran haber eludido las advertencias de seguridad.

## Conclusión

La explotación activa de CVE-2026-96951 demuestra la importancia de mantener Windows actualizado y conservar habilitados sus mecanismos de protección. **Las organizaciones deben priorizar la instalación de los parches y reforzar la prevención frente a archivos sospechosos**, especialmente en equipos que reciben y procesan documentos de fuentes externas.
