# Upgreding the cluster from CLI
[First, identify the operating system kubernetes running using below command]
[cat /etc/*release*] || <-- Or other command to fetch the OS

# Check the latest available version of kubeadm
[kubeadm upgrade plan]

# Drain the node, and unschedule the node
[kubectl drain node-01]
[kubectl get nodes] || <-- From the output of this command, can verify the status of the node

# Upgrade the node into the same Minor version latest version
[kubeadm upgrade apply v1.28.8 --force]

# Upgrade the node into the latest Minor version
[Edit the /etc/apt/sources.list.d/kubernetes.list file and set the required Minor version]
[vim /etc/apt/sources.list.d/kubernetes.list]

[Update the operating system]
[apt update]

[Check the patch list under the Minor version]
[apt-cache madison kubeadm]

[Install the required kubeadm version using the package manger]
[apt-get install kubeadm=1.29.0-1.1]

[Again run the below command and check required version is avaiable]
[kubeadm upgrade plan] || <-- Only for Master nodes

[Upgrade the node if the required version is available]
[kubeadm upgrade apply v1.29.0] || <-- Only for master nodes
[kubeadm upgrade node] || <-- Only for worker nodes
 

# Upgrade kubelet 
[Upgrade the kubelet version equals with the kubeadm version]
[apt-get install kubelet=1.29.0-1.1]

[Reaload the daemons inside the operating system]
[systemctl daemon-reload]

[Restart the kubelet service]
[systemctl restart kubelet]

[Uncorden the node]
[kubectl uncordon node-01]
