# Introducción

A lo largo de la siguiente parte de la práctica veremos cómo realizar la instalación, configuración y validación de un clúster K3s en modo HA (High Availability). Este tipo de arquitectura permite garantizar la disponibilidad del plano de control mediante la distribución del mismo entre varios nodos. 

Implementaremos un servicio nginx con 2 réplicas con HA, lo que nos permitirá comprobar tanto la correcta distribución de la carga como la tolerancia a fallos dentro del clúster. Además, utilizaremos K9s para supervisar el estado de los recursos y facilitar la gestión visual en tiempo real del entorno Kubernetes.
