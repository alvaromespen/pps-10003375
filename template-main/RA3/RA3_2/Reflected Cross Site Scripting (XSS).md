# Reflected Cross Site Scripting (XSS)

A continuación, vamos a ver como explotar Reflected Cross Site Scripting (XSS), es una vulnerabilidad común en aplicaciones web donde la entrada del usuario no es validada correctamente antes de ser reflejada en la respuesta HTML. Esto permite a un atacante inyectar scripts maliciosos.

**Explotación de dificultad Low:**

Para este nivel de dificultad DVWA refleja directamente cualquier valor introducido en el campo name dentro del HTML de respuesta, sin aplicar ningún tipo de filtrado o codificación.

![0](./Assets/Reflected%20Cross%20Site%20Scripting%20(XSS)/0.png)
