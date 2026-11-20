---
title: "Nuevas vulnerabilidades críticas en PHP permiten ejecución remota de código"
date: 2026-11-19 11:00:00
categories: [CIBERSEGURIDAD]
tags: [vulnerabilidades, servidores, hacking, ciberseguridad]
description: "PHP publicó actualizaciones para corregir siete vulnerabilidades de seguridad, algunas capaces de permitir ejecución remota de código en servidores afectados. Conoce los riesgos y cómo proteger tus sistemas."
image: /assets/319/preview1.png
---

El lenguaje de programación PHP vuelve a estar en el centro de las alertas de seguridad. El 19 de noviembre de 2026 se publicaron actualizaciones para corregir siete vulnerabilidades que afectan a diferentes versiones del lenguaje y que podrían comprometer la seguridad de aplicaciones y servidores web.

Entre los problemas identificados se encuentran fallos de uso de memoria después de su liberación (*use-after-free*), condiciones de carrera y errores en el procesamiento de solicitudes HTTP. Algunas de estas vulnerabilidades pueden permitir la ejecución remota de código (RCE), lo que representa un riesgo importante para los sistemas que utilizan versiones afectadas.

## ¿Qué está pasando con PHP?

PHP es una tecnología ampliamente utilizada para desarrollar sitios web, plataformas de comercio electrónico, sistemas empresariales y aplicaciones dinámicas.

Las nuevas vulnerabilidades identificadas afectan distintos componentes internos del lenguaje, incluyendo el manejo de sesiones, la administración de memoria y el procesamiento de solicitudes.

De acuerdo con los reportes de seguridad, varias de estas fallas tienen una puntuación CVSS de 9.2, considerada crítica, debido a su potencial para comprometer los sistemas afectados.

Uno de los aspectos más preocupantes es que ciertas condiciones de explotación no requieren que el atacante tenga una cuenta o se autentique previamente en la aplicación.

## Las vulnerabilidades identificadas

Entre los problemas corregidos se encuentran los siguientes:

- **CVE-2026-115560:** un error en la validación de entradas que podría provocar ejecución remota de código, modificación de archivos, corrupción de sesiones o denegación de servicio.
- **CVE-2026-129182:** una falla de tipo *use-after-free* que puede provocar corrupción de memoria y permitir la ejecución de código.
- **CVE-2026-126714:** una condición de carrera (TOCTOU) en el manejo de archivos de sesión que podría facilitar la ejecución de código arbitrario.
- **CVE-2026-129289:** una interpretación inconsistente de solicitudes HTTP que podría permitir ejecutar código PHP controlado por un atacante.
- **CVE-2026-129474:** otro problema de uso de memoria liberada que puede derivar en ejecución remota de código bajo determinadas condiciones.
- **CVE-2026-129481:** una falla en la limpieza de sesiones que podría provocar corrupción de memoria y comprometer los procesos de PHP.
- **CVE-2026-129496:** una vulnerabilidad en la caché de zona horaria que puede provocar fallos en los procesos y, bajo ciertas condiciones, ejecución de código.

No todas las vulnerabilidades tienen las mismas condiciones de explotación. Algunas requieren configuraciones específicas o características particulares de la aplicación; sin embargo, su gravedad justifica una revisión inmediata de los entornos afectados.

## ¿Qué sistemas están afectados?

Las vulnerabilidades afectan distintas ramas de PHP, principalmente las versiones 8.2, 8.3, 8.4 y 8.5.

Las versiones corregidas publicadas incluyen:

| Rama de PHP | Versión corregida |
|---|---|
| PHP 8.2 | 8.2.36 |
| PHP 8.3 | 8.3.37 |
| PHP 8.4 | 8.4.28 |
| PHP 8.5 | 8.5.13 |
| PHP 8.6 | 8.6.0 |

Las instalaciones que utilizan versiones anteriores deben verificar si se encuentran dentro del rango afectado y aplicar las actualizaciones correspondientes.

## ¿Qué pueden hacer las organizaciones para protegerse?

La principal recomendación es actualizar PHP a una versión corregida y comprobar que todos los componentes del entorno utilicen las versiones adecuadas.

Además, los administradores de sistemas y responsables de TI deberían:

1. **Identificar las versiones instaladas:** revisar los servidores web, aplicaciones y servicios que utilizan PHP.
2. **Aplicar las actualizaciones:** instalar las versiones corregidas disponibles para cada rama de PHP.
3. **Revisar la configuración de sesiones:** comprobar el uso de `session.upload_progress.enabled` y desactivar esta función si no es necesaria, como medida temporal frente a determinados vectores de ataque.
4. **Revisar las aplicaciones web:** identificar configuraciones inseguras, manejo inadecuado de sesiones y componentes desactualizados.
5. **Monitorear los servidores:** revisar registros de actividad, errores inusuales y solicitudes sospechosas que puedan indicar intentos de explotación.

Es importante señalar que desactivar funciones específicas puede reducir la exposición a determinados ataques, pero no sustituye la instalación de los parches de seguridad.

## La importancia de mantener actualizada la infraestructura

Las vulnerabilidades en componentes ampliamente utilizados, como PHP, pueden tener consecuencias que van más allá de una aplicación individual. Un servidor comprometido podría exponer información, permitir modificaciones no autorizadas o afectar la disponibilidad de los servicios empresariales.

Por ello, mantener actualizados los entornos de desarrollo y producción, realizar evaluaciones periódicas de seguridad y monitorear la infraestructura son acciones fundamentales para reducir los riesgos.

La seguridad de las aplicaciones también depende de mantener protegida la infraestructura sobre la que funcionan.
