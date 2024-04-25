# Service accounts in Kubernetes
[There are 2 types of accounts in Kubernetes]
[
    User accounts:      For humans
    Service accounts:   For applications
]

[For an example, When do the deployments using the Jenkins pipelines it requires SA]
[From below commands can list avaiable service accounts]
[
    kubectl get serviceaccounts
    kubectl get sa
]

[When creating the service account, it will automatically creates the token]
[External applications will use this token to perform the API calls]

[From the below command, can create a service account]
[kubectl create serviceaccount sa-dashboard] || <<-- Here, creating a SA name as "sa-dashboard"
[
    apiVersion: v1
    kind: ServiceAccount
    metadata:
    creationTimestamp: null
    name: sa-dashboard
]

[Here token will be created as "secret" boject and it can fetch using the below command]
[kubectl get secret sa-dashboard]
[This tiken will be worked as "Authorization Bearer Token" for the API]

[There, 3rd party application is hosing inside the Kubernetes cluster it will be easier]
[Because, created secret can mount to the 3rd party application as "volume"]

[When creating a pod in specific namespace, it will assign the default "ServiceAccount" automatically]
[After log in to the Pod, can read the associated token easily from below command]

[kubectl run pod-ubuntu --image=ubuntu:latest --command sleep 300]
[kubectl exec -it pod-ubuntu /bin/bash]
[cat /var/run/secrets/kubernetes.io/serviceaccount/token]

[If the content of the "jwt token" decoded from the decoder, can get the information about the service account]
[And, these jwt tokens are not expiring]

[If required to create new token, can create it using bellow command]
[kubectl create token sa-dashboard]