---
title: "Torito CertPatrol: detectar dominios de phishing en tiempo real... Open Source para proteger tus marcas"
date: 2025-08-26 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [phishing, open source, web, navegador, tools]
description: En el ecosistema digital actual, las campañas de phishing continúan evolucionando, buscando nuevas formas de engañar a los usuarios.
image: /assets/161/preview1.png
---

Una técnica común es registrar dominios que imitan marcas legítimas para crear sitios fraudulentos a través de anuncios publicitarios en buscadores y redes sociales.

En Pets Deli, el año pasado fuimos víctimas de una campaña de phishing particular: los atacantes usaban anuncios falsos (phishing Ads) que redirigían a sitios fraudulentos diseñados para parecerse a nuestra web. A diferencia del phishing tradicional vía correo electrónico, esta técnica utiliza publicidad engañosa para atraer a potenciales víctimas a traves de buscadores y redes sociales.

## ¿Phishing por anuncios o malvertising? Conociendo la diferencia

Mientras que el malvertising consiste en el uso de anuncios online con el fin principal de propagar malware (virus, ransomware, spyware), en nuestro caso nos enfrentamos a un tipo diferente: phishing por anuncios. Aquí, **los anuncios fraudulentos no instalan malware en los dispositivos, sino que llevan a usuarios a sitios falsos para robar sus datos personales o credenciales.**

Esta distinción es importante para entender cómo protegerse: si bien ambos implican riesgos por medio de anuncios, las técnicas y objetivos son diferentes. Nuestro foco fue detectar estos dominios fraudulentos usados en anuncios para anticipar la acción y actuar rápidamente para proteger a nuestros clientes.

### El desafío del monitoreo de certificados SSL

Una pieza clave en el monitoreo de certificados SSL son los CT logs (Certificate Transparency logs): registros públicos donde se almacenan todos los certificados SSL emitidos por las autoridades de certificación. Estos logs permiten detectar rápidamente la aparición de nuevos dominios, facilitando la identificación temprana de posibles intentos de phishing o abuso de marca. Sin ellos, sería prácticamente imposible conocer en tiempo real qué dominios están siendo certificados en Internet.

![Imagen 01](/assets/161/161-01.png)

### CT logs

Durante un tiempo, confiamos en CertStream de Cali Dog, una herramienta que permitía monitorizar en tiempo real los nuevos certificados SSL emitidos para detectar dominios que coincidieran con nuestras marcas. Esto nos ayudaba a reaccionar rápido.

Sin embargo, a finales del año pasado el servicio comenzó a fallar por el alto costo de mantener un servidor centralizado que procesara toda la información, dejándonos sin una alternativa estable. Y como nos estamos preparando para eventos de alto riesgo como Black Friday, necesitábamos una solución, y lo tome como un reto personal.

### Una solución local, ligera y Open Source

Antes de desarrollar esta solución, evalué otras alternativas como certstream-server-go, que es una excelente opción open source y muy robusta, pero para nuestro caso de uso era demasiado: no necesitábamos toda la información detallada de cada certificado ni métricas avanzadas, solo queríamos monitorear en tiempo real la aparición de nuevas URLs sospechosas. Por eso creé CertPatrol como una alternativa mucho más ligera y enfocada en la detección rápida de dominios relevantes para la marca, sin la complejidad de desplegar y mantener un servidor completo.

Para cubrir esta necesidad, desarrollé un script local en Python que:

- Se conecta directamente a fuentes públicas de certificados recientes.
- Busca coincidencias con palabras clave o marcas definidas (por ejemplo, "petsdeli").
- Esto nos permite generar alertas inmediatas con la información mínima necesaria para evaluar y actuar rápido.

Esta herramienta es independiente y no depende de servicios centrales inestables. Es fácil de instalar desde PyPi, totalmente configurable y Open Source, lo que permite que cualquiera la use, modifique o mejore según sus necesidades. Además, posibilita la detección en tiempo real de dominios fraudulentos utilizados en campañas de phishing a través de anuncios.

### Guía rápida: cómo instalar y usar CertPatrol paso a paso

Toda la información, documentación y el código están disponibles en: [https://torito.io/](https://torito.io/)

Aunque el phishing no va a desaparecer, y adopta diferentes formas como el phishing a través de anuncios, la detección temprana de dominios sospechosos es clave para mitigar su impacto. Esta herramienta busca ayudar a las empresas a estar un paso adelante y proteger tanto la marca como a sus clientes sin agregar demasiada complejidad a sus procesos.
