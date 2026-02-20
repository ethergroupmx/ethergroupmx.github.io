---
title: "Massiv: tu app de IPTV te quita tus ahorros"
date: 2026-02-19 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, ciberseguridad, malware, hacking, móviles]
description: Massiv es una nueva familia de malware de Toma de Control de Dispositivos (DTO) sin vínculos directos con otras amenazas conocidas, que se hace pasar por una app de IPTV.
image: /assets/220/preview1.png
---

Un troyano bancario moderno para Android, que suele distribuirse mediante carga lateral, debe hacerse pasar convincentemente por una aplicación legítima para no levantar sospechas y persuadir a las víctimas a proceder con la instalación.

Una investigación reciente realizada por el equipo de Inteligencia de Amenazas Móviles (MTI) de ThreatFabric reveló otro troyano bancario para Android. El nombre Massiv fue dado en honor a uno de sus componentes.

![Imagen 01](/assets/220/220-01.png)

**Esta nueva amenaza permite a sus operadores controlar remotamente los dispositivos infectados y realizar ataques de apropiación de dispositivos, con transacciones fraudulentas adicionales realizadas desde las cuentas bancarias de las víctimas.**

- Massiv es una nueva familia de malware de apropiación de dispositivos sin vínculos directos con otras amenazas conocidas.
- Sus capacidades de control remoto han dado lugar a casos de fraude confirmados en el sur de Europa.
- Las aplicaciones de IPTV se utilizan cada vez más como camuflaje para la distribución de amenazas móviles.
- Aunque solo se ha observado en un número limitado de campañas dirigidas, ya supone un gran riesgo para los usuarios de banca móvil.

La distribución de Massiv pone de relieve otra tendencia creciente observada en el panorama de amenazas móviles: los actores de amenazas disfrazan su malware como aplicaciones de IPTV, dirigiéndose a los usuarios que buscan aplicaciones de televisión online.

### La película más aterradora que verás

**Massiv se hace pasar por una aplicación de IPTV. Este tipo de aplicaciones proporciona acceso a servicios de televisión en línea.** Existen múltiples servicios que ofrecen esto, incluyendo algunos que podrían infringir las políticas de derechos de autor, por lo que no se permite su distribución a través de la tienda oficial de Google Play. En general, los usuarios de aplicaciones de IPTV están acostumbrados a que estas se distribuyan fuera de la tienda oficial, generalmente a través de sus propios sitios web o canales de Telegram.

Este enfoque es una presa fácil para los estafadores deseosos de distribuir malware a víctimas desprevenidas. Dado que a los usuarios de IPTV les resulta muy natural buscar estas aplicaciones fuera de la tienda, crear un sitio web falso de una aplicación nueva y atractiva (o falsificar una existente) permite a los actores de amenazas evitar que el usuario tenga que instalar la aplicación desde fuentes desconocidas. **Los usuarios que buscan contenido "premium" o con restricciones regionales ya están acostumbrados a eludir las tiendas de aplicaciones oficiales, lo que reduce las sospechas.**

En la mayoría de los casos observados, se trata simplemente de suplantación de identidad. Ninguna aplicación de IPTV real estaba infectada ni contenía inicialmente código malicioso. Normalmente, el dropper que imita la aplicación de IPTV abre una vista web con un sitio web de IPTV, mientras que el malware real ya está instalado y ejecutándose en el dispositivo.

Si analizamos el panorama actual de amenazas móviles en general, observamos que Massiv no es el único malware que utiliza este enmascaramiento. **En los últimos 6-8 meses, este señuelo se ha vuelto cada vez más popular, a medida que observamos un número creciente de muestras de dropper de malware que se hacen pasar por aplicaciones de IPTV.** Entre los países en los que se ha observado que se ha utilizado este tipo de camuflaje se incluyen España, Portugal, Francia y Turquía.

### Ataques de Massiv

Es una potente herramienta para cometer fraudes en dispositivos móviles, equipada con funcionalidad de superposición, registro de pulsaciones de teclas e interceptación de mensajes SMS/Push para obtener datos confidenciales. Además de eso, **es una herramienta de control remoto completamente funcional, que proporciona a su operador acceso directo al dispositivo de la víctima.**

