# Day 50 – Kubernetes Architecture and Cluster Setup

## 1. Kubernetes Story & Why It Exists
Docker simplifies building, packaging, and running containers on a single host. However, Docker alone cannot automatically manage workloads across multiple servers, handle self-healing when a host crashes, scale applications dynamically, or manage complex multi-node networking.

Google open-sourced Kubernetes in 2014, inspired by its internal container orchestration system called **Borg**. The name originates from the Greek word *κυβερνήτης*, meaning "helmsman" or "pilot/captain."

## 2. Kubernetes Architecture Diagram
+-------------------------------------------------------------+
|                     CONTROL PLANE (Master)                  |
|  +-------------+   +-------------------+   +-------------+  |
|  |   etcd      |<->|   kube-apiserver  |<->|  scheduler  |  |
|  +-------------+   +---------^---------+   +-------------+  |
|                              |                              |
|                    +---------v-----------+                  |
|                    |  controller-manager |                  |
|                    +---------------------+                  |
+------------------------------|------------------------------+
|
+------------------+------------------+
v                                     v
+-----------------------+             +-----------------------+
|      WORKER NODE 1    |             |      WORKER NODE 2    |
|  +-----------------+  |             |  +-----------------+  |
|  |     kubelet     |  |             |  |     kubelet     |  |
|  +--------|--------+  |             |  +--------|--------+  |
|           v           |             |           v           |
|  +-----------------+  |             |  +-----------------+  |
|  |Container Runtime|  |             |  |Container Runtime|  |
|  | (containerd)    |  |             |  | (containerd)    |  |
|  +-----------------+  |             |  +-----------------+  |
|  +-----------------+  |             |  +-----------------+  |
|  |   kube-proxy    |  |             |  |   kube-proxy    |  |
|  +-----------------+  |             |  +-----------------+  |
+-----------------------+             +-----------------------+
### Component Roles
* **API Server (`kube-apiserver`)**: The entry point for all commands (`kubectl`, controllers). Authenticates and stores data in etcd.
* **etcd**: Consistent, highly-available key-value store holding the entire cluster state.
* **Scheduler (`kube-scheduler`)**: Evaluates resource constraints and assigns unassigned Pods to healthy nodes.
* **Controller Manager (`kube-controller-manager`)**: Reconciles the active state with desired state (e.g., node controller, replica controller).
* **kubelet**: Agent running on each node that executes container runtime instructions and reports status.
* **kube-proxy**: Manages networking and iptables/IPVS rules for pod communication across nodes.
* **Container Runtime**: Underlying runtime engine (containerd) executing the containers.

## 3. Cluster Tool
* **Choice**: `kind` (Kubernetes in Docker).
* **Reason**: Lightweight, requires no separate hypervisor overhead, and boots control-plane nodes directly as Docker containers inside WSL.

## 4. Verification Outputs

### `kubectl get nodes -o wide`
