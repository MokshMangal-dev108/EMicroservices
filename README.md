# **EMicroserviceApi**

EMicroserviceApi is a project designed to demonstrate a scalable microservices architecture. This project includes multiple interconnected services: **order-service**, **product-service**, **notification-service**, and **inventory-service**, which work together to create a functional e-commerce system. The project also includes an **API gateway** for managing incoming requests and a **Dockerfile** for containerization.

---

## **Features**

### **Services Overview**
- **Order Service**: Handles product orders and interacts with the inventory service to check stock availability. If the product is in stock, it processes the order and stores it in an SQL database.
- **Product Service**: Allows for the creation and management of product information. It shares a database with the inventory service for fast data retrieval.
- **Inventory Service**: Manages product availability and checks if an item is in stock. It shares a MongoDB database with the product service for quick lookup.
- **Notification Service**: Sends notifications or emails to users about the status of their orders, operating asynchronously with the help of Kafka for efficient messaging.
- **API Gateway**: Serves as the entry point for all incoming requests, checking authorization before forwarding requests to the appropriate service.

### **Technology Stack**
- **Backend Frameworks**: Spring Boot, Java
- **Databases**: 
  - **SQL Database**: Used by the order service for structured data management.
  - **MongoDB**: Used by the product and inventory services for fast data retrieval.
- **Messaging System**: Apache Kafka for asynchronous communication between services.
- **Containerization**: Docker for packaging and managing services.
- **API Gateway**: Handles and routes requests to the appropriate service after authentication.

---

## **Requirements**
To run this project, ensure you have the following installed:

1. **Java** (version 8 or higher)
2. **Maven** (for building and managing dependencies)
3. **Docker** (for containerizing and running the services)
4. **MongoDB** (for the product and inventory services)
5. **SQL Database** (e.g., MySQL or PostgreSQL)
6. **Apache Kafka** (for messaging and notifications)

---

## **Installation Instructions**

### 1. **Backend Services Setup**
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/e-microservice-api.git
   cd e-microservice-api
2. Navigate to each service directory and build it using Maven:
   ```bash
   cd order-service
   mvn clean install
   cd ../product-service
   mvn clean install
   cd ../inventory-service
   mvn clean install
   cd ../notification-service
   mvn clean install
3. Configure the database settings in application.properties or application.yml for each service as needed.

### 2. **Running Services with Docker**
1. Build the Docker images:
  Navigate to the root directory of your project and build the Docker images for each service:
  ```bash
  docker build -t order-service ./order-service
  docker build -t product-service ./product-service
  docker build -t inventory-service ./inventory-service
  docker build -t notification-service ./notification-service

2. Run the containers:
  Run the Docker containers for each service with the following commands:
  ```bash
  docker run -d -p 8081:8081 --name order-service order-service
  docker run -d -p 8082:8082 --name product-service product-service
  docker run -d -p 8083:8083 --name inventory-service inventory-service
  docker run -d -p 8084:8084 --name notification-service notification-service

#### **Start the API Gateway**:
If the API gateway has been containerized, you can start it using the following command:

```bash
docker run -d -p 8080:8080 --name api-gateway api-gateway



