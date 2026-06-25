---
title: "Ransomware Gentlemen: EDR killer capaz de eliminar más de 400 procesos de seguridad"
date: 2026-06-19 11:00:00
categories: [CIBERSEGURIDAD]
tags: [ransomware, ciberseguridad, malware, ciberataques, news]
description: The Gentlemen incorpora una herramienta capaz de desactivar soluciones EDR y antivirus antes de ejecutar ataques de ransomware, aumentando significativamente su capacidad de evasión y compromiso de sistemas.
image: /assets/267/preview1.png
---

La operación de ransomware como servicio (RaaS) Gentlemen desarrolla y mantiene activamente un conjunto de herramientas para eliminar la detección y respuesta de endpoints (EDR) que distribuye a sus afiliados para debilitar las defensas de los sistemas antes de implementar el cifrador.

Este conjunto de herramientas para eliminar EDR se basa en un marco conocido como GentleKiller. "También incorporan herramientas de terceros o filtradas, como HexKiller, ThrottleBlood y HavocKiller", afirmó Jakub Souček, investigador de seguridad de ESET, en su informe. *"Estas herramientas están estandarizadas mediante una capa compartida de evasión de defensas, suplantando principalmente a proveedores de seguridad mediante información de versión falsa y certificados e iconos legítimos copiados"*.

La empresa eslovaca de ciberseguridad también destaca al grupo de ransomware por su capacidad para "poner en funcionamiento con una rapidez inusual" las pruebas de concepto (PoC) recién descubiertas, relacionadas con una técnica de ataque denominada "BYOVD" (Bring Your Own Vulnerable Driver), en muchos casos a los pocos días de su publicación.

Desde su aparición en marzo de 2025, The Gentlemen ha escalado rápidamente posiciones y se ha consolidado como uno de los grupos de ransomware más activos. Según datos de Ransomware.live, el grupo ha cobrado 504 víctimas hasta la fecha, la mayoría ubicadas en el sudeste asiático, Sudamérica y Europa occidental.

Informes recientes del periodista especializado en ciberseguridad Brian Krebs y PRODAFT han revelado que un ciudadano ruso de 36 años llamado Alexander Andreevich Yapaev (alias Hastalamuerte) ha estado liderando la operación, tras haber colaborado con otros esquemas de ransomware, incluido Qilin.

La empresa de ciberinteligencia Intel 471 revela que el usuario Hastalamuerte es una persona bilingüe (ruso e inglés) que se registró en casi una docena de foros de ciberdelincuencia entre 2019 y la actualidad, entre ellos Exploit, Breachforums, Ramp_V2, BHF, Raidforums y Nulled.

ESET ha descrito a The Gentlemen como uno de los grupos de RaaS (Ransomware as a Service) más ágiles técnicamente, que utiliza diversas técnicas para garantizar que las muestras compiladas de EDR killer (Early Recorder Killer) eviten la detección. Esto incluye protección binaria mediante Enigma o Themida y el uso de nombres de archivo que se asemejan a los de proveedores de ciberseguridad conocidos, incluyendo información de versión, firmas digitales e iconos.

La variante más común es GentleKiller, que se presenta en ocho variantes diferentes, cada una imitando un producto legítimo distinto y explotando un controlador vulnerable o malicioso diferente como parte del ataque BYOVD. **GentleKiller busca específicamente 400 procesos asociados con 48 programas de seguridad distintos de varios proveedores.**

La lista de controladores explotados por cada variante es la siguiente:

- Kaspersky ("eb.sys")
- FACEIT Anti-Cheat ("nseckrnl.sys")
- Valorant ("GameDriverX64.sys")
- Javelin ("stpm_old.sys" or "stpm_new.sys")
- WatchDog ("dmx.sys")
- Network Blocker ("360netmon_wfp.sys")
- Cleaner ("IMFForceDelete.sys")
- G11 ("PoisonX.sys")

Cabe destacar que el uso indebido de "PoisonX.sys" se ha registrado en los últimos meses en relación con diversos ataques BYOD, uno de los cuales se utilizó para inutilizar CrowdStrike Falcon EDR. Una segunda campaña, detallada por Huntress, implicó una intrusión en la que actores maliciosos desconocidos aprovecharon BeyondTrust Remote Support para desplegar con éxito ransomware en la red, no sin antes inutilizar las herramientas de seguridad mediante "PoisonX.sys" y "hrwfpdrv.sys".

"Al abstraer la capa de suplantación de identidad y los controladores específicos utilizados, el código subyacente revela numerosas similitudes estructurales y de comportamiento que sugieren fuertemente el uso de una plantilla de desarrollo compartida", afirmó Souček. "Este diseño prioriza la facilidad de implementación y la flexibilidad operativa para los afiliados, al tiempo que minimiza el esfuerzo de desarrollo para los operadores. Permite a los operadores de The Gentlemen integrar los controladores comprometidos en su conjunto de herramientas muy poco después de que se divulgue una prueba de concepto para inutilizar EDR".

A continuación se detallan las herramientas de eliminación de EDR de terceros basadas en BYOVD empleadas por el grupo:

- HexKiller ("googleApiUtil64.sys"), una herramienta que anteriormente se creía exclusiva del grupo de ransomware Warlock.
- ThrottleBlood ("ThrottleBlood.sys"), una herramienta detectada en ataques perpetrados por afiliados de MedusaLocker y DragonForce.
- HavocKiller o HwAudKiller ("havoc.sys").

ESET también informó haber detectado un programa de robo de credenciales basado en Rust, con nombre en clave OxideHarvest (también conocido como buildx641), capaz de extraer datos de navegadores web populares como Google Chrome, Microsoft Edge, Torch, Comodo, Epic Privacy Browser, Vivaldi, Brave, Opera, OperaGX, Mozilla Firefox, Waterfox, BlackHawk e IceCat.

*"Si bien la mayoría de las bandas de ransomware siguen delegando la eliminación de EDR a sus afiliados, Gentlemen ha optado por centralizar esta función ofreciéndoles un conjunto de herramientas estandarizadas y listas para usar para eliminar EDR.Esta decisión convierte a Gentlemen en un operador atractivo para los afiliados, ya que reduce significativamente la barrera de entrada y, por consiguiente, facilita su trabajo".*





