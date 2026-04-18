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
  - [☸️ Kubernetes Pod Creation Flow (Mermaid Diagram)](#️-kubernetes-pod-creation-flow-mermaid-diagram)
  - [✅ Notes](#-notes)
  - [🎯 Key Interview Points](#-key-interview-points)
  - [✅ Summary](#-summary-1)
  - [☸️ Kubernetes Pod Creation Flow](#️-kubernetes-pod-creation-flow)
  - [🚀 Pod Creation (Control Plane Flow)](#-pod-creation-control-plane-flow)
    - [1️⃣ API Server Request](#1️⃣-api-server-request)
    - [2️⃣ Validation \& Storage](#2️⃣-validation--storage)
    - [3️⃣ Controller Manager](#3️⃣-controller-manager)
    - [4️⃣ Scheduler](#4️⃣-scheduler)
    - [5️⃣ Scheduling Decision](#5️⃣-scheduling-decision)
    - [6️⃣ API Server → Kubelet](#6️⃣-api-server--kubelet)
  - [🖥️ Worker Node Flow](#️-worker-node-flow)
    - [7️⃣ Kubelet](#7️⃣-kubelet)
    - [8️⃣ Container Runtime](#8️⃣-container-runtime)
    - [9️⃣ Kubelet Monitoring](#9️⃣-kubelet-monitoring)
  - [🌐 Networking Setup](#-networking-setup)
    - [🔟 CNI Plugin](#-cni-plugin)
    - [1️⃣1️⃣ Kube-Proxy](#1️⃣1️⃣-kube-proxy)
  - [✅ Summary](#-summary-2)
- [☸️ Kubernetes Communication, Pods \& API Versions](#️-kubernetes-communication-pods--api-versions)
  - [📑 Table of Contents](#-table-of-contents-1)
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
  - [✅ Summary](#-summary-3)
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
  - [✅ Summary](#-summary-4)
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

## ☸️ Kubernetes Pod Creation Flow (Mermaid Diagram)

```mermaid
flowchart LR

    %% User
    U[User (kubectl)]

    %% Control Plane
    subgraph Control_Plane
        API[API Server]
        ETCD[(etcd)]
        SCHED[Scheduler]
        CM[Controller Manager]
    end

    %% Worker Node
    subgraph Worker_Node
        KLET[Kubelet]
        CRI[Container Runtime]
        CNI[CNI Plugin]
        KPROXY[Kube-Proxy]

        subgraph Pod
            POD[Pod (Containers)]
        end
    end

    %% Flow
    U -->|1. Deploy Pod| API
    API -->|2. Store State| ETCD
    API <-->|Watch| SCHED
    SCHED -->|3. Select Node| API
    API -->|4. Instruct| KLET

    KLET -->|5. Create Containers| CRI
    CRI -->|6. Start Pod| POD
    KLET -->|7. Monitor| POD

    KLET -.->|8. Call CNI| CNI
    CRI -.-> CNI
    CNI -->|9. Assign IP| POD

    KPROXY -->|10. Networking| POD
```

---

## ✅ Notes

* GitHub Mermaid **does not support icons**, so kept it clean
* Use `_` instead of spaces in subgraph names
* Works perfectly in:

  * GitHub README
  * VS Code Markdown preview


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

## ☸️ Kubernetes Pod Creation Flow

This section explains how a **Pod is created and runs inside a Kubernetes cluster**.

---

## 🚀 Pod Creation (Control Plane Flow)

When a user wants to deploy a Pod, the process works like this:

### 1️⃣ API Server Request

- The request is first sent to the **API Server**

---

### 2️⃣ Validation & Storage

- API Server validates the request
- Stores it in **etcd**

---

### 3️⃣ Controller Manager

- Watches the desired state (Pod request)
- Ensures the Pod should be created

---

### 4️⃣ Scheduler

- Watches for new Pods
- Selects a suitable Worker Node

---

### 5️⃣ Scheduling Decision

- Scheduler sends decision back to API Server

---

### 6️⃣ API Server → Kubelet

- API Server instructs **kubelet** on the selected Worker Node

---

## 🖥️ Worker Node Flow

### 7️⃣ Kubelet

- Receives Pod specification
- Instructs Container Runtime:
  - containerd
  - CRI-O

---

### 8️⃣ Container Runtime

- Pulls container image from registry
- Creates and starts containers
- Manages container lifecycle

---

### 9️⃣ Kubelet Monitoring

- Ensures Pod is running correctly
- Reports status back to API Server

---

## 🌐 Networking Setup

### 🔟 CNI Plugin

- Invoked by kubelet/container runtime
- Assigns IP address to Pod
- Enables Pod-to-Pod communication

**Examples:**

- Calico
- Flannel
- Weave Net

---

### 1️⃣1️⃣ Kube-Proxy

- Configures network rules (iptables/IPVS)
- Enables Service-to-Pod communication

---

## ✅ Summary

- API Server → Entry point
- etcd → Stores cluster state
- Controller Manager → Maintains desired state
- Scheduler → Selects node
- Kubelet → Executes Pod
- Container Runtime → Runs containers
- CNI → Networking (Pod IP)
- Kube-proxy → Traffic routing

---

# ☸️ Kubernetes Communication, Pods & API Versions

## 📑 Table of Contents

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
