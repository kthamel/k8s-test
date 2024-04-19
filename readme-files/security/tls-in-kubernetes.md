# Certificates with public keys
[These certificates can identify if its having the below extentions]
[
    *.crt
    *.pem
]

# Certificates with private keys
[These certificates can identify if its having the below extentions]
[
    *.key
    *-key.pem
]

# Find the location of kubernetes certificates
[ps -aux | grep -i "kubelet"] || <<-- From this, able to find the kubelet confing.yaml file location.
[sudo cat /var/lib/kubelet/config.yaml | grep -i static] || <<-- Then, identify the static pod manifest location.
[ cd /etc/kubernetes/manifests/] || <<-- Move to the manifest file location.
[Read the "kube-apiserver.yaml" yaml file and identify the location that certificates were stored]
[For different certificates, might be different directories]

[
     - mountPath: /etc/ssl/certs
      name: ca-certs

    - mountPath: /etc/ca-certificates
      name: etc-ca-certificates

    - mountPath: /var/lib/minikube/certs
      name: k8s-certs

    - mountPath: /usr/local/share/ca-certificates
      name: usr-local-share-ca-certificates

    - mountPath: /usr/share/ca-certificates
      name: usr-share-ca-certificates
]

[Can use same approach to fetch the associated certificates to the "ETCD" service]

[Different components of the Kubernetes cluster are using the different ".crt" and ".key" pairs to authenticate to the "kube-apiserver"]
[
    admin-user:                 admin.crt and admin.key
    kube-scheduler:             scheduler.crt and scheduler.key
    kube-controller-manager:    controller-manager.crt and controller-manager.key
    kube-proxy:                 kube-proxy.crt and kube-proxy.key
]

[If you are using the Minikube, you can find these certificates and keys inside the below file path]
[/var/lib/minikube/certs]
