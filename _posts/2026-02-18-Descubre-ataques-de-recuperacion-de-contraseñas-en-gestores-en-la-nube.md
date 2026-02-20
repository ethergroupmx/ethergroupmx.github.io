---
title: "Descubren 25 ataques de recuperación de contraseñas en gestores en la nube"
date: 2026-02-18 09:00:00 
categories: [CLOUD]
tags: [cloud, ciberseguridad, vulnerabilidad, servidores, hacking]
description: Varios gestores de contraseñas en la nube, como Bitwarden, Dashlane, LastPass y 1Password, son susceptibles a ataques de recuperación de contraseñas en determinadas circunstancias.
image: /assets/218/preview1.png
---

Todos las empresas respondieron de forma efectiva y no hay evidencia de que ninguno de estos problemas haya sido explotado en la práctica.

**¡No dejes de usar gestores de contraseñas! Usar un gestor de contraseñas es probablemente la medida más eficaz para reforzar tu seguridad.** Todos los ataques parten de la base de que existe un servidor malicioso. No hay motivos para creer que los proveedores de gestores de contraseñas sean maliciosos o estén comprometidos, y mientras esto siga así, tus contraseñas estarán seguras. Dicho esto, los gestores de contraseñas son objetivos muy valiosos y las filtraciones ocurren.

Al analizar los tres principales gestores de contraseñas que afirman tener cifrado de conocimiento cero (Bitwarden, LastPass y Dashlane), que en conjunto poseen aproximadamente el 23% del mercado. Además en un análisis adicional de 1Password, encontraron 27 ataques distintos que un servidor malicioso puede lanzar contra sus usuarios. La gravedad de los ataques varía desde violaciones de integridad hasta la vulneración total de todas las bóvedas de una organización.

Cabe destacar que el actor de amenazas, según el estudio de la ETH de Zúrich y la Università della Svizzera italiana, asume un servidor malicioso y pretende examinar las promesas de cifrado de conocimiento cero (ZKE) del gestor de contraseñas realizadas por las tres soluciones. ZKE es una técnica criptográfica que permite a una parte demostrar el conocimiento de un secreto a otra sin revelarlo.

*"La gravedad de los ataques varía desde violaciones de integridad hasta la vulneración total de todas las bóvedas de una organización", afirmaron los investigadores Matteo Scarlata, Giovanni Torrisi, Matilda Backendal y Kenneth G. Paterson. "La mayoría de los ataques permiten la recuperación de contraseñas".*

El cifrado de conocimiento cero es un término ampliamente utilizado por los proveedores de gestores de contraseñas en la nube. Aunque no tiene un significado técnico estricto, el término transmite la idea de que el servidor, que almacena las bóvedas de contraseñas cifradas en nombre de los usuarios, no puede obtener información sobre el contenido de dichas bóvedas.

Las afirmaciones de seguridad de los proveedores implican que esto debería ser así incluso si el servidor es completamente malicioso. Este modelo de amenaza se justifica en la práctica por la alta sensibilidad de los datos de las bóvedas, lo que convierte a los servidores de gestores de contraseñas en un objetivo atractivo para las vulneraciones (como lo demuestra su historial de ataques).

ZKE también es ligeramente diferente del cifrado de extremo a extremo (E2EE). Mientras que E2EE se refiere a un método para proteger datos en tránsito, ZKE se centra principalmente en almacenar datos en un formato cifrado, de modo que solo la persona con la clave pueda acceder a dicha información. Los proveedores de gestores de contraseñas implementan ZKE para mejorar la privacidad y la seguridad del usuario, garantizando que los datos de la bóveda no puedan ser manipulados.

Sin embargo, la investigación ha descubierto 12 ataques distintos contra Bitwarden, siete contra LastPass y seis contra Dashlane, que van desde violaciones de la integridad de bóvedas de usuarios específicos hasta la vulneración total de todas las bóvedas asociadas a una organización. En conjunto, estas soluciones de gestión de contraseñas prestan servicio a más de 60 millones de usuarios y casi 125.000 empresas.

Los investigadores analizaron las aplicaciones bajo un modelo de amenaza de servidor malicioso, en el que el servidor puede desviarse arbitrariamente del comportamiento esperado. Este modelo se justifica con tres argumentos: las propias afirmaciones de seguridad de los proveedores implican protección en este contexto; la alta sensibilidad de los datos de la bóveda convierte a estos servidores en objetivos atractivos (como lo demuestra su historial de filtraciones); y en áreas estrechamente relacionadas, como el almacenamiento y la mensajería en la nube con cifrado E2E, la seguridad contra servidores maliciosos ya es la norma.

*"A pesar de los intentos de los proveedores por lograr la seguridad en este entorno, descubrimos varios antipatrones de diseño comunes y conceptos criptográficos erróneos que resultaron en vulnerabilidades"*, afirmaron los investigadores en un artículo adjunto.

Los ataques se dividen en cuatro categorías generales:

- Ataques que explotan el mecanismo de recuperación de cuentas "Key Escrow" para comprometer las garantías de confidencialidad de Bitwarden y LastPass, debido a vulnerabilidades en sus diseños de custodia de claves.
- Ataques que explotan un cifrado defectuoso a nivel de elemento (es decir, cifran datos y configuraciones confidenciales del usuario como objetos separados y, a menudo, se combinan con metadatos no cifrados o no autenticados), lo que provoca violaciones de integridad, fugas de metadatos, intercambio de campos y degradación de la función de derivación de claves (KDF).
- Ataques que explotan las funciones de compartición para comprometer la integridad y la confidencialidad de la bóveda.
- Ataques que explotan la retrocompatibilidad con código heredado, lo que resulta en ataques de degradación en Bitwarden y Dashlane. El estudio también reveló que 1Password, otro popular gestor de contraseñas, es vulnerable tanto al cifrado de bóveda a nivel de elemento como a ataques de compartición. Sin embargo, 1Password ha optado por tratarlos como si se debieran a limitaciones arquitectónicas ya conocidas.

![Imagen 01](/assets/218/218-01.png)

Al ser contactado para obtener comentarios, Jacob DePriest, Director de Seguridad de la Información y Director de Información de 1Password, declaró que el equipo de seguridad de la compañía revisó el documento en detalle y no encontró nuevos vectores de ataque más allá de los ya documentados en su Libro Blanco de Diseño de Seguridad, disponible públicamente.

Por lo demás, **Bitwarden, Dashlane y LastPass han implementado contramedidas para mitigar los riesgos señalados en la investigación.** LastPass también planea reforzar sus flujos de trabajo de restablecimiento de contraseñas de administrador y compartición para contrarrestar la amenaza que representa un intermediario malicioso. 

En concreto, Dashlane ha corregido un problema que, tras comprometer sus servidores, podría haber permitido una degradación del modelo de cifrado utilizado para generar claves de cifrado y proteger las bóvedas de los usuarios. El problema se solucionó eliminando la compatibilidad con los métodos de criptografía heredados de la extensión de Dashlane.

Bitwarden afirmó que se están abordando todos los problemas identificados. Siete de estos problemas han sido resueltos o están en proceso de remediación. Los tres restantes se han aceptado como decisiones de diseño intencionales necesarias para la funcionalidad del producto.

En un aviso similar, LastPass afirmó estar trabajando activamente para añadir garantías de integridad más sólidas para vincular criptográficamente mejor elementos, campos y metadatos, contribuyendo así a mantener la seguridad de la integridad.






