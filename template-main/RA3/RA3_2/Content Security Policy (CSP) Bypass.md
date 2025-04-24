# Content Security Policy (CSP) ByPass

En esta parte de la práctica veremos como *Bypassear* el CSP, que es una capa de seguridad que ayuda a detectar y mitigar ciertos tipos de ataques como Cross Site Scripting (XSS).

**Explotación de dificultad Low:**

En este nivel, CSP permite cargar scripts desde sitios externos, como pastebin.com, no obstante, este sitio ya no se encuentra funcional, por lo que haremos uso de los nuevos sitios proporcionados por DVWA.

![0](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/0.png)

En este caso, seguiremos ejecutando payloads para poder obtener el valor de las cookies del usuario, por lo que en el campo de texto que tenemos introducimos el script que ejecutaremos, que en este caso es el cookie.js

![L1](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/LOW%20-%201.png)
![L2](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/LOW%20-%202.png)

**Explotación de dificultad Medium:**

En este nivel de dificultad, el servidor implementa una política CSP que usa un nonce (número aleatorio temporal) para autorizar solo los scripts con ese valor específico. Sin el nonce correcto, el navegador bloquea el script.

En este caso, la política CSP se ve más robusta, no obstante, el nonce es estático, lo que nos permite reutilizar el proporcionado para ejecutar el script de alerta que nos proporcionará el valor de las cookies.

El nonce es el siguiente: "TmV2ZXIgZ29pbmcgdG8gZ2l2ZSB5b3UgdXA="

Una manera de obtener el nonce es desde DevTools en la pestaña de Network --> accedemos a un paquete y en la cabecera podemos encontrar el apartado de CSP donde veremos el Nonce.

![M1](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/MEDIUM%20-%201.png)

Y una vez con el Nonce ejecutamos el siguiente paylaod:

```html
payload=<script nonce="TmV2ZXIgZ29pbmcgdG8gZ2l2ZSB5b3UgdXA=">alert(document.cookie)</script>
```

![M2](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/MEDIUM%20-%202.png)
