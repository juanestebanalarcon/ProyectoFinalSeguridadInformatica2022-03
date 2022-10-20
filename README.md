# Proyecto final **Seguridad Informática**

## Integrantes:

* Juan Esteban Alarcón Miranda
* Juan Diego Caicedo Rojas
* Juan Pablo Mora Sarria

## Sobre el proyecto:

Este proyecto está enfocado a la implementación de un firewall utilizando Centos 7.9 como distribución, en ese orden de ideas, se implementará 
un servicio Firewall el cual, a través de este la máquina anfitrión podrá acceder a un servicio FTP y una página web a través de un servicio seguro HTTP, los servicios antes mencionados estarán alojados en dos máquinas independientes respectivamente, en este repositorio encontrará los archivos de configuración necesarios para desarrollar dicho proyecto, presentación y video demostrativo.

### Tecnologías:
    - Vagrant
    - Oracle VirtualBox
### Sistemas Operativos: 
    - Centos 7.9
### Servicios a implementar:
    - Firewall
    - FTP
    - HTTPS
### Estructura planteada:

![ArquitecturaProyecto](FinalArquitectura.png)

### Vagrantfile:

```bash

Vagrant.configure("2") do |config|
config.vm.define :vmftp do |vmftp|
vmftp.vm.box = "bento/centos-7.9"
vmftp.vm.network :private_network, ip: "192.168.50.2"
vmftp.vm.hostname = "vmftp"
end

config.vm.define :vmhttp do |vmhttp|
vmhttp.vm.box = "bento/centos-7.9"
vmhttp.vm.network :private_network, ip: "192.168.50.3"
vmhttp.vm.hostname = "vmhttp"
end

config.vm.define :firewall do |firewall|
firewall.vm.box = "bento/centos-7.9"
firewall.vm.network :public_network, ip: "192.168.1.100"
firewall.vm.network :private_network, ip: "192.168.50.4"
firewall.vm.network :forwarded_port, guest: 80, host: 5000
firewall.vm.hostname = "firewall"
end

end
```