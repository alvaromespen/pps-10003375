# Parte 1: Validación del Stack de Monitorización

Vamos a proceder a implementar el stack básico siguiendo un repositorio de referencia, y haciendo uso de dockers, donde validaremos la correcta instalación y configuración de Prometheus y Grafana, incluyendo las métricas iniciales locales y el funcionamiento general de todo el stack.

El repositorio del que hemos hecho uso es el siguiente:

- [Example_repo](https://github.com/dinesh24murali/example_repo/tree/main/prometheus_grafana_example)

Una vez nos traemos el repositorio a nuestro equipo haciendo uso de git, hacemos un docker compose build para construir las imágenes Docker definidas en un archivo docker-compose.yml.

![I1](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_3/Assets%20-%20Prometheus%20%26%20Grafana/1.png)

Tras realizar el docker compose build, deberíamos realizar una pequeña modificación en el fichero yml, ya que nos generaba un error de configuración al momento de realizar el docker compose up, en el que hemos modificado lo siguiente:

- Modificamos el archivo prometheus.yml incorporando las secciones global y alerting, que inicialmente no estaban presentes o presentaban una estructura incorrecta. Asimismo, ajustamos la sintaxis dentro de scrape_configs, asegurándonos de que todos los targets estuvieran correctamente definidos como listas y con la indentación apropiada. De esta manera conseguimos que Prometheus validara correctamente la configuración y se iniciara sin errores al ejecutar docker compose up.

![I2](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_3/Assets%20-%20Prometheus%20%26%20Grafana/2.png)

Y como podemos observar ya funciona el compose up.

![I3](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_3/Assets%20-%20Prometheus%20%26%20Grafana/3.png)
