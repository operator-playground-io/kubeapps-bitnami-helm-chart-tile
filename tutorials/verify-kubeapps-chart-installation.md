---
title: Verify Kubeapps Chart Installation
description: Learn how to verify that Kubeapps chart has been installed successfully.
---


Once the helm chart installation is complete, we need to verify that all the pods and services are up and running.


### Check the Status of Operator Pod

Execute below command to check status of pods and services.


```execute
kubectl get pods --namespace kubeapps
```

You will see some output as shown below.

```
NAME                                                         READY   STATUS    RESTARTS   AGE
apprepo-kubeapps-sync-bitnami-7pltg-thb7t                    1/1     Running   2          43s
kubeapps-85779f8d67-4pz2n                                    1/1     Running   0          55s
kubeapps-85779f8d67-px72l                                    1/1     Running   0          55s
kubeapps-internal-apprepository-controller-cb578f9c6-j4f85   1/1     Running   0          55s
kubeapps-internal-assetsvc-69f67698d5-b5sr7                  1/1     Running   0          55s
kubeapps-internal-assetsvc-69f67698d5-pszh6                  1/1     Running   0          55s
kubeapps-internal-dashboard-59bfcc5c89-875c6                 1/1     Running   0          55s
kubeapps-internal-dashboard-59bfcc5c89-8gv8d                 1/1     Running   0          55s
kubeapps-internal-kubeops-857cbcf8b9-7lzfq                   1/1     Running   0          55s
kubeapps-internal-kubeops-857cbcf8b9-khp6m                   1/1     Running   0          55s
kubeapps-postgresql-primary-0                                1/1     Running   0          55s
kubeapps-postgresql-read-0                                   1/1     Running   0          55s
```

Note: Please wait for the Pod STATUS to be "Running", and then proceed further.


### Check the Status of Kubernetes Resources

You can run the following command to know status of all the deployed resources inside the namespace `kubeapps`.


```execute
kubectl get all --namespace kubeapps
```

All the deployment and service status should be Running.

```
NAME                                                         READY   STATUS    RESTARTS   AGE
apprepo-kubeapps-sync-bitnami-7pltg-thb7t                    1/1     Running   2          43s
kubeapps-85779f8d67-4pz2n                                    1/1     Running   0          55s
kubeapps-85779f8d67-px72l                                    1/1     Running   0          55s
kubeapps-internal-apprepository-controller-cb578f9c6-j4f85   1/1     Running   0          55s
kubeapps-internal-assetsvc-69f67698d5-b5sr7                  1/1     Running   0          55s
kubeapps-internal-assetsvc-69f67698d5-pszh6                  1/1     Running   0          55s
kubeapps-internal-dashboard-59bfcc5c89-875c6                 1/1     Running   0          55s
kubeapps-internal-dashboard-59bfcc5c89-8gv8d                 1/1     Running   0          55s
kubeapps-internal-kubeops-857cbcf8b9-7lzfq                   1/1     Running   0          55s
kubeapps-internal-kubeops-857cbcf8b9-khp6m                   1/1     Running   0          55s
kubeapps-postgresql-primary-0                                1/1     Running   0          55s
kubeapps-postgresql-read-0                                   1/1     Running   0          55s

NAME                                   TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
service/kubeapps                       NodePort    10.111.100.178   <none>        80:32518/TCP   56m
service/kubeapps-internal-assetsvc     ClusterIP   10.110.221.110   <none>        8080/TCP       56m
service/kubeapps-internal-dashboard    ClusterIP   10.104.147.77    <none>        8080/TCP       56m
service/kubeapps-internal-kubeops      ClusterIP   10.111.78.45     <none>        8080/TCP       56m
service/kubeapps-postgresql            ClusterIP   10.104.37.68     <none>        5432/TCP       56m
service/kubeapps-postgresql-headless   ClusterIP   None             <none>        5432/TCP       56m
service/kubeapps-postgresql-read       ClusterIP   10.96.38.221     <none>        5432/TCP       56m

NAME                                                         READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/kubeapps                                     2/2     2            2           56m
deployment.apps/kubeapps-internal-apprepository-controller   1/1     1            1           56m
deployment.apps/kubeapps-internal-assetsvc                   2/2     2            2           56m
deployment.apps/kubeapps-internal-dashboard                  2/2     2            2           56m
deployment.apps/kubeapps-internal-kubeops                    2/2     2            2           56m

NAME                                                                   DESIRED   CURRENT   READY   AGE
replicaset.apps/kubeapps-85779f8d67                                    2         2         2       56m
replicaset.apps/kubeapps-internal-apprepository-controller-cb578f9c6   1         1         1       56m
replicaset.apps/kubeapps-internal-assetsvc-69f67698d5                  2         2         2       56m
replicaset.apps/kubeapps-internal-dashboard-59bfcc5c89                 2         2         2       56m
replicaset.apps/kubeapps-internal-kubeops-857cbcf8b9                   2         2         2       56m

NAME                                           READY   AGE
statefulset.apps/kubeapps-postgresql-primary   1/1     56m
statefulset.apps/kubeapps-postgresql-read      1/1     56m

NAME                                                 COMPLETIONS   DURATION   AGE
job.batch/apprepo-kubeapps-sync-bitnami-1611746400   1/1           2s         25m
job.batch/apprepo-kubeapps-sync-bitnami-1611747000   1/1           2s         15m
job.batch/apprepo-kubeapps-sync-bitnami-1611747600   1/1           2s         5m5s
job.batch/apprepo-kubeapps-sync-bitnami-7pltg        1/1           54s        56m

NAME                                          SCHEDULE       SUSPEND   ACTIVE   LAST SCHEDULE   AGE
cronjob.batch/apprepo-kubeapps-sync-bitnami   */10 * * * *   False     0        5m13s           56m
```
