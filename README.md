# Gateway Server Microservice (gateway-server)

## Description

The Gateway Server is the main entry point for the microservices ecosystem. It handles external requests, routes traffic to the appropriate services, and applies security policies such as authentication and authorization. Additionally, it can manage load balancing and acts as a mediator to optimize communications.

## Pre - requisites

- **Java 20**
- **Maven**
- **Docker** (for Docker execution only)
- Red Docker compartida: `my-network`


## Initial Configuration

### Run Locally

#### Modify the file`bootstrap.yml`

Configure the active profile to use Docker:

```yaml
spring:
  profiles:
    active: local
```

#### Execute the Main Class

```yaml
mvn spring-boot:run
```

### Run Docker

#### Modify the file`bootstrap.yml`

Configure the active profile to use Docker:

```yaml
spring:
  profiles:
    active: docker
```
#### Compile and generate the Docker container
Build the Docker image with:

```yaml
docker build -t gateway-server:0.0.1-SNAPSHOT .
```

####  Run the microservice Docker container
Start the container with:

```yaml
docker run --name gateway-server --network my-network -p 8008:8008 gateway-server:0.0.1-SNAPSHOT
```

## Notes:
- **If you need to change ports or other settings, edit the corresponding application.yml and Dockerfile files.**
- **To debug errors, check the container logs:**
    ```yaml
    docker logs gateway-server
    ``` 
- **Make sure that the Config Server and Registry Server are running before starting other services.**
