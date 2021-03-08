---
title: Uninstall Kubeapps Bitnami Helm Chart 
description: Learn how to Uninstall Kubeapps Bitnami Helm Chart. 
---

### Uninstall Kubeapps Bitnami Helm Chart and release the Associated Resources 


**Step 1: Uninstall/delete the Kubeapps deployment.**

```execute
helm uninstall -n kubeapps kubeapps
```

This should produce the below output.

```
release "kubeapps" uninstalled
```

**Step 2: If there are no more instances of Kubeapps in the cluster, you can manually delete the "apprepositories.kubeapps.com" CRD used by Kubeapps that is shared for the entire cluster. See the command below.**


```execute
kubectl delete crd apprepositories.kubeapps.com
```

This should produce the following output:

```
customresourcedefinition.apiextensions.k8s.io "apprepositories.kubeapps.com" deleted
```

NOTE: If you delete the CRD for apprepositories.kubeapps.com, it will delete the repositories for all the installed instances of Kubeapps. This will break existing installations of kubeapps if they exist.


**Step 3: Delete the namespace.**

```execute
kubectl delete namespace kubeapps
```

Resulting Output:

```
namespace "kubeapps" deleted
```
