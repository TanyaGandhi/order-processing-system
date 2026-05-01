# Order Processing System

An event-driven microservices-based order processing system designed to demonstrate scalable backend architecture, asynchronous communication, and performance optimization techniques.

---

## 🚀 Overview

This project simulates a real-world e-commerce backend using an event-driven architecture.
Each service is independently deployable and communicates via asynchronous messaging using Apache Kafka.

The system is designed with a focus on:

* Scalability
* Resilience
* Performance optimization
* Clean microservices architecture

---

## 🧱 Architecture

### High-Level Flow

1. Order is created via REST API
2. Order Service publishes `order.created` event
3. Payment Service processes payment and emits result
4. Inventory Service updates stock
5. Notification Service consumes events and sends updates

---

## ⚙️ Tech Stack

* Java 17
* Spring Boot
* Apache Kafka
* Maven
* Docker
* PostgreSQL (optional)
* Redis (for caching – optional)

---

## 📦 Microservices

### 1. Order Service

* Handles order creation
* Publishes `order.created` event

### 2. Payment Service

* Consumes `order.created`
* Simulates payment processing
* Publishes:

  * `payment.success`
  * `payment.failed`

### 3. Inventory Service

* Consumes `payment.success`
* Updates inventory
* Publishes `inventory.updated`

### 4. Notification Service

* Consumes all events
* Logs or simulates notifications

---

## 🔄 Event-Driven Workflow

order.created → payment.success → inventory.updated → notification

---

## ⚡ Performance Optimizations

This project includes practical performance improvements:

* Caching (Redis) for frequent reads
* Database indexing for faster queries
* Pagination for large datasets
* Async processing via Kafka
* Reduced service coupling

---

## 🔁 Resilience Features

* Retry mechanisms for failed events
* Dead Letter Queue (DLQ) support
* Idempotent event handling
* Fault-tolerant message processing

---

## 🐳 Running the Project

### 1. Start Kafka (Docker)

```bash
docker-compose up -d
```

### 2. Start all services

Run each Spring Boot service from your IDE or:

```bash
mvn spring-boot:run
```

### 3. Test API

```http
POST http://localhost:8080/orders
```

---

## 📊 Future Enhancements

* Prometheus + Grafana monitoring
* Distributed tracing (Zipkin)
* API Gateway integration
* Kubernetes deployment
* Load testing with performance benchmarks

---

## 🧪 Sample Event Payload

```json
{
  "orderId": "123",
  "status": "CREATED"
}
```

---

## 📁 Project Structure

```
order-processing-system/
├── order-service/
├── payment-service/
├── inventory-service/
├── notification-service/
├── docker-compose.yml
└── README.md
```

---

## 🧠 Key Learnings

* Designing event-driven microservices
* Handling eventual consistency
* Implementing resilient messaging patterns
* Optimizing backend performance

---

## 👨‍💻 Author

Built as a backend engineering project to demonstrate real-world system design, scalability, and performance optimization.

---
