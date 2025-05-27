---
title: Dificultad para bypassear EDRs - perspectiva de un operador de ransomware
date: 2025-05-18 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ransomware, hacking, malware]
description: Un desconocido ha creado de varias extensiones maliciosas para el navegador Chrome desde febrero de 2024.
image: /assets/134/preview1.png
---

En el mundo del hacking y los ataques de ransomware, evadir las defensas de un sistema es una de las principales prioridades de los atacantes. Recientemente, un operador de ransomware compartió su perspectiva sobre la facilidad con la que se pueden bypassear distintos EDRs (Endpoint Detection and Response):

​@psexec64, el operador de ransomware que publicó el tuit, es conocido en la comunidad de ciberseguridad underground por su experiencia práctica y su implicación en ataques de ransomware que emplean técnicas avanzadas de evasión. Por lo tanto, este tipo de información es relativamente valiosa ya que proporciona una perspectiva desde el punto de vista del atacante real. Analizando el desglose de sus opiniones.

**1.- Muy Difícil de Evadir:**
- CrowdStrike
- Tanium

Estos productos sobresalen en **detección basada en comportamiento** y utilizan **telemetría avanzada** y técnicas de **inteligencia artificial.** Son reconocidos por ser de los más difíciles de eludir, especialmente cuando están correctamente configurados.

**2.- Moderadamente Difícil:**
- SentinelOne
- Cybereason
- Sophos

Aunque presentan una **detección sólida,** algunos operadores comentan que aún pueden ser evadidos si se utilizan técnicas más especializadas, como el uso de **herramientas legítimas** (LOLBins) o **payloads en memoria.**

**Muy Fácil de Evadir:**
- ESET
- Bitdefender

Los operadores de ransomware consideran que estas soluciones, aunque efectivas como antivirus tradicionales, no cuentan con características avanzadas para prevenir ataques más sofisticados.

### ¿Por qué estas diferencias?

La clave radica en cómo cada **EDR** detecta las amenazas y en qué **capas de defensa** se enfoca. **CrowdStrike** y **Defender** son líderes por su **detección en tiempo real** y sus capacidades de respuesta automática, lo que los hace resistentes a técnicas avanzadas como **inyección de código en memoria** o el uso de herramientas legítimas para explotación (LOLBins).

Por otro lado, soluciones como **ESET y Bitdefender** están diseñadas principalmente para entornos de usuario final, lo que las hace menos efectivas contra **ataques dirigidos y técnicas de evasión sofisticadas.**

Si bien **ningún EDR** es perfecto, la diferencia clave entre estos productos radica en su capacidad para detectar amenazas en **entornos corporativos** y su habilidad para hacer frente a ataques **dinámicos.** La **configuración adecuada,** junto con una **estrategia de defensa en profundidad,** sigue siendo esencial para fortalecer la seguridad.






