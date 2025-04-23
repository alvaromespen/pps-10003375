# File Inclusion

A continuación, vamos a realizar pruebas de inclusión de archivos locales (LFI - Local File Inclusion) en DVWA (Damn Vulnerable Web Application) para comprender cómo se puede leer archivos del servidor explotando parámetros mal gestionados en el backend.

**Explotación de dificultad Low y Medium:**

En este caso la vulnerabilidad puede ser explotada de la misma manera tanto en la dificultad Low y Medium.

Esta vulnerabilidad existe ya que en la página web se está cargando un fichero especificando su ruta, en este caso podemos hacer uso de este payload, donde estamos forzando al servidor a incluir y mostrar el contenido del archivo /etc/passwd, que es un archivo sensible del sistema Linux que contiene información de usuarios, reemplazando la lectura del fichero establecido por defecto en la web al fichero de usuarios y contraseñas.

![LM](./Assets/File%20Inclusion/LOW%20MEDIUM-%201.png)
