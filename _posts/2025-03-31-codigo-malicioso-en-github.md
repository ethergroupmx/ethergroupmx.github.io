---
title: Código malicioso en GitHub - cómo hacen los piratas informáticos para atacar a los programadores
date: 2025-03-31 09:00:00 
categories: [CIBERATAQUES]
tags: [hacking, malware, ciberataques, GitHub]
description: Más de 200 repositorios con proyectos falsos en GitHub. A través de ellos, los atacantes distribuyen ladrones, clippers y puertas traseras.
image: /assets/120/preview1.png
---

¿Te imaginas un mundo en el que, cada vez que quisieras ir a algún lugar, tuvieras que reinventar la rueda y construir una bicicleta desde cero? Nosotros tampoco podemos imaginarlo. ¿Por qué reinventar algo que ya existe y funciona perfectamente bien? La misma lógica se aplica a la programación: los desarrolladores enfrentan tareas rutinarias todos los días y, en lugar de inventar sus propias ruedas y bicicletas (que incluso podrían no estar a la altura), simplemente toman el código de bicicletas ya preparadas de los repositorios de código abierto de GitHub.

Esta solución está disponible para todos, incluidos los delincuentes que utilizan el mejor código abierto gratuito del mundo como cebo para sus ataques. Hay mucha evidencia que respalda esto, y esta es la última: nuestros expertos han descubierto una campaña maliciosa activa, GitVenom, dirigida a los usuarios de GitHub.

### Campaña maliciosa

Los actores desconocidos crearon más de 200 repositorios que contenían proyectos falsos con código malicioso: bots de Telegram, herramientas para piratear el juego Valorant, servicios de automatización de Instagram y administradores de carteras Bitcoin. A primera vista, todos los repositorios parecen legítimos. El archivo README.MD está particularmente bien diseñado: una guía sobre cómo trabajar con el código, con instrucciones detalladas en varios idiomas. Además de eso, los atacantes añadieron múltiples etiquetas a sus repositorios.

![Imagen 01](/assets/120/120-01.png)

*Los atacantes utilizaron IA para escribir instrucciones detalladas en varios idiomas*

Otro indicador que refuerza la aparente legitimidad de estos repositorios es la gran cantidad de commits. Los repositorios de los atacantes tienen decenas de miles. Por supuesto, los atacantes no actualizaban manualmente cada uno de los 200 repositorios para mantener la autenticidad, sino que simplemente utilizaban archivos con marcas de tiempo que se actualizaban cada pocos minutos. La combinación de documentación detallada y numerosos commits crea la ilusión de que el código es genuino y se puede utilizar con seguridad.

### Dos años de actividad

La campaña comenzó hace mucho tiempo: el repositorio falso más antiguo que encontramos tiene aproximadamente dos años. Mientras tanto, GitVenom ha afectado a desarrolladores en Rusia, Brasil, Turquía y otros países. Los atacantes cubrieron una amplia gama de lenguajes de programación: se encontró código malicioso en repositorios de Python, JavaScript, C, C# y C++.

Respecto a la funcionalidad de estos proyectos, las características descritas en el archivo README ni siquiera coinciden con el código real; en realidad, el código no hace ni la mitad de lo que afirma. Pero “gracias” a ello, las víctimas terminan descargando componentes maliciosos. Entre ellos:

- Un **ladrónjs** que recolecta nombres de usuario y contraseñas, datos de carteras de criptomonedas e historiales del navegador, empaqueta los datos robados en un archivo comprimido .7z y los envía a los atacantes a través de Telegram.
- **AsyncRAT:** un troyano de administración remota de código abierto que también puede funcionar como registrador de pulsaciones de teclas.
- **Quasar:** una puerta trasera de código abierto.
- Un **clipper** que busca en el portapapeles direcciones de carteras de criptomonedas y las reemplaza con direcciones controladas por el atacante. Cabe destacar que, en noviembre de 2024, la cartera del pirata informático utilizada en este ataque recibió un depósito único de aproximadamente 5 BTC (aproximadamente 377 000 Euro en el momento del estudio).

### Cómo protegerte del código malicioso en GitHub

En resumen, la mejor defensa es la vigilancia. Dado que más de 100 millones de desarrolladores usan GitHub, es probable que los atacantes continúen difundiendo código malicioso a través de esta popular plataforma. La única pregunta es cómo lo harán: hace una década, nadie imaginaba que los atacantes pudieran llevar a cabo campañas como GitVenom durante tanto tiempo y con tanta persistencia. Por lo tanto, cada desarrollador debe mantener buenas prácticas de ciberseguridad cuando trabaja con GitHub.

- Analiza el código antes de integrarlo en un proyecto existente.
- Usa protección contra malware tanto en ordenadores como en teléfonos inteligentes.
- Revisa cuidadosamente los indicadores menos obvios: las cuentas de los colaboradores, la cantidad de estrellas (me gusta) y la fecha de creación del proyecto. Si la cuenta se creó hace tres días, el repositorio hace dos días y solo tiene una estrella, hay grandes posibilidades de que el proyecto sea falso y el código sea malicioso.
- No descargues archivos de enlaces directos a GitHub compartidos en chats, canales sospechosos o sitios web no verificados.
- Si encuentras un repositorio sospechoso, repórtalo a GitHub; esto podría salvar los dispositivos de otros que no estén protegidos con una solución de seguridad fiable.


