---
title: "Ratty: un troyano que se propaga en latinoamérica a través de PDF maliciosos"
date: 2025-09-20 09:00:00 
categories: [CIBERATAQUES]
tags: [phishing, hacking, malware]
description: Investigadores de ESET Latinoamérica han descubierto una campaña de phishing que distribuye Ratty, un troyano de acceso remoto (RAT). Los atacantes utilizan documentos PDF maliciosos y técnicas de ingeniería social dirigidas a usuarios de habla hispana, en la región.
image: /assets/171/preview1.png
---

Los cibercriminales han utilizado diferentes servicios de alojamiento en la nube como Google Drive, Dropbox y Mediafire para alojar y propagar diferentes códigos maliciosos descriptos en este blog.

Ratty es un troyano de acceso remoto (RAT) que tiene diversas funciones como la captura de pantalla, acceso a la cámara y al micrófono, keylogging, navegación por archivos y ejecución remota de comandos en el sistema infectado. También se conecta a un servidor de comando y control.

En la imagen 1, podemos visualizar el diagrama e infección de la campaña que comienza con un correo de phishing que incluye un archivo adjunto llamado Factura.pdf que induce a la víctima a hacer clic en un enlace que produce la descarga de un archivo HTML (FACTURA-243240011909044.html), que a su vez descarga un script VBS (FA-45-04-25.vbs). Este script, al ser ejecutado, facilita la descarga de un archivo comprimido (InvoiceXpress.zip), dentro del cual se encuentra un archivo (InvoiceXpress.cmd) encargado de ejecutar InvoiceXpress.jar, identificado como el troyano de acceso remoto Ratty, que además establece conexión con un servidor de comando y control.

![Imagen 01](/assets/171/171-01.jpeg)

### Análisis de la campaña de Ratty

