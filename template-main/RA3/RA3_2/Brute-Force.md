# Brute Force Attack - DVWA

El objetivo de esta práctica es realizar un ataque de fuerza bruta a una página de login en la aplicación DVWA (Damn Vulnerable Web Application) utilizando la herramienta Hydra, con diferentes niveles de seguridad, como son en low y medium.

**Explotación de dificultad Low:**

Para proceder lo primero que necesitamos para poder ejecutar el ataque de fuerza bruta con hydra es obtener el SESSIONSID, esto lo podemos obtener haciendo uso de inspeccionar en los Storage --> Cookies.

![SID](./Assets/Brute%20Force/LOW%20-%201.png)

Una vez con esta información obtenida podemos proceder a ejecutar el ataque de fuerza bruta con Hydra

![Ataque](./Assets/Brute%20Force/LOW%20-%202.PNG)

La ejecución del comando Hydra realiza un ataque de fuerza bruta por diccionario contra el formulario de login de DVWA usando el método GET. Prueba el usuario admin con todas las contraseñas del archivo rockyou.txt, enviando cada intento a la URL del módulo de fuerza bruta de DVWA. Identifica intentos fallidos por el mensaje "Username and/or password incorrect." y utiliza una cookie de sesión PHP válida junto con el nivel de seguridad configurado en "low" para mantener la sesión activa durante el ataque.

La razón por la que vemos diferentes contraseñas válidas se debe a que Hydra fue capaz de probar una combinación de usuario y contraseñas en cada intento y mostró aquellas que no causaron el mensaje de error "Username and/or password incorrect.". 
Esto quiere decir que es probable que 15 de las 16 contraseñas sean falsos positivos que pertenecen al diccionario rockyou.txt
