# k8s-devops-gitops

![GitOps](https://img.shields.io/badge/GitOps-ArgoCD-blue?style=flat&logo=argocd)
![Infrastructure](https://img.shields.io/badge/Infrastructure-Proxmox-orange?style=flat&logo=proxmox)
![Storage](https://img.shields.io/badge/Storage-Longhorn-brightgreen?style=flat&logo=linux)

**Infrastructure & Platform Engineering — GitOps Testing & Storage Resilience**

---

### 🧪 Sandbox
> **Current Sprint:** Resilience Testing. This repository is a live-fire sandbox for testing stateful applications in a Kubernetes environment. Expect frequent commits as I simulate failures and recovery procedures.

---

### 🏗 Infrastructure Architecture
This cluster is architected for physical fault tolerance, utilizing a 3-node HA control plane hosted on Proxmox VE.

| Layer | Component | Specification |
| :--- | :--- | :--- |
| **Hypervisor** | Proxmox VE | 3-Node High-Availability Cluster |
| **Orchestration** | Kubernetes | v1.32+ (High-Availability Control Plane) |
| **Storage** | **Longhorn** | Distributed block storage with cross-node replication |
| **Networking** | **MetalLB** | Layer 2 LoadBalancer for local IP orchestration |
| **GitOps** | **ArgoCD** | App-of-Apps pattern for declarative state management |

---

### 💻 Hybrid Management Mesh
I utilize a cross-platform workflow to manage the cluster from anywhere, ensuring infrastructure management isn't tied to a single physical desk.

> [!IMPORTANT]
> **Tailscale Integration:** All nodes (including the Zenbook and MacBook) are part of a private Tailscale mesh, allowing for secure `kubectl` access without exposing management ports to the internet.

| Workstation | OS / Arch | Role | Primary Tooling |
| :--- | :--- | :--- | :--- |
| **ASUS Zenbook 14 OLED** | Windows 11 (WSL2) | **Primary Engineering** | `kubectl`, `helm`, `k9s`, `ansible` |
| **MacBook Air (M4)** | macOS (Native) | **Portable Ops / ARM64** | `brew`, `terraform`, `tailscale` |

---

### 🛠 GitOps Workflow & JIRA Integration
* **Pattern:** **App-of-Apps** — A root application manages all sub-apps, ensuring 100% of the cluster state is in Git.
* **Standards:** **Conventional Commits** (`feat:`, `fix:`, `chore:`) are strictly enforced.
* **Traceability:** Simulated **JIRA linkage** (e.g., `JIRA-101`) is used in commit messages to track feature implementation and security patches.

---

### 🚀 Key Technical Milestones

| Milestone | Status | Details |
| :--- | :--- | :--- |
| **Cluster Bootstrap** | ✅ Done | 3-node HA setup with Proxmox VM isolation. |
| **Storage Resilience** | ✅ Done | Resolved Longhorn pre-upgrade deadlocks via `SkipHooks`. |
| **Security Drills** | ✅ Done | Simulated JIRA-102: Rapid rollback of Nginx patches. |
| **Secrets Management** | ✅ Done | Integrated External Secrets Operator (ESO). |
| **Failover Testing** | 🚧 WIP | Testing Longhorn volume rebuilding during node loss. |

---

### 🧠 Post-Mortem Highlights

> **Problem:** Longhorn Pre-Upgrade Job Deadlock.
> **Root Cause:** Stale hooks from previous Helm releases prevented the controller from reconciling.
> **Resolution:** Implemented `ServerSideApply=true` and utilized `SkipHooks` in the ArgoCD sync policy to allow the state to bypass the deadlock.

---

### 🛠 Tech Stack Summary
* **Hypervisor:** Proxmox VE
* **Orchestration:** K8s / ArgoCD
* **Storage:** Longhorn
* **Networking:** MetalLB / Tailscale
* **Observability:** kube-prometheus-stack (Planned & Orchestrat

---

### 🌐 Infrastructure Ecosystem
This repository is part of a wider private cloud architecture. Cross-project dependencies and global configurations are managed across the following repositories:

| Repository | Focus | Connection to this Lab |
| :--- | :--- | :--- |
| **[homelab](https://github.com/brypreez/homelab)** | **Primary Portfolio** | The "Production" environment and source of truth for global Ansible/Terraform modules. |
| **[Security-Sentinel](https://github.com/brypreez/Security-Sentinel)** | **Blue Team / SIEM** | Orchestrates the Wazuh/XDR agents that monitor this cluster's control plane. |

---
