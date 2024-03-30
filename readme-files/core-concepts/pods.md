# A pod
[Single instance of an application]

# Helper containers
[Work along side the application inside the pod]
[Sharing same resources]

# Create pod using single command
[kubectl run nginx-pod --image=nginx]

# Create pod as dry-run
[kubectl run nginx-pod --image=nginx --dry-run=client]

# Get the pod configurations in yaml format without creating a pod
[kubectl run nginx-pod --image=nginx --dry-run=client -o yaml > nginx-pod.yaml]

# Create pod using the yaml file
[kubectl create -f nginx-pod.yaml]
[kubectl apply -f nginx-pod.yaml]

# Check the running pods
[kubectl get pods]
[kubectl get pods] <-- All namespaces
[kubectl get pods -o wide] <-- With network and node configurations 
[kubectl get pods -n kube-system]
[kubectl get pods --namespace=kube-system]
[kubectl get pods --namespace kube-system]

# Get the running pod's configurations in yaml format
[kubectl get pods nginx-pod -o yaml]

# Troubleshooting the pods with logs
kubectl describe pod nginx-pod
kubectl logs nginx-pod

