# Obligatorio de Taller Linux 2025
Este es un proyecto creado con la finalidad de poner en práctica el conocimiento adquirido en el transcurso del taller de servidores linux.

Utilizando el conocimiento adquirido en la creación de servidores y la automatización de tareas utilizando herramientas como Ansible y documentando el procedimiento en repositorios de GitHub.

# Sistemas Operativos
En este caso particular únicamente utilizaremos servidores Centos y Ubuntu.

|     SO         |           Dependencias        |     Comentarios                  |
|----------------|-------------------------------|----------------|
|CentOS          |`"ansible.posix"`              |Lo utilizaremos para manejar el firewall en CentOS.
|Ubuntu          |`"communit.general"`           |Lo utilizaremos para manejar el firewall en Ubuntu.

## Diagrama Básico.

Este diagrama dará una idea basica de como funcionara la implementación:
```mermaid
graph LR
A[Basetion-Server Primario] --> B{Ansible}
B -- Conexión SSH--> C((CentOS))
B -- Conexión SSH--> D((Ubutu))
E((Playbook))-->A
F((ad-hoc))-->A
