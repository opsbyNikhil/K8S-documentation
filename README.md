# 📦 Container Tools & Kubernetes Overview

## 📑 Table of Contents

- [📦 Container Tools \& Kubernetes Overview](#-container-tools--kubernetes-overview)
  - [📑 Table of Contents](#-table-of-contents)
  - [🐳 Container Tools](#-container-tools)
  - [☸️ Kubernetes Overview](#️-kubernetes-overview)
    - [Key Features:](#key-features)
  - [⚙️ Containerization vs Orchestration](#️-containerization-vs-orchestration)
  - [🏗️ Kubernetes Cluster Architecture](#️-kubernetes-cluster-architecture)
  - [🔀 Types of Kubernetes Clusters](#-types-of-kubernetes-clusters)
    - [1️⃣ Single Node Cluster](#1️⃣-single-node-cluster)
      - [Used For:](#used-for)
      - [Examples:](#examples)
    - [2️⃣ Multi Node Cluster](#2️⃣-multi-node-cluster)
      - [Used In:](#used-in)
      - [Provides:](#provides)
  - [🖥️ Self-Hosted Kubernetes Cluster](#️-self-hosted-kubernetes-cluster)
      - [Tools:](#tools)
  - [☁️ Cloud Hosted Kubernetes Services](#️-cloud-hosted-kubernetes-services)
  - [✅ Summary](#-summary)
- [☸️ Kubernetes Architecture (K8s)](#️-kubernetes-architecture-k8s)
  - [📌 Overview](#-overview)
  - [🧠 Control Plane Components](#-control-plane-components)
    - [1️⃣ Kube API Server](#1️⃣-kube-api-server)
    - [2️⃣ etcd](#2️⃣-etcd)
    - [3️⃣ Kube Scheduler](#3️⃣-kube-scheduler)
    - [4️⃣ Kube Controller Manager](#4️⃣-kube-controller-manager)
      - [What is Desired State?](#what-is-desired-state)
  - [🔁 Controller Manager \& Controllers](#-controller-manager--controllers)
    - [1. Node Controller](#1-node-controller)
    - [2. Replication Controller / ReplicaSet](#2-replication-controller--replicaset)
    - [3. Endpoint Controller](#3-endpoint-controller)
    - [4. Service Account Controller](#4-service-account-controller)
  - [🖥️ Worker Node Components in Kubernetes](#️-worker-node-components-in-kubernetes)
    - [1️⃣ Kubelet](#1️⃣-kubelet)
    - [2️⃣ Kube-Proxy](#2️⃣-kube-proxy)
    - [3️⃣ Container Runtime](#3️⃣-container-runtime)
  - [🎯 Key Interview Points](#-key-interview-points)
  - [✅ Summary](#-summary-1)
- [🚀 Kubernetes Pod Creation \& Networking Flow](#-kubernetes-pod-creation--networking-flow)
  - [📌 Control Plane Flow](#-control-plane-flow)
    - [Step 1: Request to API Server](#step-1-request-to-api-server)
    - [Step 2: Validation \& Persistence](#step-2-validation--persistence)
    - [Step 3: Controller Manager Reaction](#step-3-controller-manager-reaction)
    - [Step 4: Scheduler Watches for Unscheduled Pods](#step-4-scheduler-watches-for-unscheduled-pods)
    - [Step 5: Scheduler Updates API Server](#step-5-scheduler-updates-api-server)
  - [🖥️ Worker Node Flow](#️-worker-node-flow)
    - [Step 6: Kubelet Watches API Server](#step-6-kubelet-watches-api-server)
    - [Step 7: Kubelet → Container Runtime (CRI)](#step-7-kubelet--container-runtime-cri)
    - [Step 8: Container Runtime Responsibilities](#step-8-container-runtime-responsibilities)
    - [Step 9: Networking Setup via CNI](#step-9-networking-setup-via-cni)
    - [Step 10: Kubelet Ensures Desired State](#step-10-kubelet-ensures-desired-state)
    - [Step 11: kube-proxy Handles Service Networking](#step-11-kube-proxy-handles-service-networking)
  - [🔄 Summary Flow](#-summary-flow)
  - [📊 Kubernetes Pod Creation \& Networking Flow](#-kubernetes-pod-creation--networking-flow-1)
  - [🔄 Kubernetes Pod Creation \& Networking Flow (Step-by-Step)](#-kubernetes-pod-creation--networking-flow-step-by-step)
    - [🚀 Step-by-Step Flow](#-step-by-step-flow)
    - [🖥️ Worker Node Execution](#️-worker-node-execution)
    - [🌐 Networking Setup](#-networking-setup)
    - [🔁 Monitoring \& Service Networking](#-monitoring--service-networking)
  - [🔗 Control Plane Communication](#-control-plane-communication)
    - [🔹 1️⃣ kubectl (CLI)](#-1️⃣-kubectl-cli)
    - [🔹 2️⃣ API (REST / YAML / JSON)](#-2️⃣-api-rest--yaml--json)
  - [🐳 Docker vs ☸️ Kubernetes](#-docker-vs-️-kubernetes)
  - [📦 Pod Concept](#-pod-concept)
  - [🚀 Pod Creation Methods](#-pod-creation-methods)
    - [1️⃣ Imperative Way (CLI)](#1️⃣-imperative-way-cli)
      - [Commands:](#commands)
    - [2️⃣ Declarative Way (YAML)](#2️⃣-declarative-way-yaml)
  - [📝 YAML Basics](#-yaml-basics)
    - [🔹 Simple Data Types](#-simple-data-types)
      - [Text](#text)
      - [Number](#number)
      - [Boolean](#boolean)
    - [🔹 Complex Data Types](#-complex-data-types)
      - [List / Array](#list--array)
      - [Object / Map](#object--map)
  - [🔢 Kubernetes API Versions](#-kubernetes-api-versions)
    - [1️⃣ Alpha Version](#1️⃣-alpha-version)
    - [2️⃣ Beta Version](#2️⃣-beta-version)
    - [3️⃣ Stable Version (GA)](#3️⃣-stable-version-ga)
  - [✅ Summary](#-summary-2)
  - [🔍 API Resources Command](#-api-resources-command)
    - [💡 What it shows:](#-what-it-shows)
  - [📄 Basic Kubernetes Manifest (YAML)](#-basic-kubernetes-manifest-yaml)
    - [🔑 Explanation:](#-explanation)
  - [✅ Quick Note](#-quick-note)
  - [📄 Kubernetes Manifest File Structure](#-kubernetes-manifest-file-structure)
    - [🧩 Basic Structure](#-basic-structure)
  - [🔑 Field Explanation](#-field-explanation)
    - [1️⃣ apiVersion](#1️⃣-apiversion)
    - [2️⃣ kind](#2️⃣-kind)
    - [3️⃣ metadata](#3️⃣-metadata)
    - [4️⃣ spec](#4️⃣-spec)
    - [5️⃣ status (Auto-generated)](#5️⃣-status-auto-generated)
  - [📌 Example](#-example)
  - [✅ Summary](#-summary-3)
- [☸️ Kubernetes Cluster Setup (3 Nodes using kubeadm)](#️-kubernetes-cluster-setup-3-nodes-using-kubeadm)
  - [📌 Overview](#-overview-1)
  - [⚙️ Prerequisites](#️-prerequisites)
  - [🚀 Step 1: Create Instances](#-step-1-create-instances)
  - [🔄 Step 2: Initial Setup (All Nodes)](#-step-2-initial-setup-all-nodes)
  - [📦 Step 3: Install Container Runtime (All Nodes)](#-step-3-install-container-runtime-all-nodes)
    - [Install Docker](#install-docker)
    - [Install CRI-Dockerd](#install-cri-dockerd)
    - [Install Additional Packages](#install-additional-packages)
    - [Configure containerd](#configure-containerd)
  - [☸️ Step 4: Install Kubernetes Components (All Nodes)](#️-step-4-install-kubernetes-components-all-nodes)
  - [🧠 Step 5: Initialize Master Node](#-step-5-initialize-master-node)
    - [Configure kubectl (Master Node)](#configure-kubectl-master-node)
  - [🔗 Step 6: Join Worker Nodes](#-step-6-join-worker-nodes)
  - [🌐 Step 7: Install CNI Plugin (Master Node)](#-step-7-install-cni-plugin-master-node)
    - [Flannel](#flannel)
    - [Weave](#weave)
  - [✅ Step 8: Verify Cluster](#-step-8-verify-cluster)
  - [🚀 Step 9: Deploy Sample Pod](#-step-9-deploy-sample-pod)
    - [Create YAML File](#create-yaml-file)
    - [Apply Pod](#apply-pod)
    - [Check Pods](#check-pods)
  - [🎯 Final Result](#-final-result)
- [⚙️ Kubernetes Pod Commands (kubectl)](#️-kubernetes-pod-commands-kubectl)
  - [🚀 Create Pod](#-create-pod)
  - [📄 Get Pod Information](#-get-pod-information)
  - [🔄 Watch Pod Status (Real-Time)](#-watch-pod-status-real-time)
  - [❌ Delete Pod](#-delete-pod)
  - [🔁 Replace Pod (Force)](#-replace-pod-force)
  - [🖥️ Login into Pod (Exec)](#️-login-into-pod-exec)
  - [🔍 Describe Pod (Detailed Info)](#-describe-pod-detailed-info)
  - [🧾 Get Pod YAML Configuration](#-get-pod-yaml-configuration)
- [Main Containers in Kubernetes](#main-containers-in-kubernetes)
  - [Key Points](#key-points)
  - [Running Application Inside a Pod](#running-application-inside-a-pod)
    - [Example](#example)
  - [Single Container Pod Example (Nginx)](#single-container-pod-example-nginx)
  - [Alpine Container Behavior](#alpine-container-behavior)
  - [Kubernetes Pod with Command \& Args](#kubernetes-pod-with-command--args)
  - [Summary](#summary)
- [Init Containers in Kubernetes](#init-containers-in-kubernetes)
  - [Key Points](#key-points-1)
  - [Why Use Init Containers?](#why-use-init-containers)
    - [Example Use Case](#example-use-case)
  - [Example: Init Container with Shared Volume](#example-init-container-with-shared-volume)
  - [Summary](#summary-1)
- [Sidecar Containers in Kubernetes](#sidecar-containers-in-kubernetes)
  - [Key Points](#key-points-2)
  - [Why Use Sidecar Containers?](#why-use-sidecar-containers)
    - [Common Use Cases](#common-use-cases)
  - [Example: Sidecar for Log Monitoring](#example-sidecar-for-log-monitoring)
  - [Summary](#summary-2)
- [Ambassador Containers](#ambassador-containers)
  - [Key Points](#key-points-3)
    - [Communication Flow](#communication-flow)
    - [Why Use Ambassador Containers?](#why-use-ambassador-containers)
    - [Example Use Case](#example-use-case-1)
- [Ephemeral Containers](#ephemeral-containers)
  - [Key Points](#key-points-4)
  - [Why Use Ephemeral Containers?](#why-use-ephemeral-containers)
    - [Example Use Case](#example-use-case-2)
    - [Summary](#summary-3)
- [MySQL Database Pod Creation in Kubernetes](#mysql-database-pod-creation-in-kubernetes)
  - [1. Using Docker](#1-using-docker)
    - [Pull MySQL Image](#pull-mysql-image)
    - [Run MySQL Container](#run-mysql-container)
    - [Explanation](#explanation)
  - [2. Using Kubernetes Pod (YAML)](#2-using-kubernetes-pod-yaml)
  - [3. Deploy the Pod](#3-deploy-the-pod)
  - [4. Access the Pod](#4-access-the-pod)
  - [5. Login to MySQL Database](#5-login-to-mysql-database)
    - [Example](#example-1)
- [Pod Lifecycle in Kubernetes](#pod-lifecycle-in-kubernetes)
  - [1. Pending](#1-pending)
    - [Pod Status Table](#pod-status-table)
  - [2. Running](#2-running)
    - [Pod Status Table](#pod-status-table-1)
  - [3. Succeeded (Completed)](#3-succeeded-completed)
    - [Example YAML](#example-yaml)
    - [Pod Status Table](#pod-status-table-2)
  - [4. Failed](#4-failed)
    - [Example YAML](#example-yaml-1)
    - [Pod Status Table](#pod-status-table-3)
  - [5. Unknown](#5-unknown)
- [Container States in Kubernetes](#container-states-in-kubernetes)
  - [1. Waiting](#1-waiting)
  - [2. Running](#2-running-1)
  - [3. Terminated (Success)](#3-terminated-success)
  - [4. Terminated (Error)](#4-terminated-error)
  - [Summary Table](#summary-table)
- [Amazon EKS (Elastic Kubernetes Service)](#amazon-eks-elastic-kubernetes-service)
  - [EKS Cluster Architecture](#eks-cluster-architecture)
  - [1. Control Plane (Managed by AWS)](#1-control-plane-managed-by-aws)
  - [2. Data Plane (Managed by User)](#2-data-plane-managed-by-user)
  - [Summary](#summary-4)
- [Creation of EKS Cluster](#creation-of-eks-cluster)
  - [Ways to Create an EKS Cluster](#ways-to-create-an-eks-cluster)
  - [Creating EKS Cluster using eksctl](#creating-eks-cluster-using-eksctl)
    - [Step 1: Create Server \& Connect](#step-1-create-server--connect)
    - [Step 2: Update System](#step-2-update-system)
    - [Step 3: Install AWS CLI](#step-3-install-aws-cli)
    - [Step 4: Install kubectl](#step-4-install-kubectl)
    - [Step 5: Install eksctl](#step-5-install-eksctl)
    - [Step 6: Create EKS Cluster](#step-6-create-eks-cluster)
  - [Label-Based Filtering Commands](#label-based-filtering-commands)
- [EKS Cluster Creation using Terraform](#eks-cluster-creation-using-terraform)
  - [Step 1: Create Server \& Connect](#step-1-create-server--connect-1)
  - [Step 2: Install Required Packages](#step-2-install-required-packages)
  - [Step 3: Install AWS CLI](#step-3-install-aws-cli-1)
  - [Step 4: Install Terraform](#step-4-install-terraform)
  - [Step 4: Use Terraform EKS Repository](#step-4-use-terraform-eks-repository)
  - [Step 5: Deploy EKS Cluster](#step-5-deploy-eks-cluster)
  - [Step 6: Verify Cluster in AWS](#step-6-verify-cluster-in-aws)
  - [Step 7: Verify using kubectl](#step-7-verify-using-kubectl)
  - [Step 8: Install kubectl](#step-8-install-kubectl)
  - [Step 9: Configure kubeconfig](#step-9-configure-kubeconfig)
    - [Example](#example-2)
  - [Kubernetes Networking Concept](#kubernetes-networking-concept)
- [EKS Cluster Service Type: ClusterIP](#eks-cluster-service-type-clusterip)
  - [ClusterIP Service](#clusterip-service)
  - [Key Points](#key-points-5)
  - [How It Works](#how-it-works)
  - [Pod YAML Example](#pod-yaml-example)
  - [Service YAML (ClusterIP)](#service-yaml-clusterip)
  - [To Check Pods](#to-check-pods)
  - [To Check Service](#to-check-service)
  - [How to Communicate (Internal Access)](#how-to-communicate-internal-access)
    - [Get Service ClusterIP:](#get-service-clusterip)
    - [Access using curl:](#access-using-curl)
  - [Interview Point ⭐](#interview-point-)
- [NodePort Service in Kubernetes](#nodeport-service-in-kubernetes)
  - [What is NodePort?](#what-is-nodeport)
  - [Key Points](#key-points-6)
  - [Architecture](#architecture)
  - [Prerequisites (EKS Setup)](#prerequisites-eks-setup)
    - [Install:](#install)
  - [Pod YAML](#pod-yaml)
  - [Service YAML (NodePort)](#service-yaml-nodeport)
  - [To Check Pods](#to-check-pods-1)
  - [To Check Service](#to-check-service-1)
  - [How to Access Application](#how-to-access-application)
    - [1. Get Node IP:](#1-get-node-ip)
    - [2. Access in browser:](#2-access-in-browser)
- [LoadBalancer Service in Kubernetes](#loadbalancer-service-in-kubernetes)
  - [What is LoadBalancer?](#what-is-loadbalancer)
  - [Key Points](#key-points-7)
  - [Architecture](#architecture-1)
  - [Pod YAML](#pod-yaml-1)
  - [Service YAML (LoadBalancer)](#service-yaml-loadbalancer)
  - [Apply Resources](#apply-resources)
    - [Check Pods](#check-pods-1)
    - [Check Service](#check-service)
  - [How to Access](#how-to-access)
- [ExternalName / External DNS Name](#externalname--external-dns-name)
  - [Pod YAML](#pod-yaml-2)
  - [serviec YAML(Service)](#serviec-yamlservice)
- [Service types flow in K8S:](#service-types-flow-in-k8s)
- [Kubernetes Restart Policy](#kubernetes-restart-policy)
  - [Overview](#overview)
  - [Types of Restart Policies](#types-of-restart-policies)
    - [1. Always (Default)](#1-always-default)
    - [2. OnFailure](#2-onfailure)
    - [3. Never](#3-never)
- [Kubernates Restart Policy](#kubernates-restart-policy)
    - [Summary](#summary-5)
- [Kubernetes Pod Probes (Startup Probe)](#kubernetes-pod-probes-startup-probe)
  - [Overview](#overview-1)
  - [Types of Probes](#types-of-probes)
  - [Startup Probe](#startup-probe)
    - [Definition](#definition)
    - [Key Behavior](#key-behavior)
    - [Why Use Startup Probe?](#why-use-startup-probe)
- [Kubernetes Probe Types \& Arguments](#kubernetes-probe-types--arguments)
  - [Supported Probe Types](#supported-probe-types)
    - [httpGet](#httpget)
    - [grpc](#grpc)
    - [tcpSocket](#tcpsocket)
    - [exec](#exec)
  - [Probe Arguments](#probe-arguments)
    - [initialDelaySeconds](#initialdelayseconds)
    - [periodSeconds](#periodseconds)
    - [successThreshold](#successthreshold)
  - [Summary](#summary-6)
    - [Kubernates Startup Probe Figure](#kubernates-startup-probe-figure)
- [Kubernetes Liveness Probe](#kubernetes-liveness-probe)
  - [Overview](#overview-2)
  - [Key Points](#key-points-8)
  - [Why Use Liveness Probe?](#why-use-liveness-probe)
    - [Kubernates Livensss Probe Figure](#kubernates-livensss-probe-figure)
- [Kubernetes Readiness Probe](#kubernetes-readiness-probe)
  - [Overview](#overview-3)
  - [Key Points](#key-points-9)
  - [Why Use Readiness Probe?](#why-use-readiness-probe)
    - [Kubernates Readiness Probe figure](#kubernates-readiness-probe-figure)
- [Kubernates Probes](#kubernates-probes)
- [Kubernetes Pod Resource Requests \& Limits - Failure](#kubernetes-pod-resource-requests--limits---failure)
  - [Overview](#overview-4)
  - [Requests vs Limits](#requests-vs-limits)
    - [Requests](#requests)
    - [Limits](#limits)
  - [Resource Flow](#resource-flow)
  - [Scenario](#scenario)
  - [Pod Status (Tabular View)](#pod-status-tabular-view)
- [Kubernetes Resource Limits – Successful Run Example](#kubernetes-resource-limits--successful-run-example)
  - [Scenario](#scenario-1)
  - [Pod Configuration](#pod-configuration)
  - [Pod Status (Tabular View)](#pod-status-tabular-view-1)
    - [Kubernates-Resource](#kubernates-resource)
- [Kubernetes Annotations](#kubernetes-annotations)
  - [Definition](#definition-1)
  - [Core Concept](#core-concept)
  - [Key Characteristics](#key-characteristics)
  - [Common Use Cases](#common-use-cases-1)
    - [Example](#example-3)
    - [Kubernates-Annotations](#kubernates-annotations)
- [Kubernetes Namespaces](#kubernetes-namespaces)
  - [Definition](#definition-2)
  - [Resource Scope in Kubernetes](#resource-scope-in-kubernetes)
    - [1. Namespaced Resources](#1-namespaced-resources)
    - [2. Cluster-Scoped Resources](#2-cluster-scoped-resources)
  - [RBAC and Namespaces](#rbac-and-namespaces)
  - [Real-World Usage](#real-world-usage)
  - [Default Kubernetes Namespaces](#default-kubernetes-namespaces)
  - [Working with Namespaces in Kubernetes (Step-by-Step)](#working-with-namespaces-in-kubernetes-step-by-step)
    - [Step 1: Create a Namespace](#step-1-create-a-namespace)
    - [Step 2: Create a Pod](#step-2-create-a-pod)
    - [Step 3: Check Pods (Default Behavior)](#step-3-check-pods-default-behavior)
    - [Step 4: Switch to prod Namespace](#step-4-switch-to-prod-namespace)
    - [Step 5: Check Pods Again](#step-5-check-pods-again)
    - [Alternative: Access Without Switching Namespace](#alternative-access-without-switching-namespace)
    - [Example](#example-4)
    - [Kubernates - Namespaces](#kubernates---namespaces)
- [Kubernetes Networking Model (Inside a Worker Node)](#kubernetes-networking-model-inside-a-worker-node)
  - [Overview](#overview-5)
  - [Core Concept](#core-concept-1)
  - [Communication Flow (Inside a Worker Node)](#communication-flow-inside-a-worker-node)
    - [Step 1: Container Inside Pod](#step-1-container-inside-pod)
    - [Step 2: Pod Network Namespace](#step-2-pod-network-namespace)
    - [Step 3: veth Pair (Virtual Ethernet Pair)](#step-3-veth-pair-virtual-ethernet-pair)
    - [Step 4: Bridge Network](#step-4-bridge-network)
    - [Step 5: Node Network Interface (eth0)](#step-5-node-network-interface-eth0)
- [Kubernetes Networking Flow (Mermaid Diagram)](#kubernetes-networking-flow-mermaid-diagram)
- [Kubernetes Networking Flows](#kubernetes-networking-flows)
  - [Pods on (Same Node)](#pods-on-same-node)
    - [Explanation](#explanation-1)
  - [Pods on (Different Node) (Mermaid)](#pods-on-different-node-mermaid)
  - [2. Pod → Pod Networking](#2-pod--pod-networking)
    - [Same Node](#same-node)
    - [Different Nodes](#different-nodes)
  - [3. Pod → Service Networking](#3-pod--service-networking)
    - [Pod → Service](#pod--service)
    - [Service → Pod](#service--pod)
  - [4. Internet → Service](#4-internet--service)

---

## 🐳 Container Tools

Container tools are used to create and run containers. The most common tools include:

- **Docker**
  - Full container platform
  - Used to build, package, and run containers

- **containerd**
  - Lightweight container runtime
  - Extracted from Docker
  - Commonly used by Kubernetes

- **CRI-O**
  - Kubernetes-native container runtime
  - Directly implements CRI (Container Runtime Interface)

- **rkt (Rocket)**
  - Alternative container engine
  - Focused on security

---

## ☸️ Kubernetes Overview

Kubernetes is a container orchestration platform that helps manage containers across multiple servers.

### Key Features:

- Load balancing
- Auto-scaling
- Self-healing
- Zero-downtime deployments
- Rolling updates

---

## ⚙️ Containerization vs Orchestration

- **Containerization**
  - Creating containers
  - Done using tools like Docker

- **Orchestration**
  - Managing containers at scale
  - Done using Kubernetes

---

## 🏗️ Kubernetes Cluster Architecture

- **Master Node (Control Plane)**
  - Manages the cluster
  - Responsible for scheduling, API, and control

- **Worker Node**
  - Runs applications (containers)

---

## 🔀 Types of Kubernetes Clusters

### 1️⃣ Single Node Cluster

- Only one node
- Acts as both **master + worker**
- Control plane and applications run on the same machine

#### Used For:

- Learning
- Testing

#### Examples:

- Minikube
- K3s
- Kind

---

### 2️⃣ Multi Node Cluster

- Multiple nodes
  - One or more master nodes
  - Multiple worker nodes

#### Used In:

- Production environments

#### Provides:

- High availability
- Scalability
- Fault tolerance

---

## 🖥️ Self-Hosted Kubernetes Cluster

A **self-hosted cluster** is when we manually install and configure Kubernetes on our own infrastructure.

#### Tools:

- kubeadm
- KOPS
- kube-spray

👉 If a company is not using cloud, it is called **on-premises**.

---

## ☁️ Cloud Hosted Kubernetes Services

Managed Kubernetes services provided by cloud providers:

- **AWS → EKS (Elastic Kubernetes Service)**
- **Azure → AKS (Azure Kubernetes Service)**

---

## ✅ Summary

- Docker → Containerization
- Kubernetes → Orchestration
- containerd / CRI-O → Container runtimes
- Clusters → Single-node (learning) & Multi-node (production)
- Deployment → Self-hosted (on-prem) or Cloud-hosted

---

# ☸️ Kubernetes Architecture (K8s)

---

## 📌 Overview

Kubernetes architecture is divided into two main parts:

- **Control Plane (Master Node)** → Manages the cluster
- **Worker Nodes** → Run application workloads (Pods)

---

## 🧠 Control Plane Components

### 1️⃣ Kube API Server

- Main entry point of the cluster
- All components communicate through it
- Processes REST requests
- Updates cluster state in etcd

💡 **Interview Line:**
The API Server acts as the gateway of Kubernetes. All internal and external communication happens through it.

---

### 2️⃣ etcd

- Distributed key-value store (database)
- Stores:
  - Pods
  - Nodes
  - ConfigMaps
  - Secrets

- Single source of truth

💡 **Interview Line:**
etcd stores the entire cluster state in key-value format, making it critical for consistency.

---

### 3️⃣ Kube Scheduler

- Assigns Pods to Nodes
- Checks:
  - CPU
  - Memory
  - Policies

- Does NOT create pods

💡 **Interview Line:**
The scheduler watches for unscheduled pods and assigns them to the most suitable node.

---

### 4️⃣ Kube Controller Manager

- Ensures **Desired State = Actual State**

#### What is Desired State?

If 3 pods are required and 1 fails → Kubernetes creates a new pod automatically.

💡 **Interview Line:**
Controller Manager ensures the cluster always matches the desired state defined by the user.

---

## 🔁 Controller Manager & Controllers

### 1. Node Controller

- Monitors node health
- If a node fails:
  - Pods are rescheduled

---

### 2. Replication Controller / ReplicaSet

- Maintains required number of pod replicas

**Example:**

- Required: 3 Pods
- Running: 2 Pods
  → Creates 1 new pod

---

### 3. Endpoint Controller

- Manages Endpoints for Services
- Tracks pods using labels

**Example:**

- Service selector: `app=nginx`
  → Updates pod IP list

---

### 4. Service Account Controller

- Manages service accounts
- Provides identity & access

**Key Points:**

- Each namespace has a default service account
- Used for authentication & authorization
- Controls pod access to APIs across namespaces

---

## 🖥️ Worker Node Components in Kubernetes

A **Kubernetes worker node** is responsible for running application workloads (Pods). The key components are:

---

### 1️⃣ Kubelet

- Kubelet is an agent that runs on each worker node
- Registers the node with the cluster
- Communicates with the Control Plane (API Server)
- Ensures containers defined in Pod specifications are running and healthy
- Continuously watches Pod specs from the API Server and executes them on the node

---

### 2️⃣ Kube-Proxy

- Kube-proxy is a networking component
- Manages service communication and routing in Kubernetes

> ⚠️ Note:
> Kubernetes does not provide built-in networking.
> It uses **CNI plugins** like:

- Calico
- Flannel
- Weave Net

These plugins handle Pod networking and IP management.

---

### 3️⃣ Container Runtime

- Software responsible for running containers
- Pulls container images and starts/stops containers
- Works based on instructions from Kubelet

**Examples:**

- containerd
- CRI-O
- Docker (deprecated in Kubernetes)

---

## 🎯 Key Interview Points

- **API Server** → Communication gateway
- **etcd** → Cluster database (source of truth)
- **Scheduler** → Assigns pods to nodes
- **Controller Manager** → Maintains desired state
- **Kubelet** → Node agent
- **Kube-proxy** → Networking
- **CNI** → Pod networking
- **Container Runtime** → Runs containers

---

## ✅ Summary

- Control Plane manages cluster
- Worker Nodes run applications
- Kubernetes ensures:
  - High availability
  - Self-healing
  - Auto-scaling

- Desired state is always maintained automatically

---

# 🚀 Kubernetes Pod Creation & Networking Flow

This document explains the step-by-step flow of how a Pod is created and how networking is established in Kubernetes.

---

## 📌 Control Plane Flow

### Step 1: Request to API Server

The user (via `kubectl` or API call) sends a Pod creation request to the API Server, which acts as the entry point to the Kubernetes control plane.

---

### Step 2: Validation & Persistence

- The API Server:
  - Authenticates the request
  - Validates the configuration
- Stores the desired state of the Pod in **etcd** (key-value store)

---

### Step 3: Controller Manager Reaction

- Continuously watches the API Server
- Ensures desired state is maintained
- Example:
  - Ensures required Pod objects exist

---

### Step 4: Scheduler Watches for Unscheduled Pods

⚠️ Important: Scheduler looks for **unscheduled Pods** (not just new Pods)

- Scheduler:
  - Monitors Pods without assigned nodes
  - Selects best worker node based on:
    - CPU / Memory
    - Constraints (taints, affinity, etc.)

---

### Step 5: Scheduler Updates API Server

- Scheduler binds the Pod to a selected node
- Updates Pod specification in API Server

---

## 🖥️ Worker Node Flow

### Step 6: Kubelet Watches API Server

- Kubelet on the worker node:
  - Detects Pods assigned to its node
  - Watches API Server continuously

---

### Step 7: Kubelet → Container Runtime (CRI)

- Kubelet retrieves Pod spec
- Communicates with container runtime via **CRI (Container Runtime Interface)**

---

### Step 8: Container Runtime Responsibilities

The container runtime (e.g., containerd, CRI-O):

- Pulls image from registry (if not present)
- Creates container(s)
- Starts container(s)
- Manages lifecycle:
  - Start
  - Stop
  - Restart

---

### Step 9: Networking Setup via CNI

- CNI (Container Network Interface) plugin is invoked

**Responsibilities:**

- Assigns unique IP to Pod
- Configures network interfaces
- Enables Pod-to-Pod communication

---

### Step 10: Kubelet Ensures Desired State

- Monitors container health
- Restarts failed containers
- Reports status to API Server

---

### Step 11: kube-proxy Handles Service Networking

- Runs on each node
- Configures networking rules using:
  - iptables or IPVS

**Responsibilities:**

- Enables Service → Pod communication
- Provides load balancing across Pods

---

## 🔄 Summary Flow

User → API Server → etcd
↓
Controller Manager
↓
Scheduler → Assign Node
↓
Kubelet → Container Runtime
↓
CNI → Networking Setup
↓
kube-proxy → Service Routing

---

## 📊 Kubernetes Pod Creation & Networking Flow

![Kubernetes Architecture](images/Kubernates-Pod-creation-&-Network-Flow.png)

---

## 🔄 Kubernetes Pod Creation & Networking Flow (Step-by-Step)

This section outlines the complete lifecycle of a Pod from creation to networking setup.

---

### 🚀 Step-by-Step Flow

1. **User Request**
   - User sends Pod creation request to the API Server (`kubectl` / API call)

2. **API Server Validation**
   - API Server validates the request
   - Stores desired state in **etcd**

3. **Controller Manager**
   - Watches API Server
   - Ensures desired state is maintained

4. **Scheduler**
   - Identifies **unscheduled Pods**
   - Selects the most suitable worker node

5. **Node Binding**
   - Scheduler updates API Server with selected node

---

### 🖥️ Worker Node Execution

6. **Kubelet Detection**
   - Kubelet watches API Server
   - Detects Pod assigned to its node

7. **Pod Specification Retrieval**
   - Kubelet retrieves Pod spec from API Server

8. **CRI Communication**
   - Kubelet communicates with container runtime via **CRI**

9. **Image Pull**
   - Container runtime pulls image from registry (if not present)

10. **Container Creation**

- Container runtime creates and starts container(s)

---

### 🌐 Networking Setup

11. **CNI Plugin**

- Assigns Pod IP
- Configures network interfaces
- Enables Pod-to-Pod communication

---

### 🔁 Monitoring & Service Networking

12. **Kubelet Monitoring**

- Ensures Pod is running as per desired state
- Restarts containers if needed

13. **Status Reporting**

- Kubelet reports Pod status to API Server

14. **kube-proxy**

- Configures **iptables/IPVS**
- Enables Service-to-Pod communication
- Provides load balancing

---

## 🔗 Control Plane Communication

We can communicate with the **Kubernetes Control Plane (Master Node)** in the following ways:

### 🔹 1️⃣ kubectl (CLI)

- `kubectl` is a command-line tool
- Most commonly used method
- Sends requests to the API Server

---

### 🔹 2️⃣ API (REST / YAML / JSON)

- Direct communication with API Server
- Supports:
  - YAML
  - JSON

- Used by:
  - Automation tools
  - Scripts
  - CI/CD pipelines

💡 **Summary:**
We can communicate using `kubectl` or directly via API, but in real-time **kubectl is mostly used**.

---

## 🐳 Docker vs ☸️ Kubernetes

| Feature    | Docker                      | Kubernetes                 |
| ---------- | --------------------------- | -------------------------- |
| Creation   | Directly creates containers | Creates Pods first         |
| Execution  | Containers run directly     | Containers run inside Pods |
| Management | Single host                 | Multi-node orchestration   |

💡 **Key Point:**
Docker creates containers directly, whereas Kubernetes creates **Pods**, and containers run inside those Pods.

---

## 📦 Pod Concept

- Pod is the **smallest deployable unit** in Kubernetes
- Contains **one or more containers**
- Each Pod:
  - Has a **single IP address**
  - Runs in an **isolated environment**
  - Containers share:
    - Network
    - Storage

💡 **Important:**

- Containers inside a Pod **do NOT have individual IPs**
- Communication happens using the **Pod IP**

---

## 🚀 Pod Creation Methods

There are **2 ways to create Pods**:

---

### 1️⃣ Imperative Way (CLI)

- Create directly using commands
- No history maintained

#### Commands:

```bash
To create the pod: kubectl run pod bablu --image=nginx
To know the node: kubectl get no
To know the pods: kubectl get po
To see the pod is running or not: kubectl get po -w
```

---

### 2️⃣ Declarative Way (YAML)

- Used in real-time projects
- Uses **YAML manifest files**
- Maintains history (version control)

---

## 📝 YAML Basics

### 🔹 Simple Data Types

#### Text

```yaml
name: nikhil
name: "nikhil"
name: 'nikhil'
```

#### Number

```yaml
age: 22
```

#### Boolean

```yaml
pass: true
pass: false
pass: No
```

---

### 🔹 Complex Data Types

#### List / Array

```yaml
qual: ["devops", "aws", "azure"]

qual:
  - devops
  - aws
  - azure
```

---

#### Object / Map

```yaml
address:
  RoomNo: 2-7/1
  Village: "kismathpur"
  landmark:
    - yellow house
    - Vaishnavi oasis
  PhoneNumbers: ["9009001234", "7890123456"]
```

---

## 🔢 Kubernetes API Versions

Kubernetes has **3 types of API versions**:

---

### 1️⃣ Alpha Version

- Early-stage features
- Not stable
- May contain bugs
- Disabled by default
- Used for testing

```yaml
apiVersion: batch/v2alpha1
```

---

### 2️⃣ Beta Version

- More stable than Alpha
- Testing phase
- Enabled by default
- Used for pre-production

```yaml
apiVersion: apps/v1beta1
```

---

### 3️⃣ Stable Version (GA)

- Fully tested
- Production-ready
- Long-term support

```yaml
apiVersion: apps/v1
```

💡 Example:

- Deployments use `apps/v1`

---

## ✅ Summary

- `kubectl` → Most common communication tool
- API → Used for automation
- Docker → Creates containers
- Kubernetes → Creates Pods
- Pod → Smallest unit with shared IP
- YAML → Declarative configuration
- API Versions → Alpha, Beta, Stable

---

## 🔍 API Resources Command

To know details like **API versions, namespaces, and resource kinds**, use:

```bash
kubectl api-resources
```

### 💡 What it shows:

- Available Kubernetes resources (Pods, Services, Deployments, etc.)
- Supported API versions
- Whether resources are **namespaced or cluster-wide**

---

## 📄 Basic Kubernetes Manifest (YAML)

A simple Pod definition in YAML format:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: nginx-container
      image: nginx
```

---

### 🔑 Explanation:

- **apiVersion** → Defines Kubernetes API version
- **kind** → Type of resource (Pod)
- **metadata** → Name and identifiers
- **spec** → Actual configuration (containers, images, etc.)

---

## ✅ Quick Note

- `kubectl api-resources` → Helps explore cluster capabilities
- YAML manifest → Used in **declarative approach**
- `apiVersion + kind + metadata + spec` → Core structure of every Kubernetes object

---

## 📄 Kubernetes Manifest File Structure

A **Manifest file** in Kubernetes is written in YAML format and defines the desired state of a resource.

---

### 🧩 Basic Structure

```yaml id="k9d2hx"
apiVersion: <apiVersion/group>
kind: <resource-type>
metadata:
  name: <name>
  namespace: <namespace>
  annotations: <optional>
spec: <desired-state-configuration>
```

---

## 🔑 Field Explanation

### 1️⃣ apiVersion

- Defines the API version of the resource
- Format: `<group>/<version>`

**Examples:**

- `v1`
- `apps/v1`
- `batch/v1`

---

### 2️⃣ kind

- Specifies the type of Kubernetes resource

**Examples:**

- Pod
- Deployment
- Service

---

### 3️⃣ metadata

- Provides additional information about the resource

**Common fields:**

- `name` → Name of the resource
- `namespace` → Logical grouping
- `annotations` → Extra metadata
- `labels` → Used for selection & grouping

---

### 4️⃣ spec

- Defines **what you want** (desired state)

**Examples:**

- Container image
- Ports
- Replicas
- Volumes

---

### 5️⃣ status (Auto-generated)

- Shows the **current state** of the resource
- Automatically maintained by Kubernetes
- Not required in YAML file

---

## 📌 Example

```yaml id="r5z7bm"
apiVersion: v1
kind: Pod
metadata:
  name: my-nginx
  namespace: default
spec:
  containers:
    - name: nginx-container
      image: nginx
      ports:
        - containerPort: 80
```

---

## ✅ Summary

- Manifest file defines Kubernetes objects
- Written in YAML format
- Key sections:
  - `apiVersion`
  - `kind`
  - `metadata`
  - `spec`

- `status` is system-generated

---

# ☸️ Kubernetes Cluster Setup (3 Nodes using kubeadm)

---

## 📌 Overview

This guide explains how to set up a **Kubernetes cluster with:**

- 1 Master Node (Control Plane)
- 2 Worker Nodes

---

## ⚙️ Prerequisites

- 3 Ubuntu instances
- SSH access to all nodes
- Public IPs for all instances

---

## 🚀 Step 1: Create Instances

- Create:
  - 1 Master Node
  - 2 Worker Nodes

- Login to all nodes:

```bash id="cmd1"
ssh ubuntu@<public-ip>
```

---

## 🔄 Step 2: Initial Setup (All Nodes)

Update packages:

```bash id="cmd2"
sudo apt update
```

---

## 📦 Step 3: Install Container Runtime (All Nodes)

### Install Docker

```bash id="cmd3"
sudo apt install -y docker.io
```

---

### Install CRI-Dockerd

```bash id="cmd4"
wget https://github.com/Mirantis/cri-dockerd/releases/download/v0.4.0/cri-dockerd_0.4.0.3-0.ubuntu-jammy_amd64.deb
sudo dpkg -i cri-dockerd_0.4.0.3-0.ubuntu-jammy_amd64.deb
```

---

### Install Additional Packages

```bash id="cmd5"
sudo apt install -y curl gnupg2 software-properties-common apt-transport-https ca-certificates
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install -y containerd.io
```

---

### Configure containerd

```bash id="cmd6"
containerd config default | sudo tee /etc/containerd/config.toml > /dev/null
sudo sed -i 's/SystemdCgroup = false/SystemdCgroup = true/g' /etc/containerd/config.toml
sudo systemctl restart containerd
sudo systemctl enable containerd
```

---

## ☸️ Step 4: Install Kubernetes Components (All Nodes)

```bash id="cmd7"
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl gpg
sudo mkdir -p -m 755 /etc/apt/keyrings
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.33/deb/Release.key | \
sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.33/deb/ /' | \
sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
```

---

## 🧠 Step 5: Initialize Master Node

Run on **Master Node only**:

```bash id="cmd8"
sudo -i
kubeadm init --pod-network-cidr=10.244.0.0/16 \
--cri-socket=unix:///var/run/cri-dockerd.sock
```

---

### Configure kubectl (Master Node)

```bash id="cmd9"
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

---

## 🔗 Step 6: Join Worker Nodes

Run on **Worker Nodes**:

```bash id="cmd10"
sudo -i
kubeadm join <master-ip>:6443 --token <token> \
--discovery-token-ca-cert-hash sha256:<hash> \
--cri-socket=unix:///var/run/cri-dockerd.sock
```

---

## 🌐 Step 7: Install CNI Plugin (Master Node)

If nodes show **NotReady**, install CNI:

### Flannel

```bash id="cmd11"
kubectl apply -f https://github.com/coreos/flannel/raw/master/Documentation/kube-flannel.yml
```

### Weave

```bash id="cmd12"
kubectl apply -f https://github.com/weaveworks/weave/releases/download/v2.8.1/weave-daemonset-k8s.yaml
```

---

## ✅ Step 8: Verify Cluster

```bash id="cmd13"
kubectl get nodes
```

👉 Status should be **Ready**

---

## 🚀 Step 9: Deploy Sample Pod

### Create YAML File

```yaml id="cmd14"
apiVersion: v1
kind: Pod
metadata:
  name: my-pod-testing
spec:
  containers:
    - name: my-test-image
      image: httpd:latest
      ports:
        - containerPort: 8080
          protocol: TCP
```

---

### Apply Pod

```bash id="cmd15"
kubectl apply -f <file-name>.yaml
```

---

### Check Pods

```bash id="cmd16"
kubectl get po
```

---

## 🎯 Final Result

- Cluster with 3 nodes is ready
- Networking configured using CNI
- Sample Pod successfully deployed

---

# ⚙️ Kubernetes Pod Commands (kubectl)

This section covers commonly used `kubectl` commands to manage Pods.

---

## 🚀 Create Pod

```bash
kubectl apply -f <filename.yaml>
```

> Creates a Pod using the specified YAML configuration file

---

## 📄 Get Pod Information

```bash
kubectl get po
```

> Lists all Pods in the current namespace

---

## 🔄 Watch Pod Status (Real-Time)

```bash
kubectl get po -w
```

> Continuously watches Pod status (Running, Pending, Error, etc.)

---

## ❌ Delete Pod

```bash
kubectl delete pod <podname>
```

> Deletes the specified Pod

---

## 🔁 Replace Pod (Force)

```bash
kubectl replace --force -f <filename.yaml>
```

> Deletes and recreates the Pod from the YAML file

---

## 🖥️ Login into Pod (Exec)

```bash
kubectl exec -it <podname> -- bash
```

> Accesses the Pod container terminal

---

## 🔍 Describe Pod (Detailed Info)

```bash
kubectl describe pod <podname>
```

> Shows detailed Pod information:
>
> - Events
> - Status
> - Containers
> - Node details

---

## 🧾 Get Pod YAML Configuration

```bash
kubectl get pod <podname> -o yaml
```

> Displays the full Pod configuration in YAML format

---

# Main Containers in Kubernetes

Main Containers are the primary containers inside a Kubernetes Pod that run the actual application workload. They start only after all Init Containers have successfully completed and are responsible for serving the application throughout the Pod’s lifecycle.

---

## Key Points

- Main containers run **after Init Containers**.
- They run **continuously** (unlike Init Containers).
- Responsible for **business logic / application execution**.
- A Pod can have **one or more main containers**.
- If a main container crashes, Kubernetes may **restart it** based on the restart policy.
- They define the **Pod’s purpose** (e.g., web server, API, backend service).

---

## Running Application Inside a Pod

- The **main application** runs inside a Kubernetes Pod.
- The container that runs your actual application is called the **Main Container**.

### Example

- Zomato application running in a single container = **Main Container**
- One container in a Pod = **Single Pod with Main Container**

---

## Single Container Pod Example (Nginx)

- A Pod with only one container is the simplest setup.
- Here, we are using an **Nginx image** as the main container.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: mynginximage
      image: nginx:1.29.8
```

---

## Alpine Container Behavior

By default, the Alpine image exits immediately because no long-running process is defined.
To keep it running, we must provide a command.

```bash
docker container run -d -p 80:80 --name myapp alpine:latest sleep 1d
```

---

## Kubernetes Pod with Command & Args

In Kubernetes, we use command and args to override container behavior.

```bash
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: mynginximage
      image: nginx:1.29.8
      command:
        - "sleep"
      args:
        - "1d"
```

---

## Summary

Main Containers are the core of any Kubernetes Pod. They ensure that the actual application runs and remains available throughout the Pod lifecycle.

---

# Init Containers in Kubernetes

Init Containers in Kubernetes are specialized containers that run and complete **before the main application container starts** within a Pod.

---

## Key Points

- Init containers run **sequentially (one by one)**.
- Each init container must **complete successfully** before the next one starts.
- The **main application container will NOT start** until all init containers finish successfully.
- If any init container fails, Kubernetes will **restart it until it succeeds** (based on restart policy).
- They do **not run continuously** like regular containers.

---

## Why Use Init Containers?

Init containers are used to **prepare the environment** before the main application starts.

### Example Use Case

- Ensure a **database is available** before starting the application.
- Run setup scripts (e.g., create files, load configs).
- Wait for external services to become ready.

> Example: An init container runs a script to check if a database is reachable. Only after success, the main container starts.

---

## Example: Init Container with Shared Volume

- The init container writes HTML content into a shared volume.
- The main container (Nginx) serves that content.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: init-cont
spec:
  initContainers:
    - name: init-co
      image: alpine:latest
      command:
        [
          "sh",
          "-c",
          "echo '<h1> This is my app </h1>' >> /usr/share/nginx/html/index.html",
        ]
      volumeMounts:
        - name: init-data
          mountPath: /usr/share/nginx/html

  containers:
    - name: main-app
      image: nginx
      volumeMounts:
        - name: init-data
          mountPath: /usr/share/nginx/html

  volumes:
    - name: init-data
      emptyDir: {}
```

---

## Summary

> Init Containers are used for setup and initialization tasks.
> They ensure the main application starts only when everything is ready.
> They run once and exit, unlike main containers.
> Useful for dependency checks, configuration, and pre-processing tasks.

---

# Sidecar Containers in Kubernetes

A **Sidecar Container** is a secondary container that runs alongside the main container in the same Pod to provide supporting functionality such as logging, monitoring, proxying, or configuration updates.

---

## Key Points

- Runs **along with the main container** (not before like Init Containers)
- Shares:
  - **Network** (same IP address)
  - **Storage** (shared volumes)
- Used for **supporting tasks**, not business logic
- Runs **continuously** as long as the Pod is running

---

## Why Use Sidecar Containers?

Sidecar containers help extend the functionality of the main application without modifying it.

### Common Use Cases

- Log collection and forwarding
- Monitoring and metrics collection
- Reverse proxy (e.g., Envoy, Nginx sidecar)
- Configuration updates
- Security (e.g., service mesh sidecars like Istio)

---

## Example: Sidecar for Log Monitoring

- The main container (Nginx) generates logs.
- The sidecar container (BusyBox) reads and streams logs from the shared volume.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: sidecar-cont
spec:
  containers:
    - name: main-cont
      image: nginx
      volumeMounts:
        - name: nginx-logs
          mountPath: /var/log/nginx

    # Sidecar container for log monitoring
    - name: sidecar-container
      image: busybox
      command: ["sh", "-c"]
      args: ["tail -f /var/log/nginx/error.log"]
      volumeMounts:
        - name: nginx-logs
          mountPath: /var/log/nginx

  volumes:
    - name: nginx-logs
      emptyDir: {}
```

> A sidecar container collects logs from the main application and sends them to a logging system like ELK, while the main container focuses only on business logic.

---

## Summary

> Sidecar containers provide supporting features to the main container.
> They run in parallel with the main application.
> Share network and storage with the main container.
> Commonly used for logging, monitoring, and proxying.

---

# Ambassador Containers

An **Ambassador Container** is a sidecar container pattern used to act as a **proxy between the main application container and external services**.

## Key Points

- Runs inside the **same Pod**
- Acts as a **proxy / gateway**
- Simplifies communication with **external services**
- Follows the **sidecar pattern**

### Communication Flow

> Instead of the main container directly calling an external service: Main Container → Ambassador (localhost) → External Service

### Why Use Ambassador Containers?

- Abstract external service details (URLs, credentials)
- Improve security by isolating external communication
- Simplify application configuration
- Enable easier service replacement or migration

### Example Use Case

> If an application needs to connect to an external database, the **Ambassador container handles the connection**, and the main container communicates with it locally.

---

# Ephemeral Containers

An **Ephemeral Container** is a temporary container used for **debugging purposes** in a running Pod. It can be added without restarting the Pod.

## Key Points

- Used only for **debugging**
- Runs **temporarily** (not permanent)
- Can be added to an **already running Pod**
- Does **NOT restart automatically**
- Cannot define:
  - Ports
  - Volumes
  - Probes

## Why Use Ephemeral Containers?

- Debug issues in running Pods without downtime
- Inspect containers that are crashing or not accessible
- Run troubleshooting tools (e.g., `sh`, `curl`, `netstat`)

### Example Use Case

> If a container is crashing and we cannot `exec` into it, we can attach an **ephemeral container** to the Pod and debug the issue without restarting the Pod.

---

### Summary

| Type                 | Purpose                    | Lifecycle         |
| -------------------- | -------------------------- | ----------------- |
| Ambassador Container | Proxy to external services | Runs continuously |
| Ephemeral Container  | Debugging running Pods     | Temporary         |

---

# MySQL Database Pod Creation in Kubernetes

This guide explains how to create and run a **MySQL database** using both Docker and Kubernetes Pod YAML.

---

## 1. Using Docker

### Pull MySQL Image

```bash
docker pull mysql
```

### Run MySQL Container

```bash
docker container run -d -p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=rootroot \
-e MYSQL_DATABASE=dockerdb \
-e MYSQL_USER=devops \
-e MYSQL_PASSWORD=devops \
--name mysql_test_1 mysql:latest
```

### Explanation

```bash
-d → Run container in background
-p 3306:3306 → Map MySQL port
MYSQL_ROOT_PASSWORD → Root password
MYSQL_DATABASE → Default database
MYSQL_USER → Custom user
MYSQL_PASSWORD → User password
```

---

## 2. Using Kubernetes Pod (YAML)

> Pod Manifest File

```bash
apiVersion: v1
kind: Pod
metadata:
  name: database-pod
spec:
  containers:
    - name: database-cont
      image: mysql
      env:
        - name: MYSQL_ROOT_PASSWORD
          value: "root"
        - name: MYSQL_DATABASE
          value: "dockerdb-1"
        - name: MYSQL_USER
          value: "devops"
        - name: MYSQL_PASSWORD
          value: "devops"
```

---

## 3. Deploy the Pod

```bash
kubectl apply -f <your-file-name>.yaml
```

---

## 4. Access the Pod

> Enter into the Pod

```bash
kubectl exec -it <pod-name> -- bash
```

---

## 5. Login to MySQL Database

```bash
mysql -u <username> -p
```

### Example

```bash
mysql -u devops -p
```

> Enter password when prompted

---

# Pod Lifecycle in Kubernetes

The **Pod Lifecycle** defines the different phases a Pod goes through from creation to termination.

---

## 1. Pending

- The Pod has been **accepted by the cluster** but is not yet running.
- Containers are **not started yet**.

### Pod Status Table

| NAME          | READY | STATUS            | RESTARTS | AGE |
| ------------- | ----- | ----------------- | -------- | --- |
| pod-lifecycle | 1/1   | ContainerCreating | 0        | 40s |

---

## 2. Running

- The Pod is successfully **scheduled on a node**.
- At least one container is **running**.

### Pod Status Table

| NAME          | READY | STATUS  | RESTARTS | AGE |
| ------------- | ----- | ------- | -------- | --- |
| pod-lifecycle | 1/1   | Running | 0        | 40s |

---

## 3. Succeeded (Completed)

> All containers have **terminated successfully**.
> Exit code = **0**

### Example YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-lifecycle
spec:
  containers:
    - name: pod-lifecycle-cont
      image: nginx
      command: ["sh", "-c", "exit 0"]
```

### Pod Status Table

| NAME          | READY | STATUS           | RESTARTS    | AGE |
| ------------- | ----- | ---------------- | ----------- | --- |
| pod-lifecycle | 0/1   | Completed        | 1 (2s ago)  | 3s  |
| pod-lifecycle | 0/1   | CrashLoopBackOff | 1 (2s ago)  | 4s  |
| pod-lifecycle | 0/1   | Completed        | 2 (13s ago) | 15s |

---

## 4. Failed

> At least one container terminated with a non-zero exit code.
> Indicates an error or failure.

### Example YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-lifecycle
spec:
  containers:
    - name: pod-lifecycle-cont
      image: nginx
      command: ["sh", "-c", "exit 1"]
```

### Pod Status Table

| NAME          | READY | STATUS           | RESTARTS    | AGE |
| ------------- | ----- | ---------------- | ----------- | --- |
| pod-lifecycle | 0/1   | Error            | 1 (2s ago)  | 3s  |
| pod-lifecycle | 0/1   | CrashLoopBackOff | 1 (2s ago)  | 4s  |
| pod-lifecycle | 0/1   | Error            | 2 (13s ago) | 15s |

---

## 5. Unknown

> The Pod state cannot be determined.
> Usually caused by node communication issues.

---

![Pod Image](./images/pod-lifecycle.png)

---

# Container States in Kubernetes

Container states describe the current condition of a container inside a Pod.

---

## 1. Waiting

- The container is **not yet running**.
- It is waiting to start due to conditions like:
  - Image pulling
  - Dependency readiness
  - Resource allocation

**Meaning:**  
The container has not started yet and is waiting for required conditions.

---

## 2. Running

- The container is **actively executing** its main process.

**Meaning:**  
The container has started and the application is running.

---

## 3. Terminated (Success)

- The container has **completed execution successfully**.
- Exit code = **0**

**Meaning:**  
The container finished execution without any errors.

---

## 4. Terminated (Error)

- The container has **stopped due to failure**.
- Exit code ≠ **0**

**Meaning:**  
The container exited with an error or failure.

---

## Summary Table

| State                | Description                           |
| -------------------- | ------------------------------------- |
| Waiting              | Not started, waiting for conditions   |
| Running              | Actively executing the application    |
| Terminated (Success) | Completed successfully (exit code 0)  |
| Terminated (Error)   | Failed execution (non-zero exit code) |

---

![Container States](/images/container-states.png)

---

# Amazon EKS (Elastic Kubernetes Service)

Amazon EKS (Elastic Kubernetes Service) is a **managed Kubernetes service** provided by Amazon Web Services that runs Kubernetes control plane components, while allowing users to manage worker nodes and applications.

---

## EKS Cluster Architecture

An EKS cluster consists of two main parts:

---

## 1. Control Plane (Managed by AWS)

- Hosted and managed by **Amazon Web Services**
- Includes:
  - API Server
  - etcd
  - Scheduler
  - Controller Manager
- **Highly available** across multiple Availability Zones (AZs)
- **No direct access** (fully managed by AWS)

---

## 2. Data Plane (Managed by User)

- This is where your **applications run**
- Contains:
  - Worker Nodes (EC2 or Fargate)
  - Pods
  - Containers

---

## Summary

- EKS simplifies Kubernetes management by **offloading control plane operations to AWS**
- Users focus only on **deploying and managing applications**
- Provides **high availability, scalability, and security**

---

# Creation of EKS Cluster

Amazon EKS clusters can be created using multiple approaches:

---

## Ways to Create an EKS Cluster

1. Using **AWS Console (UI)**
2. Using **eksctl (CLI)**
3. Using **eksctl with Terraform (Infrastructure as Code)**

---

## Creating EKS Cluster using eksctl

### Step 1: Create Server & Connect

```bash
ssh ubuntu@<public-ip>
```

---

### Step 2: Update System

```bash
sudo apt update
sudo apt install unzip -y
```

---

### Step 3: Install AWS CLI

> Install AWS CLI using official documentation
> Create an IAM user
> Save:

- > Access Key
- > Secret Key
  > Configure AWS CLI

```bash
aws configure
```

> Enter:

- > Access Key
- > Secret Key
- > Region (e.g., ap-south-1)

---

### Step 4: Install kubectl

```bash
curl -LO https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl

sudo chmod +x kubectl
sudo mv kubectl /usr/local/bin

kubectl version --client
```

---

### Step 5: Install eksctl

```bash
# Set architecture
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

# Download eksctl
curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

# (Optional) Verify checksum
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_checksums.txt" | grep $PLATFORM | sha256sum --check

# Extract and install
tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo mv /tmp/eksctl /usr/local/bin
```

---

### Step 6: Create EKS Cluster

```bash
eksctl create cluster
```

> OR with custom configuration

```bash
eksctl create cluster \
--name mycluster \
--region ap-south-1 \
--nodes 2 \
--node-type c7i-flex.large
```

> ⏱️ Cluster creation takes around 5–15 minutes

> Automatically creates:

- > Worker Nodes
- > Load Balancer
- > Networking components

> Multiple Pod Creation in YAML

- > Use --- to separate multiple resources

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: eks-testing-pod
  labels:
    env: QA
    ver: "1.0"
spec:
  containers:
    - name: test-cont
      image: nginx
---
apiVersion: v1
kind: Pod
metadata:
  name: eks-dev-pod
  labels:
    env: DEV
    ver: "1.1"
spec:
  containers:
    - name: dev-cont
      image: nginx
```

---

## Label-Based Filtering Commands

> Get only DEV Pods

```bash
kubectl get pod -l env=DEV
```

> Get DEV and QA Pods

```bash
kubectl get pod -l 'env in (DEV,QA)'
```

> Filter by Environment and Version

```bash
kubectl get pod -l 'env in (DEV,QA), ver in (1.0,1.1)'
```

> Filter by Version Only

```bash
kubectl get pod -l 'ver in (1.0,1.1)'
```

---

# EKS Cluster Creation using Terraform

This guide explains how to create an **Amazon EKS Cluster using Terraform** and verify it using `kubectl`.

---

## Step 1: Create Server & Connect

```bash
ssh ubuntu@<public-ip>
```

---

## Step 2: Install Required Packages

```bash
sudo apt update
sudo apt install unzip -y
```

---

## Step 3: Install AWS CLI

> Install AWS CLI using official documentation
> Create an IAM user
> Save:

- > Access Key
- > Secret Key
  > Configure AWS CLI

```bash
aws configure
```

> Enter:

- > Access Key
- > Secret Key
- > Region (e.g., ap-south-1)

---

## Step 4: Install Terraform

```bash
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update && sudo apt install terraform

```

---

## Step 4: Use Terraform EKS Repository

```bash
git clone https://github.com/hashicorp-education/learn-terraform-provision-eks-cluster.git
cd learn-terraform-provision-eks-cluster
```

---

## Step 5: Deploy EKS Cluster

> terraform init
> terraform apply
> Creates:

- > EKS Cluster
- > Worker Nodes
- > Networking components

---

## Step 6: Verify Cluster in AWS

> Check cluster and nodes in AWS Console

---

## Step 7: Verify using kubectl

```bash
kubectl get nodes
```

> If this command gives an error → install kubectl

---

## Step 8: Install kubectl

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo chmod +x kubectl
sudo mv kubectl /usr/local/bin

kubectl version --client
```

---

## Step 9: Configure kubeconfig

```bash
aws eks --region <region> update-kubeconfig --name <cluster-name>
```

### Example

```bash
aws eks --region us-east-2 update-kubeconfig --name education-eks-1s7xpCRm
```

---

## Kubernetes Networking Concept

> In Kubernetes, an application can run on multiple Pods, and each Pod gets its own IP address. However, Pods are ephemeral, so when a Pod goes down, Kubernetes recreates it with a new IP address.

> Because Pod IPs are dynamic, direct communication using Pod IPs is not reliable.

> To solve this, we use a Service (SVC), which provides a static IP address and DNS name. The Service uses labels and selectors to route traffic to the available Pods.

> Even if Pods are recreated with new IPs, the Service remains constant and ensures uninterrupted communication.

> If we want the application to be accessible from the outside world, we use Service types like NodePort or LoadBalancer.

---

# EKS Cluster Service Type: ClusterIP

---

## ClusterIP Service

- Used for **internal communication** within the Kubernetes cluster
- Accessible only **inside the cluster (Pod-to-Pod communication)**
- Not exposed to external users (no public access)

---

## Key Points

- ClusterIP is the **default Service type**
- Provides a **stable internal IP address**
- Uses **labels and selectors** to route traffic
- Helps access **multiple Pods using a single IP**
- Pod IPs are dynamic, but **Service IP remains constant**

---

## How It Works

1. Create multiple Pods with the same label
2. Create a Service with a selector matching those labels
3. Service routes traffic to all matching Pods

---

## Pod YAML Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: eks-pod
  labels:
    app: payment-app
spec:
  containers:
    - name: app-image-1
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: eks-pod-2
  labels:
    app: payment-app
spec:
  containers:
    - name: app-image-2
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: eks-pod-3
  labels:
    app: payment-app
spec:
  containers:
    - name: app-image-3
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: eks-pod-4
  labels:
    app: payment-app
spec:
  containers:
    - name: app-image-4
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
```

## Service YAML (ClusterIP)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: service
spec:
  selector:
    app: payment-app
  type: ClusterIP
  ports:
    - port: 80
      protocol: TCP
```

---

## To Check Pods

```bash
kubectl get po
```

## To Check Service

```bash
kubectl get svc
```

## How to Communicate (Internal Access)

```bash
kubectl exec -it <pod-name> -- bash
```

### Get Service ClusterIP:

```bash
kubectl get svc
```

### Access using curl:

```bash
curl http://<cluster-ip>:80
```

> We can access Cluster IP using curl inside the cluster, but not via browser externally because it is a private internal service

## Interview Point ⭐

- When a **Pod is deleted**, its IP changes because Pods are **ephemeral**
- The **Service ClusterIP remains the same** since it is a **stable virtual IP**
- Service routes traffic using:
  - **Labels**
  - **Selectors**
- If the **Service is deleted and recreated**, a **new ClusterIP is assigned by default**
- To retain the same IP, we must **explicitly define a static `clusterIP`** in the Service YAML

---

![Kubernates-ClusterIP](./images/cluster-ip.png)

---

# NodePort Service in Kubernetes

---

## What is NodePort?

- **NodePort** is a Kubernetes Service type that exposes an application to **external users**
- It opens a **specific port on every node** in the cluster

---

## Key Points

- Access application using:
  - **Node IP**
  - **NodePort**
- Default NodePort range: **30000–32767**
- Used for:
  - Testing
  - Simple deployments
- Not recommended for production (use LoadBalancer instead)

---

## Architecture

> External User → Node IP:NodePort → Service → Pods

---

---

## Prerequisites (EKS Setup)

- Create EC2 instance
- Update system:

```bash
sudo apt update
```

### Install:

> AWS CLI
> Configure using aws configure
> Create EKS cluster using Terraform / eksctl

---

## Pod YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: payment-app-1
  labels:
    env: DEV
spec:
  containers:
    - name: pay-image-1
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: payment-app-2
  labels:
    env: DEV
spec:
  containers:
    - name: pay-image-2
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: payment-app-3
  labels:
    env: DEV
spec:
  containers:
    - name: pay-image-3
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: payment-app-4
  labels:
    env: DEV
spec:
  containers:
    - name: pay-image-4
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
```

## Service YAML (NodePort)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: svc-pay
spec:
  selector:
    env: DEV
  type: NodePort
  ports:
    - port: 80
      protocol: TCP
      targetPort: 80
      nodePort: 30008
```

---

## To Check Pods

```bash
kubectl get po
```

## To Check Service

```bash
kubectl get svc
```

## How to Access Application

### 1. Get Node IP:

```bash
kubectl get nodes -o wide
```

### 2. Access in browser:

```bash
"http://<Node-IP>:30008"
```

---

![Kubernates-NodePort](./images/NodePort.png)

---

# LoadBalancer Service in Kubernetes

---

## What is LoadBalancer?

- A **LoadBalancer** is a Kubernetes Service type that exposes an application to **external users**
- It automatically creates a **cloud provider load balancer** (e.g., AWS ELB in EKS)
- Distributes incoming traffic across multiple Pods

---

## Key Points

- Provides **external access** to applications
- Distributes traffic across multiple Pods
- Ensures **high availability**
- Automatically integrates with cloud providers (AWS, Azure, GCP)

---

## Architecture

> External User → LoadBalancer → Service → Pods

---

## Pod YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-lb-1
  labels:
    env: LB-DEV
spec:
  containers:
    - name: lb-cont-1
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: pod-lb-2
  labels:
    env: LB-DEV
spec:
  containers:
    - name: lb-cont-2
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: pod-lb-3
  labels:
    env: LB-DEV
spec:
  containers:
    - name: lb-cont-3
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: pod-lb-4
  labels:
    env: LB-DEV
spec:
  containers:
    - name: lb-cont-4
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
```

## Service YAML (LoadBalancer)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: svc-lb
spec:
  type: LoadBalancer
  selector:
    env: LB-DEV
  ports:
    - port: 80
      protocol: TCP
```

---

## Apply Resources

```bash
kubectl apply -f pod.yaml
kubectl apply -f svc.yaml
```

### Check Pods

```bash
kubectl get po
```

### Check Service

```bash
kubectl get svc
```

> Look for EXTERNAL-IP

## How to Access

```bash
"http://<EXTERNAL-IP>"
```

> Open in browser to access Nginx page

---

![Kubernates-LoadBalancer](/images/LoadBalancer1.png)

---

# ExternalName / External DNS Name

> ExternalName is a Kubernetes Service type that maps a service to an external DNS name instead of routing traffic to pods.

> The purpose of ExternalName is to allow applications inside the Kubernetes cluster to access external services using a simple internal service name.

> ExternalName works by creating a DNS alias (CNAME record) that resolves the Kubernetes service name to the external domain name.

> For example, if an application inside the cluster needs to access an external API like google.com, we can define an ExternalName service and access it using the service name instead of the actual domain.

---

## Pod YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-ex-1
  labels:
    env: EX-DEV
spec:
  containers:
    - name: ex-cont-1
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: pod-ex-2
  labels:
    env: EX-DEV
spec:
  containers:
    - name: ex-cont-2
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: pod-ex-3
  labels:
    env: EX-DEV
spec:
  containers:
    - name: ex-cont-3
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
---
apiVersion: v1
kind: Pod
metadata:
  name: pod-ex-4
  labels:
    env: EX-DEV
spec:
  containers:
    - name: ex-cont-4
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
```

## serviec YAML(Service)

```yaml
apiVersion: v1
kind: Service
metadata:
  name: svc-pay
spec:
  selector:
    env: DEV
  type: ExternalName
  ports:
    - port: 80
      protocol: TCP
  externalName: www.google.com
```

---

![Kubernates-External Name](/images/External%20Name.png)

---

# Service types flow in K8S:

![Kubernates-all-service-types](./images/k8s-service-types.png)

---

# Kubernetes Restart Policy

## Overview

`restartPolicy` in Kubernetes defines how the system handles container restarts when a Pod’s container stops or fails.

---

## Types of Restart Policies

### 1. Always (Default)

> The container is restarted **every time it stops**, regardless of exit status.

**Use Cases**

- Long-running applications
- Web servers (e.g., nginx)

**Behavior**

- Exit 0 (Success) → Restart
- Exit 1 (Failure) → Restart

**Example**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-ex-1
  labels:
    env: EX-DEV
spec:
  restartPolicy: Always
  containers:
    - name: ex-cont-1
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
```

### 2. OnFailure

> The container restarts only if it fails (non-zero exit code).

**Use Cases**

> Batch jobs
> Data processing tasks

**Behavior**

> Exit 0 (Success) → No restart
> Exit 1 (Failure) → Restart

**Example**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-ex-1
  labels:
    env: EX-DEV
spec:
  restartPolicy: OnFailure
  containers:
    - name: ex-cont-1
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
```

---

### 3. Never

> The container is never restarted, regardless of exit status.

**Use Cases**

> One-time execution jobs
> Debugging

**Behavior**

> Exit 0 (Success) → No restart
> Exit 1 (Failure) → No restart

**Example**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-ex-1
  labels:
    env: EX-DEV
spec:
  restartPolicy: Never
  containers:
    - name: ex-cont-1
      image: nginx
      ports:
        - containerPort: 80
          protocol: TCP
```

---

# Kubernates Restart Policy

![kubernates-restart-policy](./images/Pod-restart-policy.png)

---

### Summary

| Policy    | Restart on Success | Restart on Failure | Typical Use Case          |
| --------- | ------------------ | ------------------ | ------------------------- |
| Always    | Yes                | Yes                | Web apps, APIs            |
| OnFailure | No                 | Yes                | Batch jobs                |
| Never     | No                 | No                 | Debugging, one-time tasks |

---

# Kubernetes Pod Probes (Startup Probe)

## Overview

> Pod probes are **health checks** used by Kubernetes to determine the status of a container and take actions based on its health.

They help Kubernetes verify whether a container:

- Is **running correctly**
- Is **ready to serve traffic**
- Needs to be **restarted**

---

## Types of Probes

- Startup Probe
- Liveness Probe
- Readiness Probe

---

## Startup Probe

### Definition

> A **Startup Probe** is used to check whether the application inside a container has **started successfully**.

---

### Key Behavior

- If the startup probe **fails** → Kubernetes **restarts the container**
- Until the startup probe **succeeds**:
  - Liveness probe is **disabled**
  - Readiness probe is **disabled**
- Works **independently**:
  - It only checks its own container
  - It does **not depend on other Pods**

---

### Why Use Startup Probe?

- Handles **slow-starting applications**
- Prevents **premature restarts** by liveness probe
- Ensures application is fully initialized before other checks begin

**Pod YAML**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: start-up-pod
  labels:
    app: startup-dev-pod
    env: DEV
spec:
  containers:
    - name: starup-cont
      image: busybox
      ports:
        - containerPort: 80
          protocol: TCP
      startupProbe:
        httpGet:
          path: /site
          port: 80
        initialDelaySeconds: 10
        periodSeconds: 5
        successThreshold: 1
        failureThreshold: 3
```

# Kubernetes Probe Types & Arguments

## Supported Probe Types

### httpGet

Sends an HTTP request to a specified **path** and **port** on the container.

- Success → HTTP status code **200–399**
- Commonly used for web applications

---

### grpc

Performs health checks using **gRPC protocol** by calling a defined health check service.

- Used for applications built with gRPC

---

### tcpSocket

Checks whether a **TCP connection** can be established on a given port.

- Useful for services like databases or custom TCP apps

---

### exec

Executes a command inside the container.

- Success → Command exits with status **0**
- Useful for custom health checks

---

## Probe Arguments

### initialDelaySeconds

Time Kubernetes waits **before starting the first probe** after the container starts.

---

### periodSeconds

Defines how often (in seconds) Kubernetes performs the **health check**.

---

### successThreshold

Minimum number of **consecutive successful checks** required to mark the container as healthy.

---

## Summary

| Type      | Description                  | Success Condition     |
| --------- | ---------------------------- | --------------------- |
| httpGet   | HTTP request to container    | Status 200–399        |
| grpc      | gRPC health check            | Healthy response      |
| tcpSocket | TCP connection check         | Connection successful |
| exec      | Run command inside container | Exit code 0           |

| Argument            | Purpose                        |
| ------------------- | ------------------------------ |
| initialDelaySeconds | Delay before starting probes   |
| periodSeconds       | Interval between probe checks  |
| successThreshold    | Required consecutive successes |

---

### Kubernates Startup Probe Figure

![Kubernates-startup-probe](./images/startup-probes.png)

---

# Kubernetes Liveness Probe

## Overview

> A **Liveness Probe** is used to check whether a container is **alive and functioning properly** during runtime.

> If the liveness probe fails, Kubernetes will **automatically restart the container**.

---

## Key Points

- Detects **deadlocks** or **stuck applications**
- Runs continuously throughout the **container lifecycle**
- Failure → **Container Restart**

---

## Why Use Liveness Probe?

- Ensures application remains **responsive**
- Recovers from **unexpected failures**
- Prevents long-running but **unhealthy containers**

---

**Pod YAML**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: start-up-pod
  labels:
    app: startup-dev-pod
    env: DEV
spec:
  containers:
    - name: starup-cont
      image: busybox
      ports:
        - containerPort: 80
          protocol: TCP
      livenessProbe:
        tcpSocket:
          port: 80
      startupProbe:
        httpGet:
          path: /site
          port: 80
        initialDelaySeconds: 10
        periodSeconds: 5
        successThreshold: 1
        failureThreshold: 3
```

### Kubernates Livensss Probe Figure

![kubernates-libeness-probe-diagram](./images/liveness-probe.png)

---

# Kubernetes Readiness Probe

## Overview

A **Readiness Probe** is used to check whether a container is **ready to accept traffic**.

If the readiness probe fails, Kubernetes **does not restart the container**.  
Instead, it **removes the Pod from service endpoints**, so it temporarily stops receiving traffic.

---

## Key Points

- Failure does **not kill the Pod**
- Pod is **removed from Service endpoints**
- Container **continues running**
- Once healthy again → Pod is **added back to service**

---

## Why Use Readiness Probe?

- Prevents sending traffic to **unready applications**
- Useful during:
  - Application startup
  - Configuration loading
  - Temporary overload or maintenance

---

**Pod YAML**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: start-up-pod
  labels:
    app: startup-dev-pod
    env: DEV
spec:
  containers:
    - name: starup-cont
      image: busybox
      ports:
        - containerPort: 80
          protocol: TCP
      livenessProbe:
        tcpSocket:
          port: 80
      readinessProbe:
        exec:
          command:
            - touch pod-file
            - tail -f /var/log/busybox/error.log
      startupProbe:
        httpGet:
          path: /site
          port: 80
        initialDelaySeconds: 10
        periodSeconds: 5
        successThreshold: 1
        failureThreshold: 3
```

### Kubernates Readiness Probe figure

![kubernates-readiness-probe-diagram](./images/Readiness-probe.png)

---

# Kubernates Probes

![Kubernates-probes](./images/All-Probes.png)

---

# Kubernetes Pod Resource Requests & Limits - Failure

## Overview

In Kubernetes, Pods can define **resource requests** and **resource limits** for CPU and memory.

These settings help Kubernetes:

- **Schedule Pods efficiently**
- **Prevent resource overuse**
- **Ensure cluster stability**

---

## Requests vs Limits

### Requests

Requests define the **minimum guaranteed resources** a container needs.

- Used by the **Kubernetes scheduler**
- Determines **which worker node** can host the Pod
- Ensures the Pod gets at least this amount of resources

**Example**

- CPU request: 500m → Pod needs at least 0.5 CPU
- Memory request: 256Mi → Pod needs at least 256MB RAM

---

### Limits

Limits define the **maximum resources** a container can use.

- Enforced by the **container runtime**

**Behavior**

- CPU limit → Enforced by **throttling**
- Memory limit → Exceeding causes **OOMKilled (container terminated)**

---

## Resource Flow

Pod
└── Worker Node
├── Requests
│ ├── CPU
│ └── Memory
└── Limits
├── CPU
└── Memory

---

## Scenario

> This example demonstrates what happens when a container **exceeds its memory limit** in Kubernetes.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-stress
  labels:
    env: dev
spec:
  containers:
    - name: my-cont-stress
      image: polinux/stress
      ports:
        - containerPort: 80
          protocol: TCP
      command: ["stress", "--vm", "1", "--vm-bytes", "155M"]
      resources:
        requests:
          cpu: "150m"
          memory: 100Mi
        limits:
          cpu: "200m"
          memory: 150Mi
```

---

## Pod Status (Tabular View)

| NAME       | READY | STATUS           | RESTARTS | AGE |
| ---------- | ----- | ---------------- | -------- | --- |
| pod-stress | 0/1   | OOMKilled        | 1        | 5s  |
| pod-stress | 0/1   | CrashLoopBackOff | 1        | 14s |
| pod-stress | 0/1   | OOMKilled        | 2        | 15s |

---

# Kubernetes Resource Limits – Successful Run Example

## Scenario

> This example shows a container running **within its memory limits**, so it remains stable and healthy.

---

## Pod Configuration

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-stress
  labels:
    env: dev
spec:
  containers:
    - name: my-cont-stress
      image: polinux/stress
      ports:
        - containerPort: 80
          protocol: TCP
      command: ["stress", "--vm", "1", "--vm-bytes", "125M"]
      resources:
        requests:
          cpu: "150m"
          memory: 100Mi
        limits:
          cpu: "200m"
          memory: 150Mi
```

---

## Pod Status (Tabular View)

| NAME       | READY | STATUS  | RESTARTS | AGE |
| ---------- | ----- | ------- | -------- | --- |
| pod-stress | 1/1   | Running | 0        | 3s  |

---

### Kubernates-Resource

![Kubernates-resource-requests-limits](./images/Resource-requests-limits.png)

---

# Kubernetes Annotations

## Definition

**Annotations** in Kubernetes are key–value metadata used to attach **non-identifying information** to objects. They are not used for selection or grouping, but are instead consumed by controllers, tools, or external systems.

---

## Core Concept

Annotations are **passive metadata**—Kubernetes stores them but does not act on them unless a specific component or integration is designed to read and use them.

---

## Key Characteristics

- Store arbitrary non-identifying metadata
- Not used for object selection (unlike labels)
- Can include large or complex data (e.g., JSON, configuration details)
- Primarily used by:
  - Controllers
  - CLI tools
  - External integrations

---

## Common Use Cases

- Storing build/version information
- Tracking deployment metadata
- Attaching configuration for external tools (e.g., monitoring, logging)
- Recording audit or ownership details

---

### Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: annotation-pod
  labels:
    env: anno-prod
  annotations:
    sonar-url: "http://sonar.io/project-key"
    sonar-enabled: "true"
spec:
  containers:
    - name: anna-con
      image: jenkins/Jenkins
```

---

### Kubernates-Annotations

![Kubernates-annotations](./images/k8s-annotations.png)

---

# Kubernetes Namespaces

## Definition

A **Namespace** in Kubernetes is a logical isolation boundary used to organize and separate resources within a cluster.

---

## Resource Scope in Kubernetes

Kubernetes resources are divided into two categories:

### 1. Namespaced Resources

These exist within a specific namespace:

- Pods
- Services
- Deployments
- ReplicaSets
- ConfigMaps
- Secrets
- Ingress

### 2. Cluster-Scoped Resources

These exist at the cluster level and are not tied to any namespace:

- Nodes
- PersistentVolumes

---

## RBAC and Namespaces

Role-Based Access Control (RBAC) operates across both scopes:

- **Namespaced RBAC**
  - Roles
  - RoleBindings

- **Cluster-Wide RBAC**
  - ClusterRoles
  - ClusterRoleBindings

---

## Real-World Usage

In practice, namespaces are commonly used to represent different environments, such as:

- dev
- QA
- UAT
- production

This enables teams to run multiple environments within the same cluster while maintaining:

- Isolation
- Access control
- Resource management

> ⚠️ **Important:** Namespaces are _not_ environments themselves—they are simply a mechanism for logically separating resources.

---

## Default Kubernetes Namespaces

Kubernetes provides several built-in namespaces:

- **default** – Used for objects with no specified namespace
- **kube-system** – Contains system components
- **kube-public** – Publicly accessible resources
- **kube-node-lease** – Stores node heartbeat data for performance optimization

---

## Working with Namespaces in Kubernetes (Step-by-Step)

This guide demonstrates how Kubernetes namespaces affect resource visibility and how to work with them effectively.

---

### Step 1: Create a Namespace

```bash
kubectl create namespace prod
```

---

### Step 2: Create a Pod

```bash
kubectl apply -f pod.yaml
```

> If pod.yaml does not specify a namespace, the Pod will be created in the default namespace.

---

### Step 3: Check Pods (Default Behavior)

```bash
kubectl get po
```

> Output:

- No resources found in default namespace

> Reason:

- By default, Kubernetes looks for resources in the default namespace, not in prod.

---

### Step 4: Switch to prod Namespace

```bash
kubectl config set-context --current --namespace=prod
```

> This sets the current context to use the prod namespace by default.

---

### Step 5: Check Pods Again

```bash
kubectl get po
```

> Now, you should be able to see the Pods created in the prod namespace

---

### Alternative: Access Without Switching Namespace

> Instead of switching the namespace, you can directly specify it using the -n flag:

```bash
kubectl describe pod annotation-pod -n prod
```

---

### Example

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: annotation-pod
  labels:
    env: anno-prod
  namespaces: prod
  annotations:
    sonarurl: "http://sonar:io/project-key: enable"
spec:
  containers:
    - name: anna-con
      image: jenkins/jenkins
```

### Kubernates - Namespaces

![kubernates-namespaces](./images/k8s-namespaces.png)

---

# Kubernetes Networking Model (Inside a Worker Node)

This document explains how networking works inside a Kubernetes worker node, focusing on how Pods and containers communicate.

---

## Overview

Inside a worker node, Pods run within namespaces, and containers inside those Pods communicate through a structured networking flow. Kubernetes networking ensures seamless communication while maintaining isolation between Pods.

---

## Core Concept

- Containers inside a Pod share the same network namespace
- Pods have isolated network environments
- Communication is enabled using virtual networking components
- Traffic flows through multiple layers before reaching outside the node

---

## Communication Flow (Inside a Worker Node)

### Step 1: Container Inside Pod

- Containers within the same Pod share the **same network namespace**
- They communicate directly using:

```bash
localhost
```

---

> No external networking is required for intra-Pod communication

---

### Step 2: Pod Network Namespace

- > Each Pod gets its own network namespace
- > Inside the Pod:
  - A virtual network interface exists (typically eth0)
  - This interface allows the Pod to communicate with the outside world

---

### Step 3: veth Pair (Virtual Ethernet Pair)

- > Kubernetes creates a veth pair to connect Pod and host:
  - One end exists inside the Pod → eth0
  - Other end exists on the host node
  - These act like a virtual cable connecting Pod ↔ Node

---

### Step 4: Bridge Network

- > The host-side veth connects to a bridge network (e.g., cni0)
  - This bridge behaves like a virtual switch
- > Responsibilities:
  - Connect multiple Pods on the same node
  - Enable Pod-to-Pod communication within the node

---

### Step 5: Node Network Interface (eth0)

- > The bridge is connected to the node’s physical
  - interface:
  - eth0
- > This interface handles:
  - Communication outside the node
  - Traffic to other nodes or external networks

---

# Kubernetes Networking Flow (Mermaid Diagram)

```mermaid
flowchart TD
    A[Container (localhost)]
    B[Pod Network Namespace (eth0)]
    C[veth Pair]
    D[Bridge Network (cni0)]
    E[Node Interface (eth0)]
    F[Outside World / Other Nodes]

    A --> B --> C --> D --> E --> F
```

---

# Kubernetes Networking Flows

This document illustrates the correct network communication flow in Kubernetes for:

- Pods on the **same node**
- Pods on **different nodes**

---

## Pods on (Same Node)

```mermaid
flowchart LR
    A[Container]
    B[Pod (eth0)]
    C[veth (Pod End)]
    D[veth (Host End)]
    E[Bridge (cni0 on Host)]
    F[veth (Host End)]
    G[veth (Pod End)]
    H[Pod (eth0)]
    I[Container]

    A --> B --> C --> D --> E --> F --> G --> H --> I
```

---

### Explanation

- > Traffic flow within the same node:
  - Starts from the source container
  - Moves to the Pod's network interface (eth0)
  - Passes through the veth pair (Pod end → Host end)
  - Reaches the bridge network (cni0) on the node
  - Crosses another veth pair to the destination Pod
  - Enters the destination Pod (eth0)
  - Finally reaches the target container

---

## Pods on (Different Node) (Mermaid)

``mermaid
flowchart LR
    A[Pod (eth0)]
    B[veth]
    C[Bridge (cni0)]
    D[Node eth0]
    E[Network (via CNI)]
    F[Target Node eth0]
    G[Bridge]
    H[veth]
    I[Pod (eth0)]
    J[Container]

    A --> B --> C --> D --> E --> F --> G --> H --> I --> J
```

### Explanation

- > Traffic flow across different nodes:
  - Starts from the source container
  - Moves through Pod’s eth0
  - Enters the veth pair
  - Reaches the node’s bridge (cni0)
  - Exits via the node’s physical interface (eth0)
  - Travels across the network using a CNI plugin (e.g., Calico, Flannel)
  - Enters the target node's eth0
  - Passes through the bridge
  - Moves via veth pair into the destination Pod
  - Reaches the target container

---

![kubernates-networking-models](./images/k8s-networking-models.png)

---

# Kubernetes Networking Models

Kubernetes networking is designed to enable seamless communication between containers, Pods, Services, and external systems. There are four primary networking communication models.

---

## 1. Container → Container (Same Pod)

- Containers within the same Pod share a **single network namespace**
- Communication happens directly using:

```bash
localhost
```

- > No involvement of:
  - veth pairs
  - bridge networks
  - routing

---

## 2. Pod → Pod Networking

### Same Node

- > Traffic flow:
  - Container → Pod eth0
  - Through veth pair (Pod end → Host end)
  - To bridge (cni0)
  - Through another veth pair
  - Into destination Pod eth0
  - Reaches target container

### Different Nodes

- > Traffic flow:
  - Container → Pod eth0
  - → veth → bridge (cni0)
  - → Node eth0
  - → Network (via CNI plugin such as Calico or Flannel)
  - → Target Node eth0
  - → bridge → veth
  - → destination Pod eth0
  - → target container

---

## 3. Pod → Service Networking

### Pod → Service

- > Traffic flow:
  - Pod sends request to Service Virtual IP (ClusterIP)
  - kube-proxy applies rules (iptables/IPVS)
  - Selects a backend Pod
  - Forwards traffic using Pod-to-Pod networking

### Service → Pod

- > When a Service receives traffic:
  - kube-proxy selects one of the backend Pods
  - Routes traffic to it
  - Uses standard Pod-to-Pod communication path

---

## 4. Internet → Service
- > External traffic flow:
  - Enters through Node eth0
  - Reaches Service exposed via:
    - NodePort
    - LoadBalancer
- kube-proxy routes request
- Forwards to one of the backend Pods
- Pod receives traffic through normal Pod networking flow

---

![kubernates-networking-types](./images/k8s-networking-models-types.png)

---