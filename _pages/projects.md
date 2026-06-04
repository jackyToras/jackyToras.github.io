---
layout: page
title: projects
permalink: /projects/
nav: true
nav_order: 2
---

---

### Distributed Task Queue System
**Java, Spring Boot, RabbitMQ, Docker** · [GitHub](https://github.com/jackyToras/Distributed-tasks-queue-system)

A distributed task queue is the backbone of any system that needs to process large volumes of background jobs without blocking the main application thread. Tasks are dropped into queues, and worker nodes pick them up and process them independently, in parallel, without any single point of failure.

**Message Producer:** The Spring Boot application serializes task payloads and publishes them as messages to a RabbitMQ exchange, which routes messages to the appropriate queue based on routing keys.

**RabbitMQ as the Broker:** Messages are persisted to disk ensuring zero task loss even if the broker restarts. Exchanges, bindings, and routing keys control how messages flow between producers and consumers.

**Load Balancing:** Multiple worker instances compete to consume messages. Prefetch count configurations ensure each worker only takes on as many tasks as it can handle — preventing overload under heavy traffic spikes.

**Fault Tolerance:** Failed tasks are routed to a Dead Letter Queue with retry logic — the system attempts reprocessing a configurable number of times before parking the message for manual inspection.

---

### Scalable Microservices Salon Booking Platform
**Spring Boot, RabbitMQ, React.js, MongoDB, API Gateway, Stripe, Keycloak, Docker** · [GitHub](https://github.com/jackyToras/salon-appointment-system)

Built from the ground up as a microservices system — each concern lives in its own independently deployable service. Every request from the React.js frontend hits the API Gateway first, which handles routing, rate limiting, and request filtering.

**Service Discovery:** Each microservice registers itself with Eureka Server on startup. When services need to communicate, they ask Eureka for the current address dynamically — no hardcoded URLs.

**Event-Driven Workflows:** When a booking is confirmed, it publishes an event to RabbitMQ instead of directly calling other services. The Notification Service and Payment Service consume these events independently — fully decoupled.

**Stripe Payments:** Stripe webhooks deliver real-time transaction events directly to the Payment Service, which updates booking status in MongoDB accordingly.

**Enterprise Security:** Keycloak handles authentication — users receive a JWT token which every downstream service validates, enforcing Role-Based Access Control (RBAC) across all services.

**Fault Tolerance:** OpenFeign clients with circuit breakers wrap all synchronous service calls — if a downstream service starts failing, the circuit opens and requests fail fast instead of cascading failures.

---

### RAG Question Answering System
**FastAPI, LangChain, ChromaDB, Python, Streamlit** · [GitHub](https://github.com/jackyToras/mistral-rag-system) · [Live](https://qnaragsystem.streamlit.app/)

LLMs only know what they were trained on. Ask one about your own PDF files and it either hallucinates or admits it doesn't know. RAG solves this — at inference time, it retrieves the most relevant chunks of your documents and feeds them as context to the model, grounding its responses in real data.

**Document Ingestion:** PDFs are extracted, split into overlapping chunks of configurable size, and passed through an embedding model which converts each chunk into a high-dimensional vector capturing its semantic meaning.

**Vector Storage:** Embeddings are stored in ChromaDB — a vector database optimized for fast similarity search. When a question arrives, it is embedded and ChromaDB finds the top-K most semantically similar chunks via cosine similarity search.

**Context-Augmented Generation:** Retrieved chunks are injected into a prompt template alongside the user's question and sent to the LLM — the model answers based on what's actually in your documents, not hallucinated knowledge.

**FastAPI + Streamlit:** The pipeline is exposed through FastAPI REST endpoints and a clean Streamlit chat interface for real-time document ingestion and conversational querying.

---

### Cyber AI Network Intrusion Detection System
**Python, Scikit-learn, Pandas, NumPy, Streamlit** · [GitHub](https://github.com/jackyToras/NetworkIDS) · [Live](https://mlnetworkids.streamlit.app)

Every second, millions of packets flow through a network. Hidden among benign traffic are malicious packets — DDoS floods, botnet communications, brute force attempts. This system classifies network traffic flows as benign or malicious in real time, achieving **96.4% detection accuracy**. Won **3rd Position (Innovation Award)** at Cyber AI Hackathon 2025, University of Derby, UK.

**CICIDS Dataset:** Trained on millions of labeled network flow records capturing real attack scenarios including DoS/DDoS, Botnet, Brute Force, and Port Scans across 78+ numerical features extracted from raw packet captures.

**Random Forest Ensemble:** Hundreds of independent decision trees each trained on a random bootstrap sample. At inference time every tree votes and the majority wins — robust to noise, generalizes well to unseen traffic patterns.

**Class Imbalance:** In real networks, benign traffic vastly outnumbers malicious traffic. Careful stratified sampling and feature-importance scoring ensures the model genuinely learns attack patterns rather than just predicting everything as benign.

**Real-Time Dashboard:** Streamlit dashboard for real-time traffic classification with confidence scores and feature importance visualizations — giving security analysts actionable telemetry for firewall rule adaptation.
