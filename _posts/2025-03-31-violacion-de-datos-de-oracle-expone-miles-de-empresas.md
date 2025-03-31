---
title: Supuesta violación de datos de Oracle expone miles de empresas (confirmado)
date: 2025-03-31 09:00:00 
categories: [CIBERATAQUES]
tags: [ciberataques, vulnerabilidad, news]
description: Si se les da la opción, la mayoría de los usuarios probablemente preferirán una experiencia fluida a medidas de seguridad complejas...
image: /assets/122/preview1.png
---

El pasado jueves 20 de marzo, un atacante conocido como rose87168 publicó varios archivos de texto que contenían una base de datos de muestra, información LDAP y una lista de las empresas que, según afirmaba, fueron robadas de la plataforma SSO de Oracle Cloud. 

Oracle niega haber sufrido la vulneración de datos después de que un atacante afirmara vender 6 millones de registros de datos presuntamente robados de los servidores de inicio de sesión único (SSO) federados de Oracle Cloud y que afectarían a más de 140.621 organizaciones. Entre los registros se encuentran cientos de dominios de América Latina.

*"No se ha producido ninguna vulneración de datos en Oracle Cloud. Las credenciales publicadas no corresponden a Oracle Cloud. Ningún cliente de Oracle Cloud sufrió una vulneración ni perdió datos",* declaró la compañía.

Como prueba adicional de que tenía acceso a los servidores de Oracle Cloud, el atacante compartió una URL de Internet Archive que indica que subió un archivo .TXT con su dirección de correo electrónico de ProtonMail al servidor login.us2.oraclecloud.com.

### Presunta filtración de datos de Oracle

rose87168 ahora vende los datos presuntamente robados del servicio SSO de Oracle Cloud por un precio no revelado o a cambio de exploits de Zero-Day. Afirma que los datos (incluidas las contraseñas SSO cifradas, los archivos del almacén de claves Java (JKS), los archivos de claves y las claves JPS del administrador empresarial) fueron robados tras hackear los servidores de Oracle login.(region-name).oraclecloud.com.

"Las contraseñas SSO están cifradas y se pueden descifrar con los archivos disponibles. También se pueden descifrar las contraseñas con hash LDAP", afirma rose87168. "Enumeraré los dominios de todas las empresas incluidas en esta filtración. Las empresas pueden pagar una cantidad específica para eliminar la información de sus empleados de la lista antes de que se venda".

También han ofrecido compartir algunos de los datos con cualquiera que pueda ayudar a descifrar las contraseñas SSO o descifrar las contraseñas LDAP.

![Imagen 01](/assets/122/122-01.png)

El actor de amenazas declaró que obtuvo acceso a los servidores de Oracle Cloud hace unos 40 días y afirmó haber enviado un correo electrónico a la empresa tras exfiltrar datos de las regiones de nube US2 y EM2. rose87168 afirmó haber solicitado a Oracle el pago de 100.000 XMR por información sobre cómo vulneraron los servidores, pero la empresa supuestamente se negó a pagar tras solicitar "toda la información necesaria para la corrección y el parche".

![Imagen 01](/assets/122/122-02.png)

### Actualización: 25 de marzo de 2025

El actor de amenazas ha compartido una muestra de 10.000 líneas para fundamentar aún más sus afirmaciones. El análisis de este conjunto de datos ha revelado varias conclusiones cruciales:

- Amplio impacto en todas las organizaciones: la muestra contiene datos de más de 1.500 organizaciones únicas, lo que indica una filtración significativa.
- Autenticidad de los datos: el volumen y la estructura de la información filtrada dificultan enormemente su falsificación, lo que refuerza la credibilidad de la filtración.
- Indicadores de acceso a producción: muchas organizaciones afectadas tienen ID de tenant con el formato {tenant}-dev, {tenant}-test y {tenant}, lo que sugiere firmemente que el actor de amenazas también tiene acceso a entornos de producción.
- Exposición de correos electrónicos personales: el conjunto de datos incluye una cantidad considerable de direcciones de correo electrónico personales, probablemente debido a que las organizaciones permiten la autenticación basada en SSO para sus usuarios y clientes.
- Investigadores independientes que también recibieron este archivo pudieron verificar la validez de la filtración y confirmar que se trata de una violación legítima.

