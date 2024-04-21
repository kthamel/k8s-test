# Authrization
[In kubernetes authrization is required to control the access to the resources]
[For an example, developers are authorized only to list the opds. Other than that, nothing]
[There are 4 different authorization mechanisms as below]
[
    Node    : Node authorizer handles the autorization between "kube-apiserver" and "kubelet"
    ABAC    : Attribute Based Authorization Control || <<-- Difficult to manage, because all the time view and approve is required to the "requests"
    RBAC    : Role Base Access Control || <<-- Create pre-defined roles and add users into the groups. Like IAM roles. And It's solutions to the ABAC
    Webhook : Open Policy Management is an example for this. ie: Kyverno
] 

[If, read the "kube-apiserver.yaml" file, can identify the "default Authorization Mode" of the kubernetes cluster]
[cat kube-apiserver.yaml | grep -i "authorization-mode"] || <<-- Output will be "Node,RBAC"
[or, kubectl get pods --namespace=kube-system kube-apiserver -o yaml | grep -i "authorization-mode"]
[When authorizing, it will check the authorization in order Node -> RBAC]
[If the autorization was done from the first mechanism, it's not moving to the next mechanism. It's already authorized request]

