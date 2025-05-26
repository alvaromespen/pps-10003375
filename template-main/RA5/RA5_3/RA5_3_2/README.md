# Parte 2: Monitorización de Infraestructura Real

En esta parte, vamos a realizar una monitorización en una infraestructura con dos VM que se encuentran en la misma red, donde:

- Ubuntu Server tiene instalado Prometheus y node_exporter.
- Ubuntu Cliente tiene instalado Grafana para la monitorización y el dashboard de node_exporter.

A continuación, vamos a ver lo que ser ha realizado por partes, empezando por el Ubuntu Server:

Lo primero que vamos a hacer es instalar el node_exporter en el servidor, este es un componente de monitorización para Prometheus que se encarga de exportar métricas del sistema operativo (host) en el que se ejecuta.

Haciendo uso de wget ```bash wget https://github.com/prometheus/node_exporter/releases/download/v1.8.0/node_exporter-1.8.0.linux-amd64.tar.gz```
, obtenemos la herramienta de node_exporter comprimida en .tar.gz, y tras
