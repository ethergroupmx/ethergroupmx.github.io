---
title: "Google Chrome instala un modelo de IA de 4 GB sin consentimiento"
date: 2026-05-07 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [IA, tecnología, navegador, ciberseguridad, privacidad, news, internet, web]
description: Google Chrome estaría descargando en segundo plano un modelo de IA de hasta 4 GB para funciones basadas en Gemini Nano, generando preocupación por la falta de transparencia y control para los usuarios.
image: /assets/253/preview1.png
---

No hablamos de una actualización menor ni de un archivo residual, sino de un componente grande que muchos usuarios probablemente no esperaban ver ahí. La conversación empezó a tomar forma a partir de una publicación de Alexander Hanff en That Privacy Guy. Su hallazgo, en esencia, era sencillo de entender: según sus registros, Chrome había dejado en su ordenador un modelo de IA de varios gigas sin mostrarle un aviso claro durante el proceso.

Alexander dice que en cualquier equipo con Chrome instalado, en el perfil de usuario se encuentra un directorio llamado OptGuideOnDeviceModel. Dentro de este, hay un archivo llamado weights.bin, de aproximadamente 4 GB. Se trata del archivo de pesos para Gemini Nano. Chrome lo utiliza para habilitar funciones que Google ha promocionado con nombres como "Ayúdame a escribir", detección de estafas en el dispositivo y otras funciones del navegador con asistencia de IA.

El archivo apareció sin solicitud de consentimiento. No hay ninguna casilla de verificación en la configuración de Chrome que diga "descargar un modelo de IA de 4 GB". La descarga se activa cuando las funciones de IA de Chrome están activas, y estas funciones están activas por defecto en las versiones recientes de Chrome. En cualquier equipo que cumpla con los requisitos de hardware, Chrome trata el hardware del usuario como destino de entrega y escribe el modelo.

![Imagen 01](/assets/253/253-01.png)

Gemini Nano no funciona como una descarga tradicional que buscamos, aceptamos e instalamos manualmente. En la documentación para desarrolladores de Chrome, la compañía explica que las capacidades integradas de IA están pensadas para ser fluidas y que la gestión del modelo se realiza automáticamente en segundo plano. También señala que la descarga inicial puede activarse cuando una función de IA integrada en el navegador necesita usar Gemini Nano por primera vez. Dicho de otra forma: el modelo puede llegar al ordenador como parte del funcionamiento interno de Chrome, no necesariamente mediante una acción clara y reconocible para el usuario.

El modelo no se limita a impulsar un navegador con un chatbot integrado dentro Chrome. Google ya ha descrito usos de Gemini Nano en el propio dispositivo para detectar estafas de soporte técnico, un tipo de amenaza que muchas veces dura muy poco tiempo online y puede escapar a los sistemas tradicionales de rastreo. En ese escenario, Chrome puede proporcionar al modelo contenido de la página que el usuario está visitando para extraer indicios de riesgo. La IA, por tanto, también puede formar parte de la capa de seguridad del navegador.

Ahí está buena parte del malestar. La IA en el navegador puede tener usos razonables, desde ayudar a detectar fraudes hasta alimentar funciones de escritura, traducción o resumen, pero el problema aparece cuando el usuario no entiende bien qué se ha descargado, por qué está ahí y cómo puede gestionarlo. Hanff lo resume con una crítica muy directa: "Chrome no preguntó. Chrome no lo muestra al usuario. Si el usuario lo elimina, Chrome vuelve a descargarlo".

También hay voces que rebajan la gravedad del caso. En Reddit, un usuario defendía que el modelo solo se descarga cuando alguien intenta usar una función de IA que lo necesita y que, además, puede desactivarse desde las opciones de Chrome. Hanff respondía que sus registros mostraban otra cosa: el navegador se abrió de forma programada, permaneció unos minutos en una página sin interacción y aun así dejó rastro de la descarga. Más allá de esa discusión concreta, la propia documentación de Google apunta a un punto intermedio: la descarga puede activarse por funciones integradas y continuar en segundo plano incluso si la pestaña que la inició se cierra.

Chrome sí ofrece controles para reducir la presencia de algunas funciones de IA, pero no lo concentra todo en un panel único y fácil de entender. Desde los ajustes se pueden desactivar u ocultar determinadas piezas visibles, como Gemini en los mercados en los que está disponible, la asistencia de escritura, el historial de búsqueda o la búsqueda impulsada por IA. Para ir más al fondo, sin embargo, hay que entrar en un terreno más técnico, como las opciones experimentales de chrome://flags. Ese salto cambia bastante la experiencia: ya no hablamos de apagar una función clara, sino de tocar partes internas que también pueden estar vinculadas a prestaciones que el usuario quizá sí quiera conservar.


### Instalación y re-instalación

El ciclo de eliminación y re-descarga se ha documentado en múltiples informes independientes sobre instalaciones de Windows: el usuario elimina, Chrome vuelve a descargar, el usuario elimina de nuevo, Chrome vuelve a descargar.

Las únicas formas de que la eliminación sea permanente son deshabilitar las funciones de IA de Chrome a través de chrome://flags o herramientas de políticas empresariales que los usuarios domésticos generalmente no tienen, o desinstalar Chrome por completo.

En macOS el archivo llega como modo 600 propiedad del usuario (por lo que es eliminable en principio) pero Chrome mantiene el estado de instalación en Local State después de que se escriben los bytes, y tan pronto como el servidor de variaciones le dice a Chrome que el perfil es elegible, la descarga se inicia de nuevo: la arquitectura es la misma, solo difieren los permisos del archivo.

### El modelo de privacidad de Firefox

Firefox ofrece un contrapunto interesante porque Mozilla ha agrupado sus controles de IA en un apartado propio dentro de los ajustes. Desde Firefox 148, esa sección ya aparece disponible como "Controles de IA" y permite bloquear mejoras actuales y futuras desde un lugar visible, sin tener que perseguir opciones repartidas por el navegador. También separa apartados concretos, como la IA en el dispositivo, las traducciones y los proveedores de chatbots en la barra lateral. Es una aproximación más directa: el usuario no solo ve que existen esas funciones, también entiende mejor qué puede activar, bloquear o dejar disponible.



