---
title: "Vulnerabilidad del token de acceso de Microsoft Teams: nuevo vector de ataque para la filtración de datos"
date: 2025-11-03 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, news, tecnología, web, vulnerabilidad]
description: Una nueva técnica permite a los atacantes extraer tokens de autenticación cifrados de Microsoft Teams en Windows, lo que permite el acceso no autorizado a chats, correos electrónicos y archivos de SharePoint.
image: /assets/183/preview1.png
---

En una publicación de RandoriSec, Brahim El Fikhi, explica (video) cómo estos tokens, almacenados en una base de datos de cookies similar a Chromium, se pueden descifrar utilizando la API de protección de datos de Windows (DPAPI). Esta investigación también hace referencias a otra investigaciones previas como las de Vectra o Mr.D0x.

Este desarrollo se basa en hallazgos recientes que exponen cómo Teams almacena tokens de acceso confidenciales, lo que potencialmente permite a los atacantes hacerse pasar por usuarios y acceder a chats, correos electrónicos y documentos.

Como se describe en la publicación, Microsoft Teams incorpora una ventana del navegador utilizando el proceso msedgewebview2.exe, un componente basado en Chromium que maneja el inicio de sesión a través de los servicios en línea de Microsoft.

Durante la autenticación, este proceso escribe cookies en una base de datos SQLite de manera similar a los navegadores web tradicionales. Estas cookies contienen tokens de acceso que otorgan acceso a conversaciones de Teams, funciones de Skype e incluso a la API de Microsoft Graph para interacciones más amplias con Office 365.

Sin embargo, los navegadores Chromium modernos han reforzado sus defensas. Ahora protegen las claves de cifrado a través de un servicio IElevator basado en COM que se ejecuta con privilegios de SYSTEM, verificando la legitimidad de la persona que llama comprobando la ruta de instalación segura del ejecutable. Esta configuración exige ejecución dentro del proceso del navegador o acceso elevado de administrador para descifrar los valores de las cookies.

Por el contrario, Teams se basa en la API de protección de datos (DPAPI) más simple vinculada a la clave maestra del usuario actual, lo que hace que sus cookies sean comparativamente más fáciles de detectar una vez que se obtiene la clave de cifrado.


### Superar bloqueos de archivos con inyección de procesos

Un obstáculo clave en la investigación original fue el comportamiento en tiempo de ejecución de Teams: la aplicación bloquea su archivo de base de datos de cookies mientras se ejecuta, incluso en segundo plano, impidiendo lecturas o copias directas.

Eliminar el proceso MS-Teams.exe, como se sugiere en la publicación, alertaría a los usuarios y activaría el monitoreo de seguridad. Para abordar este "problema", los investigadores de TierZone se inspiraron en Cookie-Monster-BOF, una herramienta de código abierto que extrae cookies de procesos activos del navegador duplicando identificadores de archivos e invocando el servicio IElevator.

la nueva herramienta Teams-Cookies-BOF de Tier Zero Security reutiliza esta lógica para la aplicación de mensajería. En lugar de finalizar Teams, se ejecuta directamente dentro del proceso ms-teams.exe, potencialmente mediante secuestro de DLL o COM, para identificar procesos de vista web secundarios que mantienen identificadores abiertos para el archivo de cookies.

La herramienta adapta la técnica de explotación del navegador existente para evitar los mecanismos de bloqueo de archivos de Teams, lo que genera nuevas preocupaciones sobre la seguridad de los terminales en entornos empresariales.

![Imagen 01](/assets/183/183-01.png)

Duplica estos identificadores, lee el contenido del archivo sobre la marcha y descifra los valores utilizando la clave maestra DPAPI del usuario. Este enfoque garantiza el sigilo, ya que la herramienta imita la actividad del proceso legítimo sin interrupciones en el sistema de archivos.

En particular, la flexibilidad del BOF se extiende más allá de la inyección de Teams. Puede ejecutarse en cualquier proceso que comparta los mismos privilegios de usuario, consultando los subprocesos en todo el sistema para descargar cookies relevantes.

