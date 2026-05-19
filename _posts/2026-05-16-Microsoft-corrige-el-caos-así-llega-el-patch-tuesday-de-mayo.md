---
title: "Microsoft corrige el caos: así llega el Patch Tuesday de mayo 2026"
date: 2026-05-16 09:00:00 
categories: [VULNERABILIDAD]
tags: [vulnerabilidad, ciberseguridad, sistema operativo]
description: El nuevo Patch Tuesday de Microsoft incluye 138 actualizaciones de seguridad, 30 de ellas críticas, en un ciclo sin vulnerabilidades zero-day conocidas.
image: /assets/255/preview1.png
---

Este Patch Tuesday corrige 30 vulnerabilidades "críticas", de las cuales 14 son de ejecución remota de código, 2 de elevación de privilegios y 1 es una vulnerabilidad de divulgación de información.

El número de errores en cada categoría de vulnerabilidad se detalla a continuación:

- 61 vulnerabilidades de elevación de privilegios
- 6 vulnerabilidades de omisión de funciones de seguridad
- 31 vulnerabilidades de ejecución remota de código
- 14 vulnerabilidades de divulgación de información
- 8 vulnerabilidades de denegación de servicio
- 13 vulnerabilidades de suplantación de identidad

Por lo tanto, el número de vulnerabilidades no incluye las de Mariner, Azure, Copilot, Microsoft Teams y Microsoft Partner Center, que Microsoft corrigió a principios de este mes. También se excluyeron 131 vulnerabilidades de Microsoft Edge/Chromium que Google corrigió este mes.

Para obtener más información sobre las actualizaciones no relacionadas con la seguridad publicadas hoy, consulte nuestros artículos dedicados a las actualizaciones acumulativas KB5089549 y KB5087420 de Windows 11 y a la actualización de seguridad extendida KB5087544 de Windows 10.

**Microsoft no ha revelado ninguna vulnerabilidad de día cero en el Patch Tuesday de este mes.**

Una de las vulnerabilidades más graves corregidas por Microsoft es la CVE-2026-41096 (CVSS: 9.8), un fallo de desbordamiento de búfer basado en el montón que afecta al DNS de Windows y que podría permitir a un atacante no autorizado ejecutar código a través de la red.

*"Un atacante podría explotar esta vulnerabilidad enviando una respuesta DNS especialmente diseñada a un sistema Windows vulnerable, lo que provocaría que el cliente DNS procesara incorrectamente la respuesta y corrompiera la memoria", declaró Microsoft. "En ciertas configuraciones, esto podría permitir al atacante ejecutar código de forma remota en el sistema afectado sin autenticación".*

Como parte de las actualizaciones de hoy, Microsoft ha corregido numerosas vulnerabilidades en Microsoft Office, Word y Excel que podrían permitir la ejecución remota de código. Estas vulnerabilidades se explotan abriendo archivos maliciosos, lo que puede resultar en la ejecución remota de código. Dado que muchas de estas vulnerabilidades pueden explotarse a través del panel de vista previa, se recomienda encarecidamente actualizar Microsoft Office lo antes posible, especialmente si suele recibir archivos adjuntos.

Microsoft también ha corregido varias vulnerabilidades de gravedad crítica e importante:

