---
title: "Una contraseña predeterminada permitió acceder a cuentas y controlar vehículos de dos fabricantes"
date: 2026-11-09 11:00:00
categories: [HACKING]
tags: [ciberseguridad, hacking, vulnerabilidades]
description: "Investigadores descubrieron que dos fabricantes de automóviles utilizaban servidores de identidad con credenciales predeterminadas. El fallo permitió acceder a cuentas de clientes y desbloquear puertas y encender vehículos de forma remota."
image: /assets/315/preview1.png
---

Una contraseña tan sencilla como `admin:admin` fue suficiente para que investigadores de ciberseguridad consiguieran acceso a los sistemas de autenticación de dos fabricantes de automóviles. El hallazgo permitió demostrar cómo una configuración insegura en servidores empresariales puede comprometer cuentas de clientes y extender el acceso hasta funciones de control remoto de vehículos conectados.

La investigación fue realizada por los especialistas en seguridad Shubham Shah y Sam Curry, quienes identificaron debilidades en la infraestructura utilizada por las aplicaciones móviles de dos marcas automotrices.

De acuerdo con el reporte publicado por The Hacker News el 9 de noviembre de 2026, los investigadores consiguieron acceder a cuentas de clientes y utilizar sus permisos para desbloquear puertas y encender vehículos de prueba.

## ¿Cómo comenzó el ataque?

Ambos fabricantes utilizaban ForgeRock, una plataforma de administración de identidades y autenticación que actualmente forma parte de Ping Identity.

Dentro de esta infraestructura se encontraba OpenIDM, un componente encargado de administrar información de usuarios y registros de identidad.

El problema estaba en una consola administrativa basada en Apache Felix que permanecía habilitada en los servidores de producción y conservaba sus credenciales predeterminadas:

- **Usuario:** admin
- **Contraseña:** admin

Aunque la consola estaba configurada para bloquear el acceso desde internet, los investigadores encontraron una forma de evadir esa restricción mediante diferencias en la interpretación de las direcciones web entre los sistemas de protección perimetral y el servidor de aplicaciones.

Una vez dentro de la consola, pudieron aprovechar funciones administrativas para ejecutar código en el servidor.

## Del acceso al servidor al control de cuentas

Después de conseguir acceso al servidor de identidad, los investigadores pudieron interactuar con los registros de clientes almacenados en OpenIDM.

La secuencia permitió realizar diferentes acciones:

1. **Acceso a la consola administrativa:** utilizaron las credenciales predeterminadas para ingresar a la interfaz de administración.
2. **Ejecución de código:** aprovecharon una función de programación de tareas para ejecutar instrucciones dentro del servidor.
3. **Acceso a registros de clientes:** consiguieron interactuar con la información utilizada para autenticar a los usuarios de las aplicaciones móviles.
4. **Modificación de cuentas:** cambiaron temporalmente las direcciones de correo electrónico y contraseñas de cuentas seleccionadas.
5. **Obtención de sesiones válidas:** iniciaron sesión como los clientes afectados y consiguieron los mismos tokens de acceso utilizados por las aplicaciones oficiales.

Esto significaba que el problema ya no se limitaba a una consola administrativa expuesta: los investigadores habían conseguido comprometer el mecanismo de autenticación de las aplicaciones.

## Cuando una cuenta comprometida permite controlar un vehículo

El impacto más relevante se presentó al utilizar las sesiones obtenidas para interactuar con los servicios de vehículos conectados.

A través de los comandos disponibles en las aplicaciones móviles, los investigadores demostraron que podían:

- Desbloquear las puertas del vehículo.
- Encender el motor de forma remota.
- Ejecutar comandos asociados a las funciones conectadas del automóvil.

Las pruebas se realizaron exclusivamente con cuentas y vehículos propios o de propietarios que habían autorizado la evaluación.

Los investigadores señalaron que podían abrir sesiones correspondientes a cualquier cuenta de cliente almacenada en los servidores afectados, aunque limitaron las pruebas de control vehicular a automóviles autorizados en Estados Unidos.

También identificaron que modificar el correo electrónico y la contraseña de una cuenta no cerraba automáticamente la sesión del propietario. Esto podía permitir que un acceso no autorizado permaneciera activo sin que el usuario recibiera una señal evidente.

