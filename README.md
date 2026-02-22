# integration-sonarqube-docker
# Título
Integración de SonarQube en Docker

## Comenzando 🚀
_Estas instrucciones te permiten obtener una copia del proyecto en funcionamiento en tu máquina local para propósitos de desarrollo y pruebas._

### Pre-requisitos 📋
_Que cosas necesitas para instalar el software y como instalarlas_
- Manejar la consola de CMD para la ejecución de comandos.
- Manejar el editor Notepad o Bloc de Notas para la creación de los archivos de despliegue.


### Instalación 🔧 Pruebas ⚙️ y Despliegues 📦
Integración de SonarQube en Docker:
Vamos a necesitar dos imágenes Docker: una para el servidor SonarQube y otra para la base de datos, en este caso PostgreSQL. Concretamente, las imágenes que vamos a utilizar son la imagen oficial de SonarQube (sonarqube) y la imagen oficial de PostgreSQL (postgres).
- https://hub.docker.com/_/sonarqube/ -> enlace a la imagen de sonarqube
- https://hub.docker.com/_/postgres/ -> enlace a la imagen de postgres
Instalamos las imágenes:
- docker pull sonarqube -> comando para instalar imágenes, que se encuentran en la página oficial de docker.
- docker pull postgres

Instalación de SonarQube utilizando docker-compose:
- Para facilitar la instalación de SonarQube en contenedores Docker vamos a utilizar el comando docker-compose up -d.
- Se puede ver el fichero docker-compose.yaml que describe cómo se van a ejecutar los contenedores, pero primero hay que crearlo.
- Creamos el fichero docker-compose.yaml en una carpeta que creamos en C: llamada opt – Docker – sonar


version: "3"

services:
  sonarqube:
    image: sonarqube:8.2-community
    expose:
      - 9000
    ports:
      - "127.0.0.1:9000:9000"
    networks:
      - sonarnet
    environment:
      - SONARQUBE_JDBC_URL=jdbc:postgresql://db:5432/sonar
      - SONARQUBE_JDBC_USERNAME=sonar
      - SONARQUBE_JDBC_PASSWORD=sonar
    volumes:
      - sonarqube_conf:/opt/sonarqube/conf
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_extensions:/opt/sonarqube/extensions
      - sonarqube_bundled-plugins:/opt/sonarqube/lib/bundled-plugins
    deploy:
      resources:
        limits:
          cpus: '0.001'
          memory: 500M
        reservations:
          cpus: '0.0001'
	  memory: 200M

db:
  image: postgres
  networks:
    - sonarnet
  environment:
    - POSTGRES_USER=sonar
    - POSTGRES_PASSWORD=sonar
  volumes:
    - postgresql:/var/lib/postgresql
    - postgresql_data:/var/lib/postgresql/data


En el cmd nos situamos en la carpeta del fichero docker-compose.yaml y ejecutamos el comando docker-compose up –d y nos instala Sonar.
