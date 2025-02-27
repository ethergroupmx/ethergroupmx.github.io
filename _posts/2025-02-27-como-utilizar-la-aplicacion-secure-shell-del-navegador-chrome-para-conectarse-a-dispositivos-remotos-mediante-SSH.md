---
title: Cómo utilizar la aplicación Secure Shell del navegador Chrome para conectarse a dispositivos remotos mediante SSH
date: 2025-02-27 09:00:00 
categories: [HACKING]
tags: [ciberseguridad, hacking, tools]
description: Aprender a usar SSH puede convertirse en una mezcla confusa de programas de terceros y compatibilidad nativa con el sistema operativo. 
image: /assets/115/preview1.png
---

Muchas guías requieren el uso de Secure Shell (SSH) para conectarse a un servidor remoto. Desafortunadamente para los principiantes, aprender a usar SSH puede convertirse en una mezcla confusa de programas de terceros y compatibilidad nativa con el sistema operativo. Para los usuarios de Chrome OS, usar SSH es aún más difícil. Solucionaremos esto usando Chrome Secure Shell para establecer una conexión SSH desde cualquier dispositivo que pueda ejecutar un navegador Chrome.

La extensión y la aplicación Secure Shell para Chrome ofrecen una funcionalidad similar a la de PuTTy para aquellos que están familiarizados con el software de terceros para Windows. La extensión y la aplicación son emuladores de terminal compatibles con xterm y clientes SSH independientes para Chrome. Funcionan combinando el comando SSH portado al cliente nativo de Google con el emulador de terminal hterm , lo que permite que la aplicación proporcione un cliente Secure Shell dentro del navegador sin depender de servidores proxy externos.

En tan solo unos minutos podrás establecer una conexión SSH desde tu navegador Chrome. Por razones obvias, vas a necesitar instalar el navegador Chrome, así que asegúrate de descargar Chrome si aún no lo tienes instalado.

### Instalar el Secure Shell de Chrome

Para comenzar, debes descargar la extensión o aplicación Secure Shell desde Chrome Web Store, según el dispositivo que estés usando. Si estás usando un dispositivo con Chrome OS, necesitarás la aplicación. Todos los demás dispositivos deberían usar la extensión. Después de abrir uno de los enlaces que aparecen a continuación en tu navegador Chrome, haz clic en el botón "Agregar a Chrome" en la esquina superior derecha de la ventana emergente.

![Imagen 01](/assets/115/115-01.png)

A continuación, aparecerá una ventana de diálogo que te pedirá que confirmes que deseas agregar la extensión o la aplicación. Haz clic en "Agregar extensión" o "Agregar aplicación" para instalarla. Si elegiste la extensión, estará disponible para usarla de inmediato. En el caso de la versión de la aplicación, no debería llevar más de unos segundos completar la instalación.

![Imagen 02](/assets/115/115-02.png)

### Abra el Secure Shell de Chrome

Puede acceder a la extensión Secure Shell en Chrome haciendo clic en el icono de la extensión en la barra de herramientas y luego en "Cuadro de diálogo de conexión" o escribiendo ssh en la barra de direcciones y presionando la tecla Tab o la barra espaciadora seguida de Enter . El icono se abrirá en una nueva ventana mientras que el acceso directo de la barra de direcciones estará en la pestaña en la que se encuentra actualmente.

![Imagen 03](/assets/115/115-03.png)

Para la aplicación Secure Shell, puedes hacer clic en "Iniciar aplicación" desde la página de la tienda web. Además, puedes usar chrome://apps en la barra de direcciones o hacer clic en "Aplicaciones" en el extremo izquierdo de Chrome en la barra de marcadores y luego seleccionar "Secure Shell". También es posible abrirla en una pestaña de Chrome usando el truco ssh en la barra de direcciones como con la extensión.

![Imagen 04](/assets/115/115-04.png)

### Guardar una nueva conexión

