---
title: "Optimizely: un ataque de JavaScript comprometió a 178 organizaciones"
date: 2026-11-17 11:00:00
categories: [CIBERATAQUES]
tags: [ciberataques, ciberseguridad, vulnerabilidades, malware]
description: "Una vulnerabilidad en Optimizely permitió inyectar código JavaScript malicioso en sitios web de 178 organizaciones, exponiendo datos financieros, cookies e información de visitantes."
image: /assets/316/preview1.png
---

El investigador Scott Helme, de Report URI, descubrió la campaña. Confirmó que ya se han sustraído criptomonedas y rastreó las transacciones hasta monederos controlados por los atacantes. La lista incluye algunos de los sitios más visitados de Internet, como Zoom, Mulesoft, BBC, Fox Sport, CNN, Salesforce, GitLab, IKEA, HSBC, Equifax, Air France-KLM, Ledger y Peacock.

No se trataba de un simple skimmer; el malware funcionaba como un kit multifuncional: sustituía direcciones de monederos de criptomonedas, robaba datos de tarjetas de pago, capturaba cookies y capturas de pantalla, e instalaba los kits de exploits Coruna y DarkSword en dispositivos iPhone y iPad.

**Lo que hace que este caso sea preocupante es que no fue necesario hackear directamente ninguno de los sitios web afectados. El código malicioso llegó a través de un script de terceros de confianza que cada sitio cargaba en todas sus páginas.**

### Se abusó del snippet de Optimizely

Optimizely Web funciona mediante la carga, por parte de cada cliente, de un fragmento de código (snippet) JavaScript desde cdn.optimizely[.]com. Este archivo contiene el código de Optimizely, los experimentos del cliente y un campo opcional denominado Project JavaScript. Según la documentación de Optimizely, Project JavaScript es el primer código que se ejecuta dentro del snippet y puede afectar a todos los experimentos de un proyecto.

El atacante insertó un pequeño cargador (loader) en este campo, dejando intacto el resto del snippet. Dado que el archivo seguía sirviéndose desde el dominio de Optimizely y contaba con su certificado, los navegadores y las herramientas de seguridad lo consideraron legítimo. En el caso de Zoom, el código añadido creaba, de forma silenciosa, una nueva etiqueta script que descargaba un archivo llamado track.js desde el dominio 1688360[.]cc.

Report URI identificó tres versiones del cargador. La mayoría de los snippets utilizaban una etiqueta script convencional; otros, en cambio, ocultaban la misma URL codificada en Base64 mediante la función `atob()`, de modo que una búsqueda simple de "1688360[.]cc" no permitía detectarla. Una tercera versión incluía una copia completa del código malicioso (payload) y lo ejecutaba mediante `eval` en caso de que el dominio del atacante estuviera bloqueado.

En un momento dado, Smartsheet eliminó el fragmento de código, pero poco después volvió a infectarlo con la versión codificada en Base64, lo que demostraba que el atacante aún conservaba el acceso. Los sitios que alojaban dicho fragmento en su propio dominio —como Scheels y Vodafone Australia— también se vieron afectados, ya que el contenido provenía del mismo proyecto de Optimizely.

### Lo que robó el malware

El crypto clipper (malware de sustitución de direcciones de criptomonedas) escaneaba cada página en busca de direcciones de monederos de Bitcoin, Ethereum, TRON, Solana, TON, Litecoin, Bitcoin Cash y Dogecoin. El programa sustituía dichas direcciones por las del atacante, tanto en el texto de la página como en el portapapeles y en las solicitudes web salientes. Para las 19:25 UTC, los monederos del atacante habían recibido aproximadamente 7.040 dólares. Los fondos sustraídos fueron transferidos a plataformas de intercambio  alrededor de las 13:03 UTC.

A las 13:43 UTC, el atacante añadió un skimmer de tarjetas. Este componente monitorizaba los formularios en busca de números de tarjeta, fechas de caducidad y códigos CVV, enviando posteriormente los datos a `1688360[.]cc/card.php`. Los datos de tarjetas introducidos en marcos de pago externos, como los de Stripe o Adyen, quedaban fuera de su alcance.

Sin embargo, esto no ocurría con los datos introducidos en los campos de formulario propios del sitio web. El script también enviaba las URL de las páginas, las cookies legibles y capturas de pantalla (generadas mediante `html2canvas`) a `1688360[.]cc/hit.php`.

### Ataques a iPhones mediante Coruna y DarkSword

En los dispositivos móviles de Apple, el script cargaba un archivo de enrutamiento desde dominios con extensión `.icu` y seleccionaba una cadena de exploits en función de la versión de iOS. Los dispositivos con iOS 13 a 17 recibían Coruna, mientras que los dispositivos con iOS 18 recibían DarkSword. Una cadena distinta, destinada a iOS 26, se limitaba a recopilar información para la identificación (fingerprinting) del dispositivo.

El grupo de inteligencia sobre amenazas de Google señala que Coruna contiene 23 exploits distribuidos en cinco cadenas completas. DarkSword combina seis vulnerabilidades dirigidas contra iOS 18.4 a 18.7. Los lectores pueden encontrar más información en nuestros informes anteriores sobre el *kit* de exploits Coruna y la cadena de exploits para iOS denominada DarkSword.

Report URI afirma desconocer cómo el atacante obtuvo acceso de escritura a tantos proyectos de clientes sin relación entre sí. Los investigadores descartaron el envenenamiento de la caché de la red de distribución de contenidos (CDN). Los fragmentos de código (*snippets*) utilizados en los propios sitios de Optimizely, incluido login.optimizely.com, también contenían el código malicioso.

Report URI señaló que, al momento de publicar sus hallazgos, aún no había recibido respuesta por parte de Optimizely. Para las 21:52 UTC, la mayor parte del código ya había desaparecido; solo el fragmento de TalkTalk permanecía infectado, frente a los 169 que lo estaban a las 20:56 UTC.

Los clientes de Optimizely Web deben revisar todos los campos de Project JavaScript y el código personalizado de cada experimento. Deben buscar referencias a "1688360.cc", "atob" y cualquier script que no haya sido creado por ellos.

El historial de cambios de Optimizely registra todas las modificaciones realizadas en el JavaScript de los proyectos. Asimismo, indica si cada cambio se efectuó a través de la API REST o mediante la interfaz web. Los equipos deben revisar los usuarios, los tokens de API y las integraciones, y posteriormente renovar sus credenciales. Los datos de tarjetas introducidos el 16 de noviembre, así como cualquier información confidencial almacenada en cookies que no cuenten con el atributo HttpOnly, deben considerarse expuestos.

La política de seguridad de contenido (Content Security Policy, CSP) marcó una diferencia significativa. De las organizaciones afectadas cuyos sitios web fueron analizados por Report URI, 68 carecían por completo de CSP, mientras que solo 24 lograron bloquear la carga maliciosa en su totalidad. El uso de directivas como unsafe-eval o strict-dynamic permitió la ejecución del código. Se recomienda a los usuarios actualizar sus dispositivos a iOS 18.7.3 (o versiones posteriores) o a iOS 26.3 (o versiones posteriores). Asimismo, deben verificar minuciosamente cualquier transferencia de criptomonedas y los estados de cuenta de sus tarjetas correspondientes a esa fecha.
