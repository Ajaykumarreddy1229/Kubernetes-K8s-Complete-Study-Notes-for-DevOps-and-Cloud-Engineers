# ☸️ Kubernetes (K8s) — Complete Study Notes for DevOps & Cloud Engineers

![Kubernetes](https://img.shields.io/badge/Kubernetes-K8s-326CE5?logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containers-2496ED?logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-Cloud-FF9900?logo=amazonaws&logoColor=white)
![Learning](https://img.shields.io/badge/Status-Learning-success)

## 📌 About This Repository

This repository contains my Kubernetes learning notes, architecture diagrams, important concepts, and essential commands as part of my **DevOps and Cloud Engineering learning journey**.

The content is organized in simple English to help beginners understand Kubernetes and prepare for technical interviews.

## 📚 Table of Contents

- [What Is Kubernetes?](#-what-is-kubernetes)
- [Why Do We Need Kubernetes?](#-why-do-we-need-kubernetes)
- [Docker vs Kubernetes](#-docker-vs-kubernetes)
- [Docker Swarm vs Kubernetes](#-docker-swarm-vs-kubernetes)
- [Kubernetes Architecture](#-kubernetes-architecture)
- [Control Plane Components](#-control-plane-components)
- [Worker Node Components](#-worker-node-components)
- [Important Kubernetes Objects](#-important-kubernetes-objects)
- [Kubernetes Networking](#-kubernetes-networking)
- [Volumes, PV and PVC](#-volumes-pv-and-pvc)
- [Namespaces](#-namespaces)
- [Kubernetes Cluster Types](#-kubernetes-cluster-types)
- [Essential kubectl Commands](#-essential-kubectl-commands)
- [Key Kubernetes Features](#-key-kubernetes-features)
- [Interview Preparation](#-interview-preparation)
- [My Learning Goals](#-my-learning-goals)

---

## ☸️ What Is Kubernetes?

Kubernetes, also known as **K8s**, is an open-source container orchestration platform used to automate the deployment, scaling, networking, and management of containerized applications.

In simple words, Kubernetes helps us manage applications running inside containers across multiple servers.

## 🚀 Why Do We Need Kubernetes?

Imagine an application running inside a container. When the number of users increases, one container or server may not be enough.

Kubernetes helps us:

- Scale applications when traffic increases.
- Replace failed application Pods.
- Distribute traffic across application replicas.
- Deploy new application versions.
- Roll back to previous versions.
- Manage application workloads across multiple nodes.

## 🐳 Docker vs Kubernetes

| Docker and Container Tools | Kubernetes |
|---|---|
| Build container images | Orchestrates containerized workloads |
| Run containers | Manages Pods across a cluster |
| Package applications | Supports scaling and recovery |
| Work with container images | Manages application deployment and updates |

**Remember:** Docker tools help build and run containers, while Kubernetes orchestrates containerized applications.

## ⚖️ Docker Swarm vs Kubernetes

| Feature | Docker Swarm | Kubernetes |
|---|---|---|
| Setup | Generally simple | More concepts to learn |
| Learning curve | Lower | Higher |
| Scaling | Supports service scaling | Extensive scaling capabilities |
| Networking | Comparatively simple | Flexible and configurable |
| Self-healing | Supports task rescheduling | Controllers maintain desired state |
| Ecosystem | Smaller | Large cloud-native ecosystem |
| Common use | Simpler deployments | A wide range of workloads, including complex production systems |

Both technologies provide container orchestration. The right choice depends on application requirements, team experience, and operational needs.

---

## 🏗️ Kubernetes Architecture

A Kubernetes cluster consists of two major parts:

1. **Control Plane** — manages the cluster and makes scheduling decisions.
2. **Worker Nodes** — run application workloads inside Pods.

### Architecture Diagram

![Kubernetes Cluster Architecture](images/kubernetes-cluster-architecture.png)

### Basic Architecture Flow

```text
Developer / Administrator
          |
        kubectl
          |
    Kubernetes API Server
          |
   +------+------+------+
   |             |      |
  etcd       Scheduler  Controllers
                       |
                 Worker Nodes
                 /           \
           Worker Node 1   Worker Node 2
           +-----------+   +-----------+
           | kubelet   |   | kubelet   |
           | Runtime   |   | Runtime   |
           | Pods      |   | Pods      |
           +-----------+   +-----------+
```

## 🧠 Control Plane Components

![Kubernetes Components](images/kubernetes-components.png)

### 1. API Server — `kube-apiserver`

- Main entry point for Kubernetes API requests.
- Receives and validates requests.
- Communicates with Kubernetes clients such as `kubectl`.

**Simple meaning:** The main communication point of Kubernetes.

### 2. Scheduler — `kube-scheduler`

- Selects a suitable Worker Node for a new Pod.
- Considers CPU, memory, scheduling rules, and available resources.

**Simple meaning:** Decides where a Pod should run.

### 3. Controller Manager — `kube-controller-manager`

- Runs controllers that monitor cluster resources.
- Compares actual state with desired state.
- Takes action to maintain the requested state.

**Simple meaning:** Helps keep the cluster working as expected.

### 4. etcd

- A consistent key-value data store.
- Stores Kubernetes cluster information and state.

**Simple meaning:** The database used by Kubernetes.

### 5. Cloud Controller Manager

- Integrates Kubernetes with supported cloud-provider APIs.
- Can help manage cloud resources such as load balancers and routes.

---

## 💪 Worker Node Components

### 1. Kubelet

- Runs on each Worker Node.
- Communicates with the API Server.
- Works with the container runtime to run the containers assigned to its Pods.

### 2. Container Runtime

- Responsible for running containers.
- Pulls images and starts containers.
- Examples: `containerd` and `CRI-O`.

### 3. Kube-Proxy

- Commonly maintains network rules for Kubernetes Service traffic.
- Helps route traffic to application endpoints.

Some Kubernetes networking solutions replace kube-proxy functionality.

### 4. Pods

- The smallest deployable units in Kubernetes.
- Contain one or more containers.
- Containers within a Pod share network identity and can share storage.

**Remember:** A Pod is not the same as a container.

---

## 📦 Important Kubernetes Objects

| Object | Purpose |
|---|---|
| Pod | Runs one or more containers |
| Deployment | Manages application replicas and updates |
| ReplicaSet | Helps maintain the desired number of Pod replicas |
| Service | Provides stable network access to Pods |
| ConfigMap | Stores non-sensitive configuration |
| Secret | Stores sensitive configuration data |
| PersistentVolume (PV) | Represents storage available to the cluster |
| PersistentVolumeClaim (PVC) | Requests persistent storage |
| Namespace | Organizes resources within a cluster |

## 🌐 Kubernetes Networking

![Kubernetes Networking and Storage](images/kubernetes-networking-storage.png)

Kubernetes Services provide stable access to application Pods, even when individual Pods are replaced.

### 1. ClusterIP

- Default Service type.
- Provides internal access within the cluster.

### 2. NodePort

- Exposes a Service through a port on
