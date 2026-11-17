# Laboratorio Ansible con Docker (Segundo Parcial)

## Objetivo de la práctica

Crear un laboratorio con dos servidores Linux (contenedores Ubuntu 24.04 en Docker) y administrarlos con Ansible: verificar la conexión y ejecutar un playbook que muestra información del host, crea directorios y archivos, usa un `loop` y un mensaje condicional (`when`) para Ubuntu.

## Estructura

```
ansible-lab/
├── docker-compose.yml
├── inventory.ini
├── playbook.yml
└── README.md
```

## Comandos para iniciar los contenedores

```bash
docker compose up -d
docker ps

# Instalar Python en cada contenedor (requerido por Ansible)
docker exec -it server1 bash -c "apt update && apt install -y python3"
docker exec -it server2 bash -c "apt update && apt install -y python3"

# Probar la conexión
ansible docker -i inventory.ini -m ping
```

## Comando para ejecutar el playbook

```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Captura de la ejecución exitosa

![Ejecución exitosa del playbook](captura-playbook.png)
