# Eureka Server for Quiz and Question Microservices

This repository contains the Eureka Server for managing the microservices architecture of the quiz application, including the `quiz-service` and `question-service`.

## Overview

Eureka Server is used for service discovery, allowing microservices to register themselves and discover other services. This setup simplifies communication between microservices, provides load balancing, and enhances fault tolerance.

## Technologies Used

- **Eureka Server**: A service registry for service discovery.
- **Spring Boot**: A framework for building microservices and RESTful APIs.
- **PostgreSQL**: A relational database management system used by the microservices.

## Architecture

The system consists of the following components:

- **Eureka Server**: This server acts as the service registry where microservices can register themselves and discover other services.
- **Quiz Service**: A microservice responsible for managing quizzes.
- **Question Service**: A microservice responsible for managing questions related to the quizzes.

## Prerequisites

- Java 17 or later
- Maven 3.6 or later
- PostgreSQL 13 or later
- Spring Boot 3.x
- Eureka Server
- Docker (optional, for containerization)

## Getting Started

### Clone the Repository

```bash
git clone <repository-url>
cd eureka-server
```

### Configuration

1. **Eureka Server Configuration**:
   Update the `application.yml` or `application.properties` file with the appropriate configurations for the Eureka Server.

   ```yaml
   server:
     port: 8761

   eureka:
     client:
       register-with-eureka: false
       fetch-registry: false
     instance:
       hostname: localhost
     server:
       enable-self-preservation: false
   ```

2. **PostgreSQL Configuration**:
   Ensure that the `quiz-service` and `question-service` microservices are configured to connect to a running PostgreSQL instance. Update the database URL, username, and password in their respective configuration files.

### Running the Eureka Server

To start the Eureka Server, run the following command from the root directory:

```bash
mvn spring-boot:run
```

Alternatively, you can package the application as a JAR and run it:

```bash
mvn clean package
java -jar target/eureka-server-0.0.1-SNAPSHOT.jar
```

### Accessing the Eureka Dashboard

Once the Eureka Server is up and running, you can access the Eureka Dashboard at:

```
http://localhost:8761/
```

### Registering Microservices

Ensure that the `quiz-service` and `question-service` microservices are configured with the Eureka Client dependencies and are pointing to the Eureka Server URL (`http://localhost:8761/eureka/`). Upon starting, they will register themselves with the Eureka Server.

## Docker Support

You can also run the Eureka Server using Docker:

### Build Docker Image

```bash
docker build -t eureka-server .
```

### Run Docker Container

```bash
docker run -d -p 8761:8761 --name eureka-server eureka-server
```

## Troubleshooting

- **Eureka Server Not Accessible**: Check if the server is running on the correct port and accessible via the configured URL.
- **Microservices Not Registering**: Ensure that microservices are running, Eureka Client dependencies are correctly configured, and the Eureka Server URL is set correctly in their configuration.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or issues, please contact shakib at shakibhasann522@gmail.com
