---
title: "Certighost (CVE-2026-54121): cuando un usuario de dominio puede obtener un certificado de un Domain Controller"
date: 2026-08-11 09:00:00
categories: [CIBERSEGURIDAD]
tags: [vulnerabilidades, pentesting, ciberseguridad]
description: "Certighost (CVE-2026-54121) permite abusar de Active Directory Certificate Services para obtener potencialmente un certificado asociado a un Domain Controller y escalar privilegios."
image: /assets/289/preview1.png
---

**Active Directory Certificate Services (AD CS)** se ha convertido en uno de los componentes más interesantes para los equipos de Red Team y para los atacantes que buscan escalar privilegios dentro de entornos Windows.

Una configuración incorrecta de la infraestructura de certificados puede convertir una PKI aparentemente legítima en una vía para comprometer identidades privilegiadas.

Ahora, una nueva vulnerabilidad denominada **Certighost (CVE-2026-54121)** pone nuevamente el foco sobre AD CS. El fallo permite que un usuario autenticado pueda elevar privilegios debido a un problema de autorización en la infraestructura de certificados.

La vulnerabilidad tiene una puntuación **CVSS de 8.8** y cuenta con una prueba de concepto pública.

Lo especialmente preocupante es el resultado que puede conseguirse: en determinadas condiciones, un atacante con privilegios bajos puede conseguir un **certificado que representa a un Domain Controller**.

## ¿Por qué es tan importante un certificado de un Domain Controller?

En Active Directory, los certificados no son simplemente mecanismos para cifrar comunicaciones.

También pueden utilizarse para **autenticación e identificación de máquinas y usuarios**.

Un Domain Controller posee una identidad privilegiada dentro del dominio y participa en numerosos procesos de autenticación.

Por ello, conseguir un certificado válido asociado a un DC puede permitir a un atacante utilizar mecanismos de autenticación basados en certificados para obtener credenciales y accesos con un nivel de privilegio extremadamente elevado.

El problema, por tanto, no se limita a conseguir acceso adicional.

**El objetivo final puede ser hacerse pasar por una máquina crítica del dominio.**

---

## ¿Cómo funciona el ataque?

Certighost aprovecha una combinación de problemas relacionados con la forma en que **Active Directory Certificate Services valida determinadas solicitudes de certificados**.

A grandes rasgos, el ataque puede dividirse en varias etapas.

### 1. El atacante parte de una cuenta de dominio

No es necesario comenzar con privilegios administrativos.

Una cuenta de dominio con pocos privilegios puede ser suficiente para iniciar el proceso, dependiendo de la configuración del entorno afectado.

Esto convierte el fallo en especialmente interesante para escenarios de **post-explotación**, donde el atacante ya consiguió comprometer una cuenta básica.

### 2. Se utiliza una identidad de equipo

La prueba de concepto puede crear una nueva cuenta de equipo o utilizar una cuenta existente.

El objetivo es utilizar esta identidad durante las comunicaciones que posteriormente realizará la autoridad certificadora.

### 3. Se levantan servicios controlados por el atacante

La PoC implementa servicios que simulan determinados componentes de la infraestructura Windows.

Entre ellos se encuentran listeners relacionados con:

* SMB/LSA.
* LDAP.
* Validación de identidad mediante el entorno de Active Directory.

La finalidad es conseguir que la CA interactúe con infraestructura controlada por el atacante durante el procesamiento de la solicitud.

### 4. La CA recibe información manipulada

Durante el proceso se incorporan determinados atributos a la solicitud de certificado.

La infraestructura maliciosa responde a las consultas realizadas por la CA proporcionando información asociada al **Domain Controller objetivo**.

De esta manera, la autoridad certificadora puede terminar asociando la identidad del DC con la solicitud.

### 5. Se obtiene un certificado válido

El resultado más importante del ataque es que la **Certificate Authority puede emitir un certificado que representa al Domain Controller**.

Este certificado puede almacenarse posteriormente en formato PFX para utilizarlo en mecanismos de autenticación compatibles.

---

## La PoC pública

Poco después de hacerse pública la vulnerabilidad apareció una prueba de concepto que automatiza buena parte del proceso.

La herramienta puede encargarse de:

* Crear o reutilizar una cuenta de equipo.
* Levantar listeners SMB/LSA y LDAP.
* Preparar la solicitud de certificado.
* Interactuar con la CA.
* Obtener el certificado asociado al objetivo.
* Utilizar posteriormente mecanismos de autenticación basados en certificados.

