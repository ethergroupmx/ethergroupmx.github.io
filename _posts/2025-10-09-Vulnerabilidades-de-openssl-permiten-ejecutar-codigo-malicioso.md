---
title: "Vulnerabilidades de OpenSSL permiten ejecutar código malicioso y recuperar claves privadas de forma remota"
date: 2025-10-09 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberseguridad, vulnerabilidad, malware]
description: El Proyecto OpenSSL ha publicado un aviso de seguridad crítico que aborda tres vulnerabilidades significativas que podrían permitir a atacantes ejecutar código remoto y potencialmente recuperar claves criptográficas privadas.
image: /assets/176/preview1.png
---

Estas fallas afectan a múltiples versiones de OpenSSL en diferentes plataformas y podrían provocar corrupción de memoria, ataques de denegación de servicio y acceso no autorizado a materiales criptográficos sensibles.

Las organizaciones que utilizan proveedores criptográficos personalizados compatibles con SM2 deben priorizar la aplicación inmediata de parches para evitar la vulneración de la clave privada mediante ataques de análisis de tiempo.

**La solución inmediata requiere actualizar a las versiones parcheadas: OpenSSL 3.5.4, 3.4.3, 3.3.5, 3.2.6, 3.0.18, 1.1.1zd (soporte premium) y 1.0.2zm (soporte premium).**

### Vulnerabilidad de Corrupción de Memoria (CVE-2025-9230)

La vulnerabilidad más grave implica operaciones de memoria fuera de límites en la funcionalidad de desbloqueo de claves de cifrado (KEK) RFC 3211, identificada como CVE-2025-9230 con gravedad moderada.

Esta falla afecta a las **versiones 3.5, 3.4, 3.3, 3.2, 3.0, 1.1.1 y 1.0.2 de OpenSSL** y se produce cuando las aplicaciones intentan descifrar mensajes de sintaxis de mensajes criptográficos (CMS) mediante cifrado basado en contraseña (PWRI).

La vulnerabilidad activa operaciones de lectura y escritura fuera de los límites permitidos, lo que podría provocar daños en la memoria que los atacantes podrían aprovechar para ejecutar código arbitrario o provocar fallos del sistema.

Investigadores de seguridad de Aisle Research, dirigidos por Stanislav Fort, descubrieron esta vulnerabilidad el 9 de agosto de 2025. **El exploit requiere condiciones específicas,** como el uso de cifrado con contraseña en los mensajes CMS, lo que limita la superficie de ataque, ya que la compatibilidad con el cifrado PWRI rara vez se implementa en entornos de producción. Sin embargo, **una explotación exitosa podría comprometer completamente el sistema mediante la ejecución remota de código.**

La vulnerabilidad existe en la implementación del algoritmo de desbloqueo KEK, donde una verificación insuficiente de límites permite operaciones de memoria más allá de los límites del búfer asignado. 

Los módulos FIPS no se ven afectados, ya que la implementación de CMS opera fuera del límite FIPS de OpenSSL.

### Vulnerabilidad de canal lateral de temporización (CVE-2025-9231)

La segunda vulnerabilidad, CVE-2025-9231, introduce una vulnerabilidad de canal lateral de temporización en la implementación del algoritmo criptográfico SM2 en plataformas ARM de 64 bits.

Esta vulnerabilidad **permite a atacantes remotos recuperar claves privadas** mediante el análisis de temporización de las operaciones de cálculo de firmas, según el aviso de OpenSSL. La vulnerabilidad **afecta a las versiones 3.5, 3.4, 3.3 y 3.2 de OpenSSL,** específicamente en arquitecturas ARM de 64 bits. Las versiones anteriores, como la 3.1, 3.0, 1.1.1 y 1.0.2, no se ven afectadas debido a diferentes enfoques de implementación.

Si bien OpenSSL no admite directamente los certificados SM2 en contextos de seguridad de la capa de transporte (TLS), los proveedores personalizados podrían exponer esta vulnerabilidad en entornos de producción.

Los ataques de canal lateral de temporización aprovechan las variaciones en los tiempos de ejecución de las operaciones criptográficas para extraer información confidencial.

La implementación del algoritmo SM2 presenta discrepancias de temporización durante los procesos de generación de firmas, lo que crea patrones medibles que los atacantes pueden analizar para reconstruir el material de la clave privada.

Este vector de ataque requiere acceso a la red para medir las variaciones de tiempo en múltiples operaciones criptográficas, lo que lo hace viable para escenarios de explotación remota.

### Vulnerabilidad de operaciones de lectura fuera de límites (CVE-2025-9231)

La vulnerabilidad CVE-2025-9232 implica operaciones de lectura fuera de límites en la gestión de no_proxy del cliente HTTP para direcciones IPv6, aunque esto presenta un riesgo menor, ya que solo afecta a la denegación de servicio.







