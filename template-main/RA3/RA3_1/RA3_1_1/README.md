# 3.1.1. Práctica 1 : CSP

Este proyecto proporciona un contenedor Docker basado en Ubuntu con Apache configurado de manera segura, incluyendo medidas de seguridad como la desactivación del módulo autoindex, configuración de cabeceras HTTP seguras y certificados SSL.

## Características de la práctica 1

- **Deshabilitación del módulo autoindex para evitar la exposición no deseada de archivos y directorios.
- **Habilitación de HSTS (HTTP Strict Transport Security)** para forzar el uso de HTTPS.
- **Configuración de Content Security Policy (CSP)** para mitigar ataques XSS.
- **Uso de certificados SSL** para asegurar la comunicación HTTPS.
- **Exposición de los puertos 80 y 443** para tráfico HTTP y HTTPS.

## [Configuración del Dockerfile](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA3/RA3_1/RA3_1_1/Assets/Apache-CSP/Dockerfile)

## Capturas de Pantalla

Aquí puedes ver ejemplos de las configuraciones aplicadas y sus efectos en el servidor Apache:

1. **Apache en ejecución:**

   ![Dockerfile en ejecución: ](./Assets/2.png)

2. **Cabeceras HTTP configuradas correctamente:**

   ![Cabeceras HTTP](./Assets/6.png)

3. **Sitio web con Apache seguro cargado en el navegador:**
    
   ![Apache seguro](./Assets/5.png)

## Seguridad en Apache

### Deshabilitar `mod_autoindex`

El módulo `autoindex` se deshabilita para evitar que los directorios sin un `index.html` o `index.php` muestren su contenido públicamente.

```bash
RUN a2dismod -f autoindex
```

### Configurar HSTS

La cabecera `Strict-Transport-Security` se configura para reforzar el uso de HTTPS.

```apache
<VirtualHost *:443>
  Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains"
</VirtualHost>
```

### Configurar Content Security Policy (CSP)

Se define una política CSP para restringir la carga de contenido desde orígenes específicos.

```apache
Header set Content-Security-Policy \ 
  "default-src 'self'; img-src *; media-src media1.com media2.com; script-src userscripts.example.com"
```

# 3.1.1. Práctica 2 : Web Application Firewall

Este práctica implementa un **Web Application Firewall (WAF)** utilizando **ModSecurity** en un servidor Apache dentro de un contenedor Docker. Se encarga de filtrar y bloquear tráfico malicioso en aplicaciones web.

## Características del Proyecto

- **Implementación de ModSecurity** como WAF para protección contra ataques web.
- **Bloqueo de inyecciones SQL, XSS y CSRF**.
- **Uso de reglas básicas de seguridad del OWASP ModSecurity Core Rule Set (CRS)**.
- **Configuración de Apache con seguridad mejorada**.
- **Pruebas de funcionalidad con intentos de XSS bloqueados**.

## [Configuración del Dockerfile](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA3/RA3_1/RA3_1_1/Assets/Web%20Application%20Firewall/Dockerfile)

## Capturas de Pantalla

Aquí puedes ver ejemplos de la configuración y pruebas de ModSecurity en acción:

1. **Intento de ataque XSS bloqueado:**
   
   ![XSS bloqueado](./Assets/7.png)

La respuesta debería ser un código **403 Forbidden**, indicando que el ataque ha sido bloqueado.

## Conclusión

Este proyecto proporciona un entorno seguro para aplicaciones web mediante la implementación de un **WAF con ModSecurity** en Apache. Bloquea ataques comunes como **XSS, SQL Injection y CSRF**, protegiendo la infraestructura web sin modificar la aplicación en sí.
