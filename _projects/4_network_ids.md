---
layout: page
title: Cyber AI Network Intrusion Detection System
description: Python, Scikit-learn, Pandas, NumPy, Streamlit
importance: 4
category: work
github: https://github.com/jackyToras/NetworkIDS
website: https://mlnetworkids.streamlit.app
---

Every second, millions of packets flow through a network. Most are benign — web requests, file transfers, API calls. But hidden among them are malicious packets — port scans probing for vulnerabilities, DDoS floods trying to take down services, botnet communications exfiltrating data, brute force login attempts. The challenge: detect these threats in real time, automatically, without human intervention.

This system is a machine learning-powered Network Intrusion Detection System (NIDS) that classifies network traffic flows as benign or malicious in real time, achieving **96.4% detection accuracy**.

** Won 3rd Position (Innovation Award)** at Cyber AI Hackathon 2025 — University of Derby, UK, supported by American Society for Engineers, USA. Competed among 100+ international teams.

**The Dataset — CICIDS:**

The model was trained on the CICIDS (Canadian Institute for Cybersecurity Intrusion Detection) benchmark dataset — one of the most comprehensive network security datasets available. It contains millions of labeled network flow records capturing real attack scenarios including DoS/DDoS attacks, Botnet traffic, Brute Force attempts, Port Scans, and Web Attacks across 78+ numerical features extracted from raw packet captures — flow duration, packet length statistics, inter-arrival times, flag counts, and more.

**The Problem — Class Imbalance:**

In any real network, benign traffic vastly outnumbers malicious traffic — sometimes 99% benign to 1% malicious. A naive model could achieve 99% accuracy by simply predicting everything as benign and never catching a single attack. Careful training pipeline design using feature-importance scoring and stratified sampling ensures the model genuinely learns to distinguish attack patterns.

**The Model — Random Forest Ensemble:**

Random Forest was chosen for its robustness, interpretability, and resistance to overfitting. It works by constructing hundreds of independent decision trees during training, each trained on a random bootstrap sample of the data and a random subset of features. At inference time, every tree votes on the classification, and the majority vote wins. This ensemble approach means no single tree's errors dominate — the model is robust to noise and generalizes well to unseen traffic patterns.

**Feature Engineering & Preprocessing:**

Raw network packet data is meaningless to a model — it needs to be transformed into meaningful numerical features. The pipeline handles missing value imputation, feature normalization, and removal of correlated features that add noise without predictive value. Feature importance scores from the trained Random Forest expose which network characteristics are most predictive of malicious behavior.

**Real-Time Inference Dashboard:**

The trained model is deployed behind a Streamlit dashboard where network flow data can be submitted for real-time classification. The dashboard displays predictions, confidence scores, and feature importance visualizations — giving security analysts actionable telemetry for firewall rule adaptation.
