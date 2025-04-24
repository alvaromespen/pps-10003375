#SQL Injection

A continuación veremos como explotar la vulnerabilidad de SQL Injection, la cuál es una vulnerabilidad crítica que permite a un atacante interferir con las consultas SQL que una aplicación envía a su base de datos. Mediante esta técnica, se pueden obtener, modificar o incluso eliminar datos sin autorización.

**Explotación de dificultad Low:**

Para la explotación de este nivel de dificultad haremos uso de ', ya que cuando se envía un ' en el campo de entrada, la aplicación devuelve un error de SQL, indicando que no se están utilizando correctamente los mecanismos de protección como consultas preparadas o sanitización de entradas. Haciendo esto y introduciendo posteriormente un or 1=1# obtenemos todas las entradas, ya que 1 siempre será igual a 1.

![L1](./Assets/SQL%20Injection/LOW%20-%201.png)

Para obtener todas las contraseñas de cada usuario ejecutamos el siguiente payload

```html
' UNION SELECT user, password FROM users#
```

![L2](./Assets/SQL%20Injection/LOW%20-%202.png)
