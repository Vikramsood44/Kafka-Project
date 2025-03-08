# **Project Summary**

This project implements a **microservices architecture** using **Apache Kafka** as the messaging platform, with **Zookeeper** for Kafka coordination. The system consists of multiple **WAR** files, each performing a distinct role within the event-driven architecture. Below is a detailed breakdown of each service:

### **1. Kafka Producer - Order Service (Producer WAR):**
The **Order Service** acts as the **producer** in this Kafka-based architecture. It is responsible for generating and sending order-related events to Kafka topics. When an order is placed, this service publishes the event to the Kafka topic, which other services consume for further processing.

### **2. Kafka Consumers - Order and Email Service (Consumer WARs):**
There are **two consumer services** in this architecture:
- **Order Consumer**: This service listens to the Kafka topic to receive the order events published by the **Order Service**. It processes these events, such as updating order status, checking inventory, or fulfilling the order.
- **Email Consumer**: This service listens for events related to user notifications (e.g., order confirmation, shipping details) and handles sending out email alerts to users.

### **3. Base-Domain Service (Lombok WAR):**
This service is built using the **Lombok** framework, which generates getter and setter methods automatically, reducing boilerplate code. It handles domain entities and provides the necessary data structures and business logic for the consumers (Order and Email services) to operate seamlessly.

### **4. Kafka and Zookeeper Integration:**
- **Apache Kafka** is used for **event streaming**, allowing services to communicate asynchronously through published events.
- **Apache Zookeeper** is used to manage and coordinate Kafka brokers, ensuring high availability and reliability of the Kafka cluster.

### **Architecture Overview:**
- **Microservices Architecture**: Each service (Order, Email, and Base-Domain) runs independently, allowing for flexibility, scalability, and easy maintenance.
- **Event-Driven**: **Kafka** serves as the central communication hub, where events are published by producers (e.g., Order Service) and consumed by consumers (e.g., Order and Email services).
- **Zookeeper for Coordination**: **Zookeeper** ensures that the Kafka cluster is properly managed and fault-tolerant.

### **Technologies and Frameworks:**
- **Apache Kafka**: Event streaming platform for message queuing.
- **Apache Zookeeper**: Coordination service for Kafka.
- **Spring Boot**: Backend framework for developing microservices.
- **Lombok**: A Java library that automatically generates boilerplate code like getters and setters.
- **Java**: For developing Kafka producers, consumers, and domain services.

### **System Workflow:**
1. **Order Service (Producer)**: Publishes order events to Kafka.
2. **Order Consumer**: Listens to the Kafka topic for order events, processes them (e.g., inventory updates, status changes).
3. **Email Consumer**: Listens to order-related events and sends email notifications (e.g., order confirmation).
4. **Base-Domain Service**: Manages data structures using Lombok and supports other services with domain logic.

### **Benefits of this Architecture:**
- **Scalability**: Services can scale independently based on load.
- **Decoupling**: The system is loosely coupled, making it easier to modify or replace individual components.
- **Asynchronous Processing**: **Kafka** allows for asynchronous handling of events, improving system responsiveness and reliability.
