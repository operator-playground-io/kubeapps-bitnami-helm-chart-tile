---
title: Access Kubeapps dashboard
description: Learn how to access Kubeapps Dashboard
---


### Access Kubeapps dashboard


**Step 1. Create a Kubernetes API token to access Kubeapps and Kubernetes.**

For any user-facing installation you should configure an OAuth2/OIDC provider to enable secure user authentication with Kubeapps and the cluster.
Access to the Dashboard requires a Kubernetes API token to authenticate with the Kubernetes API server.

Execute the below command to create ServiceAccount and Cluster RoleBinding:

```execute
kubectl create --namespace default serviceaccount kubeapps-operator
kubectl create clusterrolebinding kubeapps-operator --clusterrole=cluster-admin --serviceaccount=default:kubeapps-operator
```

NOTE: It's not recommended to assign the cluster-admin role to the users for Kubeapps production usage.

Please refer the following documentation to configure fine-grained access control for users: https://github.com/kubeapps/kubeapps/blob/master/docs/user/access-control.md 

**Step 2. Retrieve the token using below command.**

```execute
kubectl get secret $(kubectl get serviceaccount kubeapps-operator -o jsonpath='{range .secrets[*]}{.name}{"\n"}{end}' | grep kubeapps-operator-token) -o jsonpath='{.data.token}' -o go-template='{{.data.token | base64decode}}' && echo
```

Output will produce a token to access Kubeapps Dashboard. We will use this token in Step 5.

**Step 3. Get the Kubeapps NODE_IP and NODE_PORT by running the below commands.**


```execute
 export NODE_IP=$(kubectl get nodes --namespace kubeapps -o jsonpath="{.items[0].status.addresses[0].address}")
 export NODE_PORT=$(kubectl get --namespace kubeapps -o jsonpath="{.spec.ports[0].nodePort}" services kubeapps)
 
```

**Step 4. Access Kubeapps dashboard using the obtained URL by executing below command.**

```execute
echo "Kubeapps URL: http://$NODE_IP:$NODE_PORT"
```

You should see your Kubeapps login page. Please see the below snapshot.

![](_images/kubeapps-login-page.PNG)


**Step 5: Paste the token generated in the previous step: Step 2 to authenticate and access the Kubeapps dashboard for Kubernetes and click on "SUBMIT".**

![](_images/token.png)


**Step 6: Once you have the Kubeapps dashboard up and running, you will see following window.**

![](_images/logged-in-dashboard.png)

Now You can start deploying applications into your cluster.

### Deploy Applications using Helm Chart


**Step 1: Use the “Catalog” option on the Dashboard to select an application from the list of charts in any of the configured Helm chart repositories. In this example we will deploy WordPress using Bitnami Helm Chart.**

![](_images/catalog.png)


**Step 2: Enter "WordPress" in search box. You will see something like the one below.**

![](_images/install-wordpress-chart.png)

Step 3: Click on "Bitnami". You will see following page on dashboard.

![](_images/deploy-chart-wordpress.png)


**Step 4: Click on "Deploy" button. You will see following page on dashboard.**

Here we need to provide all the details on the form like:

- Username and Password

- Admin email

- Blog Name

- Persistent Volume Size

- MariaDB Details

- Service Type, etc.

Sample image is given below.

![](_images/config.png)

**Step 5: Click on "Deploy V10.6.1".**

You will see following page on dashboard.

![](_images/deploy-button.png)

Here, you can see all the application details like:

- Pod status

- Access URL

- Cluster and namespace details

- Application Secrets

- Application Resources Details

- Upgrade, Rollback and Delete option

![](_images/installation-details-status.png)


**Step 6: Access the application using Access URL provided by dashboard, once the pod is up and running.**

Your chart is installed successfully.

Having this,

- You can use "Upgrade" button to upgrade the chart version.

- You can use "Rollback" option to rollback the chart version earlier to the upgraded version.

- You can use the "Delete" Button to delete the WordPress from the cluster.

![](_images/upgrade-delete-rollback.png)






