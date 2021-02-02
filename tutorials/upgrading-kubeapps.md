---
title: Upgrade Kubeapps  Tutorial
description: This tutorial explains how to upgrade Kubeapps Bitnami Helm Chart
---

### Upgrade Kubeapps from Kubeapps web interface

You can upgrade Kubeapps from the Kubeapps web interface. 

Steps:

1. Select the namespace in which Kubeapps is installed and 
2. Click on the "Upgrade" button. 
3. Select the new version and confirm.

We can also upgrade the Kubeapps helm chart by the following command:

Steps:

1. Update your local chart repository :

```execute
helm repo update
```
2. Now upgrade Kubeapps:

```execute
export RELEASE_NAME=kubeapps
helm upgrade $RELEASE_NAME bitnami/kubeapps
```

