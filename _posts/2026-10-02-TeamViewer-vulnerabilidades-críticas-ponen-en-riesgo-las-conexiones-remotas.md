---
title: "TeamViewer: vulnerabilidades críticas ponen en riesgo las conexiones remotas"
date: 2026-10-02 09:00:00
categories: [VULNERABILIDAD]
tags: [vulnerabilidad, ciberseguridad, TeamViewer, seguridad informática]
description: "TeamViewer advirtió a sus clientes sobre varias vulnerabilidades de alta gravedad que afectan a su software cliente y host, y recomendó aplicar inmediatamente los parches de seguridad disponibles."
image: /assets/298/preview1.png
---

La empresa de software de acceso remoto TeamViewer advirtió a sus clientes que deben **aplicar inmediatamente los parches de seguridad disponibles** para corregir una serie de vulnerabilidades de alta gravedad que afectan a su software **TeamViewer Full Client y Host**.

Los fallos afectan a versiones para **Windows, Linux y macOS** y podrían permitir que un atacante realice acciones no autorizadas en un equipo comprometido, incluyendo la ejecución de código y la elevación de privilegios.

### Una vulnerabilidad especialmente crítica

La vulnerabilidad de mayor gravedad corresponde a **CVE-2026-92370**, relacionada con una omisión del control de acceso a sesiones remotas. El problema se origina en una debilidad en los mecanismos utilizados por TeamViewer para controlar el acceso dentro de sus aplicaciones Full Client y Host.

En determinadas condiciones, un atacante remoto podría aprovechar este fallo para realizar acciones que normalmente deberían estar restringidas, lo que potencialmente podría llevar a la **ejecución remota de código** en el sistema afectado.

Este escenario es especialmente relevante en entornos empresariales, donde TeamViewer puede utilizarse para administrar estaciones de trabajo, servidores y otros dispositivos de manera remota.

### Cinco vulnerabilidades de seguridad

Además de CVE-2026-92370, TeamViewer corrigió otros cuatro problemas de seguridad:

- **CVE-2026-19743:** vulnerabilidad de *Path Traversal*, que podría permitir acceder o manipular archivos fuera de las ubicaciones previstas por la aplicación.
- **CVE-2026-92368:** desbordamiento de búfer en el *heap*, una condición que puede provocar corrupción de memoria y potencialmente permitir la ejecución de código.
- **CVE-2026-92369:** condición de carrera de tipo **TOCTOU (Time-of-Check to Time-of-Use)**, que puede ser aprovechada para modificar un recurso después de que haya sido validado pero antes de que sea utilizado.
- **CVE-2026-92371:** problema de validación incorrecta de rutas, que podría permitir manipular ubicaciones de archivos y ejecutar acciones con privilegios superiores.

Algunos de estos fallos requieren acceso local al equipo, pero podrían ser especialmente peligrosos cuando un atacante ya ha conseguido algún nivel de acceso al sistema.

### Riesgo de escalada de privilegios

Uno de los principales riesgos asociados a estas vulnerabilidades es la posibilidad de que un atacante **eleve sus privilegios**.

En sistemas Windows, determinadas condiciones podrían permitir alcanzar privilegios de **NT AUTHORITY\SYSTEM**, mientras que en Linux podrían llegar hasta privilegios de **root**.

Esto significa que un atacante que inicialmente solo tuviera permisos limitados podría, dependiendo de las condiciones de explotación, obtener un nivel de control mucho mayor sobre el dispositivo.

Con privilegios elevados, un atacante podría instalar malware, modificar configuraciones, acceder a información sensible, crear nuevos mecanismos de persistencia o utilizar el equipo como punto de entrada hacia otros sistemas de la organización.

### TeamViewer recomienda actualizar a la versión 15.82

TeamViewer recomienda a todos sus usuarios **actualizar a la versión 15.82**, que incorpora las correcciones necesarias para solucionar estas vulnerabilidades.

La compañía señaló que, hasta el momento, **no existen evidencias de códigos de explotación públicos ni de explotación activa** de estas vulnerabilidades. Sin embargo, esto no significa que el riesgo deba considerarse bajo.

Las vulnerabilidades que afectan a herramientas de acceso remoto suelen recibir especial atención por parte de los ciberdelincuentes debido a que estas aplicaciones tienen acceso legítimo a los sistemas y pueden utilizarse para realizar tareas administrativas.

### ¿Por qué es importante para las empresas?

Las soluciones de acceso remoto representan un objetivo atractivo para los atacantes porque pueden proporcionar una vía legítima para interactuar con los equipos de una organización.

En un escenario de ataque, una cuenta o aplicación de acceso remoto comprometida podría utilizarse para:

- Obtener acceso no autorizado a estaciones de trabajo.
- Ejecutar comandos o aplicaciones maliciosas.
- Robar información confidencial.
- Instalar malware o ransomware.
- Crear mecanismos de persistencia.
- Obtener privilegios administrativos.
- Utilizar un equipo comprometido para desplazarse hacia otros sistemas de la red.
- Interrumpir operaciones o afectar servicios críticos.

Por este motivo, las organizaciones deben considerar las herramientas de acceso remoto como parte de su **superficie crítica de ataque** y mantenerlas actualizadas y correctamente configuradas.

### TeamViewer también ha sido utilizado por ciberdelincuentes

El riesgo no se limita únicamente a las vulnerabilidades de software. Durante los últimos años, las herramientas legítimas de acceso remoto han sido utilizadas por grupos de ciberdelincuentes como parte de sus ataques.

Los grupos de ransomware y otros actores maliciosos pueden aprovechar herramientas como TeamViewer para obtener acceso remoto sin necesidad de desplegar inicialmente herramientas de administración propias. Esto puede dificultar la detección, ya que el software utilizado puede ser legítimo y estar instalado con autorización.

Por ello, las empresas deben diferenciar entre **uso legítimo y actividad anómala** dentro de sus sistemas de acceso remoto.

### Recomendaciones de seguridad

Ante la publicación de estas vulnerabilidades, se recomienda a las organizaciones que utilicen TeamViewer:

1. **Actualizar TeamViewer a la versión 15.82 o una versión posterior disponible y soportada.**
2. Identificar todos los equipos que tengan instalado **TeamViewer Full Client o Host**.
3. Revisar que las instalaciones en Windows, Linux y macOS estén correctamente actualizadas.
4. Revisar los registros de TeamViewer y del sistema en busca de conexiones o actividades inusuales.
5. Limitar el acceso remoto únicamente a los usuarios que realmente lo necesiten.
6. Utilizar contraseñas robustas y, cuando esté disponible, autenticación multifactor.
7. Revisar periódicamente las cuentas y permisos asociados a las herramientas de acceso remoto.
8. Supervisar conexiones remotas realizadas fuera del horario habitual o desde ubicaciones desconocidas.
9. Mantener soluciones de seguridad y sistemas operativos actualizados.
10. Aplicar políticas de mínimo privilegio para reducir el impacto de una posible explotación.

### Una actualización que no debería posponerse

Aunque actualmente no se ha informado de explotación activa de estas vulnerabilidades, la recomendación es **no esperar a que aparezca un exploit público para realizar la actualización**.

Las herramientas de acceso remoto forman parte de la infraestructura utilizada diariamente por muchas organizaciones y, precisamente por el nivel de acceso que pueden proporcionar, cualquier vulnerabilidad que afecte sus mecanismos de autenticación, control de acceso o privilegios debe tratarse con prioridad.

**La actualización a TeamViewer 15.82 permite corregir los cinco problemas de seguridad identificados y reducir la superficie de ataque asociada a estas vulnerabilidades.**