Ahora que tenemos la extensión o aplicación Secure Shell abierta y en funcionamiento, es sencillo establecer una conexión SSH. En la pantalla SSH, habrá un panel con varias configuraciones disponibles. Observa la primera configuración y asegúrate de que esté seleccionada la opción "Nueva conexión" haciendo clic en ella para que se parezca a la imagen que aparece a continuación. Si nunca has utilizado Secure Shell antes, se seleccionará automáticamente.

![Imagen 05](/assets/115/115-05.png)

A continuación, escribe un nombre para tu nueva conexión en el cuadro de texto superior que dice "nombre de usuario@nombre de host o texto de formato libre". El nombre puede ser cualquier cosa, así que intenta elegir el nombre más preciso que te ayude a recordar qué conexión va a qué dispositivo. Por ejemplo, puedes usar "retroPie" o "Basement media server", ya que incluso un nombre un poco específico como "Raspberry Pi" puede volverse confuso cuando tienes más de una Pi.

Otra opción es comenzar a escribir la conexión en la barra de nombre, como hice yo, y automáticamente se completarán los cuadros correspondientes que aparecen a continuación. De lo contrario, deberá completar cada cuadro manualmente.

- En el cuadro "nombre de usuario", debes colocar el nombre de usuario del servidor al que te estás conectando. Algunos nombres de usuario predeterminados comunes son root y pi .
- El nombre de host debe ser el dominio web o la dirección IP del servidor al que desea conectarse. En mi caso, me estoy conectando a mi teléfono Android, que está en mi red Wi-Fi local. Debido a que este es el caso, usaré la dirección IP local de mi teléfono Android, 192.168.0.13 .
- Después de eso, se debe seleccionar un puerto. El número de puerto predeterminado para las conexiones SSH es 22 , pero se puede cambiar fácilmente, por lo que es posible que tu servidor use un puerto diferente. Por ejemplo, yo usaré el puerto 2222, que es el que usa la aplicación SSHDroid en mi teléfono Android.

![Imagen 06](/assets/115/115-06.png)

Una vez que haya ingresado toda la información requerida, haga clic en el botón "Conectar" en la parte inferior del panel o presione Entrar . Vaya al paso 6 a continuación para ver qué hacer a continuación, o consulte el paso 5 para ver cómo acceder a su nueva conexión guardada más tarde.

### Iniciar su conexión guardada

Después de realizar la primera conexión, solo necesitarás seleccionar el nombre de la conexión en el cuadro para conectarte nuevamente, no "Nueva conexión", ya que la aplicación recordará todos los detalles de inicio de sesión.

Quizás la característica más interesante de usar con Secure Shell es que te permite establecer una conexión SSH en cuestión de segundos con solo escribir en la barra de búsqueda en la parte superior del navegador. Para hacer esto, puedes usar el siguiente formato, que es el mismo que usarías en una ventana de terminal de macOS o Linux . No olvides presionar Tap o Spacebar antes de ingresar la información de conexión.

    ssh username@host:port

Para hacerlo aún más rápido, si tienes la extensión instalada, puedes hacer clic en el icono de la extensión en la barra de herramientas y, a continuación, seleccionar el nombre de la conexión. Aparecerá una nueva ventana con la conexión realizada.

![Imagen 07](/assets/115/115-07.png)

### Inicie sesión en su servidor remoto

Una vez que se haya conectado correctamente, verá aparecer en la ventana o pestaña la ventana de terminal que siempre le resulta familiar. La primera vez que se conecte a un servidor, se le proporcionará una huella digital de clave que deberá aceptar. Esta huella digital se utiliza para facilitar la identificación y verificación de que el servidor al que se está conectando es legítimo.

    Connecting to root@192.168.0.13...
    The authenticity of host '[192.168.0.13]:2222 ([192.168.0.13]:2222)' can't be established.
    RSA key fingerprint is SHA256:fvQg9YFJSoQ5PyyaKDx4tAUOHPkSTxs0TRWiJnIEIMM.
    Are you sure you want to continue connecting (yes/no)?

