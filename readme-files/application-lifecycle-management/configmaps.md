# Configuration data and Pod definition files
[With lots of configuration data, managing kubernetes is difficult]
[Here using ConfigMaps as a solution for this difficulty]
[When the pods are created, ConfigMaps are injected to the pod as environment variables]
[It will be done by below 2 steps]

[
    Creating ConfigMap
    Injecting ConfigMap
]

[Can create the ConfigMap using Imperative way or Declarative way]
[ie: kubectl create configmap ]
[ie: kubectl create -f configmap-definition-file.yaml]

[There are 3 different ways to do it from Imperative way]
[
    --from-env-file  (Specify the path to a file to read lines of key=val pairs to create a configmap.)
    --from-file      (Key file can be specified using its file path, in which case file basename will be used as configmap key, or optionally with a key and file path)
    --from-literal   (Specify a key and literal value to insert in configmap (i.e. mykey=somevalue))
]

[kubectl create configmap config-dev --from-literal=PROJECT_NAME=dev] || <-- Created ConfigMap using "--from-literal" way.
[kubectl get configmaps config-dev] 
[kubectl describe configmaps config-dev] || <-- Read the content of the created ConfigMap

[If required, can create the definition files of ConfigMap using the imperative way and make tha changes accordingly]
[kubectl create configmap config-dev --from-literal=PROJECT_NAME=devops --from-literal=ENV_NAME=dev --dry-run=client -o yaml  > declarative-way-configmap.yaml]
[That definition file containg below content, no spec: section inside the definition file]

[
    apiVersion: v1
    data:
    kind: ConfigMap
    metadata:
]

# Access ConfigMap data from pods
[When creating the Pod definition files, have to declare configmaps as below]
[
    spec:
    containers:
    - image: nginx
      name: dev-nginx-pod
      resources: {}
      envFrom:
        - configMapRef:
            name: config-devops
]

