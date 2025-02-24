Configuración Segura de Apache con Docker

Este repositorio documenta los pasos seguidos para configurar un servidor Apache seguro con Docker, incluyendo la implementación de HSTS, CSP, deshabilitación de autoindex y la instalación de certificados SSL.

🔧 Pasos Realizados

1️⃣ Configuración de Apache

Se modificó la configuración de Apache para ocultar la firma del servidor, agregando las siguientes líneas en /etc/apache2/apache2.conf:

ServerTokens ProductOnly
ServerSignature Off

2️⃣ Implementación de HSTS

HTTP Strict Transport Security (HSTS) ayuda a evitar ataques como MITM. Se configuró en el archivo del host virtual (sslapache.sec.conf):

<VirtualHost *:443>
    ServerAdmin administrador@apachesec.mylocal
    ServerName apachesec.mylocal
    DocumentRoot /var/www/html

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/apache.crt
    SSLCertificateKeyFile /etc/ssl/private/apache.key

    Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains"
</VirtualHost>

📸 Captura de configuración HSTS: Enlace a captura

3️⃣ Configuración de CSP

Para mitigar ataques XSS y otros, se configuró la cabecera Content-Security-Policy en el archivo de configuración de Apache:

Header set Content-Security-Policy \
    "default-src 'self'; \
    img-src *; \
    media-src media1.com media2.com; \
    script-src userscripts.example.com"

📸 Captura de configuración CSP: Enlace a captura

4️⃣ Deshabilitación del Módulo autoindex

Para evitar la lista de directorios en Apache, se deshabilitó el módulo con el siguiente comando:

a2dismod autoindex
service apache2 restart

📸 Captura de deshabilitación de autoindex: Enlace a captura

5️⃣ Creación del Dockerfile

Se creó un Dockerfile para automatizar la configuración de Apache:

FROM ubuntu:latest

# Instalación de Apache y nano
RUN apt-get update && apt-get -y install apache2 nano

# Copia de archivos de configuración y contenido
COPY apachesec.html /var/www/html
COPY www.apache.sec.conf /etc/apache2/sites-available/

# Exposición del puerto 80
EXPOSE 80

# Inicio del servicio Apache en primer plano
CMD ["apachectl", "-D", "FOREGROUND"]

📸 Captura del Dockerfile y su ejecución: Enlace a captura

✅ Verificación de la Configuración

Verificar que el servidor responde correctamente con:

curl -I https://localhost --insecure

Se debe obtener un código 200 OK y las cabeceras configuradas.

Probar la página web accediendo a https://apachesec.mylocal en el navegador.

📸 Captura de la web funcionando: Enlace a captura
📸 Captura de la configuración SSL y certificado: Enlace a captura
