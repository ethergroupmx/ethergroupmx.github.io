---
title: "Tarjetas SIM maliciosas permiten ejecutar código arbitrario en dispositivos IoT y móviles"
date: 2026-08-11 09:00:00
categories: [CIBERSEGURIDAD]
tags: [IoT, móviles, malware, vulnerabilidades, ciberseguridad, ciberataques, seguridad informática]
description: "Investigadores descubren un ataque que utiliza tarjetas SIM maliciosas para enviar comandos al módem y ejecutar código arbitrario en dispositivos IoT, routers, vehículos y teléfonos móviles."
image: /assets/287/preview1.png
---

Investigadores de seguridad de la **Universidad de Birmingham** y la firma de ciberseguridad **Fuzzware** han revelado un método de ataque que permite a una tarjeta SIM maliciosa enviar comandos directos al módem celular de un dispositivo. Esta vulnerabilidad hace posible la ejecución de código arbitrario y da acceso a funciones críticas del sistema sin necesidad de interactuar con el usuario.

## Un vector de ataque basado en acceso físico

A diferencia de las amenazas convencionales que explotan vulnerabilidades de red a través de mensajes SMS o llamadas, este ataque requiere acceso físico directo. El vector de ejecución consta de tres etapas principales:

1. **Sustitución de hardware:** El atacante reemplaza la tarjeta SIM legítima del equipo por una SIM maliciosa previamente programada.
2. **Abuso del SIM Toolkit:** La tarjeta modificada utiliza el conjunto de comandos estándar del *SIM Toolkit* para comunicarse directamente con el procesador del módem.
3. **Escalado de privilegios:** A través de comandos específicos enviados al módem, el código logra comprometer el procesador principal del dispositivo host.

---

## Dispositivos vulnerables: El impacto en el ecosistema IoT

Durante la investigación se analizaron diversos módulos celulares, routers industriales y teléfonos inteligentes para determinar el nivel de exposición de los distintos mercados:

### Módems celulares y hardware Machine-to-Machine (M2M)
El sector industrial y el Internet de las Cosas (IoT) mostraron el mayor grado de riesgo debido a la falta de mecanismos de protección en sus firmwares de comunicación:

* De **8 módulos celulares analizados**, **6 resultaron vulnerables** a la ejecución de comandos maliciosos.
* Los investigadores lograron tomar el control de un **cargador comercial de vehículos eléctricos (EV)**.
* Se confirmaron fallas en **routers industriales** y **unidades de control telemático (TCU)** instaladas en automóviles modernos.

### Teléfonos móviles
Se realizaron pruebas en un lote de 26 teléfonos inteligentes de distintas marcas:

* En **9 dispositivos**, la función subyacente requerida para el ataque estaba activa por defecto.
* Únicamente **3 modelos procesaron los comandos maliciosos** con éxito: el *OPPO Find X5*, el *OPPO Reno 14 F 5G* y el *ASUS Zenfone 9*.
* Dispositivos de gama alta de fabricantes como Apple (iPhone) y Google (Pixel) **no resultaron vulnerables** durante las pruebas realizadas.

---

## Riesgo para infraestructuras críticas y recomendaciones

El mayor peligro se concentra en equipos desatendidos situados en la vía pública o en instalaciones de acceso público, como parquímetros inteligentes, estaciones de carga para vehículos eléctricos, routers de infraestructura y cámaras de vigilancia conectadas a redes móviles. En estos escenarios, un atacante con acceso físico temporal puede manipular el hardware en cuestión de segundos.

### Estrategias de mitigación

Para prevenir esta clase de exploits, las organizaciones y fabricantes deben adoptar las siguientes medidas de seguridad:

* **Protección física del hardware:** Diseñar gabinetes con sellos de seguridad, tornillos anti-manipulación o cerraduras físicas que impidan el acceso a las ranuras SIM.
* **Transición a eSIM:** Adoptar tarjetas SIM integradas (eSIM) para eliminar por completo la presencia de tarjetas físicas extraíbles.
* **Actualizaciones de firmware:** Implementar parches emitidos por los fabricantes de módems para desactivar las funciones obsoletas del *SIM Toolkit* que permiten la recepción de estos comandos.
