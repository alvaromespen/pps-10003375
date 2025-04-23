 # Command Injection

En este apartado vamos a ver como podemos explotar una vulnerabilidad de *Command Injection*, es una vulnerabilidad que permite a un atacante ejecutar comandos arbitrarios del sistema en el servidor donde se ejecuta una aplicación web.

Esto es posible en este caso gracias a una funcionalidad vulnerable que permite hacer ping a un host desde la aplicación web. El usuario puede introducir una IP o un dominio, y el backend ejecuta algo como: ping IP.

Haciendo uso de esa funcionalidad podemos hacer introducir comandos concatenados a la IP a la que se realiza el ping para poder ejecutarlos de manera remota.

**Explotación de dificultad Low:**

Para esta dificultad hemos hecho uso del ; ya que se usa como un delimitador para separar comandos, por lo que primero se ejecutará el ping y tras eso se ejecutará el comando establecido, en este caso, whoami.

![PING en Low](./Assets/Command%20Injection/LOW%20-%201.png)
