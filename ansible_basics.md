# Ejercicio 3

## 1. ¿Qué es Ansible y por qué es "sin agente" (agentless)?
Ansible es un software creado por un extrabajador de Redhat, su propósito es el de automatizar tareas para la administración centralizada de diversos servidores de forma simultánea.
Se conoce como agentless, dado que no requiere la instalación de agentes en cada servidor destino. Sino que este programa envía directamente sus tareas de automatización a través de conexiones SSH con los servidores destino.

## 2. Explica la diferencia entre un comando ad-hoc y un playbook.
Un ad-hoc y un playbook a nivel de ejecución son prácticamente lo mismo. La diferencia radica en la funcionalidad que se le da a cada uno.
Los ad-hoc buscan realizar tareas quizás poco cotidianas, que requieren poco esfuerzo como corroborar si las máquinas responden ping o cuánto tiempo de actividad pueden tener. Estas tareas se realizan mediante la ejecución de comandos manuales para el administrador.

Los Playbook, en su lugar, buscan la automatización de tareas más complejas que pueden requerir la ejecución de múltiples pasos o validar estados antes de ejecutar acciones. Por norma general son tareas que se realizan de forma recurrente.

En definitiva, podríamos realizar las mismas tareas tanto en un escenario como en otro. Pero en su lugar el ad-hoc no se almacena y el playbook es un archivo que almacena las instrucciones que debe ejecutar.

## 3. ¿Qué es la idempotencia y por qué es importante en Ansible?
La idempotencia es la propiedad que garantiza que una operación aplicada múltiples veces produce el mismo resultado que si se ejecutara una sola vez. En Ansible, esto significa que los playbooks deben diseñarse para ejecutar tareas solo si es necesario, sin alterar innecesariamente el sistema.

Esto es importante porque:
- Evita cambios redundantes en los servidores.
- Reduce el riesgo de errores al ejecutar los mismos playbooks varias veces.
- Garantiza consistencia en la configuración de los sistemas.

Un ejemplo de idempotencia en Ansible es el uso del módulo `file` para garantizar que un directorio existe. Si el directorio ya está presente, Ansible no lo recreará ni generará cambios innecesarios.

## 4. ¿Cómo funcionan los handlers y cuándo deberías usarlos?
Los Handlers son variables que se ejecutan solo si una tarea que se cumplió tiene como orden de tareas llamar a esta variable una vez realizada una acción. Un dato no menor es que los handlers se ejecutan una vez termina el orden de tareas que tiene el código. Así que por mucho que esté en la primera línea, si es llamado no se ejecutará hasta finalizar la serie de pasos que el código tenga.

Se utilizan en varias situaciones. Por ejemplo, cuando se modifica un archivo de configuración de un servicio y se debe reiniciar el mismo, o cuando se realiza una tarea que requiere el reinicio del sistema operativo, entre otras.

## 5. ¿Cómo verificas errores de sintaxis en un playbook de Ansible?
Para verificar errores de sintaxis en un playbook de Ansible, podemos utilizar el siguiente comando:
```sh
ansible-playbook playbook.yml --syntax-check
