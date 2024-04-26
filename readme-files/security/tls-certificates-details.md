# View certificate details
[If the kubernetes cluster was provisioned fully scratch, have to generate the certificates manually]
[If the kubernetes cluster was provisionde using the automated tool like "kubeadm", it will take care about the certificates]
[From executing the below command, can get the details of the specific certificate]
[openssl x509 -in apiserver.crt -text -noout] || <<-- Here getting the details of apiserver.crt
[kubectl logs --namespace=kube-system etcd-minikube | grep -i "TLS"] || <<-- Can get the caller associated certificates from the log.
