# File Upload

En esta parte de la explotaremos la vulnerabilidad de File Upload (subida de archivos) en DVWA (Damn Vulnerable Web Application), que permite subir archivos arbitrarios sin restricciones adecuadas. Este tipo de fallo puede llevar a la ejecución remota de código (RCE) si el atacante sube un archivo malicioso, como una reverse shell en PHP.

**Explotación de dificultad Low:**

En este caso, lo primero que tenemos que hacer es crear nuestro script en php para subirlo al servidor y posteriormente ejecutar para activar la reverse shell.

El script que hemos creado es el siguiente:

![SC](./Assets/File%20Upload/LOW%20-%201.PNG)
