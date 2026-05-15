---
title: "Vulnerabilidad en Microsoft Exchange Server LOCAL explotada mediante un correo electrónico manipulado"
date: 2026-05-15 09:00:00 
categories: [VULNERABILIDAD]
tags: [ciberseguridad, seguridad informática, servidores, vulnerabilidad]
description: Microsoft ha revelado una nueva vulnerabilidad de seguridad que afecta a las versiones locales de Exchange Server y que, según la compañía, está siendo explotada activamente.
image: /assets/252/preview1.png
---

La vulnerabilidad, identificada como CVE-2026-42897 (CVSS: 8.1), se describe como un fallo de suplantación de identidad derivado de una vulnerabilidad de secuencias de comandos entre sitios (XSS). Un investigador anónimo fue quien descubrió y reportó el problema.

"La neutralización incorrecta de la entrada durante la generación de páginas web (XSS) en Microsoft Exchange Server permite a un atacante no autorizado realizar suplantación de identidad a través de una red", indicó el gigante tecnológico en un aviso publicado el jueves.

Microsoft, que etiquetó la vulnerabilidad con la advertencia "Explotación detectada", explicó que un atacante podría explotarla enviando un correo electrónico manipulado a un usuario. Este correo, al abrirse en Outlook Web Access y bajo ciertas condiciones de interacción, podría permitir la ejecución de código JavaScript arbitrario en el navegador web.

Redmond también indicó que está proporcionando una solución temporal a través de su Servicio de Mitigación de Emergencia de Exchange, mientras prepara una solución permanente para la vulnerabilidad de seguridad. Este sericio proporcionará la mitigación automáticamente mediante una configuración de reescritura de URL y está habilitado de forma predeterminada. Si no está activado, se recomienda a los usuarios que habiliten el servicio de Windows.

Según Microsoft, Exchange Online no se ve afectado por esta vulnerabilidad. Las siguientes versiones locales de Exchange Server se ven afectadas:

- Exchange Server 2016 (cualquier nivel de actualización)
- Exchange Server 2019 (cualquier nivel de actualización)
- Exchange Server Subscription Edition (SE) (cualquier nivel de actualización)

Si el uso del Servicio de Mitigación de Emergencia de Exchange no es una opción debido a restricciones de aislamiento físico, la compañía ha descrito la siguiente serie de acciones:

- Descargue la última versión de la Herramienta de Mitigación de Exchange local (EOMT) desde aka.ms/UnifiedEOMT.
- Aplique la mitigación servidor por servidor o en todos a la vez ejecutando el script mediante una consola de administración de Exchange (EMS) con privilegios elevados:

Servidor único:

      .\EOMT.ps1 -CVE "CVE-2026-42897"

Todos los servidores:

      Get-ExchangeServer | Where-Object { $_.ServerRole -ne "Edge" } | .\EOMT.ps1-CVE "CVE-2026-42897"
    

Microsoft indicó que también está al tanto de un problema conocido en el que la mitigación muestra el mensaje "Mitigación no válida para esta versión de Exchange" en el campo Descripción. "Este problema es meramente visual y la mitigación se aplica correctamente si el estado se muestra como 'Aplicada'", afirmó el equipo de Exchange. "Estamos investigando cómo solucionarlo".


![Imagen 01](/assets/252/252-01.jpg)

Actualmente no se dispone de información sobre cómo se está explotando la vulnerabilidad, la identidad del responsable de la amenaza ni la magnitud de estos esfuerzos. Tampoco está claro quiénes son los objetivos ni si alguno de esos ataques tuvo éxito. Mientras tanto, se recomienda aplicar las medidas de mitigación recomendadas por Microsoft.
