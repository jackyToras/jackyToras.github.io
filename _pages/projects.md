---
layout: page
title: Projects
permalink: /projects/
nav: true
nav_order: 2
---

<style>
.project-row {
  display: flex;
  border-top: 1px solid #ddd;
  padding: 20px 0;
}
.project-content { flex: 1; }
.project-content h4 { font-weight: 700; margin-bottom: 4px; }
.project-content .links { margin-bottom: 8px; }
.project-content .links a { margin-right: 10px; }
</style>

<div class="project-row">
<div class="project-content">
<h4>Distributed Task Queue System</h4>
<div class="links"><a href="https://github.com/jackyToras/Distributed-tasks-queue-system" target="_blank">GitHub</a></div>
A distributed task queue built to process large volumes of background jobs without blocking the main application thread. Tasks are dropped into queues, worker nodes pick them up and process them independently in parallel with zero single point of failure. Built using Java, Spring Boot, and RabbitMQ — messages are persisted to disk ensuring zero task loss. Multiple worker instances compete to consume messages with prefetch count configurations preventing overload. Failed tasks route to a Dead Letter Queue with configurable retry logic.
</div>
</div>

<div class="project-row">
<div class="project-content">
<h4>Scalable Microservices Salon Booking Platform</h4>
<div class="links"><a href="https://github.com/jackyToras/salon-appointment-system" target="_blank">GitHub</a></div>
A production-grade microservices platform where each concern lives in its own independently deployable service. Every request hits the API Gateway first handling routing, rate limiting, and filtering. Eureka Server enables dynamic service registration — no hardcoded URLs. Booking confirmations publish events to RabbitMQ, Notification and Payment services consume independently — fully decoupled. Stripe webhooks deliver real-time transaction events syncing booking state across distributed MongoDB instances. Keycloak handles authentication with JWT tokens and RBAC enforced across all services. OpenFeign clients with circuit breakers prevent cascading failures across the service mesh.
</div>
</div>

<div class="project-row">
<div class="project-content">
<h4>RAG Question Answering System</h4>
<div class="links"><a href="https://github.com/jackyToras/mistral-rag-system" target="_blank">GitHub</a> <a href="https://qnaragsystem.streamlit.app/" target="_blank">Live</a></div>
LLMs only know what they were trained on — RAG grounds the model in your actual documents eliminating hallucination. PDFs are chunked, embedded into high-dimensional vectors, and stored in ChromaDB for fast similarity search. Questions are embedded and ChromaDB finds the top-K most relevant chunks via cosine similarity. Retrieved chunks are injected into the prompt alongside the question — the model answers from your documents not hallucinated knowledge. The pipeline is exposed through FastAPI REST endpoints and a clean Streamlit chat interface for real-time document ingestion and conversational querying.
</div>
</div>

<div class="project-row">
<div class="project-content">
<h4>Cyber AI Network Intrusion Detection System</h4>
<div class="links"><a href="https://github.com/jackyToras/NetworkIDS" target="_blank">GitHub</a> <a href="https://mlnetworkids.streamlit.app" target="_blank">Live</a></div>
Real-time ML-powered network intrusion detection classifying traffic flows as benign or malicious with 96.4% accuracy. Won 3rd Position (Innovation Award) at Cyber AI Hackathon 2025, University of Derby, UK among 100+ international teams. Trained on the CICIDS benchmark dataset covering DoS/DDoS, Botnet, Brute Force, and Port Scan attacks across 78+ network features. Random Forest ensemble of hundreds of decision trees with majority voting ensures robustness to noise. Stratified sampling and feature-importance scoring counter class imbalance inherent in real network traffic. Streamlit dashboard provides real-time classification with confidence scores and feature importance visualizations.
</div>
</div>
