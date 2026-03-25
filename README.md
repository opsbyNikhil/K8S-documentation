# K8S-documentation# Kubernetes Pod Creation & Networking Flow

This document outlines the step-by-step lifecycle and networking flow when a user deploys a Pod in a Kubernetes cluster.

## Architecture Flow Diagram

```mermaid
flowchart LR
    %% External Entities
    User([External User])

    %% Master Node Subgraph
    subgraph MasterNode [Master Node]
        direction TB
        API[API Server]
        ETCD[(etcd)]
        Sched[Scheduler]
    end

    %% Worker Node Subgraph
    subgraph WorkerNode [Worker Node]
        direction TB
        Kubelet[Kubelet]
        KProxy[kube-proxy]
        CRI[Container Runtime <br> e.g., containerd]
        CNI[CNI Plugin <br> e.g., Calico/Flannel]
        Pod(((Pod)))
    end

    %% Master Node Flow
    User -- "1. Deploy Pod Request" --> API
    API -- "2. Validates & Stores" --> ETCD
    Sched -- "3. Watches & Selects Node" --> API
    Sched -- "4. Sends Decision Back" --> API
    
    %% Cross-Node Flow
    API -- "5. Instructs Kubelet" --> Kubelet

    %% Worker Node Flow
    Kubelet -- "6. Talks to CRI" --> CRI
    Kubelet -. "7. Ensures Pod is running" .-> Pod
    Kubelet -- "8. Invokes CNI" --> CNI
    CRI -- "8. Invokes CNI" --> CNI
    CNI -- "9. Assigns IP & setups net" --> Pod
    KProxy -- "10. Configures network rules" --> Pod

    %% Styling
    classDef master fill:#f8f9fa,stroke:#1a73e8,stroke-width:2px;
    classDef worker fill:#f8f9fa,stroke:#34a853,stroke-width:2px;
    classDef external fill:#fff,stroke:#333,stroke-width:2px;
    
    class API,ETCD,Sched master;
    class Kubelet,CRI,CNI,KProxy,Pod worker;
    class User external;
