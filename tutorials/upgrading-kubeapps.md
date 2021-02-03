---
title: Upgrade Kubeapps  Tutorial
description: This tutorial explains how to upgrade Kubeapps Bitnami Helm Chart
---

### Upgrade Kubeapps from Kubeapps web interface

You can upgrade Kubeapps from the Kubeapps web interface. 

Steps:

1. Click on "Applications" tab.You will see Kubeapps in deployed state.
  - Select the namespace in which Kubeapps is installed.Here namespace should be "kubeapps".
  - Click on Kubeapps application.
  
  Please refer following snapshot:

  ![](_images/upgrade-kubeapps-option.png)
  
2. You will see following page on dashboard:
  
  ![](_images/kubeapps-upgrade.png)
  
  Click on the "Upgrade" button.
  
3. You will see following page on dashboard:
    

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