La campaña se desarrolla en varias etapas, que podemos mapear con las TTPs de [MITRE ATT&CK](https://attack.mitre.org/matrices/enterprise/).

### 1. Correo Electrónico Malicioso

**Acceso inicial (T1566.001 - Spearphishing Attachment)**
La forma de acceso inicial para infectar a las víctimas fue a través de un correo de phishing el cual es detectado por las soluciones de ESET como PDF/Phishing.Agent.XRC.

En la Imagen 2 podemos observar el correo detectado que contiene un archivo adjunto (Factura.pdf) e indica al usuario que lo descargue, con la excusa de ser una Factura pendiente de pago; una estrategia utilizada en este tipo de campañas.

![Imagen 02](/assets/171/171-02.jpeg)

### 2. PDF Malicioso

**Ejecución (T1204.002 – User Execution: Malicious File)**

Cuando el usuario descarga y abre el archivo adjunto, “Factura.pdf” (SHA-1 df351ea6340360de6aa0fcef30d1d252c9ce6378) este tiene las opciones de hacer clic en dos enlaces “Abrir” o “Descargar”, ambos abren una URL de Dropbox de donde se procede a la descarga automática de un archivo malicioso de tipo HTML.

En la imagen 3 podemos ver un ejemplo del archivo adjunto de tipo PDF.

![Imagen 03](/assets/171/171-03.jpeg)

Como se puede ver en la imagen 4, una vez que el usuario hace clic en el enlace, se descarga automáticamente un archivo HTML con el nombre “FACTURA-243240011909044.html” desde la siguiente URL de dropbox *“https[:]//www[.]dropbox.com/scl/fi/lzf7pwdocuhi4jl5gudhu/FACTURA-243240011909044.html?rlkey=hyg60b58keu0hxu7qx5xrqd6d&st=rxdo0z2q&dl=1”*

![Imagen 03](/assets/171/171-04.jpeg)


### 3. HTML Malicioso

**Ejecución (T1204.002 – User Execution: Malicious File)**

Una vez descargado el archivo HTML malicioso “FACTURA-243240011909044.html” (SHA-1: 33ad0a3573497373cabefce084303a48b26aa933) el usuario debe abrirlo para que se produzcan las siguientes etapas.

El archivo HTML contiene scripts ofuscados utilizando la función “String.fromCharCode” (T1027.013 Obfuscated Files or Information), aplicando ofuscación basada en objetos (object-based obfuscation) que en este caso almacena valores en arrays y objetos para luego reconstruir en forma dinámica el código malicioso al abrir el archivo.

En la imagen 5 podemos ver el fragmento ofuscado del HTML.

![Imagen 03](/assets/171/171-05.jpeg)

Durante el análisis de este archivo HTML, hemos visto que solo se va a ejecutar sí el navegador no está en inglés. En el caso de estarlo contiene scripts JS que derivan a una URL de Google Drive que tiene un archivo PDF con formato de factura que no es malicioso (como lo vemos en la imagen 6)

![Imagen 03](/assets/171/171-06.jpeg)

Solo si el navegador no está en el idioma inglés, procede a mostrar un checkbox de verificación falso, que al marcarlo desaparece y muestra contenido que estaba oculto en un background container dentro del mismo código (imagen 7)

![Imagen 03](/assets/171/171-07.jpeg)

### 4. Interacción con el HTML Malicioso

**Ejecución (T1204.001 – User Execution: Malicious Link)**

Como se puede ver en la imagen 7, luego de marcar el checkbox mencionado en el punto anterior, aparece el contenedor que estaba oculto, contiene un botón y que al hacer cliclleva a la siguiente URL "https[:]//skdjaznhajdhurkahfaproqudjahbshdjabdgajs.ngrok.io?www.google.com"

![Imagen 03](/assets/171/171-08.jpeg)

### 5. Descarga de archivo VBS malicioso

**T1105 – Ingress Tool Transfer**

Luego del clic en el botón de descarga mencionado, se produce un redireccionamiento   a otro sitio, esta vez “blob:https[:]//skdjaznhajdhurkahfaproqudjahbshdjabdgajs.ngrok.io/dc32c5a4-cf17-4c9c-9513-806f5efa5258”

El sitio visualmente está vacío, sin embargo, esconde un script que redirecciona a una URL de MediaFire, donde se produce la descarga automática de un archivo de tipo VBS (ver la imagen 9)

![Imagen 03](/assets/171/171-09.jpeg)

### 6. Ejecución del VBS malicioso

**(T1204.002 – User Execution: Malicious File y T1059.005 – Command and Scripting Interpreter: Visual Basic)**

El archivo descargado "FA-45-04-2025.vbs” (SHA1:  91f66c3d7375bb1cd70d468f27b4878261c3a008) está ofuscado (object-based ofuscation) usando un diccionario con valores ASCII que se reconstruye dinámicamente con Chr() (T1027 – Obfuscated Files or Information) (Imagen 10)

![Imagen 03](/assets/171/171-10.jpeg)

El script desofuscado (Imagen 11) nos da una idea del siguiente paso de la cadena de infección donde se abusa de Google Drive y se ejecutan algunas acciones que se describen a continuación.

![Imagen 03](/assets/171/171-11.jpeg)

Al ejecutar el archivo VBS “FA-45-04-2025.vbs” (T1204.002) este realiza varias acciones maliciosas (T1059.005 – Command and Scripting Interpreter: Visual Basic) como: 

- Abrir una URL de Google Drive donde se ve un archivo que simula ser una factura en formato PDF, "documento.pdf" pero que no contiene comportamiento malicioso.  (Imagen 12)

Descarga el archivo “InvoiceXpress.zip” desde la siguiente URL:  https[:]//skdjaznhajdhurkahfaproqudjahbshdjabdgajs.ngrok.io/InvoiceXpress.zip guardándolo en la carpeta de destino que será “C:\Users\Public” y luego lo descomprime. Verifica la existencia del archivo InvoiceXpress.cmd en la carpeta “/bin y procede a ejecutarlo

![Imagen 03](/assets/171/171-12.jpeg)

### 7. Ejecución del cmd malicioso

**(T1059.003- Execution: Command and Scripting: CMD)**

Al ejecutarse **InvoiceXpress.cmd**, detectado como BAT/Starter.NLI, (SHA-1: 7d5da2e06f23a819157327217b372369469bcf03), el archivo realiza varias acciones, funcionando básicamente como un launcher (Imagen 12):

- Verifica si existe una copia de java.exe en el path: “%TEMP%\InvoiceXpress\InvoiceXpress\bin\”
- Ejecuta “InvoiceXpress.png” que en realidad es un .jar disfrazado de archivo png (Ratty)

A continuación, podemos observar el contenido del archivo InvoiceXpress.cmd con las funcionalidades mencionadas.

![Imagen 03](/assets/171/171-13.jpeg)

### 8. Ejecución de InvoiceXpress.png

**(Variante de Ratty- Troyando de Acceso Remoto)**

El archivo ejecutado mediante cmd “InvoiceXpress.png” (SHA-1 85e6d36f1d6688e12fdfe9fa9d1adb5d853c1277) es una variante del troyano de acceso remoto (RAT) – escrito en JAVA- “Ratty” detectado por ESET como @Backdoor.JAVA/Ratty

Una vez ejecutado, Ratty realiza múltiples acciones entre las que podemos destacar, aunque no son las únicas:

- **Persistencia (T1547.001 – Boot or Logon Autostart Execution: Registry Run Keys)**
  
  Ratty logra persistencia en Windows copiándose dentro de “C:\Users\user\AppData\Roaming\DATA\1747400217088.png” disfrazándose como un archivo png (Startup Folder - T1036.007 – Masquerading: Double File). Luego crea una llave en el registro HKCU\Software\Microsoft\Windows\CurrentVersion\Run, llamada AutorunKey  garantizando que el software malicioso se inicie automáticamente con cada inicio de sesión.

- **Comando y control (T1095 Non-Application Layer Protocol)**

  Ratty se conecta al servidor de comando y control en el dominio dc8vcreun.localto.net alojado en EQUINIX-CONNECT-EMEAGB, un proveedor de servicios web.  En el análisis, la muestra intentó establecer comunicación sobre el puerto TCP 8911 (y subsiguientes como 8912 y 8913).

Asimismo, se identificaron módulos como PacketLogin, PacketKeepAlive y PacketDisconnect, empleados para gestionar la autenticación inicial y conexión con el servidor de control.

- **Ocultamiento actividades maliciosas )T1564.003 – Hide Artifacts: Hidden Window)**

