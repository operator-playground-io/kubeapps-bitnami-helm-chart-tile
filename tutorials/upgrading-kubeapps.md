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
    

### Upgrade Kubeapps helm chart through commands on CLI:

Steps:

1. Update your local chart repository :

```execute
helm repo update
```
Output:
```
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈ Happy Helming!⎈ 
```

2. Now upgrade Kubeapps:

```execute
export RELEASE_NAME=kubeapps
helm upgrade $RELEASE_NAME bitnami/kubeapps
```

Note: If the current version of Kubeapps Helm chart is latest one, then this command may fail and give error.
