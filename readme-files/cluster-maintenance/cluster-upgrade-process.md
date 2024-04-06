# Upgrade clusters
[Cluster major components can be run with different version, but there is a limitation]
[For an example, let assume kubernetes version is "v1.20" and take it as "X"]
[
    controller-manager version compatible with X or X-1
    [v1.20 or v1.19]
    kube-scheduler version compatible with X or X-1
    [v1.20 or v1.19]
]

[
    kubelet version compatible with X or X-1 or X-2
    [v1.20 or v1.19 or v1.18]
    kube-proxy version compatible with X or X-1 or X-2
    [v1.20 or v1.19 or v1.18]
]

[
    kubectl version compatible with X or X+1 or X-1
    [v1.21 v1.20 or v1.19]
]

# Upgrading strategies
[
    Down the Master nodes then upgrade, there is a downtime.
    Down the Worker nodes one by one, then upgrade the nodes.
    Add new nodes to the cluster and remove the old nodes. [Can do in cloud platforms]
]

[Can get the upgrade instructions from below command]
[kubeadm upgrade plan]
[Once the kubeadm upgrade is done, have to upgrade the kubelet version accordingly]
[Also, kubelet and kubeadm version can be upgrade using the relevant OS package manager commands as well]
[apt-get upgrade -y kubeadm=1.12.0]
[apt-get upgrade -y kubelet=1.12.0]
