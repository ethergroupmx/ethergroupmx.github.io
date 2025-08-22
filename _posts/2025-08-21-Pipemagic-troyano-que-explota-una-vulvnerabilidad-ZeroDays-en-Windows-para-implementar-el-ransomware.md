---
title: "Pipemagic: troyano que explota una vulnerabilidad ZeroDays en Windows para implementar el ransomware RansomExx"
date: 2025-08-21 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ransomware, vulnerabilidad, ciberseguridad]
description: Investigadores de ciberseguridad han desvelado la explotación por parte de actores de amenazas de fallas de seguridad, ya parcheada, en Microsoft Windows para desplegar el malware PipeMagic en ataques de ransomware RansomExx.
image: /assets/159/preview1.png
---

Los ataques implican la explotación de CVE-2025-29824, una vulnerabilidad de escalamiento de privilegios que afecta al Sistema de Archivos de Registro Común de Windows (CLFS), que Microsoft solucionado en abril de 2025, según informaron Kaspersky y BI.ZONE en un informe conjunto publicado hoy. 

Vale la pena mencionar que CVE-2025-29824 es la segunda falla de día cero de Windows que se distribuye a través de PipeMagic después de CVE-2025-24983, un error de escalamiento de privilegios del subsistema del kernel Win32 de Windows, que fue hallado por ESET y parcheado por Microsoft el mes pasado. Anteriormente, PipeMagic también se observó en relación con los ataques de ransomware Nokoyawa que explotaban otra falla Zero-Day de CLFS (CVE-2023-28252).

PipeMagic se documentó por primera vez en 2022 como parte de los ataques de ransomware RansomExx dirigidos a empresas industriales del sudeste asiático, capaces de actuar como una puerta trasera completa que proporciona acceso remoto y ejecuta una amplia gama de comandos en los hosts comprometidos.

En dichos ataques, se ha descubierto que los actores de amenazas explotan CVE-2017-0144, una falla de ejecución remota de código en Windows SMB, para infiltrarse en la infraestructura de la víctima. Se detectaron cadenas de infección posteriores observadas en octubre de 2024 en Arabia Saudita que utilizaban una aplicación falsa OpenAI ChatGPT como cebo para distribuir el malware. "Los objetivos incluyen organizaciones de los sectores de tecnologías de la información (TI) y bienes raíces de Estados Unidos, el sector financiero de Venezuela, una empresa de software española y el sector minorista de Arabia Saudita", dijo el gigante tecnológico.

A principios de abril, Microsoft atribuyó la explotación de CVE-2025-29824 y la implementación de PipeMagic a un actor de amenazas que rastrea como Storm-2460. "Una característica única de PipeMagic es que genera una matriz aleatoria de 16 bytes que se utiliza para crear una tubería con nombre y formato: \\.\pipe\1.<hex string>", explicaron los investigadores Sergey Lozhkin, Leonid Bezvershenko, Kirill Korchemny e Ilya Savelyev. "Después, se inicia un hilo que crea continuamente esta tubería, intenta leer datos de ella y luego la destruye. Este método de comunicación es necesario para que la puerta trasera transmita cargas útiles y notificaciones cifradas".

El malware es un archivo MSBuild malicioso que contiene una carga útil cifrada, que luego se descomprime para ejecutar PipeMagic. Este troyano es un malware modular basado en plugins que utiliza un dominio alojado en el proveedor de nube Microsoft Azure para preparar los componentes adicionales. Los ataques de 2025, dirigidos a Arabia Saudita y Brasil, se basan en un archivo de índice de ayuda de Microsoft ("metafile.mshi") como cargador.

El cargador, a su vez, descomprime código C# que descifra y ejecuta el shellcode incrustado. El shellcode inyectado es código ejecutable para sistemas Windows de 32 bits u carga un ejecutable sin cifrar incrustado dentro del propio shellcode.

Kaspersky afirmó haber descubierto artefactos del cargador de PipeMagic que se hacen pasar por un cliente ChatGPT en 2025, similares a los detectados previamente en octubre de 2024. Se ha observado que las muestras utilizan técnicas de secuestro de DLL para ejecutar una DLL maliciosa que imita un archivo de actualización de Google Chrome ("googleupdate.dll").

Independientemente del método de carga utilizado, todo esto conduce a la implementación de la puerta trasera PipeMagic, que admite varios módulos:

- Un módulo de comunicación asíncrona que admite cinco comandos para finalizar el complemento, leer/escribir archivos, finalizar una operación de archivo o finalizar todas las operaciones de archivo.
- Un módulo de carga para inyectar cargas útiles adicionales en la memoria y ejecutarlas.
- Un módulo de inyección para lanzar un ejecutable de C#.

*"La detección repetida de PipeMagic en ataques a organizaciones en Arabia Saudita y su aparición en Brasil indican que el malware permanece activo y que los atacantes continúan desarrollando su funcionalidad",* afirmaron los investigadores.

Las versiones detectadas en 2025 muestran mejoras con respecto a la versión 2024, orientadas a persistir en los sistemas de las víctimas y a expandirse lateralmente dentro de las redes internas. En los ataques de 2025, los atacantes utilizaron la herramienta ProcDump, renombrada como dllhost.exe, para extraer memoria del proceso LSASS.

