# k8s-test ReadMe file.

# [Master node compoents]
# kube-apiserver
[Is orchestrate the all operations, within the cluster]
[Authenticate and validate requests, then retrive data and update etcd]
[ps -aux | grep -i "kube-apiserver"]

# etcd
[Is distributed key-value database]
[etcdctl --version]
[All the changes making to the cluster, records in etcd database]

# kube-scheduler
[Scheduling pods on the nodes, which pods goes where]

# kube controller manager
[configuration file path is /etc/systemd/system/kube-controller-manager.service]
[ps -aux | grep -i "kube-controller-manager"]
[Monitor the health of nodes - Node controller]
[Monitor the health of replica sets - Replication controller]
[Deployment controller]
[Namespace controller]
[Endpoint controller]
[PV Protection controller]
[Job controller]
[Service Account controller]
[PV Binder controller]
[Replicaset]
[CronJob]
[StatefulSet]

# [Worker node compoents]
# kubelet
[Register nodes to the cluster]
[Create pods, monitor the node and pods]
[ps -aux | grep -i "kubelet"]

# kube-proxy
[Enable communication between the services, within the cluster]
[Look for new services created]
[Create appropriate rules on each nodes to forward traffic to backend pods]
