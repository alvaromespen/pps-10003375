# Introduccion

A lo largo del siguiente documento veremos cómo automatizar la provisión y configuración de una máquina virtual Ubuntu 22.04, en nuestro caso hemos hecho uso de la version 22.04, ya que en ciertas ocasiones la versión 24.04, aún no se encuentra disopnible en ciertos repositorios de imágenes, utilizando herramientas de Infraestructura como Código (IaC), integrando Terraform y Ansible para lograr un entorno reproducible y gestionado de forma eficiente.

Terraform es una herramienta que permite definir y desplegar infraestructura mediante archivos de configuración escritos en HCL (HashiCorp Configuration Language). Su enfoque declarativo y su compatibilidad con múltiples plataformas hacen posible crear entornos complejos de forma automatizada, segura y predecible.

Ansible es una herramienta de automatización de configuración que permite gestionar y configurar sistemas a través de archivos YAML llamados playbooks, sin necesidad de instalar agentes en los nodos. Es ideal para instalar servicios, aplicar parches o desplegar aplicaciones en servidores ya aprovisionados.

No obstante, mientras desarrollábamos esta práctica, recibimos una serie de problemas con Terraform, debido a que el origen de los proveedores no eran oficiales, lo que generaba un sinfin de errores debido a estos, finalmente conseguimos hacer con Terraform que se crearan las VM, pero seguía generando errores, en este caso, eran errores con los adaptadores de red, que al no generarlos como tocaba, simplemente los convertía en datos y no realizaba nada más, tras haber investigado, no hemos podido descubrir como solucionarlo, por lo que hemos tenido que utilizar Vagrant como backend de virtualización, ¿Pero que es Vagrant?

Vagrant es una herramienta que facilita la creación y gestión de entornos de desarrollo virtualizados. Se integra fácilmente con VirtualBox y otras plataformas, permitiendo levantar máquinas virtuales de manera automatizada y sencilla.

# Parte 1: Provisionar una máquina virtual Ubuntu 24.04 en Virtualbox mediante Terraform

En esta parte tenemos que realizar solo la implementación de la VM para que se encuentre funcional y podamos acceder de manera remota con SSH, para ello hemos hecho uso de el fichero main.tf, el cuál lo único que hacer es decir que el proveedor se ejecutará de manera local, y lo que hará será llamar a vagrant up para que ejecute el fichero Vagrantfile y de esa manera se automatice la creación de la VM, los ficheros utilizados son los siguientes:

- [main.tf](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_2/main.tf)
- [Vagrantfile](https://github.com/alvaromespen/pps-10003375/blob/main/template-main/RA5/RA5_2/Vagrantfile)

En este caso, la configuración del Vagrantfile en este apartado era solo hasta el primer comentario en el fichero, sin incluirlo, ya que lo único que queríamos conseguir es que se automatizara la creación de la VM.

Una vez con ambos ficheros creados, y en su directorio, vamos a inicializar el Terraform, y tras eso, ejecutaremos su contenido con *apply*, de esta manera se ejecutará el vagrant up y se creará la VM como vemos a continuación.

![I1](./Assets/1.png)
![I2](./Assets/2.png)
![I3](./Assets/3.png)
