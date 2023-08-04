# Automated SAP Installations & Operations

Dentro de este repositorio se encuentra una serie de playbooks para realizar tareas de instalacion y operacion de diferentes productos de SAP

El alcance de las tareas esta separado por diferentes playboos organizados en los siguientes directorios

- SAP INSTALLATIONS
    -- Instalacion SAP Webdispatcher 789 PL0127

    *Para correr instalaciones automatizadas se utiliza el playbook run.yml
    *Es necesario modificar el archivo inventory, agrupando los servidores de acuerdo al rol que ejecutaran (SAPRouter, SAP Web Dispatcher, etc)
    *Esta ejecucion utiliza archivos de media ubicados en el nodo de control ansible, para especificar un ruta diferente
        es necesario modificarla en el archivo playbooks/sap_installations/roles/foundation/tasks/main.yml
    *Ejemplo de ejecucion para este playbook: 
        ansible-playbook -i <inventory_file> --ask-become-pass run.yml (Corre las tareas de los roles foundation & webdispatchers)
    *Ejemplo de ejecucion para este playbook con tags: 
        ansible-playbook -i <inventory_file> --ask-become-pass run.yml --tags webdispatcher (corre las tareas del role webdispatcher)

- SAP OPERATIONS
    -- SAP Webdispatcher 
        --- Stop SAP Webdispatcher
        --- Start SAP Webdispatcher
    * Ejemplo para detener los servicios de SAP Webdispatcher:
        ansible-playbook -i inventory_customer run.yml --ask-pass --tags stop
