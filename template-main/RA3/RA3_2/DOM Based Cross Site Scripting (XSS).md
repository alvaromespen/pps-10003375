# DOM Based Cross Site Scripting (XSS)

En esta parte de la práctica veremos como explotar la vulnerabilidad de DOM-Based XSS que ocurre en el navegador del cliente, cuando el código JavaScript manipula datos sin validarlos adecuadamente, como parámetros en la URL. No depende directamente de la respuesta del servidor, sino de cómo el DOM (Document Object Model) gestiona e interpreta esos datos.

En este caso, la página tiene una funcionalidad que permite seleccionar un idioma, usando un parámetro GET como ?default=English, el valor de este parámetro se refleja directamente en el DOM, lo que permite inyectar código malicioso.

![L](./Assets/DOM%20Based%20Cross%20Site%20Scripting%20(XSS)/LOW%20-%201.PNG)

**Explotación de dificultad Low:**

