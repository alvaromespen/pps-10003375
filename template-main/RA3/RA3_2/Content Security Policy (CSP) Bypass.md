# Content Security Policy (CSP) ByPass

En esta parte de la práctica veremos como *Bypassear* el CSP, que es una capa de seguridad que ayuda a detectar y mitigar ciertos tipos de ataques como Cross Site Scripting (XSS).

**Explotación de dificultad Low:**

En este nivel, CSP permite cargar scripts desde sitios externos, como pastebin.com, no obstante, este sitio ya no se encuentra funcional, por lo que haremos uso de los nuevos sitios proporcionados por DVWA.

![0](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/0.png)

En este caso, seguiremos ejecutando payloads para poder obtener el valor de las cookies del usuario, por lo que en el campo de texto que tenemos introducimos el script que ejecutaremos, que en este caso es el cookie.js

![L1](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/LOW%20-%201.png)
![L2](./Assets/Content%20Security%20Policy%20(CSP)%20Bypass/LOW%20-%202.png)
