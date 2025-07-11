---
title: Campaña de envenenamiento SEO disfrazado de IA, infecta con malware
date: 2025-07-10 09:00:00 
categories: [LINUX]
tags: [linux, sistema operativo, software libre, vulnerabilidad]
description: Investigadores de seguridad han revelado una campaña maliciosa que aprovecha las técnicas de envenenamiento de la optimización del motor de búsqueda (SEO) para entregar un malware.
image: /assets/147/preview1.png
---

Conocido llamado Oyster (también conocido como Broomstick o CleanuplOADER).

Según la empresa Artic Woldf, esta actividad de malvertising, , promueve sitios web falsos que alojan versiones troyanizadas de herramientas legítimas como Putty y Winscp y muchas otras, con el objetivo de engañar a los profesionales de IT que buscan estos programas. "Tras la ejecución, se instala una puerta trasera conocida como Oyster/Broomstick", dijo la compañía en un breve publicado la semana pasada.

![Imagen 00](/assets/147/147-01.jpg)

*"La persistencia se establece mediante la creación de una tarea programada que se ejecuta cada tres minutos, ejecutando una DLL maliciosa (TWAIN_96.DLL) a través de RunDll32.exe utilizando la exportación DllRregisterServer, lo que indica el uso del registro de DLL como parte del mecanismo de persistencia".*

Algunos de los sitios web falsos se enumeran a continuación:

- updaterputty[.]com
- zephyrhype[.]com
- putty[.]run
- putty[.]bet, and
- puttyy[.]org

Se sospecha que los actores de amenaza detrás de la campaña también pueden estar apuntando a otras herramientas de TI para entregar el malware, lo que hace que sea imperativo que los usuarios se adhieran a fuentes confiables y sitios de proveedores oficiales para descargar el software necesario.

La divulgación se produce cuando las técnicas de envenenamiento de Blackhat SEO se están utilizando para los resultados de búsqueda de juegos asociados con las palabras clave relacionadas con la inteligencia artificial (IA) para difundir los malware Vidar, Lumma, Legion Loader.

Estos sitios web vienen equipados con un código JavaScript que verifica la presencia de bloqueadores de anuncios y reúne información del navegador de la víctima, antes de iniciar una cadena de redirección que finalmente lleva a la víctima a una página de phishing que aloja un archivo ZIP.

"Las páginas de descarga finales en esta campaña entregan Vidar Stealer y Lumma Stealer como archivos ZIP protegidos con contraseña, con la contraseña proporcionada en la página de descarga final", dijo la empresa Zscaler. "Una vez extraídos, contienen un instalador NSIS de 800 MB, un tamaño engañosamente grande destinado a parecer legítimo y los sistemas de detección de derivación con limitaciones del tamaño del archivo".

El instalador NSIS se utiliza para ejecutar un script Autoit que finalmente es responsable de iniciar las cargas útiles de Stealer. El mecanismo de entrega para Legion Loader, también aprovecha un instalador MSI para implementar el malware a través de un script en un archivo BAT.

![Imagen 00](/assets/147/147-02.jpg)

Se ha observado que una campaña de envenenamiento de SEO similar lleva a páginas de phishing cuando los usuarios buscan los nombres de las aplicaciones populares. Estos sitiosfalsifican páginas de control de Cloudflare Captcha que utilizan la infame estrategia de ClickFix para descargar RedLine Stealer , Hijack Loader.

Según los datos recopilados por Kaspersky, las empresas pequeñas y medianas (PYME) están siendo atacadas cada vez más por ataques cibernéticos que ofrecen malware disfrazado de AI y herramientas de colaboración populares como OpenAI Chatgpt, Deepseek, Cisco AnyConnect, Google Drive, Microsoft Office, Microsoft Teams, Salesforce y Zoom. "Entre en enero y abril de 2025 solo, alrededor de 8.500 usuarios fueron atacados por software potencialmente no deseado que estaban disfrazados de estas herramientas populares", dijo la compañía rusa.

Zoom representó aproximadamente el 41%del número total de archivos únicos, seguido de Outlook y PowerPoint con el 16% cada uno, 12% de Excel, 9% de Word y 5% de Teams. El número de archivos maliciosos únicos que imitan el ChatGPT aumentó en un 115% a 177% en los primeros cuatro meses de 2025.

Si bien la tendencia de abusar de los resultado falsos en motores de búsqueda para aprovecharse de las marcas populares es una táctica bien conocida, las campañas recientes han secuestrado búsquedas de páginas de soporte técnico vinculado a Apple, Bank of America, Facebook, HP, Microsoft, Netflix y PayPal para mostrar páginas legítimas a través de los resultados patrocinados en Google, pero con un giro ingenioso. "Los visitantes son llevados a la sección de Ayuda/Soporte del sitio web de la marca, pero en lugar del número de teléfono genuino, los secuestradores muestran su número de estafa", dijo Malwarebytes.



Esto se logra mediante una técnica llamada inyección de parámetros de búsqueda para mostrar dentro de una barra de búsqueda, un número que está bajo el control del atacante para dar la impresión de que es un resultado oficial de búsqueda dentro de las páginas del centro de ayuda y engaña a los usuarios desprevenidos para que los llamen.

Lo que hace que el ataque sea particularmente insidioso es que los parámetros agregados a la derecha del dominio del centro de ayuda real (por ejemplo, "llámenos 1-***-***-**** gratis") no son visibles en el resultado de la búsqueda patrocinado, lo que no da ninguna razón para que los usuarios sospechen que cualquier cosa está mal.

No es solo la plataforma publicitaria de Google. Los actores de amenaza también han sido atrapados sirviendo anuncios falsos en Facebook para las frases de recuperación de la billetera de criptomonedas y difundiendo malware junto con PI2day, un evento anual vinculado a la comunidad de la red PI.

Estas campañas van de la mano con un fenómeno en curso donde los estafadores y los ciberdelincuentes establecen redes en expansión que comprenden miles de sitios web para falsificar marcas populares y cometer fraude financiero al anunciar productos reales que nunca se entregan. Una de esas redes, denominada Ghostvendors por Silent Push, compra espacio de anuncios de Facebook para promover más de 4.000 sitios falsos.

Los anuncios maliciosos del mercado de Facebook se ejecutan durante unos días, después de lo cual se detienen, eliminando efectivamente todos los rastros de ellos de la biblioteca de meta anuncios. Vale la pena señalar que Meta solo ha retenido anuncios sobre asuntos sociales, elecciones y política durante los últimos siete años.

*"Esto ayudó a confirmar que existía una política conocida de la biblioteca de meta publicidad, y destacó que potencialmente estos actores de amenazas estaban aprovechando esto al lanzar y detener rápidamente anuncios para productos similares en diferentes páginas"*


