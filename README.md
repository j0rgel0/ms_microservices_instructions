**Final Project**

### Introduction

This project demonstrates the design and implementation of a microservices architecture using a suite of independent services that work together seamlessly.

---

### Utility Services

- **Config Server** (https://github.com/j0rgel0/ms_configserver)
  - Manages centralized configuration for all microservices, ensuring flexibility and consistency.

- **Discovery Server** (https://github.com/j0rgel0/ms_discoveryserver)
  - Built with Netflix Eureka, it facilitates service discovery and dynamic routing.

- **Gateway** (https://github.com/j0rgel0/ms_gateway)
  - Acts as a single entry point for clients, providing routing, load balancing, and security.

---

### Configuration Files

- **Config Files** (https://github.com/j0rgel0/ms_configfiles)
  - Centralized repository for environment-specific configurations, enabling smooth deployment and updates without redeployment.

---

### Core Microservices

- **Auth Service** (https://github.com/j0rgel0/ms_authservice)
  - Handles user authentication and JWT-based authorization.

- **Order Service** (https://github.com/j0rgel0/ms_orderservice)
  - Manages the creation, tracking, and fulfillment of customer orders.

- **Inventory Service** (https://github.com/j0rgel0/ms_inventoryservice)
  - Tracks product availability and updates stock levels based on processed orders.

- **Payment Service** (https://github.com/j0rgel0/ms_paymentservice)
  - Facilitates order payment processing and communicates status updates.

---

### Messaging and Observability

#### Messaging with Kafka
- **Apache Kafka** is used for event-driven communication between microservices.
  - Topics include:
    - `auth-events` for authentication-related events.
    - `order-events` for order creation and updates.
    - `inventory-events` for stock management.
    - `payment-events` for payment processing.
  - Kafka enables reliable, asynchronous communication, improving system resilience and scalability.

#### Observability with Grafana Stack
- **Grafana** provides dashboards for real-time monitoring of system metrics.
- **Loki** aggregates logs from all microservices, enabling centralized log analysis and troubleshooting.
- **Prometheus** is integrated for metrics collection and alerting.
- Observability tools ensure:
  - **Performance Insights:** Identify bottlenecks and optimize services.
  - **Centralized Monitoring:** Unified view of logs, metrics, and service health.
  - **Error Tracking:** Quick identification and resolution of issues.

---
``` 
 ███████ ████████ ███████ ██████  ███████ 
 ██         ██    ██      ██   ██ ██      
 ███████    ██    █████   ██████  ███████ 
      ██    ██    ██      ██           ██ 
 ███████    ██    ███████ ██      ███████
Local Setup Instructions for Microservices    
```                                       
## Prerequisites
Make sure the following tools are installed on your system:
- **Docker**: https://www.docker.com/
- **Docker Compose**: Comes bundled with Docker Desktop.

---

## Installation Steps

### 1. Clone the Required Repositories
Clone the following repositories needed for the setup:

1. **Configuration Files** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_configfiles
   ```
2. **ConfigServer** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_configserver
   ```
3. **DiscoveryServer** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_discoveryserver
   ```
4. **Gateway** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_gateway
   ```
5. **AuthService** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_authservice
   ```
6. **ProductCatalogService** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_productcatalogservice
   ```
7. **InventoryService** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_inventoryservice
   ```
8. **PaymentService** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_paymentservice
   ```
9. **OrdersService** repository:
   ```bash
   git clone https://github.com/j0rgel0/ms_orderservice
   ```

---

### 2. Start Required Containers
- Navigate to the `docker_config` folder within the ConfigServer repository:
  ```bash
  cd ms_configserver/docker_config
  ```
- Use Docker Compose to start all the necessary containers:
  ```bash
  docker-compose up -d
  ```

#### Containers to be Started
The following services will be started by Docker Compose:

1. **Logging & Monitoring:**
   - Loki
   - Promtail
   - Grafana
   - Prometheus
   - Zipkin
   - JSON Exporter

2. **Kafka & Zookeeper:**
   - Kafka
   - Zookeeper
   - Kafdrop

3. **Databases:**
   - `authdb` (PostgreSQL on port `5432`)
   - `orderdb` (PostgreSQL on port `5433`)
   - `inventorydb` (PostgreSQL on port `5434`)
   - `paymentdb` (PostgreSQL on port `5435`)
   - `productcatalogdb` (PostgreSQL on port `5436`)

4. **Redis:**
   - Redis (on port `6379`)

---

### 3. Run the Microservices and Supporting Applications
Follow these steps for each microservice:

1. **ConfigServer**:
   - Open the **ConfigServer** project in your preferred IDE.
   - Run the project. The ConfigServer will start on port `8888`.

2. **DiscoveryServer**:
   - Open the **DiscoveryServer** project.
   - Run the project. The DiscoveryServer will start on its configured port.

3. **Gateway**:
   - Open the **Gateway** project.
   - Run the project. The Gateway will start on its configured port.

4. **AuthService**:
   - Open the **AuthService** project.
   - Run the project. It will use the `authdb` database.

5. **ProductCatalogService**:
   - Open the **ProductCatalogService** project.
   - Run the project. It will use the `productcatalogdb` database.

6. **InventoryService**:
   - Open the **InventoryService** project.
   - Run the project. It will use the `inventorydb` database.

7. **PaymentService**:
   - Open the **PaymentService** project.
   - Run the project. It will use the `paymentdb` database.

8. **OrdersService**:
   - Open the **OrdersService** project.
   - Run the project. It will use the `orderdb` database.

---

## Notes
- Verify all services are running successfully by checking Docker containers:
  ```bash
  docker ps
  ```
- All configuration files (`application.properties`) are managed in the **Configuration Files** repository.
- Ensure each service is properly connected to its database and dependent services.

