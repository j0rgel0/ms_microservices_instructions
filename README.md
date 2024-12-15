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

For a deeper dive into the implementation, workflows, and configurations, visit the linked repositories. Each service repository contains detailed documentation and setup instructions.

