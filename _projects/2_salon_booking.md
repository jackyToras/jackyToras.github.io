---

layout: page

title: Scalable Salon Booking Platform

description: Spring Boot, RabbitMQ, React.js, MongoDB, API Gateway, Stripe, Keycloak, Docker

importance: 2

category: work

github: https://github.com/jackyToras/salon-appointment-system

---



Designed and deployed RESTful microservices using a strictly decoupled, layered architecture (Controller-Service-Repository) to guarantee modularity and separation of concerns.



### Key Implementation Details



- **Service Mesh & Routing:** Implemented dynamic service discovery using **Eureka Server** along with centralized edge routing and request filtering via an **API Gateway**.

- **Asynchronous Workflows:** Developed event-driven workflows leveraging **RabbitMQ** to fully decouple core reservation booking, real-time notification streams, and billing systems.

- **Data Sync & Payments:** Integrated Stripe webhooks to handle live transaction lifecycles, safely syncing state data across distributed MongoDB instances.

- **Enterprise Security:** Hardened the architecture using **Keycloak** Identity and Access Management (IAM), enforcing JWT-based Role-Based Access Control (RBAC).

- **Fault Tolerance:** Engineered resilient inter-service communications using **OpenFeign** clients embedded with circuit breaker mechanisms to eliminate cascading runtime failures.