- **CVE-2026-42826 (CVSS: 10.0):** Exposición de información confidencial a un usuario no autorizado en Azure DevOps que permite a un atacante no autorizado divulgar información a través de la red. (No requiere ninguna acción por parte del cliente).
- **CVE-2026-33109 (CVSS: 9.9):** Control de acceso inadecuado en Azure Managed Instance para Apache Cassandra que permite a un atacante autorizado ejecutar código a través de la red. (No requiere ninguna acción por parte del cliente).
- **CVE-2026-42898 (CVSS: 9.9):** Vulnerabilidad de inyección de código en Microsoft Dynamics 365 (local) que permite a un atacante autorizado ejecutar código a través de la red. Jack Bicer, director de investigación de vulnerabilidades en Action1, describió esta vulnerabilidad como un fallo crítico que permite a un atacante autenticado con bajos privilegios ejecutar código arbitrario a través de la red manipulando los datos de la sesión del proceso dentro de Dynamics CRM.
- **CVE-2026-42823 (CVSS: 9.9):** Un control de acceso inadecuado en Azure Logic Apps que permite a un atacante autorizado elevar privilegios en una red.
- **CVE-2026-41089 (CVSS: 9.8):** Un desbordamiento de búfer basado en pila en Windows Netlogon que permite a un atacante no autorizado ejecutar código en una red sin necesidad de iniciar sesión ni tener acceso previo, mediante el envío de una solicitud de red especialmente diseñada a un servidor Windows que actúa como controlador de dominio.
- **CVE-2026-33823 (CVSS: 9.6):** Una autorización inadecuada en Microsoft Teams que permite a un atacante autorizado divulgar información en una red. (No requiere ninguna acción por parte del cliente).
- **CVE-2026-35428 (CVSS: 9.6):** Una vulnerabilidad de inyección de comandos en Azure Cloud Shell que permite a un atacante no autorizado suplantar identidades en una red. (No requiere ninguna acción por parte del cliente).
- **CVE-2026-40379 (CVSS: 9.3)** - Exposición de información confidencial a un actor no autorizado en Azure Entra ID que permite a un atacante no autorizado suplantar identidades en una red. (No requiere ninguna acción por parte del cliente)
- **CVE-2026-40402 (CVSS: 9.3)** - Vulnerabilidad de liberación de memoria en Windows Hyper-V que permite a un atacante no autorizado obtener privilegios de SYSTEM y acceder al entorno del host Hyper-V.
- **CVE-2026-41103 (CVSS: 9.1)** - Implementación incorrecta del algoritmo de autenticación en el complemento Microsoft SSO para Jira y Confluence que permite a un atacante no autorizado obtener acceso no autorizado a Jira o Confluence como un usuario válido y realizar acciones con los mismos permisos que la cuenta comprometida.
- **CVE-2026-33117 (CVSS: 9.1):** Una autenticación incorrecta en Azure SDK que permite a un atacante no autorizado eludir una función de seguridad a través de una red.
- **CVE-2026-42833 (CVSS: 9.1):** Una ejecución con privilegios innecesarios en Microsoft Dynamics 365 (local) que permite a un atacante autorizado ejecutar código a través de una red y obtener la capacidad de interactuar con las aplicaciones y el contenido de otros inquilinos.
- **CVE-2026-33844 (CVSS: 9.0):** Una validación de entrada incorrecta en Azure Managed Instance para Apache Cassandra que permite a un atacante autorizado ejecutar código a través de una red. (No requiere ninguna acción por parte del cliente).
- **CVE-2026-40361 (CVSS: 8.4):** Una vulnerabilidad de uso después de la liberación de memoria en Microsoft Office Word que permite a un atacante no autorizado ejecutar código localmente sin requerir la interacción del usuario.
- **CVE-2026-40364 (CVSS: 8,4):** una vulnerabilidad de confusión de tipos en Microsoft Office Word que permite a un atacante no autorizado ejecutar código localmente sin necesidad de interacción del usuario.

**Otras vulnerabilidades interesantes**

- **CVE-2026-35421:** vulnerabilidad de ejecución remota de código en Windows GDI: Esta vulnerabilidad puede explotarse abriendo un archivo Enhanced Metafile (EMF) malicioso con Microsoft Paint.
- **CVE-2026-40365:** vulnerabilidad de ejecución remota de código en Microsoft SharePoint Server: Un atacante autenticado puede realizar un ataque basado en la red que ejecuta código de forma remota en un servidor SharePoint.
- **CVE-2026-41096:** vulnerabilidad de ejecución remota de código en el cliente DNS de Windows: Un servidor DNS controlado por un atacante podría enviar una respuesta DNS especialmente diseñada a un sistema Windows vulnerable, lo que provocaría que el cliente DNS procesara incorrectamente la respuesta y corrompiera la memoria. Esto permitiría al atacante ejecutar código en el sistema vulnerable de forma remota.

### Hallazgos con AI (MDASH)

Microsoft ha presentado un nuevo sistema multimodelo basado en inteligencia artificial (IA), llamado MDASH, para facilitar la detección y corrección de vulnerabilidades a gran escala. Además, ha indicado que algunos clientes lo están probando en una versión preliminar privada limitada.

MDASH, acrónimo de Multi-model Agentic Scanner Harness (Arnés de escaneo agente multimodelo), está diseñado como un sistema independiente del modelo que utiliza agentes de IA personalizados para diferentes clases de vulnerabilidades, con el fin de descubrir, validar y demostrar de forma autónoma defectos explotables en bases de código complejas como Windows.

![Imagen 01](/assets/255/255-01.webp)

**"A diferencia de los enfoques de un solo modelo, este sistema coordina más de 100 agentes de IA especializados a través de un conjunto de modelos de vanguardia y simplificados para descubrir, analizar y demostrar errores explotables de principio a fin"**, afirmó Taesoo Kim, vicepresidente de seguridad agente de Microsoft.
