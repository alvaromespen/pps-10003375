# Parte 2: Monitorización de Infraestructura Real

En esta parte, vamos a realizar una monitorización en una infraestructura con dos VM que se encuentran en la misma red, donde:

- Ubuntu Server tiene instalado Prometheus y node_exporter.
- Ubuntu Cliente tiene instalado Grafana para la monitorización y el dashboard de node_exporter.

#Ubuntu Server

A continuación, vamos a ver lo que ser ha realizado por partes, empezando por el Ubuntu Server:

Lo primero que vamos a hacer es instalar el node_exporter en el servidor, este es un componente de monitorización para Prometheus que se encarga de exportar métricas del sistema operativo (host) en el que se ejecuta.

Haciendo uso de ```wget https://github.com/prometheus/node_exporter/releases/download/v1.8.0/node_exporter-1.8.0.linux-amd64.tar.gz```, obtenemos la herramienta de node_exporter comprimida en tar.gz, y tras eso, añadimos el node exporter a los binarios del usuario, además hemos creado un usuario llamado node_exporter para modificar posteriormente los permisos.

Una vez realizado lo anterior, vamos a añadir los siguientes contenidos al siguiente fichero, para que de esta manera podamos habilitar y correr el servicio de node_exporter:

![I10](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_3/Assets%20-%20Prometheus%20%26%20Grafana/10.png)

Su función general es garantizar que node_exporter se inicie automáticamente al arrancar el sistema, después de que la red esté disponible, y que se ejecute bajo un usuario no privilegiado por seguridad, ejecutando el binario desde su ubicación correspondiente. 

Tras esto, habilitamos y corremos el servicio y si ejecutamos el curl desde localhost o desde un equipo de la red, vemos que funciona a la perfección.

![I11](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_3/Assets%20-%20Prometheus%20%26%20Grafana/11.png)
![I12](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_3/Assets%20-%20Prometheus%20%26%20Grafana/12.png)
