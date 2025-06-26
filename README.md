# Dockerized 2-Tier Web App with GitHub CI/CD

## Overview

This project demonstrates a two-tier web application with a frontend and backend containerized using Docker. The app is deployed to an Azure Linux VM using GitHub Actions for continuous integration and delivery (CI/CD).


## Project Structure

dockerproject2025/
│
├── frontend/  Frontend application (HTML, CSS)
│ ├── index.html  Main webpage
│ └── Dockerfile  Dockerfile for frontend
│
├── backend/  Backend application (Node.js + Express)
│ ├── app.js  Backend server code
│ └── Dockerfile  Dockerfile for backend
│
├── docker-compose.yml  Docker Compose file to run both services
├── .github/
│ └── workflows/
│ └── deploy.yml  GitHub Actions workflow for CI/CD
└── README.md  This file


## Features

- Dockerized frontend and backend services.
- Docker Compose for local orchestration.
- GitHub Actions workflow to build and push Docker images.
- Automated deployment to Azure VM via SSH.
- Live web app accessible through Azure VM public IP.


## Prerequisites

- Docker installed locally.
- GitHub repository with this project code.
- Docker Hub account (`ghostnoble`) with access token.
- Azure Linux VM with Docker installed.
- SSH key configured for GitHub Actions to access the VM.

---

## Setup & Usage

### 1. Clone this repo:

```bash
git clone https://github.com/Ghostnoble/dockerproject2025.git
cd dockerproject2025
2. Run locally (optional):
bash

docker-compose up -d
Access frontend: http://localhost
Access backend API: http://localhost:3000/api

3. Push to GitHub
Push your code changes to the main branch to trigger GitHub Actions workflow.

4. Deployment
The workflow will:

Build Docker images for frontend and backend.

Push images to Docker Hub.

SSH into Azure VM, pull images, and restart containers.

Access your live app via your Azure VM public IP (e.g., http://<VM_IP>).

GitHub Secrets Required
Add these secrets in your GitHub repository settings under Settings > Secrets and variables > Actions:

Secret Name	Description
DOCKER_USERNAME	Docker Hub username (ghostnoble)
DOCKER_PASSWORD	Docker Hub access token
VM_IP	Azure VM public IP address
VM_USER	Azure VM username (azureuser)
VM_PRIVATE_KEY	SSH private key (multiline)

Troubleshooting
Ensure Docker and Docker Compose are installed on your Azure VM.

Verify inbound ports 80, 3000, and 22 are open on the VM.

Check container logs on the VM with docker logs <container_id>.

Check GitHub Actions logs for build or deployment errors.

Author
Idowu Ogunsanya
Email: elijahogunsanya86@gmail.com

License
MIT License (or your preferred license)

Thank you for checking out the project!
