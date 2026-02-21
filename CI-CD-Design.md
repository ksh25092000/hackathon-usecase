# 🛠️ Hackathon Microservices Architecture & CI/CD Pipeline

## Overview
This project consists of three microservices deployed on Google Kubernetes Engine (GKE) using a CI/CD pipeline powered by Cloud Build.

---

## 📦 Microservices

| Service              | Language | Port  |
|----------------------|----------|-------|
| Patient Service      | Node.js  | 3000  |
| Application Service  | Node.js  | 3001  |
| Order Service        | Java     | 8080  |

---

## 🔄 CI/CD Flow

### 1. Developers → GitHub
- Code changes are pushed to the GitHub repository.

### 2. Cloud Build (CI/CD)
- **CI Phase**:
  - Builds Docker images for each microservice.
  - Tags images with `$SHORT_SHA` (commit hash).
  - Pushes images to **Artifact Registry**.

- **CD Phase**:
  - Substitutes the new image tag (`:$SHORT_SHA`) into Kubernetes manifests.
  - Applies updated manifests to the GKE cluster using `kubectl`.

### 3. Artifact Registry
- Stores versioned container images for:
  - `patient-service`
  - `application-service`
  - `order-service`

### 4. GKE Cluster
- Runs Kubernetes **Deployments** and **Services** for each microservice.
- Handles internal service-to-service communication.

---

## 📊 Deployment Summary

Each microservice is deployed as:
- A **Deployment** (manages pods and replicas)
- A **Service** (exposes the app internally within the cluster)

---

## 🔧 Technologies Used
- Google Cloud Build
- Google Artifact Registry
- Google Kubernetes Engine (GKE)
- Docker
- Node.js (Express)
- Java (Spring Boot or similar)

---

## 📁 Folder Structure

