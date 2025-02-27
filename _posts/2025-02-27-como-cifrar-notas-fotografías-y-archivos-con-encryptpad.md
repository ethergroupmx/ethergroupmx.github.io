---
title: Cómo cifrar notas, fotografías y archivos con EncryptPad
date: 2025-02-27 09:00:00 
categories: [HACKING]
tags: [ciberseguridad, hacking]
description: EncryptPad, una aplicación fácil de usar que permite cifrar texto, fotos o archivos con un cifrado fuerte mediante una contraseña, un archivo de claves o ambos.
image: /assets/114/preview1.png
---

Para quienes desean mantener la privacidad de sus datos, el texto simple es un formato del pasado. En su lugar, existe un cifrado barato y potente que está ampliamente disponible, pero a menudo no es lo suficientemente fácil de usar como para atraer una adopción generalizada. Una excepción a esta regla es EncryptPad, una aplicación fácil de usar que permite cifrar texto, fotos o archivos con un cifrado fuerte mediante una contraseña, un archivo de claves o ambos.

### La necesidad de información cifrada

En el mundo digital, el texto sin formato es un blanco fácil. Mantener cualquier cosa importante en texto sin formato significa, obviamente, que cualquiera puede leerlo, y si bien esto era de esperar en una época en la que la capacidad de procesamiento era costosa, ahora existen muchas formas gratuitas y sencillas de mantener el texto en un estado más seguro. El cifrado utiliza una clave que usted crea para codificar los datos que está guardando, lo que hace que sea fácil para usted recuperarlos, pero difícil o imposible para otros.

Piénsalo de esta manera: si tuvieras que grabar todo en texto sin formato en tu computadora y luego lo perdieras, quien lo encontrara podría leer todo el contenido no cifrado de tu disco. Si perdieras la misma computadora portátil pero con tus archivos cifrados, hay algunas formas en las que podrías frustrar a alguien que intente hurgar en su interior.

### Contraseñas y más para gestionar el cifrado

En primer lugar, podría establecer una contraseña que sería necesario descifrar para recuperar la información, lo que reduciría significativamente la probabilidad de que alguien pudiera acceder a los archivos que ahora están fuera de su control. Por supuesto, esto aún podría ser objeto de un ataque si eligiera una contraseña débil o común o si reutilizara la contraseña en otros lugares donde pudiera ser objeto de phishing.

Una forma más segura de hacerlo es crear un archivo de claves necesario para desbloquear archivos confidenciales y luego mantener una copia accesible a través de la red. De esa manera, puede revocar el acceso al archivo eliminando la clave de la red, lo que hace que sea imposible descifrar los archivos hasta que vuelva a cargar la clave.

EncryptPad es una aplicación fácil de usar que presenta una interfaz gráfica de usuario sencilla similar a la de otros programas de bloc de notas. Si bien no es el procesador de texto más potente, facilita el cifrado de notas y permite la misma funcionalidad que esperaría de cualquier editor de texto con interfaz gráfica de usuario.

### Instalar EncryptPad

Para descargar EncryptPad, la mejor forma de comenzar es utilizar los archivos binarios precompilados disponibles en el sitio web de EncryptPad . Seleccione la versión que coincida con su sistema operativo y luego instale EncryptPad siguiendo las instrucciones en pantalla.

Para macOS , simplemente descargue el archivo y abra la imagen del disco para encontrar la aplicación de bloc de notas encriptada completamente funcional. Puede arrastrarla y soltarla directamente en su carpeta "Aplicaciones". En otros sistemas, EncryptPad es igualmente fácil de instalar.

![Imagen 01](/assets/114/114-01.png)

### Abrir un archivo de texto usando el editor de texto

Para abrir EncryptPad, inicie la aplicación haciendo doble clic en el icono del candado de EncryptPad. Esto debería abrirlo en un archivo de EncryptPad vacío y "sin título". Notará que la extensión del archivo, EPD, es específica de este programa.

