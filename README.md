# Tournament Registration App 

![Docker Build Status](https://github.com/wifoon/hole.it/actions/workflows/docker-ci.yml/badge.svg)
![Security: Non-Root](https://img.shields.io/badge/Security-Non--Root%20Container-green?style=flat-square&logo=docker)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)

A modern frontend application built with Vite + React, with a strong focus on **automated workflows (CI/CD)**, **container security**, and **production-ready infrastructure**.

## Tech Stack & Infrastructure

* **Frontend:** React, TypeScript, Vite, TailwindCSS.
* **Containerization:** Docker (Optimized Multi-stage build).
* **Web Server:** Nginx (Custom security-hardened configuration).
* **CI/CD:** GitHub Actions (Automated build & security audit).

## DevOps & Security Implementation

* **Multi-stage Docker Build:** Optimized the final image size and security by separating the build environment from the runtime environment. The production image contains only the necessary static assets and a lightweight Nginx binary.
* **Non-Root Execution:** Following the principle of least privilege, the container is configured to run as a dedicated `nginx` user instead of the default `root` user.
* **Automated CI Pipeline:** Every `push` triggers a GitHub Actions workflow that validates the Docker build process and performs a runtime security check.

[Image of Docker multi-stage build process for web applications]

## Docker - Quick Start

The application is fully containerized. You don't need Node.js installed locally to run it.

1.  **Run with Docker Compose:**
    ```sh
    docker compose up --build
    ```
2.  **Access the app:**
    Open [http://localhost:8080](http://localhost:8080) in your browser.

## Local Development

1.  **Install dependencies:**
    ```sh
    npm install
    ```
2.  **Start development server:**
    ```sh
    npm run dev
    ```

## CI/CD Workflow Details

The `.github/workflows/docker-ci.yml` automates the following quality gates:
1.  **Build Validation:** Ensures the Dockerfile compiles correctly.
2.  **Runtime Integrity:** Spawns a container in the runner to ensure it starts without errors.
3.  **Security Audit:** Programmatically verifies that the process inside the container is **not** running as root.
