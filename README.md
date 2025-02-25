#  Obligatorio Taller de Servidores Linux
Este es un proyecto creado con la finalidad de poner en práctica el conocimiento adquirido en el transcurso del taller de servidores linux.

Utilizando el conocimiento adquirido en la creación de servidores y la automatización de tareas utilizando herramientas como Ansible y documentando el procedimiento en repositorios de GitHub.

## Requerimientos

1) Un Servidor primario desde donde haremos los deployment.
 2) Acceso a travez de **SSH** a las maquinas destino a las que queremos llegar con nuestros playbook.
 3) Se asume que se trabajara con el mismo usuario **sysadmin** en todas las maquinas.

## Como utilizar este repositorio:
```bash
#Instalamos Git para poder copiar el repositorio
sudo dnf install git

#Instalamos ansible
sudo dnf install ansible-core
```

```bash
#Nos vomevos al direcotrio donde querramos tener la raiz del repositorio y ejecutamos:
git clone https://github.com/Smile0010/Taller_Linux_2025.git
cd Taller_Linux_2025
```
#### **Importante:**
Modificar las IP's utilizadas en los archivos /inventory/servers.ini y /playbook/web_setup.yml

Particularmente dentro de  web_setup.yml:
```ini
  - name: Agregar virtualHost
    ansible.builtin.lineinfile:
     path: /etc/hosts
     line: "10.10.1.12 www.ejemplo.com.uy"
     state: present
    delegate_to: localhost
    connection: local
```
## Instalacion de dependencias:

```bash
#Este comando instalara todos los modulos necesarios para hacer uso de estos playbooks.
ansible-galaxy install -r collections/requirements.yml
```

## Ejecucion de Playbooks.

web_setup.yml:
```bash
#Solicitara la clave del usuario sysadmin luego de su ejecucion.
ansible-playbook -i inventory/servers.ini playbook/web_setup.yml --ask-become-pass
```

hardening.yml:
```bash
#Solicitara la clave del usuario sysadmin luego de su ejecucion.
ansible-playbook -i inventory/servers.ini playbook/hardening.yml --ask-become-pass
```
