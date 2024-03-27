# Defaul namespace
[If not specify the namespace, resources will be created in the "Default" namespace]
[This "default" namespace created when the cluster startup]

# kube-system namespace
[This "kube-system" namespace created when the cluster startup]
[It's containing the core services of Kubernetes cluster, like DNS, ETCD, kube-controller, kube-apiserver like wise]

# kube-public namespace
[If the resources all available to all the users, will be created in this namespace]

# If having different working environments, can create different namespaces
[kubectl create namespace develop] || <-- Namespace for develop environment 
[kubectl create namespace qa] || <-- Namespace for qa environment 

# Can assign Resource limits to the namespaces.
[Users will not utilize the resources more than the quota that was defined to the namespace]

# List all namespaces
[kubectl ket namespaces]
[kubectl get ns]

# Create namespace
[kubectl create namespace develop]
[kubectl create -f namespace-develop.yaml] || <-- Can use yaml file to create a namespace.

# List resources in specific namespace
[kubectl get all --namespace=develop]

# Switch between namespaces
[kubectl config set-context $(kubectl config current-context) --namespace=develop] || <-- Switch to develop namespace.
[kubectl config set-context $(kubectl config current-context) --namespace=default] || <-- Switch back to develop namespace.

# Resource quota
[kubectl get resourcequotas --namespace=develop] || <-- From this command can, fetch the quota information of specific namespace.

# Local DNS
[for the service, it will be ended with "svc.cluster.local"]
[nginx-test.dev.svc.cluster.local FQDN have to use access it from different namespaces]

# Same namespace resource accessing
[can use the service name to access inside the namespace. ie: In dev namespace, service name is nginx-svc and it can be accessble inside the namespace from "nginx-svc"]

# Different namespace resource accessing
[Have to use FQDN to access the services in different namespaces. ie: from test namespace, want to access "nginx-svc". It will be accessible from "nginx-svc.dev.svc.cluster.local"]
