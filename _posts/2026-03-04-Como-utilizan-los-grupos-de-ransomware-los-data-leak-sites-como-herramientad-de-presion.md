---
title: "¿Cómo utilizan los grupos de ransomware los data leak sites como herramienta de presión?"
date: 2026-03-04 09:00:00 
categories: [CIBERSEGURIDAD]
tags: [ciberataques, ciberseguridad, malware, hacking]
description: Los ataques de ransomware han evolucionado significativamente en los últimos años. Si antes el foco estaba casi exclusivamente en el cifrado de archivos para interrumpir operaciones, hoy los grupos criminales combinan técnicas y presión psicológica para maximizar la coacción sobre las víctimas.
image: /assets/222/preview1.png
---

En este nuevo modelo, los llamados data leak sites (filtración de datos) se han convertido en el eje central de la estrategia de extorsión.

En este artículo, explicaremos qué son, cómo los utilizan los grupos de ransomware, cuáles son las consecuencias para las empresas víctimas y compartiremos algunos ejemplos.

### ¿Cuáles son los data leak sites que utilizan los grupos de ransomware?

Estos sitios son portales gestionados por grupos de ransomware para publicar datos robados y amenazar a las víctimas con filtraciones públicas. Normalmente alojados en la dark web y accesibles a través de la red Tor, estos entornos forman parte del núcleo de la estrategia de extorsión, mostrando información sobre ataques en curso o ya completados.

Estos sitios funcionan como vitrinas públicas de la actividad criminal, donde los propios grupos anuncian a sus víctimas, alojan muestras de datos robados y fijan plazos para los pagos del rescate antes de que la información se divulgue completamente.

En estos sitios los delincuentes suelen revelar:

- El nombre de la empresa o institución atacada.
- Muestras de datos filtradas como prueba de acceso indebido.
- La cantidad aproximada de datos robados.
- Plazos de pago antes de la publicación pública de la información.

Al convertir el ataque en un evento público, los grupos aumentan los riesgos reputacionales, legales y comerciales para la víctima.

![Imagen 01](/assets/222/222-01.png)
*Imagen: Data leak site del grupo Akira*

### Crecimiento de los data leak sites y número de víctimas expuestas

Según datos de Ransomware.Live consolidados en diversos análisis sectoriales, durante el tercer trimestre de 2025 se registraron más de 1.590 víctimas listadas en leak sites de ransomware, lo que confirma que esta táctica dejó de ser un fenómeno aislado y se consolidó como una amenaza global en expansión.

![Imagen 02](/assets/222/222-02.png)
*Imagen: Crecimiento sostenido, a lo largo de los años, en el número de víctimas de ransomware expuestas en data leak sites. Fuente: Ransomware.live.*

### Los data leak sites como arma de presión

Los data leak sites son elementos estructurales de la estrategia de extorsión, como un mecanismo de presión cuidadosamente diseñado para forzar a la víctima a negociar.

Al hacer público el ataque, lo que comienza como un problema técnico se convierte rápidamente en una crisis reputacional, legal y comercial. La organización empieza a enfrentarse a la posibilidad concreta de exposición de información sensible, pérdida de confianza en el mercado y consecuencias legales, que se suman a los problemas de acceso a sus sistemas.

Además, la explotación de la información robada puede hacer que las consecuencias de una filtración vayan más allá. Por un lado, puede provocar que las empresas sufran ataques aún más dirigidos con campañas personalizadas de ingeniería social. Por otro lado, exponer a terceros, como clientes de las empresas afectadas, a nuevos ataques.

![Imagen 01](/assets/222/222-03.png)
*Imagen Data leak site de LockBit 5.0*

![Imagen 01](/assets/222/222-04.png)
*Imagen: Data leak site del ransomware Medusa.*

En la práctica, estos sitios se utilizan para generar cuatro tipos principales de presión:

- **Prueba de compromiso: La divulgación de documentos de muestra demuestra que los atacantes realmente tenían acceso a los datos y no están faroleando.**

![Imagen 01](/assets/222/222-05.png)
*Imagen: Ejemplo de data leak site (World Leaks)*

- **Urgencia artificial: Los plazos y las cuentas atrás crean la sensación de que el tiempo se agota, empujando a la víctima a tomar decisiones rápidas.**

![Imagen 01](/assets/222/222-06.png)
*Imagen: Ejemplo de cómo se presenta la urgencia en un leaked data site de LockBit.*

- **Exposición pública: La mera asociación del nombre de la organización con una filtración ya causa daño reputacional y atrae atención no deseada de los medios y reguladores.**

