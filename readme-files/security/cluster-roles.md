# Cluster roles and Cluster Role binding
[Using for cluster wide resource management]
[For an example, create/delete nodes, create/delete pv/pvs]
[Role binding is using for add users to perform these tasks] || << Same as the roles and role bindings.
[It's not specified to the "namespaces" and aplly to the whole cluster]

[From below command, can list the existing "cluster roles" of the cluster]
[kubectl get clusterrole]
[From below command, can list the "cluster role bindings"]
[kubectl get clusterrolebindings]

[From below, command can create a "cluster role"]
[kubectl create clusterrole cluster-role-minikue --verb=list --verb=get --resource=nodes]

[From below, command can create a "cluster role binding"]
[create clusterrolebinding cluster-role-binding-minikube --clusterrole=cluster-role-minikube --user=dev-user]

[Also, "auth can-i" command can use to check the created role as well]
[auth can-i list nodes --as dev-user]