En un laboratorio controlado, el flujo puede terminar generando archivos como un **certificado PFX** y una **caché Kerberos**, que permiten demostrar el impacto de la vulnerabilidad.

Esto también explica por qué la publicación de una PoC aumenta considerablemente el riesgo para organizaciones que todavía no han aplicado las actualizaciones correspondientes.

---

## El verdadero riesgo: la identidad del Domain Controller

Muchos ataques contra AD CS tienen como objetivo conseguir certificados asociados a usuarios privilegiados.

Certighost resulta especialmente preocupante porque el objetivo puede ser diferente.

En lugar de buscar únicamente una identidad administrativa, el atacante intenta obtener una identidad asociada a un **Domain Controller**.

Esto puede abrir la puerta a mecanismos de autenticación como **PKINIT**, utilizados por Kerberos para autenticación mediante certificados.

En un escenario de compromiso completo, una identidad de DC puede proporcionar una posición extremadamente privilegiada dentro del dominio.

Por esta razón, el impacto debe evaluarse no solamente desde el punto de vista de la emisión de certificados, sino considerando todas las funciones de autenticación que dependen de ellos.

---

## ¿Qué organizaciones deberían prestar especial atención?

El riesgo es especialmente relevante en entornos que utilizan:

* Active Directory.
* Active Directory Certificate Services.
* Enterprise Certificate Authorities.
* Autenticación basada en certificados.
* Smart cards o mecanismos equivalentes.
* Plantillas de certificados personalizadas.
* Infraestructuras con configuraciones heredadas.

Las organizaciones con PKI instalada desde hace años deberían prestar especial atención.

Una infraestructura de certificados puede continuar funcionando correctamente durante mucho tiempo mientras mantiene configuraciones antiguas que nunca fueron revisadas.

---

## ¿Qué debemos revisar?

Aplicar los parches de Microsoft es el primer paso, pero **no debería ser el único**.

Una revisión de seguridad de AD CS debería incluir al menos los siguientes puntos.

### Inventariar las Certificate Authorities

Identificar todas las **Enterprise CA** existentes dentro de la organización.

También es importante determinar qué servidores las alojan y qué servicios dependen de ellas.

### Revisar las plantillas de certificados

Las plantillas determinan quién puede solicitar certificados y qué usos pueden tener.

Es necesario identificar configuraciones excesivamente permisivas y plantillas que puedan utilizarse para autenticación.

### Auditar permisos de inscripción

Revisar cuidadosamente los permisos de:

* **Enroll**
* **AutoEnroll**

El objetivo es determinar qué usuarios y grupos pueden solicitar certificados y bajo qué condiciones.

### Revisar la autenticación mediante certificados

Es importante identificar dónde se utilizan certificados como mecanismo de autenticación y qué identidades pueden representar.

Una mala configuración puede convertir un problema de emisión de certificados en un problema de compromiso de identidad.

### Supervisar las solicitudes de certificados

Los registros de eventos de AD CS pueden proporcionar información importante para detectar comportamientos anómalos.

Conviene buscar:

* Solicitudes inesperadas.
* Certificados solicitados por cuentas que normalmente no utilizan PKI.
* Cambios repentinos en los patrones de inscripción.
* Solicitudes relacionadas con cuentas de equipo.
* Actividad procedente de sistemas que normalmente no interactúan con la CA.

---

## Parchear no significa que la revisión haya terminado

Certighost vuelve a demostrar que **AD CS debe considerarse una superficie crítica de Active Directory**.

Actualizar los sistemas afectados es fundamental, pero una estrategia de seguridad completa debe combinar:

**Parcheo + revisión de configuración + monitorización + reducción de privilegios**

Las organizaciones deberían conocer exactamente qué autoridades certificadoras tienen, qué plantillas existen, quién puede solicitar certificados y qué identidades pueden utilizarse para autenticación.

Una PKI que nadie revisa desde su implementación puede terminar convirtiéndose en una de las rutas menos visibles hacia una escalada de privilegios.

## Conclusión

Certighost demuestra que una cuenta aparentemente poco privilegiada puede representar un riesgo mucho mayor cuando existe una infraestructura AD CS vulnerable o mal configurada.

El atractivo para un atacante es evidente: en lugar de intentar comprometer directamente un Domain Controller, puede intentar **abusar del sistema de confianza que permite emitir certificados dentro del dominio**.

Por eso, AD CS debe formar parte de cualquier evaluación de seguridad de Active Directory.

**Si tu organización utiliza Active Directory Certificate Services, conocer quién puede emitir certificados y qué identidades pueden representar es tan importante como proteger las propias cuentas administrativas.**
