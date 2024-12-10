---
title: Resumen técnico troyano Silver Shifting Yak
date: 2024-12-09 09:00:00 
categories: [CIBERSEGURIDAD, HACKING]
tags: [hacking, vulnerabilidad, malware ciberataques, ciberseguridad]
description: Al analizar el código fuente de la página alojada en el dominio nvidrive[.]com mencionado anteriormente...
image: /assets/101/preview1.png
---


Al analizar el código fuente de la página alojada en el dominio nvidrive[.]com mencionado anteriormente, SCILabs identificó un código de JavaScript diseñado para impedir la visualización del código fuente, utilizando detectores de eventos (Event Listeners) para bloquear el clic derecho y secuencias de teclas como “Ctrl + U”.

![Imagen 00](/assets/101/101-01.png)
Fragmento de código JavaScript analizado.

Como se mencionó en la sección anterior, el archivo descargado es un comprimido en formato ZIP que sigue el patrón de nombre <2 letras-4 números-3 letras>.zip. Este contiene una carpeta vacía llamada “__data” y un archivo ejecutable X64, desarrollado en lenguaje C++, con un tamaño de aproximadamente 30MB, con el mismo nombre que el archivo comprimido.

![Imagen 00](/assets/101/101-02.png)
Contenido del archivo ZIP descargado.

![Imagen 00](/assets/101/101-03.png)
Información general del archivo ejecutable.

El ejecutable importa diversas bibliotecas, como Kernel32.dll, User32.dll y Ole32.dll, que en conjunto permiten acceder a recursos del sistema, como archivos, servicios y procesos, además de facilitar la manipulación de datos. También incluye bibliotecas de la serie API-MS-CRT (Microsoft C Runtime Library), que cuentan con funciones como la generación de valores aleatorios, operaciones de fecha y hora, acceso a variables de entorno, configuración del sistema, además de la  manipulación de cadenas, entre otras.

![Imagen 00](/assets/101/101-04.png)
Bibliotecas importadas por el archivo ejecutable.

Al ejecutarse, el archivo mencionado actúa inicialmente como dropper, extrayendo un archivo ZIP en la ubicación %ProgramData%/[directorio con nombre de letras aleatorias]. Este contiene una copia de sí mismo y una DLL maliciosa desarrollada en .NET, que funciona como loader para la carga útil final del troyano. Los nombres del archivo ZIP, de los archivos contenidos y del directorio creado son cadenas aleatorias de longitud variable, sin un patrón identificable hasta el momento.

![Imagen 00](/assets/101/101-05.png)
Contenido del archivo ZIP descomprimido en el directorio de instalación del troyano.

Después de instalar el troyano, este almacena el dominio de su servidor de comando y control (C2) en la llave de registro HK_CU/Environment/SFA, y una URL para descargar la carga útil en HK_CU/Environment/SFL. Ambos valores se guardan codificados en base64. En HKEY_CURRENT_USER\Environment comúnmente se almacenan variables de entorno personalizadas que afectan el entorno de trabajo del usuario al iniciar sesión. Dado que esta clave no requiere permisos administrativos para ser modificada, también es utilizada en campañas maliciosas.

![Imagen 00](/assets/101/101-06.png)
Llaves de registro en las cuales se almacena el dominio y una URL de descarga del C2 del troyano.

A continuación, Silver Shifting Yak establece persistencia mediante un script de PowerShell en la llave de registro HKEY_CU/Environment/UserInitMprLogonScript, permitiendo que el malware se ejecute automáticamente cada vez que el usuario inicie sesión en Windows.

![Imagen 00](/assets/101/101-07.png)
Script de PowerShell usado para generar persistencia

Posteriormente la DLL, desarrollada en C# .NET y ofuscada con base64,  también almacenada en el directorio %ProgramData%/[directorio con nombre de letras aleatorias], se carga en memoria con el propósito de ejecutar las siguientes acciones:

- Recupera el C2 almacenado en el registro de Windows.

  ![Imagen 00](/assets/101/101-08.png)
  Recuperación de C2 del registro de Windows.

- Descarga la carga útil que se encuentra cifrada mediante AES[1] y base64, la llave de descifrado y el vector de inicialización desde una URL que cambia en cada ejecución del troyano debido a que es generada mediante un GUID[2] y el valor DATETIME actual del equipo infectado.

  ![Imagen 00](/assets/101/101-09.png)
  Fragmento de código que construye una URL de descarga de Silver Shifting Yak mediante un GUID

