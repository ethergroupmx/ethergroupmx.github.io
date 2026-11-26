---
title: "Base de datos sin protección expone 2.000 millones de registros de credenciales"
date: 2026-11-26 13:00:00
categories: [CIBERATAQUES]
tags: [ciberataques, ciberseguridad, malware, hacking, privacidad, seguridad informática]
description: "Una base de datos sin contraseña ni cifrado dejó expuestos aproximadamente 2.000 millones de registros de credenciales, incluyendo contraseñas, cookies y tokens de sesión que podrían facilitar accesos no autorizados."
image: /assets/322/preview1.png
---

Una base de datos accesible públicamente y sin mecanismos de protección dejó expuestos aproximadamente 2.000 millones de registros relacionados con credenciales de acceso, incluyendo nombres de usuario, contraseñas, cookies y tokens de sesión.

El hallazgo fue realizado por un especialista en seguridad informática, quien identificó un repositorio en línea que no contaba con contraseña ni cifrado. Según el investigador, se trata del mayor volumen de credenciales que ha encontrado durante su trayectoria profesional.

La información almacenada no se limitaba a combinaciones tradicionales de usuarios y contraseñas. También contenía datos que podrían permitir el acceso a sesiones de navegación activas, lo que incrementa el riesgo para las cuentas y servicios asociados.

## Información recopilada mediante malware

Entre los datos identificados había archivos organizados por países y registros aparentemente recopilados mediante programas maliciosos especializados en el robo de información, conocidos como *infostealers*.

Este tipo de malware infecta dispositivos para extraer información almacenada en navegadores y aplicaciones, como credenciales, cookies, datos de autenticación y otros elementos sensibles.

El repositorio también contenía información relacionada con plataformas de la red Tor y una amplia variedad de dominios y servicios utilizados a nivel mundial.

La presencia de cookies y tokens de sesión representa un riesgo especialmente importante. Estos elementos pueden permitir que un atacante reutilice sesiones autenticadas y acceda a determinadas cuentas sin necesidad de introducir nuevamente la contraseña, dependiendo de las condiciones de validez y protección de cada sesión.

## Dos mil millones de registros no equivalen a cuentas únicas

Aunque la cifra de registros expuestos es considerable, es importante aclarar que no representa necesariamente a 2.000 millones de usuarios diferentes o cuentas activas.

El investigador señaló que los datos pueden contener duplicados, registros antiguos o múltiples credenciales pertenecientes a una misma persona en distintos servicios.

Por lo tanto, el volumen identificado corresponde a registros almacenados y no a una cantidad confirmada de cuentas comprometidas.

## El acceso público fue bloqueado

Después de que el especialista notificara el hallazgo, el servidor involucrado restringió el acceso público en un periodo breve.

Sin embargo, la identidad de los responsables del repositorio y las razones por las que se encontraba almacenando semejante cantidad de información continúan sin esclarecerse.

El incidente evidencia los riesgos asociados con la exposición accidental o deliberada de grandes volúmenes de información, especialmente cuando los datos contienen elementos que pueden facilitar el acceso no autorizado a servicios digitales.

## ¿Cómo pueden protegerse los usuarios y las organizaciones?

La exposición de credenciales puede facilitar ataques posteriores, como el robo de cuentas, el acceso no autorizado a plataformas corporativas y el uso indebido de información confidencial.

Para reducir estos riesgos, es recomendable implementar las siguientes medidas:

- **Cambiar contraseñas comprometidas:** actualizar las credenciales que hayan podido quedar expuestas y evitar reutilizar la misma contraseña en diferentes servicios.
- **Revocar sesiones activas:** cerrar las sesiones abiertas y revocar tokens de autenticación cuando exista sospecha de exposición.
- **Implementar autenticación multifactor:** utilizar métodos adicionales de verificación, preferentemente resistentes al phishing.
- **Utilizar gestores de contraseñas:** almacenar credenciales de forma segura y generar contraseñas únicas para cada plataforma.
- **Proteger los dispositivos:** mantener sistemas y soluciones de seguridad actualizados para prevenir infecciones por malware especializado en el robo de información.
- **Monitorear accesos:** revisar inicios de sesión, dispositivos registrados y actividades inusuales en las cuentas corporativas.

La seguridad de las credenciales no depende únicamente de utilizar contraseñas robustas. También requiere proteger los dispositivos desde los que se accede a los servicios, controlar las sesiones activas y detectar oportunamente cualquier exposición de información.

Una base de datos sin protección puede convertirse en una fuente de información para múltiples campañas de ciberdelincuencia, por lo que la gestión adecuada de los accesos y la protección de los datos deben ser prioridades para cualquier organización.
