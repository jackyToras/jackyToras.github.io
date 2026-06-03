
---
layout: page
title: Cyber AI Network Intrusion Detection System
description: An award-winning, AI-driven network security backend utilizing Ensemble Learning on the CICIDS benchmark dataset to classify malicious traffic in real-time.
importance: 4
category: AI Engineering
github: https://github.com/jackyToras/your-repo-name
---

Developed an advanced, real-time Network Intrusion Detection System (NIDS) designed to classify and flag malicious network packets and potential cyber threats[cite: 1]. This system won the **3rd Position (Innovation Award) at the Cyber AI Hackathon 2025** (hosted by the International University of Derby, UK)[cite: 1].

### Key Implementation Details

- **CICIDS Dataset Benchmarking:** Trained and validated the architecture using the massive CICIDS benchmark dataset, evaluating millions of high-fidelity network traffic flows capturing sophisticated attack vectors like DoS/DDoS, Botnets, and Brute Force attempts across 78+ numerical metadata features.
- **Random Forest Ensemble Learning:** Implemented a robust Random Forest classifier leveraging ensemble learning paradigms—specifically Bagging (Bootstrap Aggregating) and Feature Randomness—to construct a diverse forest of hundreds of independent decision trees to prevent model overfitting.
- **High-Throughput Inference Backend:** Engineered the pipeline to handle heavy network flow parsing with sub-millisecond inference latency, utilizing the aggregated majority-voting mechanism of the ensemble to process real-time packet anomalies.
- **Mitigating Class Imbalance:** Structured training pipelines to natively counter the heavy class imbalance inherent to live production networks (where benign traffic drastically outnumbers malicious anomalies), utilizing the model's feature-importance scoring to provide clear telemetry for automated firewall adaptations.