- Mediante las API CreateThread y WaitForSingleObject inyecta el payload final del troyano en memoria.

  ![Imagen 00](/assets/101/101-10.png)
  Inyección del Payload final de Silver Shifting Yak.

  ![Imagen 00](/assets/101/101-11.png)
  Proceso de Silver Shifting Yak en ejecución.

Una vez en ejecución, el troyano Silver Shifting Yak inicia el monitoreo del navegador de la víctima, con el objetivo de robar información de bancos brasileños y ciertos sitios de Microsoft mediante el uso de WebSockets.

![Imagen 00](/assets/101/101-12.png)
Cadenas identificadas en memoria y relacionadas con el monitoreo de instituciones bancarias brasileñas y sitios web de Microsoft durante el análisis dinámico.

Durante el análisis, se identificaron alrededor de 50 bancos e instituciones financieras de interés para Silver Shifting Yak, incluyendo entidades como Mercado Pago y Binance, así como servicios de Microsoft como Azure, Live y Hotmail.

![Imagen 00](/assets/101/101-13.png)
Sitios de instituciones bancarias de interés para Silver Shifting Yak.

Es importante destacar que durante el análisis se identificaron coincidencias en algunas capacidades y herramientas utilizadas por Silver Shifting Yak, Silver Oryx Blade[1] y Coyote, como el uso de cifrado AES para ciertas cadenas en la cadena de infección, WebSockets para la comunicación con el C2, el monitoreo de tráfico web y la utilización del framework Json.NET de Newtonsoft para la manipulación de datos transmitidos al C2, así como Fody Costura para incrustar recursos .NET.

SCILabs, con nivel de confianza medio, tiene la hipótesis de que los operadores del troyano Silver Oryx Blade, reportado en agosto de 2024 también por SCILabs, podrían ser los mismos que los del troyano Coyote y de acuerdo con esta investigación de igual manera podrían estar relacionados con Silver Shifting Yak. Debido a los cambios sustanciales observados en las campañas de estos tres troyanos, se han clasificado como variantes de malware posiblemente operadas por un mismo grupo de amenazas. Esta variabilidad permite a los atacantes:

- Adaptarse a diferentes entornos objetivo.
- Evadir la detección.
- Optimizar el impacto de sus campañas.
- Mantener sus campañas activas y efectivas frente a las defensas de seguridad.
- Dificultar el análisis y la atribución a un solo grupo de amenazas.

# Características destacables de Silver Shifting Yak, Silver Oryx Blade y Coyote

A continuación, se presentan las principales características distintivas de Silver Shifting Yak, contrastadas con campañas previamente observadas del troyano Silver Oryx Blade y Coyote en la región. Este análisis tiene como objetivo brindar mayor claridad en la identificación de esta nueva amenaza para futuras investigaciones.

![Imagen 00](/assets/101/101-14.png)
Diferencias entre Silver Oryx Blade y Coyote.

En conclusión, los tres troyanos presentan diferencias significativas en sus artefactos y TTP; sin embargo, comparten similitudes clave, como el uso de lenguajes C++ y C#, cifrado AES, ofuscación mediante MD5, bibliotecas compartidas y técnicas de desarrollo que pueden revelar pistas sobre la metodología de un actor de amenazas, como el uso de GUID para aleatorizar cadenas. Este análisis nos permite plantear la hipótesis de que los tres troyanos son operados por los mismos actores de amenaza. Por lo tanto, SCILabs llevará a cabo un perfilamiento de amenazas para confirmar o descartar esta hipótesis.

### Resumen del flujo de ataque

