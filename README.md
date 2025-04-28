#  GreenPulse Platform

GreenPulse is a modular microservices-based platform for user management, data ingestion, AI analytics, notifications, and reporting.  
It is built with Java (Spring Boot), secured with Keycloak and powered by Kafka, Redis and PostgreSQL, all orchestrated via Docker Compose.

---

##  Tech Stack

- **Java 21** + **Spring Boot**
- **PostgreSQL** — database
- **Redis** — cache and storage
- **Apache Kafka** — messaging
- **Keycloak** — authentication and authorization (OAuth2 / OpenID Connect)
- **Docker Compose** — service orchestration
- **Grafana** — metrics

---

##  Microservices

| Service Name               | Description |
| :------------------------- | :---------- |
| **Auth-Service**            | Handles user authentication and authorization with Keycloak |
| **User-Management-Service** | Manages user profiles and interactions |
| **Notification-Service**    | Sends email notifications based on Kafka events |
| **Data-Ingestion-Service**  | Collects, processes and pushes sensor data to Kafka |
| **AI-Analytics-Service**    | Predicts PM2.5 air quality values using ONNX models |
| **Reporting-Service**       | Generates and stores user activity reports |

---

##  How to Run the Full Platform

> Requirements:
> - Docker
> - Docker Compose

1. Clone the repository:

```bash
git clone https://github.com/Green-Pulse/greenpulse-platform.git
cd greenpulse-platform
```

2. Build and start all services:

```bash
docker-compose up --build -d
```

 After a few minutes, the services will be fully operational.

---

##  Service Ports

| Service | Port | Description |
| :------ | :--: | :---------- |
| **PostgreSQL** | 5432 | Database |
| **Redis** | 6379 | Redis server |
| **Keycloak** | 8180 | Authentication UI (mapped from 8080 inside container) |
| **Auth-Service** | 8087 | Authentication service API |
| **User-Management-Service** | 8085 | User management API |
| **Notification-Service** | 8083 | Email notifications service |
| **Reporting-Service** | 8088 | Reports service |
| **Data-Ingestion-Service** | 8090 | Sensor data ingestion |
| **AI-Analytics-Service** | 8086 | AI-based analytics API |

---

##  Authentication and Authorization

Keycloak manages users and roles for all services.

- **Realm**: `greenpulse`
- **Admin Username**: `admin`
- **Admin Password**: `admin`
- **Client**: `greenpulseclient`

 After starting, Keycloak will automatically import the realm from `greenpulse-realm.json`.

Keycloak UI available at:  
[http://localhost:8180](http://localhost:8180)

---

##  Notes

- All services communicate internally over a shared `greenpulse-network`.
- Each service uses **its own database connections** and **Kafka topics**.
- **JWT tokens** issued by Keycloak are used for service-to-service authentication.
- Some services also integrate with **Redis** for caching.

---

##  Future Improvements

- Add CI/CD pipelines (e.g., GitHub Actions for automatic deployment)
- Improve security with HTTPS (currently HTTP for local development)
- Add API Gateway (e.g., Spring Cloud Gateway)

---

##  Contributing

Pull requests are welcome.  
For major changes, please open an issue first to discuss what you would like to change.

---
