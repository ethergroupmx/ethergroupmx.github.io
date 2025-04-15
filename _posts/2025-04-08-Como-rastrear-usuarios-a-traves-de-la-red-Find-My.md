---
title: Cómo rastrear usuarios a través de la red Find My
date: 2025-04-08 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [android, ciberataques, news, ciberseguridad]
description: La red Find My de Apple se puede aprovechar para rastrear de forma remota dispositivos Android, Windows y Linux de otros proveedores
image: /assets/125/preview1.png
---

Los AirTags son un dispositivo de rastreo popular utilizado por todos, desde propietarios olvidadizos de llaves hasta los malintencionados, como cónyuges celosos y ladrones de coches. Usar AirTags para espiar es sencillo: se coloca discretamente una etiqueta en el objetivo para permitir supervisar cómodamente sus movimientos mediante Apple Find My. Incluso hemos añadido protección contra el seguimiento basado en AirTag a nuestros productos para Android.

Sin embargo, un estudio reciente de investigadores de seguridad ha descubierto sorprendentemente que el seguimiento remoto ni siquiera depende de comprar un AirTag o de estar físicamente cerca del objetivo. Si logras introducir un malware especial en el dispositivo Windows, Android o Linux de alguien (como un ordenador o un teléfono), podría usar el Bluetooth del dispositivo para enviar una señal que los dispositivos Apple cercanos pensarían que proviene de un AirTag. Básicamente, para los dispositivos Apple, el teléfono o el ordenador infectados se convierten efectivamente en un AirTag de gran tamaño, rastreable a través de la red Find My, que cuenta con más de mil millones de teléfonos y tabletas Apple.

### Anatomía del ataque

El ataque aprovecha dos características de la tecnología Find My.

En primer lugar, esta red utiliza cifrado de extremo a extremo, por lo que los participantes no saben de quién son las señales que están transmitiendo. Para intercambiar información, un AirTag y el teléfono de su propietario dependen de un par de claves criptográficas. Cuando un AirTag perdido transmite sus “indicativos” a través de Bluetooth, los “detectores” de la red Find My (es decir, cualquier dispositivo Apple con Bluetooth y acceso a Internet, independientemente de quién sea el propietario) simplemente transmiten los datos de geolocalización de la AirTag a los servidores de Apple. Los datos se cifran con la clave pública del AirTag perdido mediante el cifrado de datos.

Entonces, cualquier dispositivo puede solicitar los datos de ubicación cifrados del servidor. Y como está cifrada, Apple no sabe a quién pertenece la señal ni qué dispositivo la solicitó. El punto crucial aquí es que solo se pueden descifrar los datos y averiguar tanto de quién es el AirTag como su ubicación exacta si se dispone de la clave privada correspondiente. Por lo tanto, estos datos solo son útiles para el propietario del teléfono inteligente emparejado con este AirTag.

Otra característica de Find My es que los detectores no verifican si la señal de ubicación realmente se originó con un dispositivo Apple. Cualquier dispositivo que admita Bluetooth Low Energy (BLE) puede transmitirlo.

Para aprovechar estas características, los investigadores idearon el siguiente método:

- Instalan malware en un ordenador, un teléfono u otro dispositivo que funcione con Android, Windows o Linux, y verifican la dirección del adaptador Bluetooth.
- El servidor de los atacantes recibe la información y utiliza potentes tarjetas de vídeo para generar un par de claves de cifrado específicas para la dirección Bluetooth del dispositivo y compatibles con la tecnología Find My de Apple.
- La clave pública se envía de vuelta al dispositivo infectado, y el malware comienza entonces a transmitir un mensaje Bluetooth que imita las señales de AirTag e incluye esta clave.
- Cualquier dispositivo Apple cercano conectado a Internet recibe el mensaje de Bluetooth y lo transmite a los servidores de Find My.
- El servidor de los atacantes utiliza la clave privada para solicitar la ubicación del dispositivo infectado a Find My y descifrar los datos.

### ¿Qué tan bien funciona el rastreo?

