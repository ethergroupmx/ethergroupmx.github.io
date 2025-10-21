---
title: "Análisis de ClickFix: 3 razones por las que los ataques de copiar y pegar provocan brechas de seguridad"
date: 2025-10-20 09:00:00 
categories: [HACKING]
tags: [hacking, ciberataques, malware]
description: ClickFix, FileFix, CAPTCHA falso… como sea que lo llames, los ataques en los que los usuarios interactúan con scripts maliciosos en su navegador web son una fuente de violaciones de seguridad en rápido crecimiento.
image: /assets/179/preview1.png
---

Los ataques ClickFix solicitan al usuario que resuelva algún tipo de problema o desafío en el navegador (normalmente un CAPTCHA, pero también cosas como corregir un error en una página web).

Sin embargo, el nombre es un poco engañoso: el factor clave del ataque es que engañan a los usuarios para que ejecuten comandos maliciosos en sus dispositivos copiando el código malicioso del portapapeles de la página y ejecutándolo localmente.

![Imagen 01](/assets/179/2.png)

- *Ejemplos de señuelos ClickFix utilizados por atacantes en la naturaleza.*

Se sabe que ClickFix es utilizado regularmente por el grupo de ransomware Interlock y otros actores de amenazas prolíficos, incluyendo APTs patrocinadas por estados. Varias filtraciones de datos públicos recientes se han vinculado a TTPs similares a ClickFix, como las de Kettering Health, DaVita, la ciudad de St. Paul, Minnesota, y los Centros de Ciencias de la Salud de la Universidad Tecnológica de Texas (y es probable que muchas más filtraciones involucren a ClickFix donde el vector de ataque no se conocía o se divulgó).

Pero ¿por qué estos ataques resultan tan efectivos?

### Razón 1: Los usuarios no están preparados para ClickFix

Durante la última década o más, la concienciación del usuario se ha centrado en evitar que hagan clic en enlaces de correos electrónicos sospechosos, descarguen archivos peligrosos e introduzcan su nombre de usuario y contraseña en sitios web aleatorios. No se ha centrado en abrir un programa y ejecutar un comando.

La sospecha se reduce aún más si tenemos en cuenta que la acción maliciosa de copiar el portapapeles se realiza en segundo plano a través de JavaScript el 99 % de las veces.

![Imagen 01](/assets/179/3.png)

- *Ejemplo de código JavaScript no ofuscado que realiza la función de copia automáticamente en una página de ClickFix sin entrada del usuario*

Y como los sitios y señuelos modernos de ClickFix cada vez parecen más legítimos (ver el ejemplo a continuación), no es sorprendente que los usuarios se conviertan en víctimas.

![Imagen 01](/assets/179/4.png)

- *Uno de los señuelos de ClickFix que parecen más legítimos: ¡este incluso tiene un video incorporado que muestra al usuario qué hacer!*

Si tenemos en cuenta que estos ataques se están alejando por completo del correo electrónico, no se ajusta al modelo de aquello que los usuarios están acostumbrados a sospechar.

El principal vector de distribución identificado por los investigadores de Push Security fue el envenenamiento SEO y el malvertising a través de la Búsqueda de Google. Al crear nuevos dominios o apropiarse de dominios legítimos, los atacantes crean escenarios de "watering hole" para interceptar a los usuarios que navegan por internet.

E incluso si sospechara, no existe un botón conveniente para "informar phishing" ni un flujo de trabajo para notificar a su equipo de seguridad sobre los resultados de búsqueda de Google, los mensajes de redes sociales, los anuncios de sitios web, etc.

### Razón 2: ClickFix no se detecta durante la entrega

Hay algunos aspectos que explican por qué los ataques de ClickFix pasan desapercibidos para los controles técnicos.

Las páginas de ClickFix, al igual que otros sitios de phishing modernos, utilizan diversas técnicas de evasión de detección que impiden que las herramientas de seguridad las detecten, desde escáneres de correo electrónico y herramientas de rastreo web hasta servidores proxy web que analizan el tráfico de red. La evasión de detección consiste principalmente en camuflar y rotar dominios para anticiparse a las detecciones conocidas como maliciosas (es decir, listas de bloqueo), usar protección contra bots para evitar el análisis y ofuscar el contenido de la página para evitar que se activen las firmas de detección.

