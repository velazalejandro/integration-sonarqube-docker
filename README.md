# integration-sonarqube-docker
# Título
Integración de SonarQube en Docker

## Comenzando 🚀
_Estas instrucciones te permiten obtener una copia del proyecto en funcionamiento en tu máquina local para propósitos de desarrollo y pruebas._

### 🛠️ Tecnologías utilizadas
- Consola de CMD para la ejecución de comandos
- Editor Notepad o Bloc de Notas para la creación de los archivos de despliegue
- Docker Compose


### Instalación 🔧 Pruebas ⚙️ y Despliegues 📦
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



En el cmd nos situamos en la carpeta del fichero docker-compose.yaml y ejecutamos el comando docker-compose up –d y nos instala Sonar.


## Licencia 📄
Bajo licencia GNU General Public License v3.0


## Autor
Alejandro Velaz

🎓 Formación: ASIR
