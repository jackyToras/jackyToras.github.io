---
layout: page
title: projects
permalink: /projects/
nav: true
nav_order: 2
---

<style>
.project-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  padding: 24px;
  margin-bottom: 32px;
}
.project-title { font-size: 1.3rem; font-weight: 700; margin-bottom: 8px; }
.tech-stack span {
  display: inline-block;
  background: #6c63ff22;
  color: #6c63ff;
  border: 1px solid #6c63ff55;
  border-radius: 4px;
  padding: 2px 10px;
  font-size: 0.78rem;
  font-weight: 600;
  margin: 2px 3px;
}
.project-links a {
  margin-right: 12px;
  font-weight: 600;
  font-size: 0.9rem;
}
</style>

<div class="project-card">
<div class="project-title">Distributed Task Queue System</div>
<div class="tech-stack"><span>Java</span><span>Spring Boot</span><span>RabbitMQ</span><span>Docker</span></div>
<div class="project-links"><a href="https://github.com/jackyToras/Distributed-tasks-queue-system" target="_blank">GitHub</a></div>

A distributed task queue built to process large volumes of background jobs without blocking the main application thread. Tasks are dropped into queues, worker nodes pick them up and process them independently, in parallel, with zero single point of failure.

**Message Producer:** Spring Boot serializes task payloads and publishes them to a RabbitMQ exchange, routing messages to the appropriate queue based on routing keys.

**RabbitMQ Broker:** Messages are persisted to disk ensuring zero task loss even on broker restart.

**Load Balancing:** Multiple worker instances compete to consume messages. Prefetch count configurations prevent overload under heavy traffic spikes.

**Fault Tolerance:** Failed tasks route to a Dead Letter Queue with configurable retry logic before parking for manual inspection.
</div>

<div class="project-card">
<div class="project-title">Scalable Microservices Salon Booking Platform</div>
<div class="tech-stack"><span>Spring Boot</span><span>RabbitMQ</span><span>React.js</span><span>MongoDB</span><span>API Gateway</span><span>Stripe</span><span>Keycloak</span><span>Docker</span></div>
<div class="project-links"><a href="https://github.com/jackyToras/salon-appointment-system" target="_blank">GitHub</a></div>

A production-grade microservices platform where each concern lives in its own independently deployable service. Every request hits the API Gateway first — handling routing, rate limiting, and filtering before reaching any internal service.

**Service Discovery:** Eureka Server enables dynamic service registration — no hardcoded URLs, services find each other automatically.

**Event-Driven Workflows:** Booking confirmations publish events to RabbitMQ. Notification and Payment services consume independently — fully decoupled, independently scalable.

**Stripe Payments:** Webhooks deliver real-time transaction events to the Payment Service, syncing booking state across distributed MongoDB instances.

**Enterprise Security:** Keycloak handles authentication with JWT tokens and RBAC enforced across all services.

**Fault Tolerance:** OpenFeign clients with circuit breakers prevent cascading failures across the service mesh.
</div>

<div class="project-card">
<div class="project-title">RAG Question Answering System</div>
<div class="tech-stack"><span>FastAPI</span><span>LangChain</span><span>ChromaDB</span><span>Python</span><span>Streamlit</span></div>
<div class="project-links"><a href="https://github.com/jackyToras/mistral-rag-system" target="_blank">GitHub</a> <a href="https://qnaragsystem.streamlit.app/" target="_blank">Live</a></div>

LLMs only know what they were trained on. RAG grounds the model in your actual documents — at inference time it retrieves the most relevant chunks and feeds them as context, eliminating hallucination.

**Document Pipeline:** PDFs are chunked, embedded into high-dimensional vectors capturing semantic meaning, and stored in ChromaDB for fast similarity search.

**Semantic Retrieval:** Questions are embedded and ChromaDB finds the top-K most relevant chunks via cosine similarity — context-aware retrieval over large document corpora.

**Context-Augmented Generation:** Retrieved chunks are injected into the prompt alongside the question — the model answers from your documents, not hallucinated knowledge.

**FastAPI + Streamlit:** REST endpoints and a clean chat interface for real-time document ingestion and conversational querying.
</div>

<div class="project-card">
<div class="project-title">Cyber AI Network Intrusion Detection System</div>
<div class="tech-stack"><span>Python</span><span>Scikit-learn</span><span>Pandas</span><span>NumPy</span><span>Streamlit</span></div>
<div class="project-links"><a href="https://github.com/jackyToras/NetworkIDS" target="_blank">GitHub</a> <a href="https://mlnetworkids.streamlit.app" target="_blank">Live</a></div>

Real-time ML-powered network intrusion detection classifying traffic flows as benign or malicious with **96.4% accuracy**. Won **3rd Position (Innovation Award)** at Cyber AI Hackathon 2025, University of Derby, UK among 100+ international teams.

**CICIDS Dataset:** Trained on millions of labeled flows covering DoS/DDoS, Botnet, Brute Force, and Port Scan attacks across 78+ network features.

**Random Forest Ensemble:** Hundreds of decision trees trained on bootstrap samples — majority voting at inference ensures robustness to noise and strong generalization.

**Class Imbalance:** Stratified sampling and feature-importance scoring ensure genuine attack detection rather than predicting everything as benign.

**Real-Time Dashboard:** Streamlit dashboard with confidence scores and feature importance visualizations for actionable security telemetry.
</div>
