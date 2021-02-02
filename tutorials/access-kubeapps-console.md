---
title: How to Access Kubeapps dashboard
description: This tutorial explains how to access Kubeapps Dashboard
---


### Access Kubeapps dashboard


To obtain the application URL, wait until the pods are running.


Kubeapps can be accessed via port 80 on the following DNS name from within your cluster:

```
kubeapps.kubeapps.svc.cluster.local
```

To access Kubeapps from outside your K8s cluster, follow the steps below:


1. Get the Kubeapps URL by running below commands:


```execute
 export NODE_IP=$(kubectl get nodes --namespace kubeapps -o jsonpath="{.items[0].status.addresses[0].address}")
 export NODE_PORT=$(kubectl get --namespace kubeapps -o jsonpath="{.spec.ports[0].nodePort}" services kubeapps)
 
```


2. Access kubeapps dashboard using the obtained URL by executing below command:

```execute
echo "Kubeapps URL: http://$NODE_IP:$NODE_PORT"
```
You should see your Kubeapps login page.

Please see the below snapshot :

![](_images/wordpress-site.PNG)

3. 