- Aunque no se logró identificar el método de distribución, es altamente probable que el usuario objetivo sea víctima de correos de phishing o campañas de malvertising con pretextos relacionados con facturas y documentos digitales.
- El usuario es enviado a un sitio apócrifo que realiza la descarga automática de un archivo comprimido en formato ZIP, el cual contiene el primer dropper de Silver Shifting Yak en formato EXE.
- Una vez que la víctima extrae el archivo ejecutable y lo ejecuta comienza el despliegue del troyano bancario, realizando las siguientes tareas:
- Descarga un segundo archivo de tipo ZIP que contiene el mismo ejecutable abierto por primera vez y una DLL que funciona como loader del troyano.
- El archivo ZIP es descomprimido en %ProgramData%/[directorio con nombre de letras aleatorias].
- Se establece persistencia mediante un script de PowerShell en la llave de registro HKEY_CU/Environment/UserInitMprLogonScript.
- Se almacena el dominio de su servidor de comando y control (C2) en la llave de registro HK_CU/Environment/SFA, y una URL para descargar la carga útil en HK_CU/Environment/SFL.
- Silver Shifting Yak carga la DLL almacenada en %ProgramData%/[directorio con nombre de letras aleatorias] en memoria.
- La DLL obtiene la carga útil final del troyano y la carga en memoria.
- Silver Shifting Yak monitorea el navegador de la víctima, teniendo la capacidad de leer y verificar el nombre de las ventanas abiertas.
- Cuando el usuario visita algún sitio del interés del troyano es cuando comienza el robo de información confidencial como usuario, además de la contraseña para posteriormente ser compartida con el servidor de comando y control del atacante.

### Flujo de ataque 
![Imagen 00](/assets/101/101-15.png)
Diagrama general del flujo de ataque de Silver Shifting Yak.

### Conclusión

SCILabs considera a Silver Shifting Yak una amenaza significativa en la región debido a sus técnicas avanzadas para generar URLs de C2 dinámicas, lo que le permite evadir soluciones de seguridad, así como  la baja tasa de detección de algunos de sus artefactos. Sus capacidades para robar información de plataformas como Azure representan un riesgo considerable para las organizaciones. Además, si se confirma su estrecha relación con Silver Oryx Blade y Coyote, bajo los mismos operadores, estos actores de amenaza se convertirían en un riesgo mayor por su continuo desarrollo y mejora de artefactos maliciosos, así como sus esfuerzos de evasión de detección por herramientas de ciberseguridad.

Es probable que en el futuro este troyano extienda su actividad a otros países de Latinoamérica, como México, además de Brasil, y que otros troyanos como Grandoreiro, Mekotio y Red Mongoose Daemon adopten algunos TTP descritos en este informe.

SCILabs considera fundamental que instituciones y empresas monitoreen actualizaciones de TTP e indicadores de compromiso para reducir el riesgo de infección y mitigar el impacto del robo de información bancaria en sus operaciones. Se recomienda considerar las siguientes medidas:

## Con respecto a los correos electrónicos, se recomienda:

- Evitar abrir enlaces sospechosos
- Evitar abrir o descargar archivos sospechosos
- Realizar actividades de caza de amenazas en los procesos de los EndPoint, en busca de procesos sospechosos provenientes de carpetas similares a %ProgramData%/[directorio con nombre de letras aleatorias].
- Realizar tareas de caza de amenazas en busca de la existencia de la llave de registro, HKCU\Environment\UserInitMprLogonScript, en caso de existir, verificar que las aplicaciones ejecutadas sean legítimas y hayan sido instaladas por el usuario o la organización.
- Si en alguno de los equipos de la organización se encuentra algún indicio de Silver Shifting Yak, se sugiere realizar una investigación en las cuentas bancarias que se utilizan en este y realizar cambios de contraseñas inmediatamente.
- Realizar actividades de caza de amenaza en sus EndPoints en busca de llaves de registro en las rutas HK_CU/Environment/SFA y HK_CU/Environment/SFL con valores cifrados con AES o base64 y realizar una investigación a profundidad para descartar o confirmar una infección del troyano bancario.

### Se recomienda realizar el bloqueo completo de los dominios y URLs

- circulomaximo[.]com
- stakbeef[.]com
- hxxps[:]//nvidrive[.]com/download/b12aa4d64c6edf95dad972b211b79a64
- hxxps[:]//circulomaximo[.]com/0764851f-9f5b-44ae-9c3b-31daec27f939?d=NGE1MjdmODNhM2E0Y2E3ZTFkNzBhZGIyNmEzNWI3MmU=&t=2&p=MjAyNC0wOS0yM1QwODo0NzozNi43MjBa
- hxxps[:]//stakbeef[.]com/mickipbbgblzsdtwieljmons/jwijlmpriowikhgaiqbraydrxbd/mtyuzwakzcgjgjqhfjjcrgcro/?d=NGE1MjdmODNhM2E0Y2E3ZTFkNzBhZGIyNmEzNWI3MmU=&t=2&p=MjAyNC0xMC0yOVQxODo1MToxOC4xMzla
- 