Y al utilizar vectores de entrega que no son de correo electrónico, se elimina toda una capa de oportunidad de detección.

![Imagen 01](/assets/179/5.png)

- *Al igual que otros ataques de phishing modernos, los señuelos de ClickFix se distribuyen por todo Internet, no solo por correo electrónico.*

El malvertising añade un nivel adicional de segmentación. Por ejemplo, los anuncios de Google pueden segmentarse a búsquedas provenientes de ubicaciones geográficas específicas, adaptarse a dominios de correo electrónico específicos o a tipos de dispositivos específicos (por ejemplo, computadoras de escritorio, móviles, etc.). Si conoce la ubicación de su público objetivo, puede adaptar los parámetros del anuncio en consecuencia.

Junto con otras técnicas, como la carga condicional para devolver un señuelo apropiado para su sistema operativo (o no activarse en absoluto a menos que se cumplan ciertas condiciones, por ejemplo, si está visitando desde un sistema operativo móvil o desde fuera de un rango de IP objetivo), los atacantes tienen una forma de llegar a una gran cantidad de víctimas potenciales mientras evitan los controles de seguridad en la capa de correo electrónico y evitan análisis no deseados.

![Imagen 01](/assets/179/6.png)

- *Ejemplo de un señuelo ClickFix creado en un sitio con código de vibración.*

Finalmente, dado que el código se copia dentro del entorno de pruebas del navegador, las herramientas de seguridad habituales no pueden observar ni marcar esta acción como potencialmente maliciosa. Esto significa que la última —y única— oportunidad que tienen las organizaciones de detener ClickFix es en el endpoint, después de que el usuario haya intentado ejecutar el código malicioso.

### Razón 3: EDR es la última y única línea de defensa, y no es infalible

Hay múltiples etapas del ataque que pueden y deben ser interceptadas por EDR, pero el nivel de detección alcanzado y si una acción se bloquea en tiempo real depende del contexto.

Dado que no se descarga ningún archivo de la web y la ejecución del código en el equipo la inicia el usuario, no existe contexto que vincule la acción con otra aplicación y la haga parecer sospechosa. Por ejemplo, un PowerShell malicioso ejecutado desde Outlook o Chrome parecería obviamente sospechoso, pero al ser iniciado por el usuario, queda aislado del contexto donde se entregó el código.

Los comandos maliciosos podrían estar ofuscados o fragmentados para evitar su fácil detección mediante reglas heurísticas. La telemetría EDR podría registrar la ejecución de un proceso de PowerShell, pero sin una firma incorrecta conocida ni una infracción clara de la política, podría no detectarlo inmediatamente.

La etapa final en la que cualquier EDR confiable debería interceptar el ataque es en el punto de ejecución del malware. Pero evadir la detección es un juego del gato y el ratón, y los atacantes siempre buscan maneras de modificar su malware para evadir o desactivar las herramientas de detección. Por lo tanto, existen excepciones.

Y si su organización permite que sus empleados y contratistas utilicen dispositivos BYOD no administrados, es muy probable que existan lagunas en su cobertura de EDR.

En última instancia, las organizaciones terminan dependiendo de una única línea de defensa: si EDR no detecta ni bloquea el ataque, no se detecta en absoluto.

### Por qué las recomendaciones estándar se quedan cortas

La mayoría de las recomendaciones, independientes del proveedor, se han centrado en restringir el acceso a servicios como el cuadro de diálogo Ejecutar de Windows para usuarios típicos. Sin embargo, aunque mshta y PowerShell siguen siendo los más comunes, los investigadores de seguridad ya han detectado una amplia gama de LOLBINS dirigidos a diferentes servicios, muchos de los cuales son difíciles de impedir el acceso de los usuarios.

También vale la pena considerar cómo podrían evolucionar los ataques tipo ClickFix en el futuro. La ruta de ataque actual abarca el navegador y el endpoint. ¿Qué pasaría si pudiera ejecutarse completamente en el navegador y evadir la EDR por completo? Por ejemplo, pegando JavaScript malicioso directamente en las herramientas de desarrollo de una página web relevante.

![Imagen 01](/assets/179/7.png)

- *El método de ataque híbrido actual consiste en que el atacante envíe señuelos en el navegador para comprometer el endpoint y obtener acceso a las credenciales y cookies almacenadas en él.*

- Credits:Hackernews
