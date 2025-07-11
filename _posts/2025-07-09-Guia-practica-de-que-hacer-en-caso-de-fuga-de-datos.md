---
title: "¿Qué hago si se filtran datos sensibles en mi empresa?"
date: 2025-07-09 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, news, tecnología]
description: Guía práctica de qué hacer en caso de que ya hayas sido afectado con una fuga de datos.
image: /assets/148/preview1.png
---

## ¿Qué hacer si se filtran datos sensibles?  

**Guía práctica para actuar sin entrar en pánico**

Como parte de la serie Gestión de Incidentes de Seguridad de la Información: árbol de documentos necesarios, a continuación dejamos una guía práctica de qué hacer en caso de que ya hayas sido afectado con una fuga de datos, producto de, por ejemplo, un ingreso no autorizado a tu red o de ataque de ransomware.

Una filtración de datos sensibles puede generarse por un ataque externo, un error interno o un descuido cotidiano. Sea cual sea la causa, lo importante es actuar con rapidez, coordinación y criterio. 

### Fases de la gestión de incidentes: ¿qué hacer en cada etapa? 

**Detección: Identificar que algo está ocurriendo.**

-  Analizar alertas y/o logs de los sistemas, reportes internos o externos, publicaciones en redes, etc. 
-  Validar si efectivamente existe información filtrada o se trata de una "fake news",
-  Activar el Procedimiento de Gestión de Incidentes de seguridad de la Información, si aplica.

**Análisis: Entender el alcance del incidente.**

- ¿Qué tipo de información se filtró? ¿A cuántas personas afecta? ¿Afecta a procesos o aplicaciones críticas? ¿Afecta el normal funcionamiento del negocio?
  
    - Credenciales
    - Datos personales (clientes, empleados, proveedores, etc.)
    - Información confidencial (contratos, estrategias)
    - Información financiera
    - Historias clínicas o datos sensibles
    - Información del negocio o a la cadena de suministro
    - ...

- ¿Cómo ocurrió? (phishing, error humano, malware, acceso indebido, ransomware, etc.) 
- ¿Desde cuándo estaba sucediendo? ¿Sigue ocurriendo?
- ¿Cuál fue el canal de comunicación por el cual se filtraron los datos?
- ¿Se trata de archivos, bases de datos, configuraciones, etc?

**Contención: Frenar el daño**

- Revocar los accesos y credenciales comprometidos. 
- Bloquear la propagación (cerrar sesiones, limitar red, suspender cuentas, bloquear VPN y conexiones remotas, etc). 
- Preservar evidencias (logs, correos, archivos y registros originales, capturas de pantalla, etc). 
- Estabilizar la situación

  - Reforzar las configuraciones, reglas de acceso y políticas temporales. 
  - Supervisar servicios relacionados que aún estén en riesgos. 
  - Evaluar acciones de contención con impacto mínimo en el negocio.
  - Revisar o cortar accesos a los proveedores o clientes que podrían haber sido afectados en la cadena de provisión.

**Erradicación: Elimina la causa raíz**

- Eliminar / frenar la propagación del malware (si se comprueba una infección). En lo posible, preservar los archivos relacionados (IoC) para futuros análisis.
- Corregir las fallas que habilitaron la filtración (permisos, controles, procesos, roles).
- Comprobar que no existan accesos y ejecuciones persistentes.
- Revisar otros entornos o posibles vías de contacto con el proceso, area o zona afectada.

**Restauración: Volver a operar con normalidad**

- Reactivar los sistemas afectados de forma segura (desde copias de seguridad confiables o re-intalación desde cero). NUNCA re-utilizar un sistema que había sido previamente afectado.
- Comprobar que los servicios funcionen correctamente sin comprometer seguridad.
- Documentar el proceso de restauración y los tiempos necesarios.

**Comunicación**

- Ser claros, sin sobreinformar, exagerar, minimizar, ni mentir.
- Notificar interna y externamente lo que sea necesario a quienes se considere necesario: clientes, entes reguladores, proveedores, autoridades, servicios en la nube, etc. 
- Asegurarse de cumplir con la normativa local (por ejemplo, Ley de Protección de Datos y CERT en Argentina, o GDPR si aplica).

### Preguntas frecuentes

**¿Se puede evitar una filtración de datos?**

**La respuesta corta es no,** tarde o temprano toda organización sufre una brecha interna o externa.

**¿Se puede recuperar la información que se filtró?**
**No.** Una vez que los datos son filtrados, deben considerarse comprometidos y "públicos". Dependiendo el tipo de dato y dónde se encuentre, se puede solicitar la eliminación, pero esto no garantiza el borrado real o completo si ya se difundió.

**¿Se puede pedir que los borren? ¿Cómo?**

Sí, pero depende de a quién:

- Plataformas públicas: solicitud formal por derechos de autor, imagen corporativa o daños.
- Plataformas en la nube: solicitud formal por formularios o correos de la organización.
- Colaboradores conocidos: carta de pedido o declaración de destrucción.
- Atacantes maliciosos: poco probable.

**¿Qué debería tener una nota de eliminación o declaración de destrucción de datos?**

- Datos del receptor
- Confirmación de que recibió la información por error
- Compromiso de no usar ni compartir los datos
- Confirmación de que fue eliminada sin copias
- Firma del responsable

**¿Qué pasa si los datos filtrados son personales o confidenciales?**

- Debe evaluarse si el incidente constituye una violación de datos personales. 
- Puede ser necesario notificar a la autoridad reguladora (por ejemplo, AAIP en Argentina o GDPR) y a los afectados.
- Es clave documentar todo para evitar sanciones y demostrar diligencia debida.

**¿Qué controles se pueden implementar para evitar nuevas filtraciones?**

- Segmentación de accesos, roles, permisos y privilegios adecuados por necesidad de conocimiento. 
- Eliminación y control adecuado de permisos administrativos y privilegiados.
- Accesos remotos controlados (o su eliminación completa).
- Autenticación multifactor (MFA).
- Revisión periódica de permisos.
- Sensibilización y educación continua a empleados.
- Uso de herramientas de Gestión de Identidades y Accesos (IAM), Gestión del Acceso Privilegiado (PAM) y Gestión de Identidades Privilegiadas (PIM).
- Uso de DLP (Data Loss Prevention) y/o monitoreo de comportamiento (User Entity and Behavior Analytics - UEBA).

**Credits: Bernardita Götte**

## ¿Necesitas ayuda con ciberseguridad?

En EtherGroup somos especialistas en proteger la información de tu empresa. Si has sufrido una filtración de datos o quieres prevenir futuros incidentes, contáctanos y te ayudaremos a fortalecer tu seguridad digital.

<https://ethergroup.mx/>


