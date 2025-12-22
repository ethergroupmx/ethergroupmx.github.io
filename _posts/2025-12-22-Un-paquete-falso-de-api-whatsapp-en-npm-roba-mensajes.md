---
title: "Un paquete falso de API de WhatsApp en npm roba mensajes, contactos y tokens de inicio de sesión"
date: 2025-12-22 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, ciberseguridad, móviles, vulnerabilidad]
description: Un paquete malicioso en npm, disfrazado de API de WhatsApp, ha superado las 56 000 descargas mientras roba credenciales, intercepta mensajes y compromete cuentas. Analizamos cómo opera y por qué representa un riesgo crítico para desarrolladores y empresas.
image: /assets/201/preview1.png
---

Investigadores de ciberseguridad han revelado detalles de un nuevo paquete malicioso en el repositorio npm que funciona como una API de WhatsApp completamente funcional, pero también contiene la capacidad de interceptar cada mensaje y vincular el dispositivo del atacante a la cuenta de WhatsApp de la víctima.

El paquete, llamado " lotusbail ", se ha descargado más de 56.000 veces desde que el usuario "seiren_primrose" lo subió por primera vez al registro en mayo de 2025. De estas, 711 descargas se realizaron durante la última semana. La biblioteca aún está disponible para su descarga al momento de escribir este artículo.

Bajo la apariencia de una herramienta funcional, el malware "roba tus credenciales de WhatsApp, intercepta cada mensaje, recopila tus contactos, instala una puerta trasera persistente y encripta todo antes de enviarlo al servidor del actor de la amenaza", dijo el investigador de Koi Security, Tuval Admoni, en un informe publicado durante el fin de semana.

En concreto, está equipada para capturar tokens de autenticación y claves de sesión, historial de mensajes, listas de contactos con números de teléfono, así como archivos multimedia y documentos. Más importante aún, la biblioteca está inspirada en @whiskeysockets/baileys , una biblioteca TypeScript legítima basada en WebSockets para interactuar con la API web de WhatsApp.

Esto se logra mediante un contenedor WebSocket malicioso a través del cual se enrutan la información de autenticación y los mensajes, lo que permite capturar credenciales y chats. Los datos robados se transmiten cifrados a una URL controlada por el atacante.

El ataque no termina ahí, ya que el paquete también alberga una funcionalidad encubierta para crear acceso persistente a la cuenta de WhatsApp de la víctima secuestrando el proceso de vinculación del dispositivo mediante un código de emparejamiento codificado.

"Al usar esta biblioteca para autenticar, no solo vinculas tu aplicación, sino también el dispositivo del atacante", explicó Admoni. "Tienen acceso completo y persistente a tu cuenta de WhatsApp, y tú no tienes ni idea de que están ahí".

Al vincular su dispositivo al WhatsApp del objetivo, no solo permite el acceso continuo a sus contactos y conversaciones, sino que también permite el acceso persistente incluso después de que el paquete se desinstala del sistema, dado que el dispositivo del actor de amenazas permanece vinculado a la cuenta de WhatsApp hasta que se desvincula navegando a la configuración de la aplicación.

Idan Dardikman de Koi Security dijo a The Hacker News que la actividad maliciosa se activa cuando el desarrollador usa la biblioteca para conectarse a WhatsApp.

El malware envuelve el cliente WebSocket, por lo que, una vez que te autenticas y empiezas a enviar/recibir mensajes, se activa la intercepción, explicó Dardikman. No se requiere ninguna función especial más allá del uso normal de la API. El código de emparejamiento de la puerta trasera también se activa durante el proceso de autenticación, por lo que el dispositivo del atacante se vincula en cuanto conectas tu aplicación a WhatsApp.

Además, "lotusbail" viene equipado con capacidades anti-depuración que hacen que entre en una trampa de bucle infinito cuando se detectan herramientas de depuración, lo que hace que congele la ejecución.

"Los ataques a la cadena de suministro no están disminuyendo, sino mejorando", afirmó Koi. "La seguridad tradicional no detecta esto. El análisis estático detecta el código de WhatsApp que funciona y lo aprueba. Los sistemas de reputación han registrado 56.000 descargas y confían en él. El malware se esconde entre el "este código funciona" y el "este código solo hace lo que promete".

### Los paquetes NuGet maliciosos atacan el ecosistema criptográfico#

La revelación se produce cuando ReversingLabs compartió detalles de 14 paquetes NuGet maliciosos que se hacen pasar por Nethereum, una biblioteca de integración .NET para la cadena de bloques descentralizada Ethereum, y otras herramientas relacionadas con criptomonedas para redirigir los fondos de las transacciones a billeteras controladas por los atacantes cuando el monto de la transferencia excedía los $100 o exfiltrar claves privadas y frases semilla.

![Imagen 01](/assets/201/201-01.png)

A continuación se enumeran los nombres de los paquetes, publicados desde ocho cuentas diferentes:

- binance.csharp
- Bitcoin Core
- por bitapi.net
- API de coinbase.net
- googleads.api
- nbitcoin.unificado
- nethereumnet
- nethereumunificado
- netherеum.all
- solananet
- solnetall
- solnetall.net
- solnetplus
- solnetunificado

Los paquetes han empleado diversas técnicas para infundir en los usuarios una falsa sensación de confianza en la seguridad, como inflar el número de descargas y publicar docenas de nuevas versiones en poco tiempo para dar la impresión de que se mantiene en activo. La campaña se remonta a julio de 2025.

La funcionalidad maliciosa se inyecta de forma que solo se activa cuando los desarrolladores instalan los paquetes y se integran funciones específicas en otras aplicaciones. Entre estos paquetes destaca GoogleAds.API, que se centra en robar información OAuth de Google Ads en lugar de exfiltrar información confidencial de la billetera.

"Estos valores son muy sensibles, porque permiten el acceso programático completo a una cuenta de Google Ads y, si se filtran, los atacantes pueden hacerse pasar por el cliente publicitario de la víctima, leer todos los datos de la campaña y el rendimiento, crear o modificar anuncios e incluso gastar fondos ilimitados en una campaña maliciosa o fraudulenta", dijo ReversingLabs.

