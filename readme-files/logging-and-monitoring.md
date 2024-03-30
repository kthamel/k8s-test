# Monitoring 
[Monitoring resource consumption, performance, disk utilization]
[No inbuilt monitoring solution for Kubernetes and have to use 3rd party solutions like]
[
    Metrics Server
    Prometheus
    Elastic Stack
    DataDog
    Dynatrace
]

[To monitor the node resource utilization, can use below command. It's from Metric Server.]
[In kubernetes clusters "cadvisor" is sending the metrics from pods to the Metric server via kubelet]
[In minikube, have to enable the "Metric server" from below command]
[minikube addons enable metrics-server]
[Once executing the bellow command, able to retreive the metrics]
[kubectl top node node_name]
[top pod --namespace=kube-system kube-apiserver-controlplane]

# Logging 
[Using the below command, can get the logs associated with the pod. And, "-f" will provide the tail of live log]
[kubectl logs -f --namespace=kube-system kube-apiserver-controlplane ]
