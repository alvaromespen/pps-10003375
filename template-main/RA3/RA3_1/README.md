# Apache Hardening

*Introducción *
A lo largo de esta práctica veremos cómo fortalecer la seguridad de Apache mediante diversas configuraciones y módulos de protección. Implementaremos medidas como la deshabilitación del módulo autoindex, la configuración de cabeceras de seguridad (HSTS y CSP) y la integración de un Web Application Firewall (WAF) con ModSecurity y reglas OWASP. También configuraremos el módulo mod_evasive para mitigar ataques de denegación de servicio (DoS) y restringiremos accesos para mejorar la seguridad. Finalmente, encapsularemos todas estas configuraciones en una imagen Docker, asegurando una implementación segura y reproducible.


# Tasks

* [TASK_1](#URL_TASK_1): XXX
* [TASK_2](#URL_TASK_2): XXX

# Task_1

Intro...

![IMG](URL_IMG)

Example code:

```
$ git clone https://github.com/openssh/openssh-portable
$ patch -p1 < ~/path/to/openssh.patch
$ autoreconf
$ ./configure
$ make
```

# Task_2
