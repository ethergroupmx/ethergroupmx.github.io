---
title: "WhatsApp corrige de forma silenciosa vulnerabilidades que permitían fingerprinting"
date: 2026-01-08 09:00:00 
categories: [VULNERABILIDAD]
tags: [vulnerabilidad, ciberseguridad, móviles, redes]
description: El investigador Tal Be'ery afirma que han descubierto que WhatsApp está implementando silenciosamente correcciones para las vulnerabilidades de privacidad de huellas dactilares de los dispositivos.
image: /assets/207/preview1.png
---

Aunque la empresa no lo reconozca públicamente y la corrección siga incompleta, al menos indica que WhatsApp finalmente está comenzando a abordar las vulnerabilidades que fueron divulgadas responsablemente por la comunidad de seguridad.

Si bien el protocolo de cifrado de Extremo a Extremo (E2EE) de WhatsApp protege la confidencialidad de los mensajes, sus fallos de diseño e implementación exponen los detalles del dispositivo de los usuarios (fingerprinting). Esta información proporciona a los atacantes que utilizan WhatsApp como vector de ataque datos cruciales de reconocimiento sobre las posibles víctimas.

![Imagen 01](/assets/207/207-01.png)

Recientemente, WhatsApp comenzó a solucionar algunos de estos problemas de forma discreta.

### Los problemas originales

Por qué es importante la huella digital. Cuando los atacantes avanzados intentan infectar el dispositivo móvil de sus víctimas con malware, WhatsApp es su principal vehículo debido a su ubicuidad.

El primer paso en una campaña cibernética es el reconocimiento. Los atacantes deben conocer el sistema operativo del dispositivo de su víctima para infectarlo con éxito. Enviar un exploit de Android a un iPhone (o viceversa) no solo es ineficaz, sino que puede alertar a las víctimas de que están siendo atacadas. Este descubrimiento puede desencadenar un efecto dominó, poniendo en peligro las vulnerabilidades Zero-Day y Zero-Click valoradas en millones de dólares de los atacantes, su infraestructura completa y su lista de objetivos.

Este fue el caso reciente en el que Citizen Lab y WhatsApp aprovecharon un exploit detectado para exponer las operaciones del grupo de spyware Paragon.

### Múltiples filtraciones de privacidad en WhatsApp

A principios de 2024, se publicó en Usenix una investigación sobre los problemas de privacidad de WhatsApp y los investigadores mostraron cómo WhatsApp filtra la identidad y la cardinalidad de los dispositivos de los usuarios:

El problema principal radica en que, bajo el protocolo multidispositivo E2EE de WhatsApp, cada dispositivo del usuario receptor mantiene una sesión independiente con el dispositivo del remitente, con diferentes claves de cifrado, lo que permite su identificación.

Más tarde ese mismo año, demostraron cómo los atacantes pueden abusar de estas sesiones individuales por dispositivo para dirigir sus ataques a un dispositivo específico de su elección.

En 2025, Gabriel Karl Gegenhuber (University of Vienna) demostró que los atacantes no solo pueden conocer la identidad de los dispositivos a partir de las claves de cifrado, sino que también pueden identificarlos mediante huellas dactilares, es decir, determinar su sistema operativo (SO) exacto.

Con esta cadena de vulnerabilidades, los atacantes ahora pueden:

- Descubrir qué dispositivo móvil usa su víctima: Android o iPhone.
- Distribuir el exploit relevante a este dispositivo específico y no a otros dispositivos de usuario.

Todos estos problemas se comunicaron responsablemente a WhatsApp, pero no se habían abordado hasta ahora.

### Lo bueno

**¡WhatsApp finalmente ha comenzado a abordar este importante problema!**

Este es un cambio muy bienvenido respecto a la postura original de Meta, que no consideraba este problema de huellas digitales como un vulnerabilidad de privacidad relevante que requiriera una solución.

### Lo (no tan) MALO

Los atacantes aún pueden distinguir con alta precisión entre Android y iPhone basándose en el PK ID de un solo uso.

Dado que iPhone inicializa este parámetro con un valor bajo y lo incrementa lentamente (cada pocos días), aún es muy distinguible del valor aleatorio de Android, que utiliza todo su rango de 24 bits.

Sin embargo, parece razonable creer que este es el primer paso de WhatsApp hacia una solución más completa que hará que estos campos sean aleatorios en todos los sistemas operativos y plataformas. Si este es el plan, eliminará esta vulnerabilidad de privacidad de huellas digitales.

### El (algo) FEO

Parece que WhatsApp implementó esta solución de forma discreta, sin notificar a los investigadores originales de estos problemas, otorgar las recompensas correspondientes ni asignar a estas vulnerabilidades un número CVE.

En un problema de identificación de dispositivos diferente, pero similar, que se comunicó a WhatsApp. La empresa implementó una solución y otorgó una pequeña recompensa, pero no asignó un CVE por "no cumplir con el umbral de gravedad". Un CVE no debe considerarse una "marca de vergüenza", sino una herramienta para documentar y debatir adecuadamente los problemas de seguridad y privacidad.

WhatsApp de Meta está mejorando su seguridad y privacidad contra las vulnerabilidades de identificación. El trabajo de investigación realizado por la comunidad de seguridad no fue en vano. Sin embargo, creemos que WhatsApp podría ser más transparente y colaborativo, trabajando más abiertamente con la comunidad de seguridad para el bien común de sus usuarios.





