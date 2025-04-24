# JavaScript Attacks

En este reto de JavaScript Attacks en DVWA, el objetivo es ver cómo interactúan los valores calculados y manipulados en formularios web. Usaremos un proceso basado en la tokenización y técnicas de codificación para evadir controles, manipulando las valores haciendo uso de DevTools.

**Explotación de dificultad Low:**

En este nivel de seguridad, el formulario está diseñado para recibir una cadena de texto, “ChangeMe”, que se convierte en un token mediante una combinación de funciones, donde el servidor valida que el token enviado sea el valor MD5 de un rot13 de la palabra "success".

Pero antes de seguir, ya sabemos lo que es MD5, pero que es rot13.

ROT13 -->  Esta es una técnica de codificación sencilla que se utiliza principalmente para ocultar temporalmente texto en claro. Es un tipo de cifrado de sustitución basado en el alfabeto, donde cada letra se reemplaza por la letra que se encuentra 13 posiciones después en el alfabeto.

Sabiendo esto, lo que tenemos que hacer es transofmar success usando rot13, donde se queda fhpprff, y esto lo hasheamos usando MD5.

![image](https://github.com/user-attachments/assets/bebd848a-22ee-4952-aadb-9119dc3d518b)

![image](https://github.com/user-attachments/assets/33143761-c9bd-41c8-b3b3-5e76c8a6d16c)

Una vez tenemos este token, accedemos a DevTools y buscamos el parametro que almacena el valor de los tokens y lo modificamos por el que acabamos de conseguir

Token --> 38581812b435834ebf84ebcc2c6424d6

![L1](./Assets/JavaScript%20Attacks/LOW%20-%201.png)
![L2](./Assets/JavaScript%20Attacks/LOW%20-%202.png)
