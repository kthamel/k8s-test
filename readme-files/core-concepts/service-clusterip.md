# Cluster IP 
[There is a 3 tier web application hosted in Kubernetes]
[Front-end:Nginx, Back-end:Python and Database:Postgres]
[Here Nginx pods want to call Python Pods. But these pods are terminating and re-creating time to time and don't have the static IP addresses]
[Here, Kubernetes is providing a solution for this. Group of pods can be accessible through one IP address.]
[This IP address based service is also know as ClusterIP]

# From single command can create the ClusterIP service
[kubectl expose deployment nginx-deployment --type ClusterIP --port 80 --dry-run=client -o yaml > clusterip.yaml]
[kubectl create -f clusterip.yaml]
[Make sure to add the "selector" section and put the lables of it]
[Inside the Kubernetes cluster, can user the created ClusterIP for internal communication]

