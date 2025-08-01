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

