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
![SC](./Assets/File%20Upload/LOW%20-%204.PNG)

**Explotación de dificultad Medium:**

En este nivel de dificultad, ya no acepta archivos .php, por lo que hemos realizado una copia del código anterior, renombrandolo con un .jpg al final, una vez hecho eso nos dará un bloqueo de subida, por lo que si accedemos a las DevTools y vamos a la pestaña de Network y le damos click derecho en la petición y seleccionamos *Edit and Resend* podemos modificar el Content-Type a image/jpg, y tras eso podremos subirlo.

![image](https://github.com/user-attachments/assets/ca64edf2-f727-4d2c-9277-f1421dba421a)

Una vez con el archivo subido accedemos a la URL, y esta se quedará cargando, en este momento, si accedemos a nuestra terminal que estaba escuchando en el puerto 9001 veremos que hemos conseguido una reverse shell.

![image](https://github.com/user-attachments/assets/bebc74d2-058c-44d2-8d2c-d16ebac5ad71)