Contiene también paquetes como PacketBlackScreen utilizado para bloqueo de pantalla para ocultar actividades maliciosas. También PacketMouseFixer yPacketScreenFreezer que permiten controlar o congelar el ratón y la pantalla para impedir interacción del usuario, por ejemplo. (ver imagen 13)

- **Transferencia de archivos y exfiltración (T1105 – Ingress Tool Transfer - T1041 – Exfiltration Over C2 Channel)**

Presencia de PacketDownloadBytes y PacketUploadBytes que permitirían descargar y subir archivos entre el C2 y el dispositivo infectado. También HTTPUtil.java que gestionaría comunicaciones HTTP. (ver imagen 14)

- **Recolección de información (ver imagen 14)**
  - T1125 – Video Capture: captura de imágenes y video desde la cámara web de la víctima.
  - T1123 – Audio Capture: grabación de audio a través del micrófono.
  - T1113 – Screen Capture: capturas de pantalla del dispositivo de la víctima.
  - T1056.001 – Input Capture: Keylogging: captura de pulsaciones de teclado (keylogging).

![Imagen 03](/assets/171/171-14.jpeg)

### Conclusión:
Ratty es un RAT escrito en Java que, aunque no es habitual en la región latinoamericana, está siendo utilizado en campañas maliciosas debido a la gran cantidad de funcionalidades con las que cuenta.

Entre sus capacidades más relevantes se destaca la de recolección de información mediante keylogging, capturas de pantalla y grabación de audio, entre otros, así como la exfiltración de datos, conexión C2 y persistencia. Estas no son sus únicas funcionalidades y existen diversas variantes con distintos paquetes y módulos.

### Indicadores de Compromiso

#### Registros

A continuación, se listan las claves de registro de Windows manipuladas por Ratty:

- HKCU\Software\Microsoft\Windows\CurrentVersion\Run

  - o AutoRunKey – "C:\Program Files (x86)\Java\jre-1.8\bin\javaw.exe -jar C:\Users\user\AppData\Roaming\DATA\1747400217088.png"

### Persistencia

A continuación, se listan las rutas utilizadas por el código malicioso para persistir en la máquina de la víctima:

- “C:\Users\user\AppData\Roaming\DATA\1747400217088.png”

### Hashes, URLs y C&C:

Hashes de muestras analizadas: 
Dominios e IPs detectados en las muestras analizadas:

- https[:]//www[.]dropbox.com/scl/fi/lzf7pwdocuhi4jl5gudhu/FACTURA-243240011909044.html?rlkey=hyg60b58keu0hxu7qx5xrqd6d&st=rxdo0z2q&dl=1
- https [:]//skdjaznhajdhurkahfaproqudjahbshdjabdgajs[.]ngrok.io?www.google.com
- blob:https[:]//skdjaznhajdhurkahfaproqudjahbshdjabdgajs[.]ngrok.io/dc32c5a4-cf17-4c9c-9513-806f5efa5258
- http[:]//skdjaznhajdhurkahfaproqudjahbshdjabdgajs[.]ngrok.io/InvoiceXpress.zip
- Dc8vcreun.localto[.]net 
- 158.178.201[.]63

### Técnicas MITRE ATT&CK

A continuación, se listan las técnicas de MITRE ATT&CK vistas en las muestras analizadas:

![Imagen 03](/assets/171/171-15.png)

Fuentes: [WeliveSecurity](https://www.welivesecurity.com/es/)

























