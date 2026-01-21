````md
# 🚀 GitOps Demo with Spring Boot, Kubernetes & FluxCD

This repository demonstrates the **very basics of GitOps**, using a simple **Spring Boot application** deployed on **Kubernetes** and managed with **FluxCD**.

The goal of this project is not complexity, but **clarity**:
- understand what GitOps is
- understand how Kubernetes behaves
- understand what FluxCD really does
- learn by observing real behavior

---

## 👤 Author

**Salah-Eddine**  
GitHub: [ramisalah2002](https://github.com/ramisalah2002)

---

## 🎯 Project Objective (Very Simple)

The main idea of this project is:

> **Git describes what should run.  
> Kubernetes makes sure it really runs that way.**

Instead of deploying applications manually:
- we write configuration files
- we store them in Git
- the cluster automatically applies them

This approach is called **GitOps**.

---

## 🧠 What is GitOps (Basics of the Basics)

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

### 📌 (Schema to add later)

**Title:** GitOps High-Level Architecture  
**AI Prompt to generate image:**

> “Diagram showing GitOps workflow: Developer pushes code to GitHub, FluxCD watches the repository, Kubernetes cluster applies manifests and runs a Spring Boot application. Clean, minimal, professional DevOps style.”

_(Insert image here later)_

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

## 📁 Repository Structure (Explained Simply)

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

The application is intentionally very simple:

* one REST endpoint
* one container
* one replica

This simplicity helps focus on **GitOps behavior**, not application logic.

---

## 🐳 Docker (Basics)

Docker is used to:

* package the Spring Boot app
* make it runnable anywhere
* provide an immutable artifact

Basic idea:

> “Build once, run everywhere.”

---

## ☸️ Kubernetes (Basics)

Kubernetes is **not just a container runner**.

It constantly does this loop:

> **Observe → Compare → Correct**

### 📌 (Schema to add later)

**Title:** Kubernetes Reconciliation Loop  
**AI Prompt:**

> “Simple diagram illustrating Kubernetes reconciliation loop: Observe current state, Compare with desired state, Correct differences. Minimal and educational style.”

*(Insert image here later)*

---

## 🔁 What FluxCD Does (Very Important)

FluxCD connects **Git** and **Kubernetes**.

Its role is:

* watch a Git repository
* detect changes
* apply them to the cluster
* continuously check if the cluster matches Git

FluxCD does **not deploy once**.  
It **reconciles forever**.

---

## 🔄 GitOps Reconciliation Explained Simply

When something changes in Git:

1. FluxCD detects the change
2. Kubernetes applies new manifests
3. Kubernetes checks if the state matches
4. If not, it fixes it automatically

If nothing changes:

* Flux waits
* Kubernetes does nothing
* This is **normal behavior**

---

## 📌 Common Real-World Observations (Learned in This Project)

* `flux reconcile` can wait or timeout → **not an error**
* Kubernetes does not restart pods if nothing really changed
* Image tags alone are not enough → image digest matters
* Local clusters (kind + macOS) have limitations
* The **application behavior** is the final truth

---

## 🧪 How to Verify That GitOps Works

You don’t trust logs.  
You trust **results**.

Example:

* change something in Git
* wait
* see the application behavior change

That is GitOps.

---

## 📌 (Schema to add later)

**Title:** GitOps Observe–Compare–Correct in Action  
**AI Prompt:**

> “Educational diagram showing Git change triggering FluxCD reconciliation, Kubernetes detecting drift and correcting the running application. Clean DevOps illustration.”

*(Insert image here later)*

---

## ✅ What This Project Demonstrates

* Understanding of GitOps fundamentals
* Kubernetes reconciliation logic
* FluxCD behavior and limitations
* Docker image lifecycle

---
```` 