Dado que los supuestos datos podrían dar lugar a ataques generalizados a la cadena de suministro, CloudSek publicó una herramienta gratuita para comprobar si su organización figura en la lista de víctimas compartida por el atacante.

### CVE-2021-35587

El actor de amenazas afirmó que todos los servidores de Oracle Cloud utilizan una versión vulnerable con un CVE-2021-35587 público que ya ha sido explotado anteriormente y que en 2022 ya tenía un exploit público conocido. Aquí se puede ver un análisis técnico de lo que se conoce hasta ahora de la brecha.

El CVE-2021-35587 (CVSS 9.8) se publicó en enero de 2022. Se trata de una vulnerabilidad en el producto Oracle Access Manager de Oracle Fusion Middleware que permite a un atacante no autenticado (Pre-auth) con acceso a la red a través de HTTP comprometer Oracle Access Manager y tomar el control total del sistema para llevar a cabo la ejecución remota de código (RCE).

Es decir que, esta vulnerabilidad, fácilmente explotable, permite que un atacante no autenticado con acceso a la red vía HTTP comprometa Oracle Access Manager. Una explotación exitosa puede llevar al control total de Oracle Access Manager.

Dado que Oracle Access Manager, definido en la guía de instalación, es una aplicación de seguridad de nivel empresarial que proporciona una gama completa de funciones de seguridad de perímetro web, esto puede tener graves consecuencias para las víctimas de este tipo de ataques.

**Las versiones afectadas son: 11.1.2.3.0, 12.2.1.3.0 y 12.2.1.4.0**

La primera prueba de concepto fue publicada en marzo de 2022 por los investigadores de seguridad Janggggg y Peterjson. Desde entonces, también han aparecido otras PoC, ofreciendo a los atacantes una gran variedad de opciones.

### Filtración confirmada

La negación por parte de Oracle contradice las conclusiones de BleepingComputer, que recibió muestras adicionales de los datos filtrados del atacante y contactó a las empresas asociadas. Lo mismo han hecho diversos investigadores y todos llegan a al misma conclusión: la filtración es real.

Representantes de estas empresas, quienes aceptaron confirmar los datos bajo la promesa de anonimato, confirmaron la autenticidad de la información. Las empresas declararon que los nombres para mostrar, las direcciones de correo electrónico, los nombres de pila y demás información de identificación de LDAP asociados eran correctos y les pertenecían.

El atacante también compartió correos electrónicos con BleepingComputer, afirmando formar parte de un intercambio entre ellos y Oracle. Un correo electrónico muestra al atacante contactando con el correo electrónico de seguridad de Oracle (secalert_us@oracle.com) para informar que habían pirateado los servidores.

Otro hilo de correo electrónico compartido con BleepingComputer muestra un intercambio entre el atacante y alguien que usa una dirección de ProtonMail y afirma ser de Oracle. En este intercambio de correos electrónicos, el atacante afirma que alguien de Oracle, usando la dirección @proton.me, le dijo: "Hemos recibido sus correos. Usemos este correo para todas las comunicaciones a partir de ahora. Avísenme cuando lo reciban".

La empresa de ciberseguridad Cloudsek también encontró una URL de Archive.org que muestra que el servidor "login.us2.oraclecloud.com" ejecutaba Oracle Fusion Middleware 11g el 17 de febrero de 2025. Oracle desconectó este servidor tras informarse de la presunta brecha.

Esta versión del software se veía afectada por la vulnerabilidad mencionada (CVE-2021-35587) que permitía a atacantes no autenticados comprometer Oracle Access Manager. El actor de amenazas afirmó que esta vulnerabilidad se aprovechó para vulnerar los servidores.





