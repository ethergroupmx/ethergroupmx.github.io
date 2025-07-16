---
title: "Vulnerabilidad de eSIM (de Kigen) expone dispositivos IoT a ataques maliciosos"
date: 2025-07-15 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, ciberseguridad, móviles]
description: Investigadores de ciberseguridad han descubierto una nueva técnica de hacking que explota las vulnerabilidades de la tecnología eSIM utilizada en los smartphones modernos, exponiendo a los usuarios a graves riesgos.
image: /assets/150/preview1.png
---

Los problemas afectan a la tarjeta eUICC de Kigen. Según el sitio web de la empresa irlandesa, hasta diciembre de 2020 se habían habilitado más de dos mil millones de tarjetas SIM en dispositivos IoT.

Los hallazgos provienen de Security Explorations, un laboratorio de investigación de AG Security Research. Kigen otorgó a la empresa una recompensa de 30.000 dólares por su informe.

Una eSIM, o SIM integrada, es una tarjeta SIM digital que se integra directamente en un dispositivo mediante software instalado en un chip de Tarjeta de Circuito Integrado Universal Integrada (eUICC).

Las eSIM permiten a los usuarios activar un plan de telefonía móvil de un operador sin necesidad de una tarjeta SIM física. El software eUICC permite cambiar los perfiles del operador, el aprovisionamiento remoto y la gestión de perfiles SIM. "La tarjeta eUICC permite instalar los llamados perfiles eSIM en el chip objetivo", declaró Security Explorations. "Los perfiles eSIM son representaciones de software de las suscripciones móviles".

Según un aviso publicado por Kigen, la vulnerabilidad se origina en el Perfil de Prueba Genérico GSMA TS.48, versiones 6.0 y anteriores, que se dice se utiliza en productos eSIM para pruebas de conformidad con las normas de radio.

**En concreto, esta deficiencia permite la instalación de applets no verificados y potencialmente maliciosos. La versión 7.0 de GSMA TS.48, publicada el mes pasado, mitiga el problema restringiendo el uso del perfil de prueba. Todas las demás versiones de la especificación TS.48 han quedado obsoletas.**

*"Para explotar la vulnerabilidad con éxito se requiere una combinación de condiciones específicas. Un atacante primero debe obtener acceso físico a una eUICC objetivo y usar claves conocidas públicamente", explicó Kigen. "Esto le permite instalar un applet JavaCard malicioso".*

Además, la vulnerabilidad podría facilitar la extracción del certificado de identidad eUICC de Kigen, lo que permitiría descargar perfiles arbitrarios de operadores de redes móviles (MNO) en texto plano, acceder a la información confidencial de los MNO y manipular perfiles para introducirlos en una eUICC arbitraria sin ser detectados por el MNO.

Security Explorations afirmó que los hallazgos se basan en su propia investigación previa de 2019, que detectó múltiples vulnerabilidades de seguridad en Oracle Java Card que podrían facilitar la implementación de una puerta trasera persistente en la tarjeta. Una de las fallas también afectó a Gemalto SIM, que utiliza la tecnología Java Card.

Estos defectos de seguridad pueden explotarse para vulnerar la seguridad de la memoria de la máquina virtual (VM) Java Card subyacente y obtener acceso completo a la memoria de la tarjeta, vulnerar el firewall del applet e incluso, potencialmente, lograr la ejecución de código nativo.

Sin embargo, Oracle minimizó el posible impacto e indicó que los "problemas de seguridad" no afectaron la producción de la máquina virtual Java Card. Security Explorations afirmó que estas "preocupaciones" han demostrado ser "errores reales".

Los ataques pueden parecer prohibitivos, pero, por el contrario, están al alcance de grupos de estados-nación con capacidad de ataque. Podrían permitir a los atacantes comprometer una tarjeta eSIM e implementar una puerta trasera sigilosa, interceptando eficazmente todas las comunicaciones.

*"El perfil descargado puede modificarse de tal manera que el operador pierda el control sobre él (sin posibilidad de control remoto, deshabilitarlo o invalidarlo, etc.), se le proporcione una visión completamente falsa del estado del perfil o se monitorice toda su actividad"*, añadió la compañía.

*"En nuestra opinión, la posibilidad de que un solo eUICC vulnerado o un solo certificado GSMA eUICC robado acceda (descargando en texto plano) a eSIM de cualquier operador de red móvil constituye un punto débil significativo de la arquitectura eSIM".*
