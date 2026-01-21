# 🚀 GitOps Demo with Spring Boot, Kubernetes & FluxCD

This repository demonstrates the **very basics of GitOps**, using a simple **Spring Boot application** deployed on **Kubernetes** and managed with **FluxCD**.

The goal of this project is not complexity, but **clarity**:
- understand what GitOps is
- understand how Kubernetes behaves
- understand what FluxCD really does
- learn by observing real behavior

---

## 👤 Authors

**Abderrahim MOUNOUAR**
GitHub: [Abderrahimoun](https://github.com/Abderrahimoun)

**Salah-Eddine RAMI**
GitHub: [ramisalah2002](https://github.com/ramisalah2002)

---

## 🎯 Project Objective

The main idea of this project is:

> **Git describes what should run.  
> Kubernetes makes sure it really runs that way.**

Instead of deploying applications manually:
- we write configuration files
- we store them in Git
- the cluster automatically applies them

This approach is called **GitOps**.

---

## 🧠 What is GitOps

GitOps is a way of managing infrastructure and applications where:

- **Git is the single source of truth**
- Everything is described as code (YAML files)
- Changes are made by **git commit + git push**
- Automation tools apply the changes

In GitOps:
- You don’t “deploy”
- You **declare**
- The system enforces your declaration

---

## 🏗️ High-Level Architecture

Below is the global idea of the project.

**Title:** GitOps High-Level Architecture  
<img width="4128" height="2752" alt="img1" src="https://github.com/user-attachments/assets/7232407f-7253-4a7e-909d-106f43a3fada" />



---

## 🧩 Technologies Used

| Layer            | Technology   | Purpose                     |
|------------------|--------------|-----------------------------|
| Backend          | Spring Boot  | Simple REST API             |
| Container        | Docker       | Package the application      |
| Orchestration    | Kubernetes   | Run and manage containers    |
| Local Cluster     | kind        | Local Kubernetes cluster     |
| GitOps Tool      | FluxCD      | Continuous reconciliation    |
| Version Control   | GitHub      | Source of truth             |

---

## 📁 Repository Structure

```text
clusters/
└── dev/
    ├── flux-system/     # FluxCD installation & config
    └── gitops-demo/     # Application manifests
```

### What this means:

* `flux-system/`
  → contains everything related to FluxCD itself

* `gitops-demo/`
  → contains Kubernetes manifests for the application
  (Deployment, Service, Kustomization)

---

## 📦 The Application (Spring Boot)
**Repo:** [gitops-spring-demo](https://github.com/ramisalah2002/gitops-spring-demo)

The application is intentionally very simple:

* one REST endpoint
* one container
* one replica

This simplicity helps focus on **GitOps behavior**, not application logic.

---

## 🐳 Docker

Docker is used to:

* package the Spring Boot app
* make it runnable anywhere
* provide an immutable artifact

Basic idea:

> “Build once, run everywhere.”

---

## ☸️ Kubernetes

Kubernetes is **not just a container runner**.

It constantly does this loop:

> **Observe → Compare → Correct**

**Title:** Kubernetes Reconciliation Loop  
<img width="1536" height="1024" alt="img2" src="https://github.com/user-attachments/assets/e55f1daa-7899-4e4e-ac71-363a9d0217b7" />

---

## 🔁 What FluxCD Does

FluxCD connects **Git** and **Kubernetes**.

Its role is:

* watch a Git repository
* detect changes
* apply them to the cluster
* continuously check if the cluster matches Git

FluxCD does **not deploy once**.  
It **reconciles forever**.

---

## 🔄 GitOps Reconciliation

When something changes in Git:

1. FluxCD detects the change
2. Kubernetes applies new manifests
3. Kubernetes checks if the state matches
4. If not, it fixes it automatically

If nothing changes:

* Flux waits
* Kubernetes does nothing
* This is **normal behavior**

## ✅ What This Project Demonstrates

* Understanding of GitOps fundamentals
* Kubernetes reconciliation logic
* FluxCD behavior and limitations
* Docker image lifecycle
