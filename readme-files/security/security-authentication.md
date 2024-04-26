# Authentication
[Access the kubernetes clusters from below mechanisms are not allowed]
[
    ssh to the kubernetes nodes
    username/password authentication
]

[Basically, users and services are require to access the kubernetes clusters]
[All the requests to the kubernetes cluster is going through the kube-apiserver component]
[kube-apiserver can authenticate, below auth mechanisms]
[
    static password files
    static token files
    certificates
    identity services - ie: LDAP
]

