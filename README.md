# Obligatorio de Taller Linux 2025
Este es un proyecto creado con la finalidad de poner en practica el conocimiento adquirido en el transcurso del taller de servidores linux.

Utilizando el conocimiento adquirido en la creación de servidores y la automatizacion de tareas utilizando herramientas como Ansible y documentando el procedimiento en repositorios de GitHub.

# Sistemas Operativos
En este caso particular unicamente utilizaremos servidores Centos y Ubuntu.

|     SO         |           Dependencias        |     Comentarios                  |
|----------------|-------------------------------|----------------|
|CentOS          |`"ansible.posix"`              |Dentro de sus funciones , lo implementaremos para manejar el firewall en CentOS.
|Ubuntu          |`"communit.general"`           |Dentro de sus funciones , lo implementaremos para manejar el firewall en Ubuntu.

## Diagrama Basico.

Este diagrama dara una idea basica de como funcionara la implementación:
```mermaid
graph LR
A[Basetion-Server Primario] --> B{Ansible}
B -- Conexión SSH--> C((CentOS))
B -- Conexión SSH--> D((Ubutu))
E((Playbook))-->A
F((ad-hoc))-->A
