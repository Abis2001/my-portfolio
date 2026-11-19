# 🚀 Personal Portfolio Website

A modern, responsive personal portfolio website built with HTML, CSS, and JavaScript, containerized using Docker and deployed through a Jenkins CI/CD pipeline.

## 📌 Project Overview

This project showcases my personal portfolio as an aspiring Cloud and DevOps Engineer. It demonstrates frontend development, Docker containerization, Git version control, and CI/CD automation using Jenkins.

## 🛠️ Technologies Used

- **HTML5** — Website structure
- **CSS3** — Styling and responsive design
- **JavaScript** — Interactive functionality
- **Git & GitHub** — Version control and source code management
- **Docker** — Containerization
- **Nginx** — Web server
- **Jenkins** — CI/CD automation
- **Docker Hub** — Docker image registry

## ✨ Features

- Responsive portfolio website
- About me section
- Technical skills showcase
- Featured projects section
- Contact section
- Dockerized Nginx web server
- Jenkins pipeline for automated build and deployment workflow
- Docker Hub image publishing

## 📂 Project Structure

```text
my-portfolio/
├── index.html
├── style.css
├── script.js
├── Dockerfile
├── Jenkinsfile
└── README.md
```

## 🐳 Run Locally Using Docker

### 1. Clone the repository

```bash
git clone https://github.com/Abis2001/my-portfolio.git
cd my-portfolio
```

### 2. Build the Docker image

```bash
docker build -t my-portfolio .
```

### 3. Run the container

```bash
docker run -d \
  --name my-portfolio1 \
  -p 8081:80 \
  my-portfolio
```

### 4. Access the website

Open your browser and visit:

```text
http://localhost:8081
```

If running on a remote server, use the server's public IP address and ensure the required port is allowed by its firewall and cloud security group.

### 5. Stop and remove the container

```bash
docker stop my-portfolio1
docker rm my-portfolio1
```

## ⚙️ CI/CD Pipeline Using Jenkins

The Jenkins pipeline automates the following stages:

1. **Git Checkout** — Retrieves the project source code from GitHub.
2. **Docker Build** — Builds the Docker image.
3. **Docker Login** — Authenticates with Docker Hub using Jenkins credentials.
4. **Docker Push** — Publishes the image to Docker Hub.
5. **Docker Run** — Starts the application container.
6. **Docker Logout** — Ends the Docker Hub CLI session.

### Jenkins Prerequisites

- Jenkins installed and configured
- Git installed on the Jenkins agent
- Docker installed and accessible by the Jenkins user
- Docker Hub account and access token with appropriate permissions
- Jenkins credential configured with the ID `dockerhub-credentials`

## 📦 Docker Hub

The Docker image is intended to be published to:

```text
abishek2305/my-portfolio:latest
```

Pull the image after it has been successfully published:

```bash
docker pull abishek2305/my-portfolio:latest
```

Run it locally:

```bash
docker run -d \
  --name my-portfolio1 \
  -p 8081:80 \
  abishek2305/my-portfolio:latest
```

## 🎯 Learning Objectives

Through this project, I practiced:

- Building a responsive website
- Managing source code with Git and GitHub
- Creating Docker images using a Dockerfile
- Serving static content with Nginx
- Configuring Jenkins pipeline stages
- Managing Docker Hub credentials securely
- Building a CI/CD workflow for a web application

## 👨‍💻 Author

**Abishek Baskaran**

Aspiring Cloud and DevOps Engineer

- GitHub: [Abis2001](https://github.com/Abis2001)
- Portfolio Repository: [my-portfolio](https://github.com/Abis2001/my-portfolio)

---

⭐ If you find this project useful, feel free to explore the repository and share feedback.

*This is a learning project developed to practice web development, containerization, and CI/CD automation.*
