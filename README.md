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


### Automating Docker Hub Pushes with GitHub Actions

This project includes a GitHub Actions workflow that automatically builds and pushes the Docker image to Docker Hub on every push to the ```main``` branch.

#### Workflow File

The workflow is defined in ```.github/workflows/docker-publish.yml``` It performs the following steps:

   - Checks out the code.
   - Logs in to [Docker Hub](https://hub.docker.com).
   - Builds and pushes the Docker image to Docker Hub.


#### Setting Up GitHub Secrets

To allow GitHub Actions to push to Docker Hub, you need to set up secrets in your GitHub repository. These secrets include your Docker Hub username and password (access token).

#### Step 1: Generate a Docker Hub Access Token

   1. Go to Docker Hub.
   2. Log in to your Docker Hub account.
   3. Navigate to **Account Settings** > **Security** > **New Access Token**.
   4. Create a new access token with the following permissions:
      - **Read**, **Write**, **Delete** (for full access to push and manage images).
   5. Copy the generated token. This will be your Docker Hub **password** for authentication.


#### Step 2: Add Secrets to GitHub

   1. Go to your GitHub repository.
   2. **Navigate to Settings** > **Secrets and variables** > **Actions** > **New repository secret**.
   3. Add the following secrets:
      - **Secret Name:** ```DOCKER_HUB_USERNAME```
         - **Value:** Your Docker Hub username.
      - **Secret Name:** ```DOCKER_HUB_TOKEN```
         - **Value:** The Docker Hub access token you generated in Step 1.
   
#### Step 3: Verify Secrets

   - Ensure the secrets are correctly added under **Settings** > **Secrets and variables** > **Actions**.
   - These secrets will be used by the GitHub Actions workflow to authenticate with Docker Hub.

### Triggering the Workflow

The workflow is automatically triggered when you push to the ```main``` branch. To trigger it manually:
   1. Make changes to your code.
   2. Commit and push to the main branch:
   
      ```git add .```
      ```git commit -m "Your commit message"```
      ```git push origin main```

   3. Check the workflow status:
      - Go to the Actions tab in your GitHub repository.
      - Verify that the workflow runs successfully.

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