- **Presión legal y regulatoria: La amenaza de divulgación activa riesgos de multas, investigaciones y demandas, aumentando considerablemente el coste del impago.**

Este conjunto de factores convierte a los data leak sites en mucho más que un canal de publicación. Se convierten en un instrumento de coacción, utilizado para inclinar el equilibrio de la negociación a favor de los atacantes y aumentar significativamente la probabilidad de un pago de rescate.

### Otras formas en que los grupos de ransomware los utilizan

Además de extorsionar a las víctimas revelando sus nombres, presionando para que paguen un rescate y amenazando con publicar los datos robados o hacerlos públicos, algunos grupos han ido más allá y han empezado a explorar otros usos para estos sitios.

Un ejemplo son los programas de Bug Bounty, como los promovidos por LockBit, que ofrecen recompensas a quienes encuentran fallos y otros tipos de vulnerabilidades.

![Imagen 01](/assets/222/222-07.png)
*Imagen; Programa de Bug Bounty promovido por LockBit.*

Algunos grupos también buscan conectar con empleados que forman parte de las empresas para obtener acceso. Esto refuerza la importancia de que las organizaciones mantengan un control de acceso bien definido y adopten las medidas necesarias para prevenir ataques que puedan comenzar dentro de la propia empresa.

Muchos grupos también utilizan estos sitios para explicar cómo funciona el modelo de negocio y reclutar afiliados que se convierten en parte del modelo de ransomware as a service (RaaS).

En este modelo, los operadores reclutan afiliados y ofrecen acceso a la infraestructura del malware a cambio de un porcentaje de los beneficios. En estos casos, son los afiliados quienes distribuyen el malware, lo que hace que diferentes afiliados puedan actuar dentro del mismo grupo.

Como parte del proceso de extorsión, también se utilizan data leak sites para informar a las víctimas sobre cómo realizar el pago y qué condiciones imponen los ciberdelincuentes.

### ¿Por qué funciona esta estrategia

La eficacia de los leak sites radica no solo en la amenaza técnica, sino en el hecho de que explotan vulnerabilidades que van más allá de la tecnología. Al exponer públicamente a una organización y amenazar con divulgar sus datos, los grupos de ransomware trasladan el problema del ámbito de TI al centro de la gestión corporativa.

La amenaza de fuga activa simultáneamente diferentes tipos de riesgo: daños reputacionales, pérdida de confianza de clientes y socios, impactos financieros, sanciones regulatorias y demandas. Esto crea un ambiente de alta presión en el que la víctima debe tomar decisiones rápidamente, a menudo sin tiempo suficiente para evaluar todas las consecuencias.

Además, los ataques de ransomware también han evolucionado en su ejecución. En muchos casos, los grupos ni siquiera cifran los sistemas, centrándose directamente en la exfiltración de datos con especial atención a la fuga pública. En este escenario, la empresa deja de comunicar el incidente de forma planificada y comienza a reaccionar ante la narrativa impuesta por los propios atacantes, lo que intensifica el estrés interno y la inseguridad del liderazgo.

Este modelo de extorsión ayuda a explicar por qué el ransomware sigue siendo un negocio muy lucrativo. Según la revista Cybercrime, basada en un análisis de Cybersecurity Ventures, se espera que los costos globales causados por ataques de ransomware superen los 265.000 millones de dólares anuales para 2031, teniendo en cuenta los pagos de rescate, los tiempos de inactividad, la pérdida de datos y los costes de recuperación.

En este contexto, pagar el rescate puede parecer una solución para contener un mayor daño reputacional y legal, pero la recomendación es nunca pagar el rescate. Por un lado, pagar no garantiza que las víctimas recuperen los archivos ni que se evite filtrar o comercializar los datos tras el pago. Muchas empresas que ya habían sido víctimas y pagadas acabaron siendo atacadas de nuevo. Por otro lado, también se recomienda no pagar porque contribuye al crecimiento de este modelo y al fortalecimiento de estos grupos criminales.

### Las consecuencias de que tus datos se publiquen en un data leak site

Además del ataque de ransomware y la demanda de rescate, muchos grupos ofrecen en estos sitios la posibilidad de descargar la información robada, permitiendo que cualquiera tenga acceso a estos datos. Este material alimenta un mercado para la compra y venta de información, lo que puede dar lugar a nuevos ataques, como campañas personalizadas de phishing, fraude de identidad o ataques dirigidos a empresas que forman parte de la cadena de suministro.


