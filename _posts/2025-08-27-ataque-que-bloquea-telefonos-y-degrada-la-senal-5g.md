---
title: "Sni5Gect: ataque que bloquea teléfonos y degrada la señal 5G a 4G (sin una estación base no autorizada)"
date: 2025-08-27 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberataques, ciberseguridad, tecnología]
description: Un equipo de académicos ha ideado un novedoso ataque que permite degradar una conexión 5G a una generación inferior sin depender de una estación base (gNB) no autorizada.
image: /assets/162/preview1.png
---

El ataque, según el Grupo de Investigación ASSET (Automated Systems SEcuriTy) de la Singapore University of Technology and Design (SUTD), se basa en un nuevo conjunto de herramientas de software de código abierto llamado Sni5Gect (abreviatura de "Sniffing 5G Inject"), diseñado para rastrear mensajes no cifrados enviados entre la estación base y el equipo del usuario (UE, es decir, un teléfono) e inyectar mensajes al UE objetivo de forma inalámbrica.

Este marco puede utilizarse para llevar a cabo ataques como bloquear el módem del UE, degradar a generaciones anteriores de redes, tomar huellas digitales o eludir la autenticación, según Shijie Luo, Matheus Garbelini, Sudipta Chattopadhyay y Jianying Zhou.

*"A diferencia del uso de una estación base no autorizada, que limita la viabilidad de muchos ataques 5G, SNI5GECT actúa como un tercero en la comunicación, rastreando mensajes silenciosamente y rastreando el estado del protocolo decodificando los mensajes rastreados durante el procedimiento de conexión del UE",* explicaron los investigadores. *"La información de estado se utiliza para inyectar una carga útil de ataque dirigida en la comunicación de enlace descendente".*

Los hallazgos se basan en un estudio previo de ASSET de finales de 2023 que condujo al descubrimiento de 14 fallas en la implementación del firmware de los módems de red móvil 5G de MediaTek y Qualcomm, denominados colectivamente 5Ghoul, que podrían explotarse para lanzar ataques que interrumpan las conexiones, bloqueen la conexión (lo que implica un reinicio manual) o reduzcan la conectividad 5G a 4G.

Los ataques Sni5Gect están diseñados para rastrear mensajes pasivamente durante el proceso de conexión inicial, decodificar el contenido del mensaje en tiempo real y, a continuación, aprovechar el contenido decodificado para inyectar cargas útiles de ataque dirigidas.

Específicamente, los ataques están diseñados para aprovechar la fase previa al procedimiento de autenticación, momento en el cual los mensajes intercambiados entre el gNB y el UE no están cifrados. Como resultado, el modelo de amenaza no requiere el conocimiento de las credenciales del UE para rastrear el tráfico de enlace ascendente/descendente o inyectar mensajes.

*"Hasta donde sabemos, SNI5GECT es el primer marco que ofrece a los investigadores capacidades tanto de rastreo inalámbrico como de inyección con estado, sin necesidad de un gNB malicioso", afirmaron los investigadores.*

Esto permite al atacante bloquear el módem del dispositivo de la víctima, identificar el dispositivo objetivo e incluso degradar la conexión a 4G, que presenta vulnerabilidades conocidas que el atacante puede explotar para rastrear la ubicación del usuario a lo largo del tiempo.

En pruebas realizadas con cinco smartphones, incluyendo OnePlus Nord CE 2, Samsung Galaxy S22, Google Pixel 7 y Huawei P40 Pro, el estudio alcanzó una precisión del 80% en el rastreo de enlaces ascendentes y descendentes, y logró inyectar mensajes con una tasa de éxito del 70% al 90% desde una distancia de hasta 20 metros (65 pies).

La Asociación del Sistema Global para las Comunicaciones Móviles (GSMA), una asociación comercial sin fines de lucro que representa a los operadores de redes móviles de todo el mundo y desarrolla nuevas tecnologías, ha reconocido el ataque de degradación en varias etapas y le ha asignado el identificador CVD-2024-0096.

*"Sostenemos que SNI5GECT es una herramienta fundamental en la investigación de seguridad 5G que permite no solo la explotación inalámbrica de 5G, sino también el avance de futuras investigaciones sobre la detección y mitigación de intrusiones 5G a nivel de paquetes, mejoras de seguridad en la capa física 5G y más allá",* concluyeron los investigadores.
