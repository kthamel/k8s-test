# KubeConfig file
[All the time, specifying the client key/crt for the authentication is not a good practice]
[From using the config file, can avoid this]
[By default it's stored the ~/.kube/config path]
[Simply it's contain the below content] || <<-- For minikube
[

apiVersion: v1
clusters:
- cluster:
    certificate-authority: /Users/kthamel/.minikube/ca.crt
    extensions:
    - extension:
        last-update: Sun, 21 Apr 2024 11:12:21 WEST
        provider: minikube.sigs.k8s.io
        version: v1.32.0
      name: cluster_info
    server: https://127.0.0.1:49831
  name: minikube
contexts:
- context:
    cluster: minikube
    extensions:
    - extension:
        last-update: Sun, 21 Apr 2024 11:12:21 WEST
        provider: minikube.sigs.k8s.io
        version: v1.32.0
      name: context_info
    namespace: default
    user: minikube
  name: minikube
current-context: minikube
kind: Config
preferences: {}
users:
- name: minikube
  user:
    client-certificate: /Users/kthamel/.minikube/profiles/minikube/client.crt
    client-key: /Users/kthamel/.minikube/profiles/minikube/client.key

]

# Content of the kube config file
[Mainly there are 3 sections of this file]
[
    Clusters    : Various clusters, users have to access [ie: Dev, QA, Prod]
    Context     : Mapping between the users and clusters [ie: user-dev --> Dev cluster]
    Users       : Useraccounts, that have the access of the cluster [ie: admin, user-dev, user-prod]
]

# Context
[Sample context as below]
[
    - context:
       cluster: minikube
       extensions:
       - extension:
          last-update: Sun, 21 Apr 2024 11:12:21 WEST
          provider: minikube.sigs.k8s.io
          version: v1.32.0
         name: context_info
       namespace: default
       user: minikube
    name: minikube
]

# Users
[Unders the user section, there specifying the certificate file paths]
[
    users:
    - name: minikube
      user:
        client-certificate: /Users/kthamel/.minikube/profiles/minikube/client.crt
        client-key: /Users/kthamel/.minikube/profiles/minikube/client.key
]

# View and modify the kube config file from CLI
[From below command can view the current context]
[kubectl config current-context]
[More options from: kubectl config --help]

[Switch to different kubernetes cluster, using different context]
[kubectl config use-context admin@cluster-prod]
[By default its swtiching into the default namespace, if different namespace is required have to define inside the Context]

[Using the custom config file and use the specific context of it]
[kubectl config --kubeconfig=/root/custom-config use-context pre_production] || <<-- Here "custom-config" is the custom config file
