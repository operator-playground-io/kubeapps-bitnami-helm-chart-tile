---
title: How to Uninstall Kubeapps Bitnami Helm Chart 
description: This tutorial explains how to Uninstall Kubeapps Bitnami Helm Chart 
---

### Uninstall Kubeapps Bitnami Helm Chart and release the associated resources 

Steps:

1. Uninstall/delete the kubeapps deployment:

```execute
helm uninstall -n kubeapps kubeapps
```
Output:
```
release "kubeapps" uninstalled
```

2. If there are no more instances of Kubeapps in the cluster, you can manually delete the "apprepositories.kubeapps.com" CRD used by Kubeapps that is shared for the entire cluster.


```execute
kubectl delete crd apprepositories.kubeapps.com
```

Output:
```
customresourcedefinition.apiextensions.k8s.io "apprepositories.kubeapps.com" deleted
```

NOTE: If you delete the CRD for apprepositories.kubeapps.com it will delete the repositories for all the installed instances of kubeapps. This will break existing installations of kubeapps if they exist.


3. Delete the namespace:

```execute
kubectl delete namespace kubeapps
```

Output:
```
namespace "kubeapps" deleted
```