![Imagen 01](/assets/114/114-02.png)

Aquí puedes ver que tenemos el mismo tipo de editor de texto básico que esperaríamos que se instale junto con un sistema operativo. Si bien no hay muchas opciones de formato, la magia realmente aparece después de bloquear el contenido con una contraseña o un archivo de claves.

Haga clic en el icono de engranaje para mostrar las opciones de cifrado de EncryptPad. Aquí puede ver el tipo de cifrado simétrico que puede seleccionar. Si desea aumentar la potencia de la función hash de SHA-256 a SHA-512, puede hacerlo aquí.

![Imagen 01](/assets/114/114-03.png)

Una vez que se configuran estas opciones, podemos pasar a bloquear nuestro archivo para que solo nosotros podamos verlo. Agreguemos algo de texto y luego procedamos a cifrarlo.

### Proteja su archivo con una contraseña

Una vez que hayas configurado el cifrado a tu gusto, haz clic en "Cifrado" y luego en "Establecer frase de contraseña" para establecer una contraseña para el archivo. También puedes ver las opciones "Borrar frase de contraseña", que puedes usar para eliminar una contraseña si deseas que el archivo sea accesible sin una frase de contraseña.

![Imagen 01](/assets/114/114-04.png)

En la ventana emergente, escriba y confirme una contraseña segura . No escriba una contraseña débil como password123, ya que al hacerlo se anula por completo el objetivo de cifrar esta información en primer lugar.

![Imagen 01](/assets/114/114-05.png)

Después de configurar la contraseña, puede guardar el archivo y estar seguro de que, sin la frase de contraseña, un atacante no podrá abrirlo. Dicho esto, con el tiempo, un atacante decidido aún podría entrar mediante un ataque de fuerza bruta a la contraseña si obtuviera posesión de los archivos.

Entonces, ¿qué más podemos hacer además de agregar una contraseña para mantener a la gente fuera de nuestros archivos?

### Generar un archivo de clave

Una de las formas más sólidas y flexibles de proteger su documento es con un archivo de claves. Un archivo de claves es más seguro que una contraseña y, en algunos aspectos, más fácil de administrar, ya que puede usar EncryptPad para confiar en claves compartidas a través de una red. Esto significa que un archivo de claves se puede eliminar más adelante para denegar el acceso a la información almacenada en los archivos de EncryptPad.

Configurar un archivo de claves es fácil, pero el primer paso es generar uno. En la pestaña "Encriptación", seleccione "Generar clave".

![Imagen 01](/assets/114/114-06.png)

A continuación, seleccione la ubicación en la que desea guardar el archivo de clave. La clave también estará protegida con contraseña, así que asegúrese de tener una buena contraseña lista para protegerla.

![Imagen 01](/assets/114/114-07.png)

Introduce una contraseña para proteger la clave en el siguiente campo y tendrás un archivo .key esperándote donde hayas elegido guardarlo. Por último, aparecerá un mensaje que te preguntará si quieres utilizar la clave generada para este archivo. Por ahora, selecciona "No" para continuar.

![Imagen 01](/assets/114/114-08.png)

### Proteja sus datos con un archivo clave

Ahora, encriptemos nuestro archivo con la clave que acabamos de crear o cualquier otra clave. Haga clic en "Encriptación" nuevamente y luego seleccione "Establecer clave de encriptación". En la ventana emergente que se abre, seleccione una ruta al archivo de clave que desea utilizar para encriptar el archivo. Aquí también puede especificar una clave remota, como una almacenada en un servidor que usted controla.

Una configuración importante aquí es "Conservar la ubicación de la clave en el archivo cifrado". Esto significa que la ubicación de su archivo de clave se guardará en su archivo cifrado, lo que facilita el uso de una clave cifrada remota. Si selecciona esta opción, este archivo de clave se vinculará a su documento cifrado hasta que lo elimine.

