# Stored Cross Site Scripting (XSS)

En este caso vamos a ver como explotar una vulnerabilidad de Stored XSS, esta es una vulnerabilidad en la que se logra inyectar un script malicioso que queda almacenado en el servidor, y cada vez que otro usuario accede a la página afectada, el script se ejecuta automáticamente en su navegador.

**Explotación de dificultad Low:**

En este nivel, los campos Name y Message aceptan cualquier entrada sin validación ni codificación.

![0](./Assets/Stored%20Cross%20Site%20Scripting%20(XSS)/0.png)

Por lo que podemos inyectar código malicoso haciendo uso de esto, por lo que vamos a utilizar el mismo payload que en Reflected XSS para obtener el valor de las cookies.

```html
payload=<img src=x onerror="alert(document.cookie)">
```

Este payload, como sabemos de anteriormente, lo que realiza es que crea una etiqueta de imagen con un src inválido (la imagen no se puede cargar), lo que provoca un error. Aprovechando esto, se usa el atributo onerror para ejecutar el código alert(document.cookie), que muestra una ventana emergente con las cookies del usuario.

![L1](./Assets/Stored%20Cross%20Site%20Scripting%20(XSS)/LOW%20-%201.png)

Introducimos el payload en este caso en el campo de Message, y al enviarlo obtenemos el valor de las cookies.

![L2](./Assets/Stored%20Cross%20Site%20Scripting%20(XSS)/LOW%20-%202.png)

**Explotación de dificultad Medium:**

En este nivel de dificultad, el campo message esta más protegido frente a payloads, no obstante, el campo name sigue siendo vulnerable. Sin embargo, tiene una limitación de longitud impuesta por el atributo maxlength, lo que evita inyectar scripts largos directamente, por lo que desde DevTools modificamos el valor del atributo maxlength del campo name, para poder introducir nuestro payload.

![M1](./Assets/Stored%20Cross%20Site%20Scripting%20(XSS)/MEDIUM%20-%201.png)

Una vez modificado el valor de dicho atributo podemos introducir todo el siguiente paylaod, que en este caso ya no podemos hacer uso del mismo, por lo que usamos el siguiente:

```html
payload=<sCrIpT>alert(document.cookie);</ScRiPt>
```

En este caso, mezclamos mayúsculas y minúsculas para evitar filtros de palabras como script, e introducimos dentro una alerta para que cuando enviemos la información, al momento de recargarse la página nos muestre el valor de las cookies.

![M2](./Assets/Stored%20Cross%20Site%20Scripting%20(XSS)/MEDIUM%20-%202.png)

![M3](.Assets/Stored%20Cross%20Site%20Scripting%20(XSS)/MEDIUM%20-%203.png)
