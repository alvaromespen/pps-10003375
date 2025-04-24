# SQL Injection

A continuación veremos como explotar la vulnerabilidad de SQL Injection, la cuál es una vulnerabilidad crítica que permite a un atacante interferir con las consultas SQL que una aplicación envía a su base de datos. Mediante esta técnica, se pueden obtener, modificar o incluso eliminar datos sin autorización.

**Explotación de dificultad Low:**

Para la explotación de este nivel de dificultad haremos uso de ', ya que cuando se envía un ' en el campo de entrada, la aplicación devuelve un error de SQL, indicando que no se están utilizando correctamente los mecanismos de protección como consultas preparadas o sanitización de entradas. Haciendo esto y introduciendo posteriormente un or 1=1# obtenemos todas las entradas, ya que 1 siempre será igual a 1.

![L1](./Assets/SQL%20Injection/LOW%20-%201.png)

Para obtener todas las contraseñas de cada usuario ejecutamos el siguiente payload

```html
' UNION SELECT user, password FROM users#
```

![L2](./Assets/SQL%20Injection/LOW%20-%202.png)

**Explotación de dificultad Medium:**

En este nivel de dificultad ya no se utilizan métodos GET sino que se utilizan métodos POST, además de que las comillas están filtradas, por lo que no podemos ejecutar el mismo payload, no obstante, se puede introducir el parámetro ID por lo que haciendo uso del siguiente payload podemos obtener las credenciales.

Por lo que si cambiamos desde DevTools el valor del campo que hace referencia a la ID 1, y ejecutamos la consulta de la ID 1 obtenemos toda la información que queríamos.

![M1](./Assets/SQL%20Injection/MEDIUM%20-%201.png)
![M2](./Assets/SQL%20Injection/MEDIUM%20-%202.png)