![Imagen 01](/assets/114/114-09.png)

Una vez que hayas configurado esto, haz clic en "Aceptar" y establece una contraseña para el archivo de claves. Ahora, tu documento debería indicar que está protegido tanto por una contraseña como por una clave de cifrado.

### Cifrar una imagen o un archivo

EncryptPad no solo encripta texto, también puede encriptar archivos e imágenes. Lo demostraremos creando una versión encriptada de un horrible meme de Garfield usando el archivo de claves que generamos antes.

![Imagen 01](/assets/114/114-10.png)

Primero, comenzaremos con una imagen que queremos cifrar. Haga clic en "Cifrado" y verá el siguiente cuadro de diálogo.

![Imagen 01](/assets/114/114-11.png)

En este cuadro, deberá ingresar el archivo que desea cifrar en el campo "Archivo de entrada" y dónde desea guardar el archivo cifrado en el campo "Archivo de salida". Asegúrese de tener seleccionada la opción "Cifrar" y luego puede seleccionar EPD o GPG como formato de archivo.

Escriba una frase de contraseña para cifrar el archivo y, a continuación, seleccione el archivo de clave que creó anteriormente en el campo "Ruta del archivo de clave". Cuando todo esté seleccionado, haga clic en "Iniciar" e ingrese la contraseña que estableció con el archivo de clave.

![Imagen 01](/assets/114/114-12.png)

Perfecto, cuando volvemos a la carpeta donde guardamos el archivo, podemos ver que ahora hay una versión cifrada guardada allí. Con este proceso, podemos cifrar todo lo que queramos en nuestro sistema.

![Imagen 01](/assets/114/114-13.png)

### Descifrar un archivo cifrado con una clave y una contraseña

Por último, lo más importante es saber cómo descifrar un archivo con una clave y contraseña. Para ello, pulsamos de nuevo en la opción “Encriptación” y nos encontraremos haciendo el proceso inverso a lo que hicimos para cifrar el archivo.

Seleccione la opción "Descifrar" en la parte superior del menú, luego ingrese el archivo que desea descifrar en el campo "Archivo de entrada". Ingrese la ruta y el nombre de archivo que desea que utilice el archivo descifrado en el campo "Archivo de salida" y luego ingrese la ruta al archivo de clave con el que cifró el archivo dentro del campo "Ruta del archivo de clave". Una vez que haya completado estos datos, haga clic en el botón "Iniciar".

Cuando se le solicite, ingrese la contraseña asociada con el archivo y el archivo de clave que está utilizando. Una vez que haya descifrado correctamente el archivo, debería ver el cuadro de confirmación a continuación.

![Imagen 01](/assets/114/114-14.png)

Para abrir un archivo de texto cifrado, puede simplemente abrir el archivo en EncryptPad haciendo clic en "Archivo", "Abrir" y luego proporcionando la contraseña para acceder al archivo cuando se le solicite.

### El cifrado de archivos es potente, privado y fácil de usar

Una cosa que hay que tener en cuenta con el cifrado es que puede funcionar en ambos sentidos. Si establece una contraseña tan fuerte que no puede recordarla, o si establece un archivo de claves y luego lo pierde, no podrá recuperar sus datos. El objetivo del cifrado es que no hay puertas traseras y que es increíblemente difícil recuperar datos para los que no tiene la clave o la contraseña. Por lo tanto, debe realizar copias de seguridad de todos los archivos de claves que utilice, ya que puede necesitarlos si por alguna razón se destruye su copia principal.

Si administra bien sus claves y mantiene sus archivos confidenciales encriptados, no debería tener que preocuparse por que los curiosos desencripten los archivos que desea mantener seguros. Con herramientas como EncryptPad, almacenar texto de forma segura no tiene por qué ser difícil ni complicado.

Espero que hayas disfrutado de esta guía sobre cómo usar EncryptPad para cifrar texto e información. 

Creditos - NULLBYTE















