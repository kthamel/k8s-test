# Static pods
[Without kube-api server kubelet can create the pods from reading the yaml files, located in specific location]
[If the created pods delete using kubectl command, it will created automatically]
[Onle to create pods from this way]

# Identify the static pod placing directory path
[Fist, have to use linux command to get the details of the kubelet process]
[ps -aux | grep -i "kubelet"]
[It will give the path of "config" file begins with --config=]
[ie: --config=/var/lib/kubelet/config.yaml]
[Then search "staticPodPath" in this file. Path is declared with it]
[ie: /etc/kubernetes/manifests]
[Have to put the pod definition yaml files to this directory]
[If want to delete the pod permanently, have to delete the yaml file from the staticPodPath]
[ie: rm -rf /etc/kubernetes/manifests/nginx-pod.yaml]

# Difference between static pods and DaemonSets
[Both deployments are ignored by the kube-scheduler]
[Static pods]
[Created by kubelet]
[Deploying controlplane components]

[DaemonSets]
[Created by kubeApiServer, aka DaemonSet Controller]
[Deploying monitoring tools and plugins to the nodes]
