# OS upgrade
[If pod goes offline for than 5 minutes, that will be indicated as "terminated" pod]
[From the below command, can set the timeout value for it]
[kube-controller-manager --pod-eviction-timeout=5m0s]

[Same logic is applicable for the Nodes as well. If the node goes offline for more than 5 minutes and come back online, it will contain 0 pods]
[If there using the replicaSet no issues, after 5 minutes new pods will created on remaining nodes and consider the offline node as dead]
[If there is a Pod, not belong to the repolicaSet this pod will be lost]

# Drain the nodes
[If the node was draind using the command, purposely that pod will be scheduled in another node]
[kubectl drain node-01]
[Some cases, just above command is not capable to perform the draining action. Because DaemonSets are running and have to ignore it as well]
[kubectl drain node-01 --ignore-daemonsets --delete-emptydir-data --force]
[With this "kubectl drain" command execution, node will be marked as "cordon" That means, pods will not be scheduled on this node]
[Then, can perform the maintenance or upgrade activity of the node]
[After completing the maintenance task, have to "uncordon" the node to schedule the pods again as normally]
[kubectl uncorden node-01]

# Corden and Uncorden
[From the command called "cordon", it will stop the pod scheduling on specific node]
[ie: kubectl cordon node-02]
[If want to allow the node to scheduling the pods, have to uncorden the node]
[ie: kubectl uncordon node-02]
