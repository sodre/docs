---
title: "Networking"
weight: 35
---

Open Ports
----------
Please reference the [Node Requirements]({{< baseurl >}}/k3s/latest/en/installation/node-requirements/#networking) page for port information.

Flannel
-------

Flannel is included by default, if you don't want flannel then run each agent with `--no-flannel` option.

In this setup you will still be required to install your own CNI driver.  More info [here](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/#pod-network)

CoreDNS
-------

CoreDNS is deployed on start of the agent, to disable run each server with the `--no-deploy coredns` option.

If you don't install CoreDNS you will need to install a cluster DNS provider yourself.

Traefik Ingress Controller
--------------------------

Traefik is deployed by default when starting the server. For more information see [Auto Deploying Manifests]({{< baseurl >}}/k3s/latest/en/configuration/#auto-deploying-manifests). The default config file is found in `/var/lib/rancher/k3s/server/manifests/traefik.yaml` and any changes made to this file will automatically be deployed to Kubernetes in a manner similar to `kubectl apply`.

The Traefik ingress controller will use ports 80, 443, and 8080 on the host (i.e. these will not be usable for HostPort or NodePort).

You can tweak traefik to meet your needs by setting options in the traefik.yaml file.
Reference the official [Traefik for Helm Configuration Parameters](https://github.com/helm/charts/tree/master/stable/traefik#configuration) readme for more information.

To disable it, start each server with the `--no-deploy traefik` option.

Service Load Balancer
---------------------

K3s includes a basic service load balancer that uses available host ports.  If you try to create
a load balancer that listens on port 80, for example, it will try to find a free host in the cluster
for port 80.  If no port is available the load balancer will stay in Pending.

To disable the embedded load balancer run the server with the `--no-deploy servicelb` option. This is necessary if you wish to run a different load balancer, such as MetalLB.
