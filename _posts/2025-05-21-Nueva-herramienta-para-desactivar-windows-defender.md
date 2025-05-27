---
title: Nueva herramienta para desactivar Windows Defender
date: 2025-05-21 09:00:00 
categories: [HACKING]
tags: [hacking, tools, vulnerabilidad, ciberseguridad, malware]
description: Defendnot explota la API del Centro de Seguridad de Windows (WSC)..
image: /assets/135/preview1.png
---

Hoy traemos una herramienta para desactivar Microsoft Defender creada por es3n1n, hablamos de defendnot y se trata de la evolución de su no-defender, que fue retirada de GitHub tras una DMCA. Lo que ha hecho esta vez el propio es3n1n es un clean-room implementation: sin depender de AVs reales ni DLLs de terceros, y más centrado en un reverse engineering profundo del WSC.

![Imagen 01](/assets/135/preview1.png) width="300" height="200"

La verdadera joya está en el writeup que el propio es3n1n publicó, donde describe cómo desmontó pieza a pieza el WSC para burlar sus defensas:

- WSC usa un API COM que verifica quién llama, validando la firma digital, que el proceso esté PPL, y otros checks en la seguridad del token del proceso (concretamente el SID de WinDefend).
- Los primeros intentos inyectando código en procesos comunes (como cmd.exe) fallaron porque no tenían las banderas correctas ni la firma PPL necesaria.
- Se dio cuenta que el proceso WSC está protegido con PPL, pero eso se puede saltar con un driver en modo kernel que desactiva esa protección (en entornos de pruebas).
- El punto clave fue elegir Taskmgr.exe como víctima para la inyección DLL, porque cumple con todos los requisitos de firma y PPL, pero no es un AV, lo que permite “engañar” al WSC.
- Además, entendió que WSC verifica el flag ForceIntegrity en las características DLL (DllCharacteristics) para validar que el proceso que hace las llamadas es legítimo.
- Para pasar el chequeo de tokens y evitar que se vincule con Windows Defender, no basta con impersonar el SID WinDefend (de hecho, esa técnica no funcionó), sino que hay que tener un proceso legítimo que cumpla todas las verificaciones.
- Finalmente, definió un mecanismo propio para transferir parámetros entre loader y DLL usando un archivo ctx.bin y para gestionar la persistencia con el Task Scheduler (teniendo cuidado con las condiciones de energía del sistema que pueden impedir la ejecución automática).

![Imagen 01](/assets/135/135-02.jpg) width="300" height="200"

Es decir, básicamente Defendnot explota la API del Centro de Seguridad de Windows (WSC), la misma que usan los antivirus para decir “eh, soy el p*** amo aquí”. Y Windows, para evitar conflictos, automáticamente desactiva Defender cuando detecta un antivirus registrado. Hasta aquí, normal.

Pero la gracia está en cómo Defendnot hace el registro. No solo engaña a Windows haciéndole creer que hay un antivirus activo, sino que además:

**Bypassea mecanismos de defensa clave:**
- Protected Process Light (PPL): ese "muro" que impide meter código no firmado en procesos críticos.
- Firmas digitales previamente válidas:  no hay necesidad de firmar nada, porque inyecta una DLL dentro del proceso Taskmgr.exe (el Administrador de tareas), que es un proceso protegido y firmado por Microsoft.

**Inyección de DLL:**: Defendnot introduce su código malicioso dentro de Taskmgr.exe para registrar el antivirus falso. Al estar dentro de un proceso de confianza, se evita que Windows levante alarmas inmediatas.

**Loader personalizable**: Puedes cambiar el nombre del antivirus falso, desactivar el registro si quieres, y activar un logging bien verboso para trazar cada movimiento.

**Persistencia**: Usa el Windows Task Scheduler para automatizar su ejecución tras reinicios, manteniendo el truco vivo incluso después de apagar y encender el PC.

##### Instalación

Abre PowerShell como administrador y ejecuta cualquiera de estos comandos:

    # Example 1: Basic installation
    irm https://dnot.sh/ | iex
    
    # Example 2: With custom AV name
    & ([ScriptBlock]::Create((irm https://dnot.sh/))) --name "Custom AV name"
    
    # Example 3: Without allocating console
    & ([ScriptBlock]::Create((irm https://dnot.sh/))) --silent

**Nota**
Como se muestra en los ejemplos 2 y 3, puedes pasar argumentos por línea de comandos al script de instalación y este los enviará a defendnot-loader. Para referencia sobre qué argumentos están permitidos, consulta la sección Uso más abajo.

**Nota**
También puedes usar directamente la versión ‘larga’ del script de instalación, que es:
[https://raw.githubusercontent.com/es3n1n/defendnot/refs/heads/master/install.ps1](https://raw.githubusercontent.com/es3n1n/defendnot/refs/heads/master/install.ps1)

**Manual**
Descarga la última release, extráela en algún lugar y ejecuta defendnot-loader.

**Uso**

    Usage: defendnot-loader [--help] [--version] [--name VAR] [--disable] [--verbose] [--silent] [--autorun-as-user] [--disable-autorun]
    
    Optional arguments:
      -h, --help         prints help message and exits
      --version          shows version and exits
      -n, --name         av display name [default: "https://github.com/es3n1n/defendnot"]
      -d, --disable      disable defendnot
      -v, --verbose      verbose logging
      --silent           do not allocate console
      --autorun-as-user  create autorun task as currently logged in user
      --disable-autorun  disable autorun task creation

**Para cerrar**

Defendnot es el resultado de días de ingeniería inversa, debugging remoto con latencia de 210ms, uso de drivers para saltarse protecciones kernel, y un conocimiento profundo del funcionamiento interno de WSC y Windows Defender.

Si estás en el mundo del pentesting, red teaming o simplemente te mola entender cómo funcionan los sistemas de defensa de Windows y cómo romperlos (todo con la intención de mejorar la seguridad, claro), Defendnot es un proyecto que deberías tener en el radar ;)



