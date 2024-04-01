# Encrypting secrets
[By default secrets are encoded, it can decode very easily from bash command]
[Its not secure and required the more secure mechenism to store secrets]
[If we stored the data in ETCD, can avoid this issue]
[From the below command can install etcd-client on Mac os]
[brew install etcd] 
[etcd --version]
[etcdctl version]

[As a solution for this workaround can use HashiCorp Vault]
[Here we have to make changes to the kube-apiserver configurations, mount the yaml file as a volume mount]
