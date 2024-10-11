---
marp: true
title: Short and Sweet - Kustomize
description: Short and Sweet about the Kubernetes tool kustomize
theme: uncover
paginate: true
_paginate: false
header: "Marvin Rensing -  Short and Sweet - Kustomize"
footer: "![image height:75px](https://www.openvalue.eu/images/openvalue-color-square.png)"



---

# Short and sweet

## `kustomize` Kubernetes native configuration management 

---

# Intro, reason & background

* small tool to ease managing K8s resources for multiple environments
* often a base resource, but different details for different environments
* used by GitOps tools like FluxCD

---

# Basic usage

File structure like
```
├── base
│   ├── deployment.yaml
│   ├── kustomization.yaml
│   └── service.yaml
└── overlays
    ├── development
    │   ├── cpu_count.yaml
    │   ├── kustomization.yaml
    │   └── replica_count.yaml
    └── production
        ├── cpu_count.yaml
        ├── kustomization.yaml
        └── replica_count.yaml
```

---

# Basic usage

Two possible usages:
* `kubectl kustomize <path>`
* `kustomize build <path>`

To apply it then on Kubernetes run
`kubectl kustomize ~/someApp/overlays/production | kubectl apply -f -`

---

# Demo

* basic idea (update replicas)
* generate ConfigMap
* patch a deployment
* use a prefix for all names
* set namespace for all resources

---

# What else?

* basically any field can be updated using [`patchesJson6902` transformer](https://kubectl.docs.kubernetes.io/references/kustomize/builtins/#field-name-patchesjson6902)


---

# Links

* [kustomize.io](https://kustomize.io/)
* [list of builtin transformers](https://kubectl.docs.kubernetes.io/references/kustomize/builtins/)
* [kustomize examples](https://github.com/kubernetes-sigs/kustomize/tree/master/examples)

---

# Q&A
