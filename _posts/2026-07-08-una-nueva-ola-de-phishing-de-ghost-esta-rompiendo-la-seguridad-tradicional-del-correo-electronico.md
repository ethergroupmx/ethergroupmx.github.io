---
title: "Una nueva ola de phishing de Ghost está rompiendo la seguridad tradicional del correo electrónico"
date: 2026-07-08 11:00:00
categories: [CIBERATAQUES]
tags: [phishing, ciberseguridad, ciberataques]
description: Una nueva campaña de EvilTokens utiliza "phishing fantasma" para ocultar páginas maliciosas hasta que la víctima abre el enlace, evadiendo filtros de seguridad y facilitando el robo de credenciales.
image: /assets/272/preview1.png
---

Para los responsables de seguridad, el riesgo es evidente: las comprobaciones de URL tradicionales pueden pasar por alto el ataque, mientras que el acceso a Microsoft 365, los datos confidenciales y el tiempo de respuesta ya están en riesgo.

### El correo electrónico parece seguro. El navegador cuenta una historia diferente.

Un reciente ataque de EvilTokens demuestra cómo un enlace de phishing puede parecer inofensivo durante una inspección inicial, pero aun así conducir al secuestro de una cuenta de Microsoft 365.

El kit utiliza la técnica de phishing mediante código de dispositivo de Microsoft para convencer a las víctimas de que completen un proceso de inicio de sesión legítimo de Microsoft y, sin saberlo, autoricen el acceso a sus cuentas. No necesita robar la contraseña directamente.

El ataque real permanece oculto hasta que la página se abre en el navegador. Su código HTML está cifrado con AES-GCM y solo se hace visible después de que el navegador lo descifra y muestra el contenido de phishing en el DOM.

Como resultado, las comprobaciones de URL estáticas y los controles a nivel de red pueden capturar la respuesta inicial sin ver lo que realmente ve el empleado. Esta falta de visibilidad puede provocar:


- Mayor exposición a la adquisición de cuentas de Microsoft 365
- Decisiones de contención y respuesta tardías
- Acceso no autorizado al correo electrónico corporativo, archivos y servicios en la nube.
- Las alertas más inciertas se elevaron a analistas sénior.
- Mayor carga de trabajo de investigación y mayores costos operativos.
- Pruebas incompletas para bloquear la infraestructura relacionada.

Sin embargo, el flujo de ataque completo se descubrió dentro del entorno de pruebas interactivo de ANY.RUN. Explore la sesión de análisis para ver qué reveló el navegador y cómo los equipos pueden usar esta evidencia para responder con mayor rapidez.


![Imagen 01](/assets/272/272-01.jpg)

### Donde el phishing fantasma está golpeando con más fuerza

El análisis de amenazas de ANY.RUN muestra que la actividad reciente de EvilTokens se ha concentrado en Estados Unidos y Europa, y tiene como objetivo los sectores de tecnología, manufactura, educación, banca, consultoría, servicios financieros y proveedores de seguridad gestionada.

![Imagen 02](/assets/272/272-02.jpg)

La superposición es difícil de ignorar. Según los datos de envíos de sandbox de ANY.RUN de 15.000 organizaciones, la exposición al phishing en 2026 alcanzó el 75,6% en consultoría, el 72,8% en servicios financieros, el 71,9% en manufactura, el 67,9% en tecnología, el 66,7% en banca y el 66,1% entre los MSSP .

Esto hace que el phishing oculto sea especialmente peligroso para estos sectores. Una cuenta de Microsoft 365 comprometida puede exponer datos confidenciales, propiciar el fraude y la suplantación de identidad por correo electrónico, y desencadenar una costosa respuesta ante incidentes.

Cuanto más tiempo permanezca oculto el ataque, mayor será la probabilidad de que una sola cuenta se convierta en un incidente empresarial de mayor envergadura.

### Haz visible el fantasma antes de que el negocio pague las consecuencias

La forma más eficaz de detectar el phishing fantasma es abrir enlaces sospechosos en un entorno aislado (sandbox) que permita la inspección de datos en el navegador.

Dentro del entorno de pruebas interactivo de ANY.RUN, los analistas van más allá de la respuesta cifrada AES-GCM y observan qué sucede después de que la página se descifra. Pueden ver cómo aparece el contenido de phishing en el DOM, vincular el cambio con una solicitud Fetch/XHR y rastrear el código del dispositivo de Microsoft hasta el punto final /api/device/start.

![Imagen 03](/assets/272/272-03.jpg)

La visualización de datos en el navegador integra todo el flujo del ataque en una sola investigación:

- Las instantáneas del DOM muestran cuándo cambia la página oculta y aparece el código del usuario.
- Las solicitudes HTTP revelan la comunicación de backend que subyace al flujo de código del dispositivo.
- Los detalles de la URL revelan el destino final y las firmas de detección activadas.
- Los indicadores proporcionan dominios, puntos finales, hashes e infraestructura para una búsqueda más exhaustiva.

En lugar de reconstruir el ataque manualmente, los equipos obtienen evidencia directa de cómo se comporta la página, qué solicita y qué elementos contribuyen a la contención y detección.

![Imagen 04](/assets/272/272-04.jpg)

### De la evidencia a nivel de navegador a una transferencia SOC más clara

Para trasladar esta evidencia del Nivel 1 al Nivel 2, la investigación genera automáticamente un informe con un resumen mediante IA y recomendaciones sobre los pasos a seguir.

![Imagen 05](/assets/272/272-05.jpg)

En lugar de reconstruir el caso a partir de datos brutos del navegador, los analistas sénior reciben los hallazgos clave, el comportamiento observado, los indicadores y el contexto de la respuesta en un solo lugar. Esto agiliza las transferencias de información, reduce el trabajo repetitivo y ayuda a los equipos a pasar de la validación a la contención con menor demora.

### Detenga el phishing fantasma en el navegador antes de que llegue a su negocio

El caso EvilTokens pone al descubierto una verdad incómoda: un correo electrónico puede pasar la inspección mientras el verdadero ataque espera dentro del navegador.

Sin visibilidad a nivel de navegador, el SOC se ve obligado a tomar decisiones de alto riesgo con información parcial. Esta demora les da a los atacantes más tiempo para obtener acceso, ampliar su alcance y convertir una cuenta de Microsoft 365 comprometida en un costoso incidente empresarial.

Esto ayuda a los responsables de seguridad:

- Reduzca el período de exposición antes de que una cuenta comprometida se convierta en un incidente de mayor envergadura.
- Reduzca la presión sobre los analistas sénior proporcionando al nivel 1 pruebas suficientes para resolver más casos.
- Acelere la contención con el contexto completo del ataque disponible desde la primera escalada.
- Mejorar la cobertura de detección utilizando el comportamiento del navegador, la infraestructura y los patrones de ataque repetibles.
- Reduzca el coste de respuesta al phishing eliminando la investigación manual y el trabajo duplicado.
- Tome decisiones sobre riesgos basándose en evidencia, en lugar de confiar en análisis limpios o veredictos no concluyentes.

El phishing moderno ya no se revela por completo en el correo electrónico o la respuesta inicial a la URL. Los equipos de seguridad necesitan visibilidad que permita rastrear el ataque hasta el navegador y detectarlo antes de que la empresa sufra las consecuencias.
