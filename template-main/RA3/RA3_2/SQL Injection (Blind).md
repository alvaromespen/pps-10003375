# SQL Injection (Blind)

En este reto de DVWA trabajamos sobre una vulnerabilidad de Blind SQL Injection. Aquí, no vemos directamente el resultado de nuestras consultas, así que debemos interpretar si la inyección fue exitosa mediante cambios en el comportamiento del servidor, como los tiempos de respuestaa.

El objetivo será comprobar que existe la vulnerabilidad y después extraer la versión de la base de datos usando un script en Python.

**Explotación de dificultad Low:**

En el nivel de seguridad bajo, podemos hacer uso del siguiente payload

```html
1' and sleep(5)#
```

En caso de que exista ese ID, en este caso el 1, el servidor tardará 5 segundos en respondernos, que en este caso es así, por lo que a continuación, sabiendo que existe esta vulnerabilidad ejecutamos el siguiente script de python para obtener la versión.

![L1](./Assets/SQLi%20Blind/LOW%20-%201.PNG)

Y tras tener el código creado, ejecutamos este mismo script para obtener la versión de la base de datos.

Este script funciona de la siguiente manera explicado de manera sencilla:

En primer lugar, el script prueba números del 0 al 99 para averiguar cuántos caracteres tiene el resultado de version(). Cuando acierta, averiguamos la longitud.

En segundo lugar, el script va letra por letra para cada posición haciendo uso de fors, por lo que probamos todos los caracteres posibles (códigos ASCII) hasta encontrar el correcto.
Cuando acierta una letra, la escribe en pantalla, y pasa a buscar la siguiente, obteniendo finalmente toda la versión.

![L2](./Assets/SQLi%20Blind/LOW%20-%202.PNG)

**Explotación de dificultad Medium:**

En este caso, el nivel de seguridad medio introduce cambios para hacerlo un poco más difícil. Ahora el formulario filtra las comillas ', pero el campo id sigue siendo vulnerable, por lo que el payload a ejecutar es el siguiente:

```html
1 and sleep(5)
```

Y vuelve a tardar 5 segundos en responder, por lo que la vulnerabilidad sigue siendo existente, por lo que ahora creamos el siguiente código de python:

![M1](./Assets/SQLi%20Blind/MEDIUM%20-%201.PNG)

En este caso, el script funciona de una manera similar al anterior, donde haciendo uso de bucles con for volvemos a averiguar poco a poco la versión de la base de datos, y obtenemos el siguiente resultado.

![M2](./Assets/SQLi%20Blind/MEDIUM%20-%202.PNG)
