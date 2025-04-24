# Weak Session IDs

Las IDs de sesión son valores que permiten identificar de forma única a un usuario autenticado en una aplicación web. Si estas IDs son predecibles, podríamos secuestrar sesiones activas y obtener acceso no autorizado. Por lo que a continuación veremos funciones de como se generan ciertas IDs y como podríamos modificar nuestro ID de Sesión para acceder.

**Explotación de dificultad Low:**

En este nivel, el valor de la cookie de sesión se genera de forma incremental. Esto significa que si un usuario tiene el ID 0, el siguiente tendrá el 1, y así sucesivamente.

En este caso, modificamos el valor de nuestra ID de Sesión para obtener el siguiente ID predecible que será y de esta manera obtener una sesión activa de manera no autorizada.

![image](https://github.com/user-attachments/assets/c5b11a4b-7c36-4575-9005-7fa8e2182239)

Ahora le damos a generate otra vez y obtenemos acceso a una sesión activa.

![L2](./Assets/Weak%20Session%20ID/LOW%20-%202.png)

**Explotación de dificultad Medium:**

En este nivel, el ID de sesión se genera usando la función time();, que devuelve el timestamp UNIX actual (segundos desde 1970).

![M1](./Assets/Weak%20Session%20ID/MEDIUM%20-%201.png)

En este caso, sigue siendo predecible si un atacante sabe o estima la hora exacta en la que un usuario se conectó. También se puede automatizar la prueba de rangos de timestamps cercanos.

Para esta ocasión podríamos volver a modificar las cookies y obtener acceso de nuevo a dicha sesión sin que nos pida iniciar sesión de nuevo.
