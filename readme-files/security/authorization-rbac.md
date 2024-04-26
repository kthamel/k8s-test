# RBAC - Role Base Access Control
[Can create the roles using the YAML files]
[
    apiVersion: rbac.authorization.k8s.io/v1
    kind: Role
    metadata:
    creationTimestamp: null
    name: role-dev
    rules:
    - apiGroups:
    - ""
    resources:
    - pods
    verbs:
    - get
    - list
]

[Can create this using the kubectl]
[ie: kubectl create -f rbac-pods-get-list.yaml]
[And, list the existing roles using the below command]
[kubectl get roles]

[After, the role creation have to assign the users to the roles]
[It's called rolebinding]
[kubectl create rolebinding rolebinding-dev --role=role-dev --dry-run=client -o yaml > rbac-role-binding.yaml]
[
    apiVersion: rbac.authorization.k8s.io/v1
    kind: RoleBinding
    metadata:
    creationTimestamp: null
    name: rolebinding-dev
    roleRef:
    apiGroup: rbac.authorization.k8s.io
    kind: Role
    name: role-dev
]

[Can create this using the kubectl]
[ie: kubectl create -f rbac-role-binding.yaml]
[And, list the existing roles using the below command]
[kubectl get rolebindings]

# Check the created roles as loged in user
[kubectl auth can-i create pods]

# Check the created roles, without login
[kubectl auth can-i create pods --as role-dev]