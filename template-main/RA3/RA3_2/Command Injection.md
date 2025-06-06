 # Command Injection

En este apartado vamos a ver como podemos explotar una vulnerabilidad de *Command Injection*, es una vulnerabilidad que permite a un atacante ejecutar comandos arbitrarios del sistema en el servidor donde se ejecuta una aplicación web.

Esto es posible en este caso gracias a una funcionalidad vulnerable que permite hacer ping a un host desde la aplicación web. El usuario puede introducir una IP o un dominio, y el backend ejecuta algo como: ping IP.

Haciendo uso de esa funcionalidad podemos hacer introducir comandos concatenados a la IP a la que se realiza el ping para poder ejecutarlos de manera remota.

**Explotación de dificultad Low:**

Para esta dificultad hemos hecho uso del ; ya que se usa como un delimitador para separar comandos, por lo que primero se ejecutará el ping y tras eso se ejecutará el comando establecido, en este caso, whoami.

![PING en Low](./Assets/Command%20Injection/LOW%20-%201.png)

**Explotación de dificultad Medium:**

A continuación vamos a realizar la explotación en medium, en este caso, separar los comandos con ; ya no funciona, no obstante, realizando pruebas vemos que haciendo uso de *pipelines* la ejecución remota de comandos funciona a la perfección.

![PING en Medium](./Assets/Command%20Injection/MEDIUM%20-%202.png)

**Explotación de dificultad High:**

En esta parte los comandos anteriores, haciendo uso de primero realizar el ping y tras eso concatenar un segundo comando que es el que queríamos ejecutar en la máquina que contiene el servidor ya no funciona, por lo que simplemente podemos ejecutar "|whoami" y así se ejecuta este comando remoto. Este método también sirve para los otros niveles de dificultad, asi hemos podido ver diferentes maneras de ejecutar comandos remotos a través de hacer uso de ping.

![image](https://github.com/user-attachments/assets/9b417e27-3aef-465e-9a58-47e272538830)
