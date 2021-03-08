---
title: Upgrade Kubeapps  Tutorial
description: This tutorial explains how to upgrade Kubeapps Bitnami Helm Chart
---

### Upgrade Kubeapps from Kubeapps Web Interface

You can upgrade Kubeapps from the Kubeapps web interface. 

**Step 1: Click on "Applications" tab. You will see Kubeapps in deployed state.**

 - Select the namespace in which Kubeapps is installed. Here, namespace should be "kubeapps".

 - Click on Kubeapps application.

Please refer following snapshot.

![](_images/upgrade-kubeapps-option.png)

  
**Step 2: Click on the "Upgrade" button. You will see following page on dashboard:**
  
  ![](_images/kubeapps-upgrade.png)  
    

### Upgrade Kubeapps Helm Chart through Commands on CLI:

Step 1: Update your local chart repository.

```execute
helm repo update
```

This should display something like below.

```
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈ Happy Helming!⎈ 
```

Step 2: Now upgrade the Kubeapps.

```execute
export RELEASE_NAME=kubeapps
helm upgrade $RELEASE_NAME bitnami/kubeapps
```