Cuantos más dispositivos Apple haya cerca y más lento sea el movimiento de la víctima, mayor será la exactitud y la velocidad del rastreo de la ubicación. En entornos urbanos típicos, como casas u oficinas, la ubicación normalmente se determina en seis o siete minutos, y con una exactitud de alrededor de tres metros. Incluso en situaciones extremas, como estar en un avión, el rastreo puede producirse porque el acceso a Internet está ahora ampliamente disponible en los vuelos. Los investigadores obtuvieron 17 puntos de geolocalización a lo largo de un vuelo de 90 minutos, lo que les permitió reconstruir con bastante precisión la trayectoria de vuelo de la aeronave.

Naturalmente, el éxito del ataque depende de si la víctima puede infectarse con malware, y los detalles son ligeramente diferentes según la plataforma. En los dispositivos Linux, el ataque solo requiere infectar el dispositivo de la víctima debido a la implementación específica de Bluetooth. Por el contrario, Android y Windows emplean la aleatorización de direcciones Bluetooth, lo que significa que el atacante necesita infectar dos dispositivos Bluetooth cercanos: uno como objetivo de rastreo (el que imita a un AirTag), y otro para obtener su dirección de adaptador.

La aplicación maliciosa necesita acceso al Bluetooth, pero no es difícil conseguirlo. Muchas categorías de aplicaciones comunes (como reproductores multimedia, herramientas para compartir archivos e incluso aplicaciones de pago) suelen tener razones legítimas para solicitarlo. Es probable que se cree una aplicación cebo convincente y funcional para este tipo de ataque, o incluso que se “troyanice” una aplicación existente. El ataque no requiere permisos administrativos ni acceso raíz.

Es importante destacar que no estamos hablando solo de teléfonos y ordenadores: el ataque es efectivo en una amplia variedad de dispositivos, incluidos televisores inteligentes, gafas de realidad virtual y otros electrodomésticos, ya que Android y Linux son sistemas operativos comunes en muchos de ellos.

Otra parte clave del ataque implica el cálculo de claves criptográficas en el servidor. Debido a la complejidad de esta operación, que requiere un hardware de alquiler con tarjetas de vídeo modernas, el coste de generar una clave para una sola víctima se estima en unos 2,2 USD. Por este motivo, consideramos poco probables los escenarios de rastreo masivo que tengan como objetivo, por ejemplo, a los visitantes de un centro comercial. Sin embargo, los ataques selectivos a este precio están al alcance de prácticamente cualquiera, incluidos estafadores o compañeros de trabajo, y cónyuges entrometidos.

### La respuesta de Apple

La empresa parcheó la vulnerabilidad de la red Find My en diciembre de 2024 en iOS 18.2, visionOS 2.2, iPadOS 17.7.3 (para dispositivos más antiguos) y 18.2 (para dispositivos más nuevos), watchOS 11.2, tvOS 18.2, macOS Ventura 13.7.2, macOS Sonoma 14.7.2 y macOS Sequoia 15.2. Por desgracia, como suele ocurrir con Apple, no se han revelado los detalles de las actualizaciones. Los investigadores enfatizan que este método de rastreo seguirá siendo técnicamente factible hasta que todos los usuarios de Apple actualicen al menos a las versiones mencionadas anteriormente, aunque menos dispositivos podrán informar la ubicación de un dispositivo rastreado. Y no es imposible que otro truco de ingeniería pueda derrotar al parche de Apple.

### Cómo protegerte de este ataque

- Desactiva el Bluetooth cuando no lo estés utilizando si tu dispositivo dispone de esta opción.
- Cuando instales aplicaciones, utiliza solo fuentes de confianza. Comprueba que la aplicación existe desde hace mucho tiempo y que tiene muchas descargas y una alta valoración en su última versión.
- Solo concede acceso al Bluetooth y de localización a las aplicaciones si estás seguro de que necesitas esas funciones.
- Actualiza periódicamente tu dispositivo: tanto el sistema operativo como las aplicaciones principales.
- Asegúrate de tener activada una protección antimalware integral en todos tus dispositivos.

### Si estás listo para proteger tu negocio en el mundo digital, no dudes en contactarnos. ¡Somos [EtherGroup](https://ethergroup.mx/)!

