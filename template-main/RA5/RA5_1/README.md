# Jenkins

**Introducción**

A lo largo de esta práctica nos proponemos diseñar y poner en marcha una pipeline de integración continua utilizando Jenkins, Docker y Docker Compose. Nuestro objetivo principal es automatizar el ciclo de vida de una aplicación, desde la construcción de su imagen hasta la ejecución de pruebas, todo ello dentro de un entorno controlado y reproducible mediante contenedores. No obstante, primero lo realizaremos de manera básica y posteriormente ya haremos uso de jenkinsfile.docker.

A lo largo del proceso, configuraremos Jenkins para clonar un repositorio, construir la imagen Docker de la aplicación, ejecutar los contenedores necesarios y realizar pruebas automatizadas sobre el entorno desplegado. 

# Parte 1: Creación de los programas de python:

Para este caso, hemos creado una calculadora que se centre en multiplicar números (calculadora.py) y una serie de pruebas unitarias para realizar pruebas (test_calculator.py), los cuáles son los siguientes:



![image](https://github.com/user-attachments/assets/12eed50c-e8c6-4ca3-9262-90da07940dfa)

![image](https://github.com/user-attachments/assets/c03a1550-c54a-482d-be47-ecffa3653718)

![image](https://github.com/user-attachments/assets/8b95dbcb-8348-49cc-ab7f-74452e769169)
