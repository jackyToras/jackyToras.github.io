---
layout: page
title: Distributed Task Queue System
description: Java, Spring Boot, RabbitMQ, Docker
importance: 1
category: work
github: https://github.com/jackyToras/Distributed-tasks-queue-system
---

A distributed task queue is the backbone of any system that needs to process large volumes of background jobs without blocking the main application thread. Think of it like a postal system — tasks (letters) are dropped into queues (post offices), and worker nodes (postmen) pick them up and process them independently, in parallel, without any single point of failure.

This system was built to handle high volumes of asynchronous background tasks — operations that don't need an immediate response but must be reliably executed: sending emails, processing payments, generating reports, resizing images, and more.

**What's actually happening under the hood:**

**Message Producer:** The Spring Boot application acts as a producer — whenever a task needs to be executed asynchronously, it serializes the task payload and publishes it as a message to a RabbitMQ exchange. The exchange routes messages to the appropriate queue based on routing keys.

**RabbitMQ as the Broker:** RabbitMQ sits at the center — it receives messages from producers, durably stores them, and delivers them to consumers. Messages are persisted to disk, so even if the broker restarts, no task is lost. Exchanges, bindings, and routing keys control how messages flow between producers and consumers.

**Worker Nodes as Consumers:** Multiple worker node instances subscribe to the queue and compete to consume messages. This is the core of load balancing — RabbitMQ distributes messages across all active workers using a round-robin strategy, ensuring no single worker is overwhelmed while others sit idle.

**Load Balancing:** Advanced prefetch count configurations ensure each worker only takes on as many tasks as it can handle. If a worker is busy, RabbitMQ holds the message and delivers it to the next available worker — preventing system overload under heavy traffic spikes.

**Fault Tolerance with Dead Letter Queues:** If a worker fails to process a task (exception thrown, timeout, crash), the message is not lost. It gets routed to a Dead Letter Queue (DLQ) with retry logic — the system attempts reprocessing a configurable number of times before parking the message for manual inspection.

**Containerization:** The entire system — RabbitMQ broker, producer service, and multiple worker instances — is containerized using Docker Compose, enabling multi-node orchestration locally and making it trivially deployable to any cloud environment.
