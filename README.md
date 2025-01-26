# Flask Docker Project

This is a simple Flask application dockerized and automated with GitHub Actions to push to Docker Hub.

---

## Table of Contents
- [Prerequisites](#prerequisites)
- [How to Build and Run the Docker Image Locally](#how-to-build-and-run-the-docker-image-locally)
- [Automating Docker Hub Pushes with GitHub Actions](#automating-docker-hub-pushes-with-github-actions)
- [Setting Up GitHub Secrets](#setting-up-github-secrets)
- [Triggering the Workflow](#triggering-the-workflow)
- [Accessing the Application](#accessing-the-application)
- [Troubleshooting](#troubleshooting)
---

## Prerequisites

Before you begin, ensure you have the following installed:

- **Docker**: [Install Docker](https://docs.docker.com/get-docker/)
- **Git**: [Install Git](https://git-scm.com/downloads)
- **Python 3.x**: [Install Python](https://www.python.org/downloads/)
- **Docker Hub Account**: [Sign up for Docker Hub](https://hub.docker.com/signup)
- **GitHub Account**: [Sign up for GitHub](https://github.com/join)

---

## How to Build and Run the Docker Image Locally

1. **Clone the repository**:

   ```bash
   git clone https://github.com/adbrahman22053/flask-docker-project.git
   cd flask-docker-project

2. **Build the Docker image**:

   ```bash
   docker build -t flask-docker-project .

3. **Run the Docker container**:
   ```bash
   docker run -p 5000:5000 flask-docker-project
4. **Access the application :**
      - Open your browser and go to ```http://localhost:5000```

### Troubleshooting

1. **Docker Build Fails**
   - Ensure your ```Dockerfile``` and ```requirements.txt``` are correctly configured.

2. **GitHub Actions Workflow Fails**
   - Verify that the secrets (```DOCKER_HUB_USERNAME``` and ```DOCKER_HUB_TOKEN```) are correctly set.

3. **Application Not Accessible**
   - Ensure the Docker container is running and the correct port (```5000```) is exposed.
   - Check for errors in the container logs:
      ```bash
      docker logs <container_id>
