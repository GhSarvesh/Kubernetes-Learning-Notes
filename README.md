---

# 📘 Kubernetes Learning Notes

---

## 🧠 Core Components in a Kubernetes Cluster

Kubernetes architecture is divided into two main parts:

1. **Control Plane (Master Node)** – Handles the management and coordination of the cluster.
2. **Worker Node** – Runs the actual application workloads.

---

### 🔹 1. Control Plane Components (Master Node)

These components manage the overall cluster state, make decisions, and expose APIs.

#### ✅ API Server

* Acts as the **entry point** for all Kubernetes operations.
* Accepts **requests from users, kubectl, and other components**.
* Communicates with all other control plane components.
* 📌 *Think of it as the "brain" interface of the cluster.*

#### ✅ Scheduler

* **Decides where to run Pods** (which node).
* Considers resource availability and constraints.
* 📌 *Responsible for intelligent Pod placement.*

#### ✅ etcd

* A **key-value store** used as the **backbone database** of Kubernetes.
* Stores **all cluster data**, configuration, and current state.
* 📌 *Acts as the single source of truth.*

#### ✅ Controller Manager

* Runs **various controllers** to maintain the desired state of the cluster.

  * Example: Node Controller, Replication Controller, Endpoints Controller.
* 📌 *Like a watchman — fixes drift between desired and actual state.*

#### ✅ Cloud Controller Manager

* Connects Kubernetes to **cloud provider APIs**.
* Manages cloud-specific resources like **load balancers, volumes, etc.**
* 📌 *Essential for running Kubernetes in cloud environments (AWS, GCP, Azure).*

---

### 🔹 2. Node Components (Worker Node)

These components run on every worker node and are responsible for running containers.

#### ✅ Kubelet

* An agent that runs on each worker node.
* **Responsible for creating Pods** and ensuring containers from PodSpecs are running and healthy.
* Communicates with the API Server and uses the container runtime to manage containers.

#### ✅ Kube Proxy

* Handles the **networking part** of Kubernetes.
* Responsible for **IP allocation to Pods** and managing routing rules.
* Enables communication between Pods and Services.

#### ✅ Container Runtime

* The actual software (like Docker, containerd) that **runs containers**.
* Pulls images, creates containers, and manages lifecycle as per Kubelet’s instructions.

---

You're right to expect consistency — let me now give you the **complete README** from the section `🧰 Kubernetes Installation Types` all the way to the **end**, including the `🧱 Kubernetes Architecture` section and your interview Q\&A, all formatted in the same clean, human-made style.

---

## 🧰 Kubernetes Installation Types

| Type                | Description                                                                                                |
| ------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Minikube**        | A lightweight Kubernetes that runs locally in a VM on your laptop. Great for **learning and development**. |
| **kubeadm**         | A toolkit to set up Kubernetes clusters manually. Used in **real clusters** for better control.            |
| **k3s**             | Lightweight Kubernetes for IoT/Edge devices. Easy to install and use.                                      |
| **kind**            | Kubernetes in Docker – runs clusters in Docker containers. Good for **CI/CD pipelines**.                   |
| **Cloud Providers** | GKE (Google), EKS (AWS), AKS (Azure) – Fully managed Kubernetes services.                                  |

---

## ⚙️ Kubernetes Components – Control Plane (Master Node)

| Component                    | Role                                                                                                                                                             |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **API Server**               | Acts as the **frontend** of Kubernetes. All commands (kubectl, dashboard, etc.) hit this component first.                                                        |
| **Scheduler**                | Decides **on which node** a new pod should be scheduled.                                                                                                         |
| **etcd**                     | A consistent and distributed **key-value store** that stores the **entire cluster state**.                                                                       |
| **Controller Manager**       | Ensures that the **actual state** of the cluster matches the **desired state** by running various controllers like node controller, replication controller, etc. |
| **Cloud Controller Manager** | Talks to **cloud service APIs** (like AWS/GCP) to manage storage, networking, and load balancers.                                                                |

---

## 🛠️ Kubernetes Components – Worker Node

| Component             | Role                                                                                                       |
| --------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Kubelet**           | Agent that runs on each node. It ensures the containers described in PodSpecs are **running and healthy**. |
| **Kube Proxy**        | Maintains **network rules and routing**. Allocates IP addresses and handles communication to/from pods.    |
| **Container Runtime** | Software that is responsible for **running containers**. Examples: Docker, containerd, CRI-O.              |

---

## ❓ Interview Questions

### 🔹 Difference Between Container, Pod, Deployment

| Term           | Description                                                                                                                                                 |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Container**  | Basic unit from Docker or other runtimes. Runs one app or process. Used via **CLI (command line)**.                                                         |
| **Pod**        | A group of one or more containers, sharing network and storage. Defined using **YAML**.                                                                     |
| **Deployment** | A higher-level concept that manages **replica sets** and ensures **desired number of pods** are running. Used for **rolling updates** and **self-healing**. |

---

### 🔹 Difference Between Deployment and ReplicaSet

| Term           | Description                                                                                                       |
| -------------- | ----------------------------------------------------------------------------------------------------------------- |
| **ReplicaSet** | Ensures a **specific number of pod replicas** are running. Created and managed automatically by a **Deployment**. |
| **Deployment** | A controller that **manages ReplicaSets** and handles **rolling updates**, rollbacks, and ensures desired state.  |

📌 **Key Insight**: When you create a Deployment, Kubernetes **automatically creates a ReplicaSet** behind the scenes.

---

## 🧱 Kubernetes Architecture

Kubernetes architecture follows a **client-server model** and is split into:

* **Control Plane (Master Node)** – brain of the system
* **Worker Nodes** – actual workload execution

---

### 🧠 1. Control Plane (Master Node)

Handles **overall cluster management**. All decisions (scheduling, responding to cluster events, etc.) happen here.

#### Components:

| Component                    | Description                                                                               |
| ---------------------------- | ----------------------------------------------------------------------------------------- |
| **API Server**               | Receives all requests. It is the **entry point** of the cluster.                          |
| **Scheduler**                | Assigns pods to appropriate nodes based on resource requirements and policies.            |
| **etcd**                     | **Key-value store** that holds all Kubernetes cluster data like states, configs, secrets. |
| **Controller Manager**       | Watches the cluster state and triggers changes to match the desired state.                |
| **Cloud Controller Manager** | Manages cloud-specific operations (e.g., attaching load balancers, storage from AWS/GCP). |

---

### 🛠️ 2. Worker Nodes

They do the **real work** – running applications (containers inside pods).

#### Components:

| Component             | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| **Kubelet**           | Node agent. It ensures the containers in a pod are running properly.  |
| **Kube Proxy**        | Maintains networking rules and routes traffic to the right pods.      |
| **Container Runtime** | Executes containers. Examples: **Docker**, **containerd**, **CRI-O**. |

---

