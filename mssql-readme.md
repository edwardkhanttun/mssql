# Mssql Setup
### Install Mssql on Kubernetes using Helm

Run command to install the mssql database

helm install mssql-latest-deploy . --set ACCEPT_EULA.value=Y --set MSSQL_PID.value=Developer

The output should look as shown below:

1.kubectl get deployments

```sh
NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
mssql-latest-deploy      1/1     1            1           4h12m
```

2.kubectl get pods
```sh
NAME                                      READY   STATUS    RESTARTS   AGE
mssql-latest-deploy-6745ffcf8b-b9tt7      1/1     Running   0          4h12m
```

3.kubectl get services
```sh
NAME                   TYPE           CLUSTER-IP       EXTERNAL-IP      PORT(S)           AGE
kubernetes             ClusterIP      10.96.0.1        <none>           443/TCP           357d
mssql-latest-deploy    LoadBalancer   10.97.76.26      172.20.105.226   1433:32107/TCP    4h12m
mssql-sample-service   ClusterIP      10.101.184.128   <none>           1433/TCP          352d
sample-angular         ClusterIP      10.111.195.160   <none>           80/TCP            48d

```


## Connect to SQL Server

Now you are ready to connect to the SQL Server using any of the familiar tools that you work with, like the [SSMS](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15) (SQL Server Management Studio) or [SQLCMD](https://docs.microsoft.com/en-us/sql/tools/sqlcmd-utility?view=sql-server-ver15) or [ADS](https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15) (Azure Data Studio), etc. The IP address that you will use to connect is the External-IP address for the mssql-latest-deploy service which in this case is 20.44.43.212 that will be used to connect to SQL Server.

For more details on the SQL Server deployment on AKS using manual method please refer [Deploy a SQL Server container in Kubernetes with Azure Kubernetes Services (AKS)](https://docs.microsoft.com/en-us/sql/linux/tutorial-sql-server-containers-kubernetes?view=sql-server-ver15).