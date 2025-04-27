# Brute Force Attack - DVWA

El objetivo de esta práctica es realizar un ataque de fuerza bruta a una página de login en la aplicación DVWA (Damn Vulnerable Web Application) utilizando la herramienta Hydra, con diferentes niveles de seguridad, como son en low y medium.

**Explotación de dificultad Low:**

Para proceder lo primero que necesitamos para poder ejecutar el ataque de fuerza bruta con hydra es obtener el SESSIONSID, esto lo podemos obtener haciendo uso de inspeccionar en los Storage --> Cookies.

![SID](./Assets/Brute%20Force/LOW%20-%201.png)

En esta captura donde vemos el valor de las cookies, podemos ver que la dificultad está en Impossible, por lo que la tenemos que cambiar a Low antes de proseguir.

Una vez con esta información obtenida podemos proceder a ejecutar el ataque de fuerza bruta con Hydra

![Ataque](./Assets/Brute%20Force/LOW%20-%202.PNG)

La ejecución del comando Hydra realiza un ataque de fuerza bruta por diccionario contra el formulario de login de DVWA usando el método GET. Prueba el usuario admin con todas las contraseñas del archivo rockyou.txt, enviando cada intento a la URL del módulo de fuerza bruta de DVWA. Identifica intentos fallidos por el mensaje "Username and/or password incorrect." y utiliza una cookie de sesión PHP válida junto con el nivel de seguridad configurado en "low" para mantener la sesión activa durante el ataque.

La razón por la que vemos diferentes contraseñas válidas se debe a que Hydra fue capaz de probar una combinación de usuario y contraseñas en cada intento y mostró aquellas que no causaron el mensaje de error "Username and/or password incorrect.". 
Esto quiere decir que es probable que 15 de las 16 contraseñas sean falsos positivos que pertenecen al diccionario rockyou.txt

**Explotación de dificultad High:**

Debdio a que el ataque de fuerza bruta en dificultad media decia que tardaba 32 horas en ejecutarse, hemos decidido realizar la dificultad High haciendo uso de un código de python.


En este nivel, el sistema implementa varias medidas de seguridad para protegerse contra ataques de fuerza bruta, como la validación de tokens CSRFy el uso de cookies para autenticación de sesión. 

Sin embargo, aún es posible realizar un ataque de fuerza bruta utilizando herramientas y técnicas avanzadas, como la extracción del user_token para completar la autenticación.

En este caso hemos hecho uso del siguiente script de Python para automatizar la tarea de obtener los credenciales.

![H1](./Assets/Brute%20Force/HIGH%20-%201.PNG)

Lo que realiza este script es lo siguiente:

- El script primero obtiene el valor del parámetro user_token de la página de inicio de sesión (esto es necesario para evitar ataques CSRF). Luego, recorre las contraseñas del diccionario rockyou.txt y las prueba para ver si alguna de ellas otorga acceso al sistema.

En nuestro caso, hemos modificado la URL para que fuera la correcta, además, también hemos introducido nuestra PHPSESSID, y finalmente hemos utilizado un diccionario más pequeño basado en las primeras 1000 contraseñas de rockyou.txt obtenido de la siguiente manera.

![H0](./Assets/Brute%20Force/HIGH%20-%200.PNG)

Finalmente, hemos ejecutado el script de python y hemos obtenido el siguiente output con la contraseña obtenida.

![H2](./Assets/Brute%20Force/HIGH%20-%202.PNG)
