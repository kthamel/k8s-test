# Network policies
[Simply, the Network policies are similar to the "firewall rules"]
[For an example, there is DB pod and Web application Pod  inside the kubernetes cluster]
[DB Pod is only allowed to acces from Web application pod via "3306/TCP" port]
[There using the "Network Policies" to allow traffic to the DB pod]

[
    Web app pod -->> DB pod || <<-- Only allowed from Web app pod 
]

# Network security
[All kubernetes resources inside the cluster, can communicate with each other components without adding "New routes"]
[Because, by default kubernetes configured with "Allow all" rule]
[Using the network policy, can control the access]
[Inside the network policies, there define the "podSelector" to allow traffic from specific pods]
[ie: DB pod is allow inbound from Web app pod from specific "port/TCP"]

[First, have to create the "Network Policy" using the YAML file]
[Inside the definition file, have to define allowed source as below]

[
    apiVersion: networking.k8s.io/v1
    kind: NetworkPolicy
    metadata:
        name: workspace-pod-network-policy
        amespace: default
    spec:
        podSelector:
            matchLabels:
                version: httpd
]

[In this example going to allow access to the "workspace pod" from "httpd pod"]
[Then, have to define the policy types]
[
    -   Ingress     || Inbound traffic
    -   Egress      || Outbound traffic
]

[There after have to define "policyTypes" Then ingress/egress rules according to the requirement]
[
    policyTypes:
    - Ingress
    ingress:
    - from: 
      - podSelector:
            matchLabels:
                version: workspace
      ports:
      - protocol: TCP
        port: 80
]

[Using the below command, can fetch the created network policies]
[kubectl get networkpolicies.networking.k8s.io]

[Sample "NetworkPolicy" as below]

[

apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: httpd-network-policy
  namespace: default
spec:
  podSelector:
    matchLabels:
      version: httpd    <<--The pod, that we want to secure
  policyTypes:
    - Ingress
  ingress:
  - from: 
    - podSelector:
        matchLabels:
          version: nginx  <<-- Required label to access the "httpd pod"
    ports:
    - protocol: TCP
      port: 80      <<-- Required protocol to access the "httpd pod"

]