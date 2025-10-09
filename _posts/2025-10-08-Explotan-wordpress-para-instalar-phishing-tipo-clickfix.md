---
title: "Explotan WordPress para instalar Phishing tipo ClickFix"
date: 2025-10-08 09:00:00 
categories: [CIBERATAQUES]
tags: [phishing, hacking, ciberataques]
description: Investigadores de ciberseguridad están alertando sobre una campaña maliciosa dirigida a sitios de WordPress para realizar inyecciones de JavaScript diseñadas para redirigir a los usuarios a sitios sospechosos.
image: /assets/175/preview1.png
---

*"Los visitantes del sitio reciben contenido inyectado que es malware oculto, como una verificación falsa de Cloudflare",* declaró Puja Srivastava, investigadora de Sucuri, en un análisis publicado la semana pasada.

La empresa de seguridad web informó que inició una investigación después de que uno de los sitios de WordPress de uno de sus clientes mostrara JavaScript sospechoso de terceros a los visitantes, y finalmente descubrió que los atacantes introdujeron modificaciones en un archivo relacionado con el tema ("functions.php").

El código insertado incorpora referencias a Google Ads, probablemente con el objetivo de evadir la detección. Pero, en realidad, funciona como un cargador remoto al enviar una solicitud HTTP POST al dominio "brazilc[.]com", que, a su vez, responde con una carga útil dinámica que incluye dos componentes:

- Un archivo JavaScript alojado en un servidor remoto ("porsasystem[.]com"), que, al momento de escribir este artículo, ha sido referenciado en 17 sitios web y contiene código para realizar redirecciones de sitios;
- Un fragmento de código JavaScript que crea un iframe oculto de 1x1 píxeles, dentro del cual inyecta código que imita recursos legítimos de Cloudflare como "cdn-cgi/challenge-platform/scripts/jsd/main.js", una API esencial de su plataforma de detección y desafío de bots;

Cabe destacar que el dominio "porsasystem[.]com" ha sido marcado como parte de un sistema de distribución de tráfico (TDS) llamado Kongtuke (también conocido como 404 TDS, Chaya_002, LandUpdate808 y TAG-124).

Según la información compartida por una cuenta llamada "monitorsg" en Mastodon el 19 de septiembre de 2025, la cadena de infección comienza cuando los usuarios visitan un sitio comprometido, lo que resulta en la ejecución de "porsasystem[.]com/6m9x.js", que luego conduce a "porsasystem[.]com/js.php" para eventualmente llevar a las víctimas a páginas de estilo ClickFix para la distribución de malware.

![Imagen 01](/assets/175/175-01.png)

Los hallazgos ilustran la necesidad de proteger los sitios de WordPress y garantizar que los plugins, temas y software del sitio web se mantengan actualizados, implementando contraseñas seguras, analizando los sitios en busca de anomalías y creando cuentas de administrador inesperadas para mantener el acceso persistente incluso después de detectar y eliminar el malware.

### Crear páginas ClickFix con el generador IUAM ClickFix

Esta revelación surge después de que la Unit 42 de Palo Alto Networks detallara un kit de phishing llamado IUAM ClickFix Generator que permite a los atacantes infectar a los usuarios con malware aprovechando la técnica de ingeniería social ClickFix y crear páginas de destino personalizables que imitan los desafíos de verificación del navegador que se utilizan a menudo para bloquear el tráfico automatizado.

Las páginas de phishing personalizadas también permiten manipular el portapapeles, un paso crucial en el ataque ClickFix, además de detectar el sistema operativo utilizado para adaptar la secuencia de infección y distribuir malware compatible.

En al menos dos casos diferentes, se ha detectado que actores de amenazas utilizan páginas generadas con el kit para implementar ladrones de información como DeerStealer y Odyssey Stealer, este último diseñado para sistemas macOS de Apple.

La aparición del generador IUAM ClickFix se suma a una alerta previa de Microsoft sobre el aumento de desarrolladores comerciales de ClickFix en foros clandestinos desde finales de 2024. Otro ejemplo notable de un kit de phishing que ha integrado la oferta es Impact Solutions.

*"Los kits ofrecen la creación de páginas de destino con diversos señuelos, incluyendo Cloudflare",* señaló Microsoft en agosto de 2025. *"También permiten la creación de comandos maliciosos que los usuarios pegarán en el cuadro de diálogo Ejecutar de Windows. Estos kits afirman garantizar la elusión de antivirus y protección web (algunos incluso prometen que pueden eludir Microsoft Defender SmartScreen), así como la persistencia de la carga útil".*

No hace falta decir que estas herramientas reducen aún más la barrera de entrada para los ciberdelincuentes, permitiéndoles lanzar sofisticados ataques multiplataforma a escala sin mucho esfuerzo ni experiencia técnica.

### ClickFix se vuelve sigiloso mediante el contrabando de caché

Los hallazgos también se producen tras el descubrimiento de una nueva campaña que ha innovado en la fórmula de ataque de ClickFix empleando una técnica furtiva conocida como contrabando de caché (cache smuggling) para pasar desapercibido en lugar de descargar explícitamente archivos maliciosos en el host objetivo.

*"Esta campaña se diferencia de las variantes anteriores de ClickFix en que el script malicioso no descarga ningún archivo ni se comunica con internet",* afirmó Marcus Hutchins, investigador principal de amenazas de Expel. *"Esto se logra utilizando la caché del navegador para almacenar preventivamente datos arbitrarios en el equipo del usuario".*

En el ataque documentado por la empresa de ciberseguridad, la página con temática de ClickFix se hace pasar por un verificador de cumplimiento de VPN de Fortinet, utilizando tácticas de FileFix para engañar a los usuarios y lograr que inicien el Explorador de archivos de Windows y peguen un comando malicioso en la barra de direcciones para activar la ejecución de la carga útil.

![Imagen 02](/assets/175/175-02.jpg)

El comando invisible está diseñado para ejecutar un script de PowerShell a través de conhost.exe. Lo que distingue al script es que no descarga malware adicional ni se comunica con un servidor controlado por el atacante. En su lugar, ejecuta una carga útil ofuscada que se hace pasar por una imagen JPEG y que ya está almacenada en la caché del navegador cuando el usuario accede a la página de phishing.

![Imagen 02](/assets/175/175-03.png)

Ni la página web ni el script de PowerShell descargan archivos explícitamente, explicó Hutchins. *"Con solo dejar que el navegador almacene en caché la imagen falsa, el malware puede obtener un archivo zip completo en el sistema local sin que el comando de PowerShell tenga que realizar ninguna solicitud web".*

Las implicaciones de esta técnica son preocupantes, ya que el contrabando de caché puede ofrecer una forma de evadir las protecciones que, de otro modo, detectarían archivos maliciosos al descargarse y ejecutarse. Se descarga un archivo 'image/jpeg' de apariencia inofensiva, solo para que su contenido se extraiga y se ejecute mediante un comando de PowerShell oculto en un señuelo de phishing de ClickFix.


