# POC ANGULAR KEYCLOAK
The goal of this POC is to configure security layer to establish secure oauth2 connection between angular front end application and spring boot resource server 

## Necessary tools to build and launch POC SPRING LDAP project

- [JDK 21.0.2](https://jdk.java.net/21/)
- [Maven 3](https://maven.apache.org)
- [Docker Desktop](https://docs.docker.com/get-started/overview/)
- [Node.js v22.12.0(LTS)](https://nodejs.org/en/download)

## Keycloak server and PostgreSQL database management

- A Keycloak authorization server, and a PostgreSQL database can be launched with the following files: ``./docker/docker-compose.yaml``
- Create the containers using the following command line executed from the ``./docker`` folder: ``docker-compose up -d``
- A Keycloak admin interface is accessible at http://localhost:8080
- Access the PostgreSQL database using the following command: ``psql --username=pocdb  --dbname=pocdb``
- You can initialize ``t_poc_vhl_vehicle`` table with ``./docker/data/t_poc_vhl_vehicle.csv`` content: ``\COPY poc.t_poc_vhl_vehicle from '/absolute/path/t_poc_vhl_vehicle.csv' with (null 'NULL', format CSV, ENCODING 'UTF-8');``
- Create a snapshot of keycloak server content with the following command: ``docker cp keycloak:/opt/keycloak/data/h2 ./h2-keycloak-sv``
- Delete the containers using the following command line executed from the ``./docker`` folder: ``docker-compose down``

## A series of command lines to use to launch POC SPRING LDAP application
### Package and launch back-end application
Execute the following command lines in project folder:
- ``mvn clean package``
- ``java -jar ./target/jar_file_name.jar``
### launch front-end application
Execute the following command lines in ``./src/main/js/front_end``:
- ``npm install``
- ``npm run start``
### Package and launch both back-end and front-end application
- ``mvn clean package -P prod``
- ``java -jar ./target/jar_file_name.jar``
