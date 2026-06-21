# 🚀 Full-Stack Node.js & React CI/CD Capstone

This repository accompanies the **[Build a Node.js and React app with npm](https://jenkins.io/doc/tutorials/build-a-node-js-and-react-app-with-npm/)** tutorial from the Official Jenkins User Documentation, upgraded with a cutting-edge GitHub Actions CI/CD GitOps workflow.

---

## 📊 Pipeline Status

| Pull Request Pipeline | Main Branch Pipeline | Automated Health Check |
| :--- | :--- | :--- |
| [![pr pipeline](https://github.com/Afroz-J-Shaikh/github-actions-capstone/actions/workflows/pr-pipeline.yml/badge.svg?branch=feature&event=pull_request)](https://github.com/Afroz-J-Shaikh/github-actions-capstone/actions/workflows/pr-pipeline.yml) | [![main pipeline](https://github.com/Afroz-J-Shaikh/github-actions-capstone/actions/workflows/main-pipeline.yml/badge.svg)](https://github.com/Afroz-J-Shaikh/github-actions-capstone/actions/workflows/main-pipeline.yml) | [![health checkout](https://github.com/Afroz-J-Shaikh/github-actions-capstone/actions/workflows/health-check.yml/badge.svg)](https://github.com/Afroz-J-Shaikh/github-actions-capstone/actions/workflows/health-check.yml) |

---

## 🛠️ Tech Stack

**Frontend:** ![React](https://img.shields.io/badge/react-%2320232a.svg?style=flat-square&logo=react&logoColor=%2361DAFB) ![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=flat-square&logo=vite&logoColor=white)  
**Backend:** ![NodeJS](https://img.shields.io/badge/node.js-%23339933.svg?style=flat-square&logo=nodes.js&logoColor=white) ![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=flat-square&logo=express&logoColor=%2361DAFB)  
**DevOps & Security:** ![GitHub Actions](https://img.shields.io/badge/github%20actions-%232088FF.svg?style=flat-square&logo=githubactions&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat-square&logo=docker&logoColor=white) ![Trivy](https://img.shields.io/badge/security-trivy-blueviolet?style=flat-square)

---

## 🏗️ Full-Stack Architecture

The repository hosts a decoupled, production-ready full-stack ecosystem:

* **Frontend**: A lightning-fast **Vite-powered React application** pre-configured with modern SPA routing capabilities.
* **Backend**: A robust **Express.js server** engineered to handle business logic, serve structured data, and handle client asset fallback.

### 🔌 API Endpoints

| Endpoint | Type | Description |
| :--- | :--- | :--- |
| `/api/hello` | `GET` | Serves a beautifully styled dynamic HTML view utilizing a modern glassmorphic UI, fluid CSS gradients, and an animated pulsing status badge. |
| `/*` | `GET` | Catch-all fallback route that securely serves the production-built React frontend (`index.html`) to facilitate seamless client-side SPA routing. |

---

## ⚙️ DevOps & Pipeline Architecture

The workflow is completely automated via GitHub Actions, securing the application from code commit all the way to deployment and continuous monitoring.

```mermaid
graph TD
    A[PR opened] --> B[Build & Test]
    B -->|Pass| C[Dependency vulnerability check]
    C --> D[PR Comment]
    
    E[Merge to main] --> F[Build & Test]
    F -->|Pass| G[Docker Build & Push]
    G -->|Pass| H[Trivy image scan]
    H -->|Pass| I[Deploy to environment]
    H -->|Fail| J[Exit]

    I --> K[Every 12 hours]
    K --> L[Health Check]
    L --> M[Summary]

    N[Always active] --> O[GitHub secret scanning]
    N --> P[Push protection for secrets]

    style A fill:#f9f,stroke:#333,stroke-width:2px
    style E fill:#bbf,stroke:#333,stroke-width:2px
    style I fill:#bfb,stroke:#333,stroke-width:2px
    style L fill:#ffb,stroke:#333,stroke-width:2px
