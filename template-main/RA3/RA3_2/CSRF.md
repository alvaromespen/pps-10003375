# Cross-Site Request Forgery (CSRF)

En este caso veremos como explotar la vulnerabilidad CSRF, esta es un tipo de vulnerabilidad que permite a un atacante realizar acciones no autorizadas, como por ejemplo cambiar las contraseñas a los usuarios, en nombre de un usuario autenticado, sin su consentimiento.

**Explotación de dificultad Low:**

En este nivel de dificultad, la funcionalidad de cambio de contraseña no cuenta con ninguna protección CSRF, por lo que nos permitecrear una página maliciosa que, al ser visitada por un usuario autenticado, envíe automáticamente una solicitud para cambiar su contraseña sin su conocimiento.

El payload que hemos utilizado es un código que crea una página web que, al ser visitada, envía automáticamente una solicitud para cambiar la contraseña de un usuario en la aplicación vulnerable DVWA, que está corriendo localmente en http://127.0.0.1/vulnerabilities/csrf/. Como el formulario contiene campos ocultos con una nueva contraseña (pass) y se autoenvía con JavaScript (document.forms[0].submit()), si el usuario está autenticado en DVWA en el momento de visitar esta página, su navegador enviará la petición con sus cookies de sesión, y la contraseña será cambiada sin su consentimiento.

![L1](./Assets/CSRF/LOW%20-%201.png)

Para poder simular esto de manera rápida hacemos uso de python y nos conectamos a un servidor web en el puerto 8000 y accedemos al fichero html que hemos creado, y deberíamos ver este output, en la máquina que aloja el servidor http.

![L2](./Assets/CSRF/LOW%20-%201.5.png)
![L3](./Assets/CSRF/LOW%20-%202.png)
