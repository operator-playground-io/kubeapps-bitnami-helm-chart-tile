---
title: Kubeapps Bitnami Helm Chart Installation Tutorial
description: This tutorial explains how we Installed Kubeapps Bitnami Helm Chart
---

### Install Kubeapps Bitnami Helm Chart

This tutorial is made just to describe what all steps are actually being performed behind the Kubeapps Chart "Install" button and is just for knowledge perspective.
Please do not execute these manually if you already installed the Kubeapps Helm Chart using "Install" button. 

We have followed following steps to install Kubeapps Bitnami Helm Chart :

Step 1: Create a namespace : "kubeapps". 

```
kubectl create namespace kubeapps
```

output:

```
namespace/kubeapps created
```



Step 2: Add ‘bitnami' to your repo list:

Command:

```
helm repo add bitnami https://charts.bitnami.com/bitnami
```

you should see the following output:

```
"bitnami" has been added to your repositories
```


Step 3:  Command for Kubeapps Helm Chart installation:

```
helm install kubeapps --namespace kubeapps --set frontend.service.type=NodePort bitnami/kubeapps
```

output:

```
NAME: kubeapps
LAST DEPLOYED: Wed Jan 27 04:48:43 2021
NAMESPACE: kubeapps
STATUS: deployed
REVISION: 1
NOTES:
** Please be patient while the chart is being deployed **

Tip:

  Watch the deployment status using the command: kubectl get pods -w --namespace kubeapps

Kubeapps can be accessed via port 80 on the following DNS name from within your cluster:

   kubeapps.kubeapps.svc.cluster.local

To access Kubeapps from outside your K8s cluster, follow the steps below:

1. Get the Kubeapps URL by running these commands:

   export NODE_IP=$(kubectl get nodes --namespace kubeapps -o jsonpath="{.items[0].status.addresses[0].address}")
   export NODE_PORT=$(kubectl get --namespace kubeapps -o jsonpath="{.spec.ports[0].nodePort}" services kubeapps)
   echo "Kubeapps URL: http://$NODE_IP:$NODE_PORT"

2. Open a browser and access Kubeapps using the obtained URL.
```




