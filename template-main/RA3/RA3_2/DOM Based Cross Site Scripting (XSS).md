# DOM Based Cross Site Scripting (XSS)

En esta parte de la práctica veremos como explotar la vulnerabilidad de DOM-Based XSS que ocurre en el navegador del cliente, cuando el código JavaScript manipula datos sin validarlos adecuadamente, como parámetros en la URL. No depende directamente de la respuesta del servidor, sino de cómo el DOM (Document Object Model) gestiona e interpreta esos datos.

En este caso, la página tiene una funcionalidad que permite seleccionar un idioma, usando un parámetro GET como ?default=English, el valor de este parámetro se refleja directamente en el DOM, lo que permite inyectar código malicioso.

![L](./Assets/DOM%20Based%20Cross%20Site%20Scripting%20(XSS)/LOW%20-%201.png)

**Explotación de dificultad Low:**

Para poder realizar la explotación con esta dificultad, tenemos que modificar la URL, quitando el English y pasando el paylaod siguiente: <script>alert(document.cookie);</script> obteniendo así el valor de las cookies.

![L](./Assets/DOM%20Based%20Cross%20Site%20Scripting%20(XSS)/LOW%20-%202.png)

**Explotación de dificultad Medium:**

En este nivel, el payload se inyecta dentro de una etiqueta <option> ya que no podemos usar la etiqueta de script, ya que está bloqueada, por lo que usaremos una etiqueta de imagen siguiendo el mismo proceso.

payload="></option></select><im src=x onerror="alert(document.cookie)" >

![L](./Assets/DOM%20Based%20Cross%20Site%20Scripting%20(XSS)/MEDIUM%20-%201.png)

**Explotación de dificultad High:**

Este nivel de dificultad complica más las cosas, ya que aquí el servidor utiliza una lista blanca (whitelist) y filtra el contenido malicioso. No obstante, se puede eludir utilizando el fragmento de URL (#), que no se envía al servidor, pero sí lo interpreta el navegador si está programado para leerlo, obteniendo así los valores de las cookies.

payload=#<script>alert(document.cookie);</script>

![L](./Assets/DOM%20Based%20Cross%20Site%20Scripting%20(XSS)/HIGH%20-%201.png)
