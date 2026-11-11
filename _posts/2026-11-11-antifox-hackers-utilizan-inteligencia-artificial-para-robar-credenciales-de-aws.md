---
title: "AntiFox: hackers utilizan inteligencia artificial para robar credenciales de AWS"
date: 2026-11-11 11:00:00
categories: [HACKING]
tags: [IA, ciberataques, ciberseguridad, pentesting, cloud computing, hacking]
description: "Investigadores vinculan AntiFox, una plataforma de pentesting basada en inteligencia artificial, con ataques que roban credenciales de AWS, acceden a secretos de producción y comprometen entornos en la nube."
image: /assets/313/preview1.png
---

# AntiFox: la inteligencia artificial detrás de ataques que comprometieron secretos de AWS

La inteligencia artificial está transformando la forma en que se realizan las pruebas de seguridad, pero también está abriendo nuevas oportunidades para los ciberdelincuentes. Investigadores de ciberseguridad identificaron una campaña en la que **AntiFox**, una plataforma autónoma de pentesting impulsada por inteligencia artificial, fue vinculada con ataques dirigidos a servidores web y entornos de Amazon Web Services (AWS).

De acuerdo con una investigación de Arctic Wolf Labs, la infraestructura que alojaba interfaces de AntiFox fue relacionada con actividades maliciosas que permitieron obtener credenciales, explorar servicios en la nube y acceder a información confidencial de entornos de producción.

## ¿Qué es AntiFox y cómo funciona?

AntiFox es una plataforma de pruebas de penetración que utiliza agentes de inteligencia artificial para automatizar diferentes etapas de una evaluación de seguridad.

Su funcionamiento permite ejecutar tareas como:

- Reconocimiento de activos y servicios expuestos.
- Identificación de superficies de ataque.
- Detección y explotación de vulnerabilidades.
- Recopilación de evidencias.
- Generación de informes técnicos.

A diferencia de las herramientas tradicionales que se concentran principalmente en identificar vulnerabilidades, AntiFox está diseñado para coordinar distintas tareas mediante agentes autónomos, facilitando la ejecución de procesos completos de pentesting.

Sin embargo, estas capacidades también pueden ser aprovechadas con fines maliciosos cuando se utilizan contra sistemas sin autorización.

## ¿Cómo se desarrollaron los ataques?

Los investigadores identificaron diferentes actividades relacionadas con esta campaña. Una de ellas comenzó con el compromiso de una aplicación web expuesta a internet que operaba sobre Microsoft Internet Information Services (IIS).

Después de obtener acceso, los atacantes utilizaron el proceso `w3wp.exe`, encargado de ejecutar aplicaciones web en IIS, para crear una puerta trasera conocida como *web shell*.

A través de ella realizaron distintas acciones:

1. **Exploración del servidor:** ejecutaron comandos para identificar el contexto de ejecución, revisar permisos y explorar directorios.
2. **Búsqueda de información:** localizaron archivos de configuración como `web.config`, que pueden contener parámetros de conexión y credenciales.
3. **Obtención de credenciales:** revisaron cadenas de conexión a bases de datos y configuraciones de aplicaciones.
4. **Extracción de archivos:** copiaron configuraciones y registros hacia directorios accesibles desde internet.
5. **Intento de acceso interno:** utilizaron credenciales encontradas para intentar conectarse a una base de datos de producción.

La vulnerabilidad específica que permitió ejecutar código en el servidor IIS no fue identificada por los investigadores.

## Credenciales de AWS: el siguiente objetivo

En otros incidentes relacionados, los atacantes utilizaron credenciales válidas de AWS para explorar diferentes servicios de la plataforma.

Mediante identidades de AWS Identity and Access Management (IAM), realizaron solicitudes a servicios como:

- **Amazon S3:** almacenamiento de archivos y objetos.
- **Amazon EC2:** infraestructura de servidores virtuales.
- **AWS Lambda:** ejecución de funciones.
- **AWS Secrets Manager:** administración de credenciales y secretos.
- **Amazon RDS:** bases de datos administradas.
- **AWS KMS:** administración de claves criptográficas.

Aunque gran parte de las solicitudes fueron rechazadas por falta de permisos, algunas operaciones tuvieron éxito.

Uno de los hallazgos más relevantes fue una solicitud exitosa para recuperar un secreto de producción mediante la operación `GetSecretValue` de AWS Secrets Manager.

También se identificaron operaciones sobre objetos almacenados en Amazon S3, incluyendo lectura, copia y eliminación de información.

Esto demuestra que una credencial comprometida puede convertirse en un punto de entrada para explorar otros servicios y acceder a recursos que deberían permanecer protegidos.

## La inteligencia artificial acelera los ciberataques

El caso de AntiFox refleja una tendencia creciente: el uso de herramientas autónomas para ejecutar actividades que anteriormente requerían una mayor intervención humana.

Los agentes de inteligencia artificial pueden coordinar tareas, analizar resultados y continuar con diferentes etapas de una operación de ataque. Esto permite realizar múltiples acciones de manera automatizada y reducir el tiempo necesario para identificar y aprovechar configuraciones inseguras.

El problema no se limita a AntiFox. Otras plataformas, como ARTEX, también han sido relacionadas con actividades maliciosas que aprovechan la automatización para comprometer sistemas y obtener información.

La combinación de inteligencia artificial, herramientas de pentesting y credenciales expuestas representa un desafío adicional para las organizaciones.

## ¿Cómo pueden protegerse las organizaciones?

Ante este escenario, las empresas necesitan fortalecer tanto la seguridad de sus aplicaciones como los controles de acceso a sus servicios en la nube.

Estas son algunas medidas recomendadas:

**1. Proteger las aplicaciones expuestas a internet**

Mantener servidores y aplicaciones actualizados, realizar evaluaciones periódicas de vulnerabilidades y supervisar cualquier actividad inusual en los procesos de ejecución.

**2. Evitar almacenar credenciales en archivos de configuración**

Revisar archivos como `web.config`, registros, respaldos y variables de entorno para identificar información sensible que pueda quedar expuesta ante una intrusión.

**3. Aplicar el principio de mínimo privilegio**

Limitar los permisos de usuarios, aplicaciones y roles de IAM exclusivamente a los recursos que necesitan para operar.

**4. Supervisar la actividad en AWS**

Utilizar AWS CloudTrail para registrar y analizar solicitudes API, prestando especial atención a accesos inusuales, múltiples intentos de autenticación y operaciones exitosas después de una serie de solicitudes rechazadas.

**5. Proteger los secretos y las credenciales**

Utilizar servicios especializados para administrar información confidencial, rotar periódicamente las credenciales y revocar inmediatamente aquellas que puedan haber sido comprometidas.

**6. Contar con monitoreo y respuesta ante incidentes**

Implementar mecanismos de detección que permitan identificar comportamientos sospechosos, investigar incidentes y contener amenazas antes de que afecten operaciones críticas.

## Conclusión

La campaña relacionada con AntiFox demuestra que las herramientas de inteligencia artificial pueden convertirse en un recurso para automatizar ataques y facilitar el acceso no autorizado a infraestructuras empresariales.

El compromiso de un servidor web puede representar mucho más que una afectación aislada: también puede abrir el camino hacia bases de datos, credenciales y servicios en la nube.

Por ello, **la seguridad debe abordarse de manera integral**, considerando aplicaciones, servidores, identidades, permisos y servicios cloud como partes de un mismo entorno.

