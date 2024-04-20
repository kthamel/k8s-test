# Certificates to the Kubernetes cluster
[Can use dedicated CA server for generate the certificates to the users as well]
[Have to store the certificate key file inside of this server]
[Can use the kubernetes master node as thie CA server]
[But, when the team grows its not a good approach]

# Certifiactes API
[This case, uses don't want to log in to the master node to sign the certificates]
[There, creating an object called, "CertificateSigningRequest"]
[Then administrators of the kubernetes cluster, can review and approve the certificates using the "kubectl" commands]

[First user has to generate the own key using the terminal]
[openssl genrsa -out kthamel.key 2048]

[Then generate the CSR using the generated key file] || <<- CSR: Certificate Signing Request 
[openssl req -new -key kthamel.key -subj "/CN=kthamel" -out kthamel.csr]

[Now, administrator has to create the CSR object using the above generated CSR file]
[There, administrator has to create a kubernetes manifest file]

[
    apiVersion: certificates.k8s.io/v1
    kind: CertificateSigningRequest
    metadata:
      name: kthamel
    spec:
      expirationSeconds: 3600
      signerName: kubernetes.io/kube-apiserver-minikube
      usages:
      - server auth
      - digital signature
      - key encipherment
      request: put_the_base64_encoded_value_of_the_csr_file
]

[Then create the object using the kubectl command]
[create -f certificate-signing-request.yaml]
[From the below command, can verify the csr status]
[kubectl get csr ] || or || [kubectl get certificatesigningrequests.certificates.k8s.io]

[Now administrator can approve the certificates, using the below command]
[kubectl certificate approve kthamel]  || <<-- Name of the pending CSR is kthamel
[Once, running the get csr command, user can get the status of the csr]

[Can use below command, to get existing CSR in YAML format]
[kubectl get csr kthamel -o yaml]

[All the certificates related things managed by "kube-controller-manager" component]
