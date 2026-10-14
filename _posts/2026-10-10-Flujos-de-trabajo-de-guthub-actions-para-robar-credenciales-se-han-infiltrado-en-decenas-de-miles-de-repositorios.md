---
title: "Flujos de trabajo maliciosos de GitHub Actions roban credenciales en miles de repositorios"
date: 2026-10-10 09:00:00
categories: [CIBERSEGURIDAD]
tags: [GitHub ,ciberseguridad, ciberataques]
description: "Investigadores alertan sobre una campaña que introduce flujos de trabajo maliciosos de GitHub Actions en miles de repositorios para robar credenciales y secretos de entornos de desarrollo."
image: /assets/301/preview1.png
---


Investigadores de ciberseguridad han revelado detalles de una campaña en curso de robo de credenciales que ha comprometido dos cuentas de mantenedores de código abierto de alto perfil para introducir un flujo de trabajo malicioso en más de 340 repositorios.

Según StepSecurity, "utilizando la cuenta de Takashi Kitao, autor del motor de juegos pyxel, que cuenta con 18.400 estrellas, el atacante envió un flujo de trabajo malicioso a 27 repositorios a partir de las 13:20 UTC. Ocho horas después, se utilizó la cuenta de Henry Wu (henrywoo), el autor original de athenadriver de Uber, para enviar el mismo flujo de trabajo a 318 repositorios en un lapso de 16 minutos, entre las 21:10 y las 21:26 UTC".

Según Socket, a fecha de 9 de octubre de 2026, ha identificado más de 500 cuentas de GitHub que han implementado el flujo de trabajo malicioso en decenas de miles de repositorios desde el 7 de octubre de 2026.

La actividad se ha atribuido a GhostAction , una campaña de ataque masivo a la cadena de suministro que salió a la luz por primera vez en septiembre de 2025. La actividad afectó a 817 repositorios de 327 usuarios de GitHub, lo que resultó en la exfiltración de 3325 secretos, incluidos tokens de PyPI, npm y DockerHub, a través de cuentas de desarrolladores comprometidas.

Al igual que antes, se ha descubierto que ambas cuentas impulsan un flujo de trabajo llamado Security Audit ("security-audit.yml") o GitHub Actions Security ("github_actions_security.yml"), diseñados para extraer datos confidenciales a una dirección IP codificada ("193.32.204[.]199") a través de HTTP simple.

Los datos capturados contienen los secretos de GitHub Actions del repositorio, incluidos los secretos de CI/CD, y las credenciales de la nube, IA y SaaS presentes en el árbol de trabajo y todo el historial de git, como las claves de AWS, las claves de API de Anthropic, OpenAI y OpenRouter, y los tokens de GitHub y GitLab.

La cadena de ataque completa se desarrolla de la siguiente manera:

- El atacante obtiene las credenciales de GitHub de un mantenedor, muy probablemente un token de acceso personal (PAT) filtrado a partir de registros de robo de información o volcados de credenciales.
- Los archivos de flujo de trabajo del repositorio se analizan en busca de información confidencial como parte de una fase de reconocimiento.
- Se inyecta un flujo de trabajo que simula ser una auditoría de seguridad en la rama principal, utilizando la identidad de la víctima.
- La carga útil incrustada extrae los datos y los envía a un punto final controlado por el atacante a través de curl.

<img src="/assets/301/301-1.png" alt="Imagen 01" style="width: 80%;">

"Se activa en workflow_dispatch y en un push sin filtrar (cualquier rama, cualquier etiqueta), se extrae con fetch-depth: 0 y ejecuta un único paso de 'Auditoría' que hace cuatro cosas", añadió StepSecurity. Esto incluye:

- Agregar los secretos con nombre del repositorio encontrados durante el reconocimiento.
- Analice el árbol de trabajo en busca de 13 patrones de credenciales asociados con claves de AWS, servicios de IA, servicios de control de versiones y claves de API de SaaS y la nube.
- Revisa todo el historial de Git para encontrar los mismos 13 patrones y así obtener credenciales que podrían haber sido confirmadas inadvertidamente en el repositorio y posteriormente eliminadas.
- Empareja los ID de claves de acceso de AWS con sus claves de acceso secretas correspondientes.

A principios de esta semana, GitGuardian informó que la campaña GhostAction impulsó el flujo de trabajo malicioso a 772 repositorios públicos pertenecientes a 373 usuarios y organizaciones de GitHub entre el 31 de agosto y el 30 de septiembre de 2026.

Los flujos de trabajo inyectados tienen como objetivo 2577 secretos, incluidas claves privadas SSH, credenciales de Azure, credenciales de registro de contenedores de DockerHub y GHCR, credenciales de bases de datos, claves de acceso de AWS, credenciales FTP, credenciales de Google Cloud y Firebase, tokens de GitHub, tokens de bots de Telegram, Slack y Discord, y claves asociadas con Cloudflare, npm, PyPI y proveedores de IA.

En al menos un caso detectado el 30 de agosto de 2026, los ciberdelincuentes modificaron el repositorio "kuafuai/DevOpsGPT" para insertar un minero de criptomonedas XMRig en la imagen Docker del proyecto. Hasta la fecha, no se han publicado paquetes maliciosos utilizando credenciales de publicación comprometidas.

Se recomienda a los desarrolladores que revisen sus repositorios en busca de cualquiera de los dos flujos de trabajo de GitHub desde el 31 de agosto de 2026 y que asuman que existe una vulnerabilidad, en caso de detectarla. Se recomienda revocar las credenciales de GitHub comprometidas, rotar las credenciales, eliminar el flujo de trabajo malicioso de todas las ramas y revisar las bifurcaciones de los repositorios infectados.

«Las 279 bifurcaciones del espacio de nombres henrywoo contienen el archivo de flujo de trabajo. Si las acciones están habilitadas, las actualizaciones posteriores pueden provocar la obtención de credenciales», declaró Socket. «Las bifurcaciones posteriores también corren riesgo si heredan el flujo de trabajo malicioso, ya sea al crearse o al sincronizarse con el repositorio principal afectado».

Las bifurcaciones privadas y las réplicas descendentes son las más vulnerables, ya que es en los repositorios privados donde se encuentran las credenciales comprometidas. En ambas cuentas, cada ejecución también devuelve un identificador de repositorio, independientemente de si se encontraron credenciales o no, por lo que el operador mantiene un mapa de los contextos de ejecución accesibles, independientemente de cualquier robo de credenciales.




