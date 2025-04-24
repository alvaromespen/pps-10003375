# Reflected Cross Site Scripting (XSS)

A continuación, vamos a ver como explotar Reflected Cross Site Scripting (XSS), es una vulnerabilidad común en aplicaciones web donde la entrada del usuario no es validada correctamente antes de ser reflejada en la respuesta HTML. Esto permite a un atacante inyectar scripts maliciosos.

**Explotación de dificultad Low, Medium y High:**

Para este nivel de dificultad DVWA refleja directamente cualquier valor introducido en el campo name dentro del HTML de respuesta, sin aplicar ningún tipo de filtrado o codificación.

![0](./Assets/Reflected%20Cross%20Site%20Scripting%20(XSS)/0.png)

Por lo que si en la casilla de Name introducimos el siguiente payload:

```html
payload=<img src=x onerror="alert(document.cookie)">
```

Podemos obtener el valor de las cookies y lo visualizaremos por pantalla.

![L](./Assets/Reflected%20Cross%20Site%20Scripting%20(XSS)/LOW%20-%202.png)

Este mismo payload puede ser utilizado tanto en las dificultades de Medium y High, por lo que si cambiamos la dificultad y lo volvemos a ejecutar obtenemos el valor de las cookies también.

![M](./Assets/Reflected%20Cross%20Site%20Scripting%20(XSS)/MEDIUM%20-%201.png)

![H](./Assets/Reflected%20Cross%20Site%20Scripting%20(XSS)/HIGH%20-%201.png)
