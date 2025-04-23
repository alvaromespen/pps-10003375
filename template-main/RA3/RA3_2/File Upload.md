# File Upload

En esta parte de la explotaremos la vulnerabilidad de File Upload (subida de archivos) en DVWA (Damn Vulnerable Web Application), que permite subir archivos arbitrarios sin restricciones adecuadas. Este tipo de fallo puede llevar a la ejecución remota de código (RCE) si el atacante sube un archivo malicioso, como una reverse shell en PHP.

**Explotación de dificultad Low:**

En este caso, lo primero que tenemos que hacer es crear nuestro script en php para subirlo al servidor y posteriormente ejecutar para activar la reverse shell.

El script que hemos creado es el siguiente:

![SC](./Assets/File%20Upload/LOW%20-%201.PNG)

Una vez con el script creado vamos a poner nuestro equipo en escucha en el puerto 9001 haciendo uso de netcat.

![SC](./Assets/File%20Upload/LOW%20-%202.PNG)

Tras esto, vamos a subir el fichero al servidor desde la página web, y ejecutaremos el php haciendo uso de curl, obteniendo así acceso remoto a los comandos a través de una reverse shell.

![SC](./Assets/File%20Upload/LOW%20-%203.png)
![SC](./Assets/File%20Upload/LOW%20-%204.png)