Si bien esto amplía su aplicabilidad, también introduce indicadores detectables, como operaciones de manejo inusuales en procesos no relacionados.

### En resumen

Los investigadores han detectado técnicas que permiten a atacantes acceder a información sensible mediante la exfiltración de cookies y tokens de acceso, todo ello gracias a la explotación del proceso ms-teams.exe y la manipulación avanzada de handles de sistema.

La explotación consiste en la inyección de código dentro del proceso legítimo de Microsoft Teams, permitiendo el acceso directo a archivos de cookies protegidos. A través del uso del Data Protection API (DPAPI) de Windows, los atacantes descifran y extraen estos datos, obteniendo así los tokens que permiten el acceso no autorizado a recursos y conversaciones de Teams. La técnica logra camuflarse como actividad legítima y evitar la detección por soluciones de seguridad tradicionales.

![Imagen 01](/assets/183/183-02.png)

El principal impacto es el secuestro de sesiones de usuario, poniendo en peligro la información empresarial, credenciales e integridad de las comunicaciones. Además, la sigilosidad del ataque favorece movimientos laterales y la posibilidad de que actores maliciosos permanezcan largos periodos de tiempo dentro del entorno corporativo. Otros productos basados en tecnologías similares también podrían verse afectados.

![Imagen 01](/assets/183/183-03.png)

![Imagen 01](/assets/183/183-04.png)

### Implicancia para los defensores
El mecanismo de descifrado refleja exactamente Cookie-Monster-BOF, empleando AES-256-GCM después de extraer el nonce y la carga útil cifrada de los valores etiquetados "v10" en la base de datos.

Una vez obtenidos, los tokens permiten llamadas API para recuperar historiales de conversaciones, leer mensajes o enviar contenido de phishing en nombre de las víctimas, lo que aumenta los riesgos en el movimiento lateral o en campañas de ingeniería social.

Tier Zero Security ha hecho pública la herramienta en GitHub y es compatible con cualquier marco C2 que admita cargas útiles de Beacon y no requiere argumentos para su uso básico.

Esta versión subraya una brecha persistente en el modelo de seguridad de Teams en comparación con los navegadores reforzados. Las organizaciones deben priorizar el monitoreo del comportamiento para la inyección de procesos, imponer la ejecución con privilegios mínimos y considerar reglas de detección de puntos finales dirigidas a accesos DPAPI o manipulaciones de controles de vistas web.

Dado que el trabajo híbrido depende en gran medida de Teams, estas vulnerabilidades resaltan la necesidad de un escrutinio continuo de los componentes integrados del navegador en las aplicaciones de productividad.

### Mitigaciones
Herramientas como GraphSpy ingieren el token para la lectura indebida de SharePoint o correos electrónicos, limitados a los permisos de Teams (por ejemplo, Chat.ReadWrite, Mail.Send). El token de actualización principal (PRT) de Microsoft se relaciona con esto, lo que permite un SSO fluido pero amplifica los riesgos de reutilización de tokens en todas las aplicaciones.

Las mitigaciones incluyen monitorear "la muerte de ms-teams.exe" o patrones inusuales de ProcMon, aplicar el cifrado vinculado a la aplicación y preferir Teams basados en web para evitar el almacenamiento local.

Rotar tokens a través de políticas de ID de Entra y auditar los registros de API para detectar anomalías. A medida que las amenazas de Teams evolucionan, las reglas EDR compatibles con DPAPI son esenciales.

Se recomienda aumentar la monitorización de actividades sospechosas sobre procesos de Teams y accesos a DPAPI, así como revisar y limitar los privilegios de las cuentas. Es crucial mantener Teams y el sistema operativo actualizados, desplegar soluciones EDR con reglas que detecten manipulaciones de handles y sesiones, y realizar auditorías periódicas. La concienciación de los usuarios sobre riesgos asociados y la adopción de políticas Zero Trust ayudarán a mitigar el riesgo.

