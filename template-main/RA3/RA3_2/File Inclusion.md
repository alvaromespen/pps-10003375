# File Inclusion

A continuación, vamos a realizar pruebas de inclusión de archivos locales (LFI - Local File Inclusion), esta es una vulnerabilidad que permite a un atacante leer archivos del servidor cuando una aplicación web utiliza entradas del usuario para construir rutas de archivos sin la validación adecuada, en DVWA (Damn Vulnerable Web Application) para comprender cómo se puede leer archivos del servidor explotando parámetros mal gestionados en el backend.

**Explotación de dificultad Low y Medium:**

En este caso la vulnerabilidad puede ser explotada de la misma manera tanto en la dificultad Low y Medium.

Esta vulnerabilidad existe ya que en la página web se está cargando un fichero especificando su ruta, en este caso podemos hacer uso de este payload, donde estamos forzando al servidor a incluir y mostrar el contenido del archivo /etc/passwd, que es un archivo sensible del sistema Linux que contiene información de usuarios, reemplazando la lectura del fichero establecido por defecto en la web al fichero de usuarios y contraseñas.

![LM](./Assets/File%20Inclusion/LOW%20&%20MEDIUM-%201.png)

**Explotación de dificultad High:**

En este caso existen una serie de cambios, con esta dificultad el servidor filtra los archivos que pueden ser incluidos, por lo que solo mostrará archivos cuyo nombre empiece con file. 

![image](https://github.com/user-attachments/assets/356c2cbc-0099-483d-b48e-bddc1676f969)

No obstante, este no es un gran problema, ya que podemos *bypassearlo* haciendo uso de un payload de path traversal, vulnerabilidad que permite a un atacante acceder a archivos o directorios fuera del directorio raíz permitido por la aplicación web.

![H](./Assets/File%20Inclusion/HIGH%20-%201.png)
