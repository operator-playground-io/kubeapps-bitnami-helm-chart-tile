---
title: How to Access Kubeapps dashboard
description: This tutorial explains how to access Kubeapps Dashboard
---


### Access Kubeapps dashboard


Step 1. Create a Kubernetes API token to access Kubeapps and Kubernetes:

For any user-facing installation you should configure an OAuth2/OIDC provider to enable secure user authentication with Kubeapps and the cluster.
Access to the Dashboard requires a Kubernetes API token to authenticate with the Kubernetes API server.

Execute below command to create serviceaccount and cluster rolebinding:

```execute
kubectl create --namespace default serviceaccount kubeapps-operator
kubectl create clusterrolebinding kubeapps-operator --clusterrole=cluster-admin --serviceaccount=default:kubeapps-operator
```

NOTE It's not recommended to assign users the cluster-admin role for Kubeapps production usage. Please refer to the Access Control documentation to configure fine-grained access control for users.

Step 2. Retrieve the token using below command:

```execute
kubectl get secret $(kubectl get serviceaccount kubeapps-operator -o jsonpath='{range .secrets[*]}{.name}{"\n"}{end}' | grep kubeapps-operator-token) -o jsonpath='{.data.token}' -o go-template='{{.data.token | base64decode}}' && echo
```
Step 3. Get the Kubeapps NODE_IP and NODE_PORT by running below commands:


```execute
 export NODE_IP=$(kubectl get nodes --namespace kubeapps -o jsonpath="{.items[0].status.addresses[0].address}")
 export NODE_PORT=$(kubectl get --namespace kubeapps -o jsonpath="{.spec.ports[0].nodePort}" services kubeapps)
 
```


Step 4. Access kubeapps dashboard using the obtained URL by executing below command:

```execute
echo "Kubeapps URL: http://$NODE_IP:$NODE_PORT"
```
You should see your Kubeapps login page.

Please see the below snapshot :

![](_images/kubeapps-login-page.PNG)


Step 5: Paste the token generated in the previous Step 2 to authenticate and access the Kubeapps dashboard for Kubernetes.

![](_images/token.png)


Step 6: Once you have the Kubeapps Dashboard up and running, you will see following on dashboard:

![](_images/logged-in-dashboard.png)

Now You can start deploying applications into your cluster.


Step 7: Use the “Catalog” option on the Dashboard to select an application from the list of charts in any of the configured Helm chart repositories. In this example we will deploy WordPress.

![](_images/catalog.png)


Step 8: Enter "WordPress" in search box. You will see similar to following snapshot:

![](_images/install-wordpress-chart.png)

Click on "Bitnami".

You will see following page on dashboard.

![](_images/deploy-chart-wordpress.png)


Step 9:Click on "Deploy" button.


Step 10: You will see following page on dashboard. 

![](_images/config.png)

Here we need to provide all the details on the Form like : Username, Password, Admin email, Blog Name,Persistent Volume Size, MariaDB Details,Service Type etc as shown in below snapshot.

Step 11: Click on "Deploy V10.6.1".

![](_images/deploy-button.png)


Step 12: You will see following page on dashboard:

![](_images/installation-details-status.png)

Here you can see all the application details like : 
- Pod status.
- Access URL.
- Cluster and namespace details.
- Application Secrets
- Application Resources Details.
- Upgrade, Rollback and Delete option.


Step 13: Access the application using Access URL provided by dashboard once pod is up and running.

Step 14: Once the pod is up and running, your chart is installed successfully.
Now you can use "Upgrade" button to upgrade the chart version.
You can use "Rollback" option to Rollback the chart version previous to upgraded version.
Also you can use the "Delete" Button to delete the WordPress from the cluster.

![](_images/upgrade-delete-rollback.png)






