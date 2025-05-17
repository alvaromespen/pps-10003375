# Introduccion

A lo largo de la siguiente práctica veremos cómo automatizar la provisión y configuración de una máquina virtual Ubuntu 22.04, en nuestro caso hemos hecho uso de la version 22.04, ya que en ciertas ocasiones la versión 24.04, aún no se encuentra disopnible en ciertos repositorios de imágenes, utilizando herramientas de Infraestructura como Código (IaC), integrando Terraform y Ansible para lograr un entorno reproducible y gestionado de forma eficiente.

Terraform es una herramienta de IaC desarrollada por HashiCorp que permite definir y desplegar infraestructura mediante archivos de configuración escritos en HCL (HashiCorp Configuration Language). Su enfoque declarativo y su compatibilidad con múltiples plataformas hacen posible crear entornos complejos de forma automatizada, segura y predecible.

Ansible es una herramienta de automatización de configuración desarrollada por Red Hat, la cuál permite gestionar y configurar sistemas a través de archivos YAML llamados playbooks, sin necesidad de instalar agentes en los nodos. Es ideal para instalar servicios, aplicar parches o desplegar aplicaciones en servidores ya aprovisionados.

No obstante, mientras desarrollábamos esta práctica, recibimos una serie de problemas con Terraform, debido a que el origen de los proveedores no eran oficiales, lo que generaba un sinfin de errores debido a estos, finalmente conseguimos hacer con Terraform que se crearan las VM, pero seguía generando errores, en este caso, eran errores con los adaptadores de red, que al no generarlos como tocaba, simplemente los convertía en datos y no realizaba nada más, tras haber investigado, no hemos podido descubrir como solucionarlo, por lo que hemos tenido que utilizar Vagrant como backend de virtualización, ¿Pero que es Vagrant?

Vagrant es una herramienta que facilita la creación y gestión de entornos de desarrollo virtualizados. Se integra fácilmente con VirtualBox y otras plataformas, permitiendo levantar máquinas virtuales mediante un solo comando y asegurando que todos los desarrolladores trabajen con el mismo entorno base.
