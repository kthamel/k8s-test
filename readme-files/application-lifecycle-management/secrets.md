# Secrets 
[Can store the configuration data like environmental varibles using the ConfigMap]
[But, passwords or login credentials are not storing as ConfigMap]
[Can create the secrets using below 3 mothods]

[
    docker-registry : docker-registry type secret is for accessing a container registry.

    generic : A generic type secret indicate an Opaque secret type.

    tls : A tls type secret holds TLS certificate and its associated key.
]

[Also, we can create secrets using the Imperative and Declarative methods]
[Same as the ConfigMaps, can create the Secrets as below under generic category]

[
    --type=string
    --from-file
    --from-literal
]

[Example for --from-literal method]
[kubectl create secret generic dev-login  --type=string --from-literal=user=root --from-literal=password=passwrd] || <-- This is Imperative method
[kubectl create -f secret-01.yaml] || <-- This is declarative method

[

    apiVersion: v1
    data:
      password: cGFzc3dyZA==
      user: cm9vdA==
    kind: Secret
    metadata:
      creationTimestamp: null
      name: dev-login
      type: string
]

[Here the values of password and user are encoded from "base64"]
[Can fetch the exact value from decoding it, using the terminal]
[ie: echo "cGFzc3dyZA==" | base64 -d ]
[Once, created the secrets can list secrets from below command]
[kubectl get secrets]

# Injecting secrets to the pods 
[
    apiVersion: v1
    kind: Pod
    metadata:
      creationTimestamp: null
      labels:
        run: dev-nginx-pod
        name: dev-nginx-pod
    spec:
      containers:
      - image: nginx
        name: dev-nginx-pod
        resources: {}
        envFrom:
          - secretRef:
              name: dev-login
      dnsPolicy: ClusterFirst
      restartPolicy: Always
    status: {}
]

[Once created the pod, and login to it can fetch the provided secrets easily]
[ie: kubectl exec -it dev-nginx-pod /bin/bash
     echo $user
     echo $password
]
[It will show the decoded values]
