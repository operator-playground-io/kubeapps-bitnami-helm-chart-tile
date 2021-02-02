---
title: How to Uninstall Kubeapps Bitnami Helm Chart 
description: This tutorial explains how to Uninstall Kubeapps Bitnami Helm Chart 
---

### Uninstall Kubeapps Bitnami Helm Chart and release the associated resources 

To uninstall Kubeapps Bitnami Helm Chart, use the helm delete command:

```execute
helm delete kubeapps -n kubeapps
```

Output:

```
release "kubeapps" uninstalled
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

```execute
helm status kubeapps -n kubeapps
```

Output:

```
Error: release: not found
```

- Delete the namespace :

```execute
kubectl delete ns kubeapps
```


This will release all the resources associated with installed chart.
