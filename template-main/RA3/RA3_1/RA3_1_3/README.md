# 3.1.3. Apache Hardening Best Practices

Este repositorio contiene un Dockerfile configurado para mejorar la seguridad del servidor Apache, aplicando mejores prácticas de seguridad.

## Descripción

El archivo [Dockerfile](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA3/RA3_1/RA3_1_3/Apache%20_Hardening%20_Best%20_Practices/Dockerfile) en este repositorio implementa varias medidas de seguridad para endurecer un servidor web Apache en un entorno Docker.

## Configuraciones de Seguridad Aplicadas

Las siguientes configuraciones han sido implementadas en el Dockerfile:

1. **Deshabilitar métodos HTTP inseguros**: Solo se permiten los métodos `GET` y `POST`, denegando cualquier otro método HTTP.
2. **Deshabilitar el listado de directorios**: Se eliminan las opciones que permiten listar el contenido de directorios.
3. **Ejecutar Apache con un usuario sin privilegios**: Se crea un usuario sin privilegios `apache` para evitar la ejecución como `root`.
4. **Proteger la configuración del sistema**: Se desactiva `AllowOverride All` para evitar sobrescrituras inseguras.
5. **Deshabilitar el rastreo de solicitudes HTTP**: Se usa `TraceEnable off` para evitar ataques de tipo Cross-Site Tracing (XST).

## Capturas de Pruebas de Seguridad

Las siguientes pruebas fueron realizadas para verificar las configuraciones de seguridad:

- **Redirección forzada a HTTPS**
  
  ![Redirección HTTPS](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA3/RA3_1/RA3_1_3/Apache%20_Hardening%20_Best%20_Practices/10.png)

- **Métodos HTTP restringidos (DELETE y PUT)**
  ![Métodos HTTP restringidos](./mnt/data/11.png)

- **Verificación de ejecución con usuario apache**
  ![Ejecución usuario Apache](./mnt/data/12.png)

- **Método TRACE deshabilitado**
  ![Método TRACE deshabilitado](./mnt/data/13.png)

## 🏗 Construcción y Ejecución del Contenedor

Para construir y ejecutar el contenedor con Apache endurecido, sigue estos pasos:

```sh
# Construir la imagen
docker build -t apache-secure .

# Ejecutar el contenedor
docker run -d -p 80:80 -p 443:443 --name apache-secure apache-secure
```

## 📖 Referencias

Para más información sobre prácticas de seguridad en Apache, consulta el siguiente artículo:

🔗 [Best Practices for Securing Apache Web Server](https://geekflare.com/cybersecurity/apache-web-server-hardening-security/)

