---
title: "K3s - 5 less than K8s"
shortTitle: K3s
date: 2019-02-05T09:52:46-07:00
name: "menu"
---

Lightweight Kubernetes.  Easy to install, half the memory, all in a binary less than 40mb.

Great for:

* Edge
* IoT
* CI
* ARM
* Situations where a PhD in k8s clusterology is infeasible

What is this?
---

K3s is a fully compliant Kubernetes distribution with the following enhancements:

* An embedded SQLite database has replaced etcd as the default datastore. External datastores such as PostgreSQL, MySQL, and etcd are also supported.
* Simple but powerful "batteries-included" features have been added, such as: a local storage provider, a service load balancer, a helm controller, and the Traefik ingress controller.
* Operation of all Kubernetes control plane components is encapsulated in a single binary and process. This allows K3s to automate and manage complex cluster operations like distributing certificates.
* In-tree cloud providers and storage plugins have been removed.
* External dependencies have been minimized (just a modern kernel and cgroup mounts needed). K3s packages required dependencies, including:
    * containerd
    * Flannel
    * CoreDNS
    * Host utilities (iptables, socat, etc)
