# Connecting applications together
[Enabling connectivity between deployments]
[For an example, enable outside users to communicate to the frontend application]
[For an example, enable connectivity between frontend application and backend application or databases]

# Accessing the 10.244.0.0/8 ip range Nginx deployment pods from 172.16.127.0/24 ip range.
[Can access the 10.244.0.0/8 range pods after login to the Kubernetes cluster. But it's not good]
[Here, services will establish the connectivity]
[Assume this Nginx service running in port 80 and we are going to access it using the specific port. ie 30008 port]
[Going to expose the Nginx service using this 30008 port, and these kind of services are also known as "Node Port"]

# Service types
[NodePort] || <-- Accessing the service using specific port.
[ClusterIP] || <-- Accessing the service using the virtual IP in the cluster.
[LoadBalancer] || <-- AWS ALB and NLB are example for this.
[NodePort IP range is 30000 - 32767]

# Service cont...
[Service is looks like a virtual server inside the Kubernetes cluser]
[That means it has an IP address]
[This IP address is also known as cluster IP of the service]
[Port that we are going to access this service called NodePort, In this example its 30008]
[outside_user -> http://192.168.49.2:30008 [ip addr of the cluster] --[nginx_service:80]--> nginx_deployment:80]

# Create service from single command and edit the definition file accordingly
[kubectl expose deployment nginx-deployment --name nginx-service --type NodePort --port=80 --dry-run=client -o yaml > service.yaml]
[There we have to add the NodePort under the ports: configuration]
[kubectl create -f service.yaml] <-- Can create the service using the service definition file.
[kubectl get services] || <-- Can list the services created in the cluser.
[kubectl get svc] || <-- Can list the services created in the cluser. 
[From the above command, will preview the virtual ip address of the service]
[curl http://192.168.49.2:30008] || <-- Here curl the IP address of the Kubernetes cluster with the specified NodePort.
[If have multiple nodes, when the deployment was deployed accross multiple nodes we can access using the IP address with the same NodePort]
[ie: http://192.168.39.2:30008 || http://192.168.29.2:30008 like wise]

# Describe the service
[kubectl describe svc nginx-service ] <-- From describing the service, can identify which pods are working as endpoints.