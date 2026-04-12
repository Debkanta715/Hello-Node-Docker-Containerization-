<<<<<<< HEAD
# Hello Node Docker Containerization

A Beginner’s Guide to Docker, Microservices, and Kubernetes

This project provides a structured and practical introduction to containerization using Docker, orchestration with Docker Compose, and deployment using Kubernetes. It includes multiple services and demonstrates how microservices communicate with each other in both local and cluster environments.

---

# Project Structure

```
Hello-Node-Docker-Containerization/
│
├── docker/
│   ├── app1-hello/
│   │   ├── docker-compose.yml
│   │   ├── node/
│   │   │   ├── app.js
│   │   │   ├── Dockerfile
│   │   │   └── package.json
│   │   └── python/
│   │       ├── Dockerfile
│   │       ├── main.py
│   │       └── requirements.txt
│
│   └── app2-tax-calculator/
│       ├── docker-compose.yml
│       ├── node/
│       │   ├── service-a/
│       │   └── service-b/
│       └── tax-calculator-frontend/
│
├── k8s/
│   ├── app1-hello/
│   │   ├── app.yaml
│   │   ├── config.yaml
│   │   └── secret.yaml
│
└── README.md
```

---

# Docker Overview

Docker allows you to package an application along with its dependencies into a container. Containers ensure consistency across different environments such as development, testing, and production.

## Common Docker Commands

```
docker pull <image>
docker build -t <name> .
docker run -d -p 3000:3000 <image>
docker ps
docker stop <container>
docker rm <container>
docker images
docker logs <container>
docker exec -it <container> bash
```

---

# Writing a Dockerfile

Example for a Node.js application:

```
FROM node:18

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "app.js"]
```

Explanation:

- FROM: Defines the base image
- WORKDIR: Sets working directory
- COPY: Copies files into container
- RUN: Executes commands
- EXPOSE: Declares port
- CMD: Starts the application

---

# Docker Compose

Docker Compose is used to run multiple services together.

Example:

```
version: '3'

services:
  node-app:
    build: ./node
    ports:
      - "3000:3000"

  python-app:
    build: ./python
    ports:
      - "5000:5000"
```

Commands:

```
docker-compose up --build
docker-compose down
```

---

# Microservices Concept

In this project:

- service-a communicates with service-b
- frontend communicates with backend services

Docker networking allows services to communicate using service names:

```
http://service-b:4000
```

---

# Kubernetes Overview

Kubernetes manages containerized applications across clusters.

## Core Components

- Pod: Smallest deployable unit
- Deployment: Manages pods and replicas
- Service: Exposes applications
- ConfigMap: Stores configuration
- Secret: Stores sensitive data

---

# Kubernetes Service Types

- ClusterIP: Internal communication only
- NodePort: Exposes service externally via node port
- LoadBalancer: External load balancing

---

# Kubernetes Example

## Deployment

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: servicea
spec:
  replicas: 1
  selector:
    matchLabels:
      app: servicea
  template:
    metadata:
      labels:
        app: servicea
    spec:
      containers:
        - name: servicea
          image: embarkx/tax-service-a:latest
          ports:
            - containerPort: 3000
```

## Service

```
apiVersion: v1
kind: Service
metadata:
  name: servicea
spec:
  type: NodePort
  selector:
    app: servicea
  ports:
    - port: 3000
      targetPort: 3000
      nodePort: 32110
```

---

# Microservices in Kubernetes

This project demonstrates communication between services:

```
service-a → service-b
```

Important rule:

Service names must match exactly:

```
http://serviceb:4000
```

---

# How to Deploy

If your structure is:

```
service/
  service-a/app.yaml
  service-b/app.yaml
```

Run:

```
kubectl apply -f service/
```

Or individually:

```
kubectl apply -f service/service-a/app.yaml
kubectl apply -f service/service-b/app.yaml
```

---

# Useful Kubernetes Commands

```
kubectl get pods
kubectl get svc
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl delete -f <file>
```

---

# Accessing the Application

If using NodePort:

```
http://<node-ip>:32110
```

If using Minikube:

```
minikube service servicea
```

---

# Common Issues and Fixes

## Service Name Mismatch

Incorrect:

```
service-b
```

Correct:

```
serviceb
```

---

## Incorrect Service Type

Incorrect:

```
ClusterIp
```

Correct:

```
ClusterIP
```

---

## Port Mismatch

Ensure:

- containerPort matches application port
- targetPort matches containerPort

---

## Missing YAML Separator

Use:

```
---
```

Between multiple resources.

---

# Learning Approach

1. Start with Docker basics
2. Run a single container
3. Use Docker Compose
4. Move to Kubernetes
5. Experiment and debug

---

# References

- Docker Documentation
- Docker Compose Documentation
- Kubernetes Documentation
- Node.js Documentation

---

# Summary

This project demonstrates:

- Containerization using Docker
- Multi-service orchestration
- Kubernetes deployment
- Microservice communication
=======

>>>>>>> c1c5dbdeb317ff14f8141c9daba4446505347899
