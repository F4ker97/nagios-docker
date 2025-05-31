# Nagios Core en Docker

Este repositorio contiene los archivos necesarios para construir una imagen Docker personalizada de **Nagios Core**, lista para ejecutar localmente con Apache y supervisada por runit.

---

## Requisitos

- Docker instalado en tu sistema (Docker Desktop en Windows o Docker Engine en Linux)
- Terminal (como Git Bash o PowerShell)

---

## Pasos para construir la imagen

1. Clona este repositorio (si es remoto) o ubica el `Dockerfile` y el directorio `overlay/` en una misma carpeta:

git clone https://github.com/F4ker97/nagios-docker.git
cd nagios-docker

2. Construye la imagen Docker:

docker build --no-cache -t nagios-core .

## Pasos para ejecutar el contenedor

1. Una vez construida la imagen, puedes ejecutarla con:

docker run -d -p 8080:80 --name nagios-core nagios-core

Este comando:

Inicia Nagios y Apache en segundo plano
Mapea el puerto 80 del contenedor al localhost:8080

## Acceso a la interfaz web

1. Abre tu navegador y accede a:

http://localhost:8080

Credenciales por defecto:

Usuario: nagiosadmin
Contraseña: nagios

## Estructura del proyecto

nagios-docker/
├── Dockerfile
├── overlay/
│   ├── etc/sv/apache/run
│   ├── etc/sv/nagios/run
│   ├── etc/sv/rsyslog/run
│   └── usr/local/bin/start_nagios
└── README.md

## Como detener el contenedor

docker stop nagios-core

Si se desea eliminar completamente, ejecuta:

docker rm nagios-core