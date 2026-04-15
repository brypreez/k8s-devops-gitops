# K8s Home Lab GitOps

This repository is an active DevOps/GitOps testing environment. It is used to simulate enterprise SDLC workflows, including JIRA-tracked feature branches, security patching, and automated storage orchestration. Expect frequent breaking changes as I iterate on cluster resilience.

🛠 Project Overview
A declarative Kubernetes management lab focused on the App-of-Apps pattern. This project bridges the gap between infrastructure as code and application lifecycle management.

GitOps Pattern: App-of-Apps for centralized cluster management.

Storage: Automated Longhorn orchestration with Helm.

Networking: MetalLB LoadBalancer integration and Service optimization.

Workflow: Conventional Commits with simulated JIRA-linkage (feat, fix, chore).

💻 Local Management Environment
The cluster is managed through a hybrid, cross-platform workstation setup connected via a Tailscale mesh for secure, remote access.

Node 1: Windows Powerhouse
Hardware: ASUS Zenbook 14 OLED (Windows 11)

Environment: WSL2 (Ubuntu)

Key Tools: kubectl, helm, k9s, git

Node 2: Ultra-Portable Management
Hardware: MacBook Air (M4 Chip)

Environment: Native macOS + Homebrew

Key Tools: brew, tailscale, terraform

Connectivity
Tailscale: Provides a flat, secure network overlay across the Zenbook, MacBook, and the Kubernetes nodes, allowing for kubectl access regardless of physical location.

🚀 Key Learning Milestones
[x] Initial Cluster Bootstrap

[x] Implement Nginx with MetalLB LoadBalancing

[x] Longhorn Integration: Resolved pre-upgrade job deadlocks and repository URL sync issues.

[x] Rollback Drills: Successfully simulated security patch rollbacks and re-applications (JIRA-102).

[X] External Secrets Operator integration

[ ] Multi-node HA failover testing (In Progress)