## Una segunda debilidad en los sistemas de Australia

La investigación también documentó otro problema relacionado con los sistemas australianos de las mismas marcas.

En este caso, los investigadores encontraron credenciales administrativas del servidor de identidad directamente dentro del código de la aplicación móvil.

Estas credenciales habían sido utilizadas para pruebas, pero permanecieron incorporadas en una versión de la aplicación.

Este hallazgo permitió desarrollar una segunda cadena de ataque que, según los investigadores, podía afectar vehículos conectados en Australia, Estados Unidos y Canadá.

El caso demuestra que las credenciales de prueba también representan un riesgo cuando llegan a entornos de producción o quedan expuestas en aplicaciones distribuidas públicamente.

## ¿Fue una vulnerabilidad de ForgeRock?

Es importante aclarar que el incidente no se originó por una nueva vulnerabilidad del software ForgeRock.

El problema estuvo relacionado con decisiones de configuración y administración de los sistemas:

- Credenciales administrativas predeterminadas que nunca fueron modificadas.
- Consolas de administración innecesariamente habilitadas en producción.
- Restricciones de acceso que podían evadirse por diferencias en la interpretación de las rutas web.
- Credenciales de prueba incorporadas directamente en el código de una aplicación.

Los investigadores notificaron los problemas a los fabricantes y, según el reporte, los sistemas estadounidenses fueron corregidos aproximadamente dos horas después de recibir el aviso.

No se publicó un identificador CVE porque el origen del incidente fue una configuración insegura, no un defecto nuevo del producto.

## ¿Cómo pueden evitarse este tipo de ataques?

Este incidente demuestra que proteger una infraestructura no consiste únicamente en instalar herramientas de seguridad. También es necesario revisar las configuraciones, los permisos y los mecanismos de autenticación.

Estas son algunas medidas recomendadas:

**1. Eliminar las credenciales predeterminadas**

Cambiar todas las contraseñas iniciales durante la instalación de servidores, aplicaciones y dispositivos. Las credenciales de fábrica nunca deben permanecer activas en producción.

**2. Deshabilitar consolas administrativas innecesarias**

Retirar herramientas de desarrollo, depuración y administración que no sean indispensables para la operación. Si deben permanecer habilitadas, restringir su acceso a redes administrativas.

**3. Proteger los servidores de identidad**

Revisar las configuraciones de plataformas como ForgeRock y PingIDM, aplicar las recomendaciones de endurecimiento del fabricante y limitar los permisos de las cuentas administrativas.

**4. Evitar credenciales dentro del código**

No incorporar contraseñas, claves API ni tokens directamente en aplicaciones móviles, repositorios o archivos de configuración. Utilizar mecanismos seguros de administración de secretos.

**5. Revisar las reglas de protección perimetral**

No depender exclusivamente de firewalls de aplicaciones web (WAF) o proxies para proteger interfaces administrativas. Los controles de acceso también deben aplicarse directamente en el servidor y en la aplicación.

**6. Supervisar las actividades administrativas**

Registrar los accesos a consolas, cambios en cuentas, modificaciones de contraseñas y creación de tareas programadas. Las actividades fuera de los patrones habituales deben generar alertas.

**7. Implementar autenticación multifactor y controles de sesión**

Proteger las cuentas administrativas con autenticación multifactor y revocar las sesiones activas cuando se modifiquen credenciales o datos sensibles de una cuenta.

## Conclusión

El caso de los dos fabricantes automotrices demuestra que un error aparentemente sencillo puede convertirse en un incidente de seguridad con consecuencias que van más allá de los sistemas informáticos.

Una contraseña predeterminada, una consola administrativa olvidada o una credencial de prueba expuesta pueden convertirse en puntos de entrada para comprometer información, identidades digitales y servicios conectados.

A medida que las organizaciones incorporan más servicios digitales y dispositivos conectados, resulta indispensable mantener controles de acceso adecuados y evaluar continuamente la seguridad de sus infraestructuras.

**La seguridad no depende únicamente de la tecnología implementada, sino también de cómo se configura, administra y supervisa.**
