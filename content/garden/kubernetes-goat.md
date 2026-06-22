---
title: "Kubernetes Goat"
date: 2026-06-15
lastmod: 2026-06-22
draft: false

keywords:
  - Kubernetes Goat
  - K8s Goat

params:
  aliases:
    - K8s Goat
  garden:
    kind: item
    usefulness: trial
    category: tool
    movement: "New"
---

[Kubernetes Goat](https://github.com/madhuakula/kubernetes-goat) is an intentionally vulnerable **[[Kubernetes]]** cluster lab by Madhu Akula. It deploys misconfigured workloads for hands-on attack and defense scenarios. We **trial** it for cluster security training, runtime exploitation practice, and calibrating **[[Kubescape]]** or **[[kube-bench]]** CIS drills. Never run it on production clusters or shared infrastructure.

## Blurb

> The Kubernetes Goat is designed to be an intentionally vulnerable cluster environment to learn and practice Kubernetes security.

## Summary

Kubernetes Goat extends the Goat tradition (**[[DVWA]]**, **[[Juice Shop]]**, **[[TerraGoat]]**) into live cluster security. Bridgecrew goats target **[[IaC]]** files; this lab targets running pods, RBAC, and cluster misconfigurations.

**When to use:** teaching **[[DevSecOps]]** and K8s red-team basics; walking through 20+ documented scenarios (RBAC abuse, container escape, SSRF, registry attacks); pairing manual exploits with **[[Kubescape]]** or **[[kube-bench]]** CIS modules in the curriculum.

**When to skip:** you cannot provision an isolated lab cluster (KIND, K3s, minikube, or disposable cloud); you only need static manifest scanning (use **[[Checkov]]** on repos); you need web-app vuln labs only (use **[[DVWA]]** or **[[Juice Shop]]**).

**Setup:** clone repo, run `setup-kubernetes-goat.sh`, then `access-kubernetes-goat.sh` for local UI at `http://127.0.0.1:1234`. Full guide at [madhuakula.com/kubernetes-goat](https://madhuakula.com/kubernetes-goat).


## Details

### Compared to IaC Goats

| Lens | Kubernetes Goat | [[TerraGoat]] / Bridgecrew goats |
|------|-----------------|----------------------------------|
| Target | Running **[[Kubernetes]]** cluster | **[[IaC]]** files (Terraform, CFN, Bicep, CDK) |
| Skills | RBAC, escapes, SSRF, runtime abuse | Misconfiguration detection pre-deploy |
| Scanner pairing | **[[Kubescape]]**, **[[kube-bench]]**, **[[Checkov]]** on manifests | **[[Checkov]]** on IaC |
| Best fit | Cluster security and exploitation labs | Cloud template scanning labs |

### Scenario Highlights

Upstream documents 20+ modules, including sensitive keys in repos, docker-in-docker abuse, container escape, private registry attacks, RBAC misconfiguration, CIS Docker/K8s benchmark analysis, and policy engine hardening exercises.

### Deployment Guardrails

- Use a dedicated lab cluster with no production namespaces or data.
- Requires cluster admin and `kubectl`; **[[Helm]]** for install scripts.
- Read upstream disclaimer before setup: vulnerabilities are intentional.
- Tear down the lab when finished; do not co-locate with real workloads.
- Prefer KIND, K3s, or a sandbox EKS/GKE/AKS account per upstream docs.

### Install Sketch

```bash
git clone https://github.com/madhuakula/kubernetes-goat.git
cd kubernetes-goat
bash setup-kubernetes-goat.sh
kubectl get pods   # wait until ready
bash access-kubernetes-goat.sh
# UI: http://127.0.0.1:1234
```