La huella digital debe ser la misma cada vez que inicie sesión en el mismo sistema. Si alguna vez recibe un mensaje que indica que la huella digital ha cambiado, es una señal de advertencia de que alguien está interfiriendo con la conexión. Después de aceptar la huella digital, se le solicitará que ingrese sus credenciales, como en cualquier otra conexión SSH.

    Connecting to root@192.168.0.13...
    The authenticity of host '[192.168.0.13]:2222 ([192.168.0.13]:2222)' can't be established.
    RSA key fingerprint is SHA256:fvQg9YFJSoQ5PyyaKDx4tAUOHPkSTxs0TRWiJnIEIMM.
    Are you sure you want to continue connecting (yes/no)? yes
    Warning: Permanently added '[192.168.113.113]:2222' (RSA) to the list of known hosts.
    SSHDroid
    Use 'root' as username
    Default password is 'admin'
    root@192.168.113.113's password:
    :/data/data/berserker.android.apps.sshdroid/home $ c

¡Eso es todo! Has utilizado con éxito tu navegador Chrome para establecer una conexión SSH con tu dispositivo remoto.

### Habilitar la autenticación basada en clave

Las contraseñas no son la única forma de autenticar una conexión SSH. El otro método más común se denomina autenticación con clave pública. Este método utiliza un par de claves criptográficas, una pública y otra privada, en lugar de una contraseña. La clave pública se configura en el servidor para autorizar el acceso al servidor a aquellos usuarios que tengan una copia de la clave privada.

El uso de la autenticación basada en claves agrega una capa adicional de comodidad cuando una persona se conecta, ya que elimina el requisito de ingresar una contraseña. En cambio, se considera que el intercambio de claves es la contraseña. La autenticación con claves también es la forma de facto de configurar una conexión SSH automatizada, como las transferencias de archivos automatizadas.

Secure Shell incluye la capacidad de emplear autenticación basada en claves, a la que denomina "archivos de identidad". Para importar archivos de identidad desde la pantalla de conexión, haga clic en "Importar" debajo de la información de conexión y seleccione sus claves públicas y privadas.

![Imagen 08](/assets/115/115-08.png)

La clave privada no debe tener una extensión de archivo, mientras que la clave pública debe tener la extensión PUB. Por ejemplo, puede tener "id_rsa" como clave privada y "id_rsa.pub" como clave pública.

Si el par de claves está almacenado en un archivo PEM, debes dividirlo en dos archivos antes de importarlo. Para ello, puedes abrir el archivo PEM en un editor de texto y copiar y pegar cada clave en un documento nuevo. Si no lo haces, la aplicación no lo aceptará. El archivo PEM tendrá un aspecto similar al siguiente:

    -----BEGIN RSA PRIVATE KEY-----
    [[KEY HERE]]
    -----END RSA PRIVATE KEY-----

    -----BEGIN PUBLIC KEY-----
    [[KEY HERE]]
    -----END PUBLIC KEY-----

Guarde los nuevos documentos con el nombre de archivo original. Por ejemplo, "id_rsa.pub" sería el nombre de archivo de la clave pública.

Si alguna vez desea eliminar alguna de estas claves porque ya no son válidas, navegue hasta la pantalla de conexión y seleccione la identidad asociada con esa clave en el menú. Ahora, presione la tecla Eliminar . Esto eliminará los archivos de clave pública y privada del sistema de archivos HTML5, así como la conexión guardada.

### SSH en cualquier lugar donde Chrome pueda ejecutarse

La aplicación Secure Shell de Chrome es una herramienta fantástica que facilita la vida a los desarrolladores, programadores y hackers a la hora de conectarse a dispositivos remotos. La capacidad de usar SSH directamente desde el navegador Chrome no es una hazaña revolucionaria, pero aporta una comodidad multiplataforma al uso de SSH que no se puede subestimar. Para los usuarios de Chrome OS, en particular, la aplicación Secure Shell es la mejor manera de poder establecer una conexión SSH.











