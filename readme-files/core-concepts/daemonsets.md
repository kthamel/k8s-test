[DaemonSets are looks like replicaSets, Different is daemonSet is running only one copy in each node.]
[If new node as added to the cluster, daemonSet will automatically replicate to the new node]
[When setting up the Monitoring solution, Log viewer for nodes, daemonSets will be required.]
[Can deploy the kube-proxy as daemonSet]
[DaemonSet yaml file is similar to the ReplicaSet yaml file, Difference is kind]
[kubectl get daemonsets] || <-- From this command, can list the available daemonSets 
