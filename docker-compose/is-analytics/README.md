# WSO2 Identity Server with Analytics

Runs a pre configured Identity Server container and Identity Server Analytics container.

## Prerequisites

 * [Docker](https://www.docker.com/get-docker) and [Docker Compose](https://docs.docker.com/compose/install/#install-compose) are required for running this Docker Compose file.

## How to deploy

  1. Pull WSO2 Identity Server and Identity Server Analytics Docker images or build them:

     * [Identity Server Dockerfile](../../dockerfiles/is/README.md)
     * [Identity Server Analytics Dockerfile](../../dockerfiles/is-analytics/README.md)

  2. Pull MySQL Docker image:
     ```
     docker pull mysql:5.7.19
     ```

  3. Download the latest Identity Server Docker resources release zip file from the [releases](https://github.com/wso2/docker-is/releases) page or clone this repository and switch to the latest tag.

  4. Switch to the docker-compose/is-analytics folder:
     ```
     cd [docker-is]/docker-compose/is-analytics
     ```

  5. Download [MySQL Connector/J](https://downloads.mysql.com/archives/c-j/) v5.1.35 and copy its JAR file to the following path:
     ```
     cp path/to/mysql-connector-java-5.1.35/mysql-connector-java-5.1.35-bin.jar [docker-is]/docker-compose/is-analytics/identity-server/repository/components/lib/
     cp path/to/mysql-connector-java-5.1.35/mysql-connector-java-5.1.35-bin.jar [docker-is]/docker-compose/is-analytics/identity-server-analytics/repository/components/lib/
     ```

  6. Execute the following Docker Compose command to start the deployment:
     ```
     docker-compose up
     ```

  7. Once the deployment process is complete add a host entry pointing to the Docker host machine IP address. For an example if the Docker host is accessible via 127.0.0.1 on a Linux or Mac machine, add the following entry in /etc/hosts file:

     ```
     127.0.0.1 wso2is
     127.0.0.1 wso2is-analytics
     ```

  8. Access the Identity Server carbon console using the below URL via a web browser:
     ```
     https://wso2is/carbon
     ```
  9. Access the Identity Server Analytics portal using the below URL via a web browser:
     ```
     https://wso2is-analytics:9444/portal/dashboards/IsAnalytics-AuthenticationData/
     ```

  10. When configuring an application with Identity Server, use the following properties
      * IdPEntityId - wso2is
