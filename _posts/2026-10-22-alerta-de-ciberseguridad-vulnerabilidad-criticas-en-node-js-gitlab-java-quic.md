---
title: "Alerta de ciberseguridad: vulnerabilidades críticas en Node.js, GitLab, Java y QUIC"
date: 2026-10-22 09:00:00
categories: [CIBERSEGURIDAD]
tags: [GitLab, vulnerabilidades, ciberseguridad]
description: "Nuevas vulnerabilidades en Node.js, GitLab, Java y QUIC podrían permitir ejecución remota de código, eludir la validación de certificados y provocar denegación de servicio. Conoce los riesgos y las medidas de mitigación."
image: /assets/303/preview1.png
---

## Node.js

El 21 de octubre de 2026, Node.js publicó una [actualización de seguridad](https://www.linuxcompatible.org/story/nodejs-october-2026-security-update-10-vulnerabilities-patched-across-3-release-lines/) que corrige diez vulnerabilidades en sus tres líneas de versiones compatibles: **v26.12.1 (Lithium), v24.22.1 (Krypton) y v22.23.4 (Jod)**. Cuatro de los fallos tienen gravedad alta, incluido **CVE-2026-111497**, una vulnerabilidad en la descompresión Brotli que podría permitir la ejecución remota de código.

El problema puede afectar a aplicaciones que utilizan funciones como `fetch()` y Express 5, debido a la descompresión automática de respuestas Brotli. Otras vulnerabilidades afectan a TLS y DNS, permitiendo, bajo determinadas condiciones, eludir la verificación de certificados o manipular la resolución de nombres.

### Impacto

- **Ejecución remota de código:** posible compromiso de aplicaciones y servidores vulnerables.
- **Fallos en TLS:** riesgo de eludir mecanismos de verificación de certificados.
- **Vulnerabilidad en DNS:** truncamiento silencioso de nombres durante su resolución.

### Recomendaciones

- Actualizar Node.js a las versiones corregidas correspondientes a cada línea compatible.
- Verificar la versión del entorno de ejecución instalado en servidores y aplicaciones.
- No depender únicamente de `npm audit`, ya que no detecta vulnerabilidades del runtime.
- No desactivar la validación TLS mediante `rejectUnauthorized: false` o `NODE_TLS_REJECT_UNAUTHORIZED=0`.

Las versiones que finalizaron su ciclo de vida, como Node.js 20 y Node.js 25, no reciben estas correcciones. Se recomienda migrar a una versión con soporte vigente.

## GitLab

La vulnerabilidad **CVE-2026-110264** tiene una puntuación de **10.0 en CVSS**, el nivel máximo de gravedad. Bajo determinadas condiciones, permitiría a un atacante no autenticado ejecutar código arbitrario en el servidor mediante un desbordamiento de enteros durante el procesamiento de una expresión regular especialmente diseñada.

Las versiones publicadas para corregir el problema son:

- 19.5.1
- 19.4.3
- 19.3.6
- 19.2.9
- 19.1.9
- 19.0.10
- 18.11.13

**Recomendación:** actualizar GitLab a una versión corregida compatible con la rama instalada, siguiendo el [aviso oficial de seguridad](https://docs.gitlab.com/releases/patches/patch-release-gitlab-19-5-1-released/).

## Java

Oracle alertó el 21 de octubre sobre la vulnerabilidad **CVE-2026-91403**, con una puntuación de **9.1 en CVSS**, relacionada con el componente JSSE, responsable de implementar TLS y otras funciones de seguridad de las comunicaciones.

El incidente está vinculado al descubrimiento de claves privadas criptográficamente débiles generadas por la autoridad de certificación eMudhra. Oracle y OpenJDK distribuyeron medidas para dejar de confiar en los certificados intermedios comprometidos.

Entre las versiones de Oracle Java SE mencionadas en el aviso se encuentran:

- Java 8u511
- Java 11.0.33
- Java 17.0.21
- Java 21.0.13
- Java 25.0.5
- Java 27.0.1

También se identifican versiones afectadas de Oracle GraalVM.

**Recomendación:** consultar los [avisos de Oracle](https://blogs.oracle.com/security/security-alert-cve-2026-91403-released) y [OpenJDK](https://openjdk.org/groups/vulnerability/advisories/2026-10-21), verificar los certificados de confianza y aplicar las actualizaciones correspondientes.

## QUIC y HTTP/3

La investigación denominada *Header Accordions* identifica vulnerabilidades de consumo de memoria en implementaciones de HTTP/3 y QPACK. Según [FoxIO](https://foxio.io/blog/header-accordions-qpack-amplification-attacks-against-http-3-servers), se detectaron problemas en siete de las diez implementaciones examinadas.

Un atacante remoto sin autenticación podría provocar un consumo de memoria desproporcionado al enviar solicitudes relativamente pequeñas, especialmente cuando el servidor no limita adecuadamente el tamaño acumulado de las cabeceras después de su descompresión.

### Impacto

- Agotamiento de la memoria RAM del servidor.
- Degradación del rendimiento y pérdida de disponibilidad.
- Posibles ataques de denegación de servicio (DoS).

Entre los componentes mencionados se encuentran **quic-go, Cloudflare quiche, lsquic y Wireshark**.

**Recomendación:** revisar las implementaciones de HTTP/3 y QPACK utilizadas, aplicar las actualizaciones disponibles y establecer límites adecuados para el tamaño de las cabeceras y el consumo de recursos.

## Acciones prioritarias

1. **Actualizar:** instalar los parches correspondientes en Node.js, GitLab y Java.
2. **Verificar:** identificar versiones vulnerables y componentes que utilicen HTTP/3 y QPACK.
3. **Reforzar:** mantener activa la validación TLS y limitar el consumo de recursos.
4. **Monitorear:** revisar registros, conexiones inusuales y posibles señales de explotación.

La aplicación oportuna de parches y la revisión de los componentes expuestos son medidas esenciales para reducir el riesgo de ejecución de código, compromiso de comunicaciones y denegación de servicio.