Los ataques de superposición sirven como una técnica inicial que los operadores de Massiv aprovechan para facilitar actividades fraudulentas. Al igual que otras familias de malware bancario, Massiv monitorea las aplicaciones que se inician en los dispositivos infectados y muestra una superposición falsa si la víctima inicia una aplicación específica. La pantalla falsa imita la interfaz de usuario de la aplicación original y solicita al usuario que ingrese credenciales y otra información confidencial, como los datos de su tarjeta de crédito.

Curiosamente, una de las campañas de Massiv analizadas por los analistas se dirigió a la aplicación del gobierno portugués, solicitando a la víctima su número de teléfono y código PIN. Esta aplicación funciona como monedero de identidad digital para Portugal. Es probable que los delincuentes la estén utilizando para utilizar los datos de la víctima y eludir la verificación KYC que podría realizarse a través de ella.

La investigación de MTI identificó casos en los que se abrieron nuevas cuentas a nombre de la víctima (usuario del dispositivo infectado) en nuevos bancos y servicios (no utilizados por la víctima). Dado que estas cuentas están completamente bajo el control de los estafadores, pueden utilizarlas para blanquear dinero, además de obtener préstamos y retirar el dinero, dejando a la víctima desprevenida con deudas en el banco en el que nunca abrió una cuenta.

![Imagen 01](/assets/220/220-02.png)

### Control del dispositivo

Al robar las credenciales y otros datos confidenciales mediante superposiciones y registro de pulsaciones de teclas, Massiv proporciona al operador acceso remoto al dispositivo infectado a través de VNC e implementa una capacidad de monitorización visual e interacción remota basada en AccessibilityService de Android. Su funcionalidad establece un canal de control que permite a un operador remoto observar y manipular la interfaz de usuario del dispositivo casi en tiempo real.

Toda la comunicación se realiza a través de un canal WebSocket, que actúa como transporte de comando y control (C2) tanto para los comandos entrantes como para los datos salientes de la interfaz de usuario.

Como algunas aplicaciones implementan protección contra capturas de pantalla, para evitarlo, Massiv utiliza el modo UI-tree que recorre recursivamente los objetos AccessibilityNodeInfo para crear una representación JSON del contenido a de la interfaz de usuario y las coordenadas de pantalla.

### Conclusión

Massiv, al ser otro nuevo troyano bancario en el ya rico panorama de amenazas, muestra una demanda continua de estas herramientas por parte de los delincuentes. Sus capacidades reflejan las últimas tendencias y la necesidad de los estafadores de realizar fraudes en el canal móvil.

Si bien aún no se ha observado que se promocione como malware como servicio, el operador de Massiv muestra claras señales de seguir este camino, introduciendo claves API para la comunicación del malware con el backend. El análisis de código reveló un desarrollo continuo, con la probable incorporación de más funciones en el futuro.

Se recomienda a las organizaciones financieras que monitoreen esta amenaza, ya que tiene potencial de crecer como malware como servicio. Sin embargo, al seguir siendo operada de forma privada, aumenta sus posibilidades de pasar desapercibida debido a campañas pequeñas, pero dirigidas y potentes, que atraen menos la atención de las soluciones de detección.Massiv, al ser otro nuevo troyano bancario en el ya rico panorama de amenazas, muestra una demanda continua de estas herramientas por parte de los delincuentes. Sus capacidades reflejan las últimas tendencias y la necesidad de los estafadores de realizar fraudes en el canal móvil.

Si bien aún no se ha observado que se promocione como malware como servicio, el operador de Massiv muestra claras señales de seguir este camino, introduciendo claves API para la comunicación del malware con el backend. El análisis de código reveló un desarrollo continuo, con la probable incorporación de más funciones en el futuro.

**Se recomienda a las organizaciones financieras que monitoreen esta amenaza, ya que tiene potencial de crecer como malware como servicio.** Sin embargo, al seguir siendo operada de forma privada, aumenta sus posibilidades de pasar desapercibida debido a campañas pequeñas, pero dirigidas y potentes, que atraen menos la atención de las soluciones de detección.

