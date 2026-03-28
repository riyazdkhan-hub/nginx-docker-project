# 🚀 Jenkins + Docker + Nginx CI/CD Project

This project demonstrates a **complete CI/CD pipeline** where a web application is automatically built and deployed using Jenkins and Docker.

The application is served using **Nginx** and deployed from a **GitHub repository** through a Jenkins pipeline.

---

# 📌 Project Overview

This project automates the following workflow:

1. Developer pushes code to GitHub
2. Jenkins pulls the latest code
3. Jenkins builds a Docker image
4. Jenkins stops the old container
5. Jenkins deploys a new container
6. Nginx serves the application

This simulates a **real-world DevOps CI/CD deployment pipeline**.

---

# 🏗️ Architecture Diagram

```
             +------------------+
             |    Developer     |
             |  Push Code       |
             +--------+---------+
                      |
                      v
             +------------------+
             |      GitHub      |
             | Source Code Repo |
             +--------+---------+
                      |
                      v
             +------------------+
             |      Jenkins     |
             |   CI/CD Pipeline |
             +--------+---------+
                      |
        Build Docker Image & Deploy
                      |
                      v
             +------------------+
             |      Docker      |
             |  Containerized   |
             |    Application   |
             +--------+---------+
                      |
                      v
             +------------------+
             |      Nginx       |
             |    Web Server    |
             +--------+---------+
                      |
                      v
                🌐 End User
             http://SERVER_IP:5002
```

---

# ⚙️ Technologies Used

* Jenkins (CI/CD Automation)
* Docker (Containerization)
* Nginx (Web Server)
* GitHub (Source Code Management)
* Linux / Ubuntu Server

---

# 📂 Project Structure

```
nginx-docker-project
│
├── Dockerfile
├── index.html
└── Jenkinsfile
```

---

# 📄 Dockerfile

```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html
```

This builds a Docker image using Nginx and serves the HTML page.

---

# 🔄 Jenkins Pipeline

The pipeline performs the following stages:

1️⃣ Clone Repository
2️⃣ Build Docker Image
3️⃣ Stop Old Container
4️⃣ Run New Container

Example pipeline:

```
pipeline {
 agent any

 stages {

  stage('Clone Repo') {
   steps {
    git branch: 'main', url: 'https://github.com/your-username/nginx-docker-project.git'
   }
  }

  stage('Build Docker Image') {
   steps {
    sh 'docker build -t myapp .'
   }
  }

  stage('Stop Old Container') {
   steps {
    sh 'docker stop mycontainer || true'
    sh 'docker rm mycontainer || true'
   }
  }

  stage('Run Container') {
   steps {
    sh 'docker run -d -p 5002:80 --name mycontainer myapp'
   }
  }

 }
}
```

---

# 🚀 How to Run This Project

### 1 Install Docker

```
sudo apt update
sudo apt install docker.io -y
```

---

### 2 Install Jenkins

```
sudo apt install openjdk-17-jdk -y
sudo apt install jenkins -y
```

---

### 3 Add Jenkins to Docker Group

```
sudo usermod -aG docker jenkins
sudo systemctl restart docker
sudo systemctl restart jenkins
```

---

### 4 Create Jenkins Pipeline

In Jenkins:

```
New Item
 → Pipeline
 → Pipeline script from SCM
```

Repository:

```
https://github.com/YOUR_USERNAME/nginx-docker-project.git
```

Branch:

```
main
```

Script path:

```
Jenkinsfile
```

---

### 5 Run Pipeline

Click **Build Now**.

Jenkins will:

```
Clone Repo
↓
Build Docker Image
↓
Deploy Container
```

---

# 🌐 Access the Application

Open in browser:

```
http://SERVER_IP:5002
```

You will see the deployed web page.

---

# 🎯 Learning Outcomes

This project demonstrates:

✔ CI/CD pipeline automation
✔ Docker container deployment
✔ Jenkins pipeline configuration
✔ GitHub integration
✔ Web application deployment with Nginx

---

# 📈 Future Improvements

* Add GitHub Webhook for automatic builds
* Push Docker images to DockerHub
* Add Nginx Reverse Proxy
* Deploy using Kubernetes
* Implement monitoring with Prometheus & Grafana

---

# 👨‍💻 Author

**Riyaz Khan**

DevOps Enthusiast | Docker | Jenkins | Linux | CI/CD
