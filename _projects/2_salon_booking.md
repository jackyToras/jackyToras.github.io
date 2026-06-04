---
layout: page
title: Scalable Microservices Salon Booking Platform
description: Spring Boot, RabbitMQ, React.js, MongoDB, API Gateway, Stripe, Keycloak, Docker
importance: 2
category: work
github: https://github.com/jackyToras/salon-appointment-system
---

Most booking platforms are built as monoliths — one giant application handling everything from authentication to payments to notifications. This works at small scale but becomes a nightmare when you need to scale individual components, deploy updates without downtime, or isolate failures. This platform was built from the ground up as a microservices system — each concern lives in its own independently deployable service.

**The Architecture — What Services Exist and What They Do:**

**API Gateway:** The single entry point for all client requests. Every request from the React.js frontend hits the API Gateway first. It handles routing to the correct downstream service, rate limiting, and request filtering. Nothing talks directly to internal services — everything goes through the gateway.

**Service Discovery with Eureka:** In a distributed system, services need to find each other dynamically. Each microservice registers itself with Eureka Server on startup, publishing its host and port. When Service A needs to call Service B, it asks Eureka for Service B's current address — no hardcoded URLs, no manual configuration updates when services scale or move.

**Booking Service:** Handles appointment creation, rescheduling, and cancellation. When a booking is confirmed, it doesn't directly call the notification or payment service — instead it publishes an event to RabbitMQ. This decoupling means the booking service doesn't care whether the notification service is up or down.

**Notification Service:** Subscribes to booking events from RabbitMQ. When a booking event arrives, it processes it independently — sending confirmation emails or SMS. Because it's event-driven, it can be scaled independently during high-traffic periods without touching the booking service.

**Payment Service with Stripe:** Handles payment processing via Stripe. Stripe webhooks deliver real-time transaction events (payment succeeded, payment failed, refund issued) directly to this service, which then updates the booking status in MongoDB accordingly.

**Security with Keycloak:** All services are secured using Keycloak — an enterprise-grade Identity and Access Management (IAM) solution. Users authenticate via Keycloak and receive a JWT token. Every downstream service validates this token on every request, enforcing Role-Based Access Control (RBAC) — customers can only book appointments, admins can manage everything.

**Fault Tolerance with OpenFeign + Circuit Breaker:** When services need to communicate synchronously (not via events), they use OpenFeign clients. Circuit breakers wrap these calls — if a downstream service starts failing, the circuit opens and requests fail fast instead of cascading failures bringing down the whole system.
