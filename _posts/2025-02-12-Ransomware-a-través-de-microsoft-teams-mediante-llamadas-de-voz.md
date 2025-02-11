---
title: Los atacantes difunden ransomware a través de Microsoft Teams mediante llamadas de voz
date: 2025-02-12 09:00:00 
categories: [HACKING]
tags: [ciberseguridad, ciberataques, hacking, ransonware]
description: Informe de Kaspersky Lab revela que el 52% de las empresas admite que el personal es la mayor debilidad de su seguridad informática.
image: /assets/111/preview1.png
---

Sophos Managed Detection and Response (MDR) ha descubierto dos campañas de ransomware distintas que explotan Microsoft Teams para obtener acceso no autorizado a organizaciones específicas.

Los actores de amenazas, identificados como STAC5143 y STAC5777, están aprovechando una configuración predeterminada de Microsoft Teams que permite a los usuarios externos iniciar chats o reuniones con usuarios internos.

La metodología de ataque implica varios tipos y enfoques para lograr una mayor sofisticación.

Además de esto, los investigadores de Sophos notaron que los actores de amenazas emplean un enfoque de varios pasos:

- **Bombardeo por correo electrónico**: los objetivos se ven abrumados con hasta 3.000 correos electrónicos spam en menos de una hora.
- **Ingeniería social**: haciéndose pasar por soporte informático, los atacantes inician llamadas de Microsoft Teams a las víctimas.
- **Acceso remoto**: los actores de amenazas guían a las víctimas para que instalen Microsoft Quick Assist o utilicen la función de control remoto incorporada de Teams.
- **Implementación de malware**: una vez que tienen el control, los atacantes ejecutan cargas útiles maliciosas.

### Campañas

**Campaña STAC5143**: La campaña STAC5143 es una sofisticada operación cibernética que emplea una variedad de herramientas y técnicas para infiltrarse en los sistemas objetivo y controlarlos. En esencia, la campaña aprovecha los archivos JAR (Java Archive) junto con puertas traseras basadas en Python para establecerse en las máquinas comprometidas.

Uno de sus componentes clave es la implementación de una versión ofuscada de RPivot, una herramienta de proxy SOCKS inverso que permite a los atacantes mantener acceso sigiloso a la red de la víctima.

Para evadir aún más la detección, la campaña incorpora una función lambda para ofuscar el código, un método que recuerda a los utilizados por el conocido grupo de ciberdelincuencia FIN7. Por último, los operadores de STAC5143 establecen conexiones con sus servidores C2 a través del puerto 80, probablemente en un intento de mimetizarse con el tráfico HTTP normal y eludir las medidas de seguridad habituales.

![Imagen 01](/assets/111/111-01.jpg)
###### _Código Python de una copia ofuscada de RPivot en el archivo winter.zip (Fuente: Sophos)_

**Campaña STAC5777**: La campaña STAC5777 es un ciberataque sofisticado que utiliza una combinación de software legítimo y componentes maliciosos para infiltrarse y persistir en los sistemas objetivo.

Utiliza una DLL maliciosa denominada winhttp.dll, que se carga de forma lateral mediante el ejecutable legítimo de Microsoft OneDriveStandaloneUpdater.exe. La campaña establece conexiones de comando y control (C2) mediante controladores de kit de herramientas OpenSSL sin firmar, lo que mejora su capacidad para evadir la detección.

Para mantener la persistencia, los atacantes modifican el registro de Windows y agregan entradas bajo “HKLM\SOFTWARE\TitanPlus” que especifican las direcciones del servidor C2. Además, la campaña crea un servicio y un archivo .lnk para garantizar que permanezca activo en el sistema comprometido. Para el movimiento lateral, STAC5777 realiza un escaneo SMB, lo que le permite propagarse a través de las redes.

En un intento por deshabilitar las medidas de seguridad , el malware intenta desinstalar el software de seguridad y las soluciones de autenticación multifactor (MFA), lo que potencialmente deja los sistemas más vulnerables a una mayor explotación.

El malware utilizado en estas campañas puede hacer lo siguiente:

- Recopilar detalles del sistema y del SO.
- Recopilar credenciales de usuario.
- Registrar pulsaciones de teclas mediante funciones API de Windows.
- Realizar descubrimiento de red y movimiento lateral.
- Exfiltrar datos confidenciales.

![Imagen 01](/assets/111/111-02.jpg)
###### _Actividad entrante del actor de amenazas capturada por la integración de Microsoft Office 365 (Fuente: Sophos)_

En una instancia, STAC5777 intentó implementar el ransomware Black Basta, que fue bloqueado por la protección de puntos finales de Sophos.

Las organizaciones deben restringir las llamadas de Teams desde entidades externas, limitar el uso de herramientas de acceso remoto como Quick Assist e implementar configuraciones de control de aplicaciones para evitar la ejecución no autorizada de Quick Assist.

No sólo eso, también deberían aprovechar la integración de Microsoft Office 365 para mejorar la supervisión de la seguridad .

Sophos ha implementado detecciones para el malware utilizado en estas campañas, incluidos ATK/RPivot-B, Python/Kryptic.IV y Troj/Loader-DV.




