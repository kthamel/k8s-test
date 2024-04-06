# Init containers
[After execution of specific task "Init Containers" are]
[Inside the pod definition files, normal containers are defines under the spec: as "- containers:".]
[But init containers are defiles as "initContainers:"]
[This definition file is an example for it]
[
spec:
  containers:
  - image: nginx:latest
    name: application-container
    resources: {}
  initContainers:
  - image: busybox:latest
    name: init-container
    command: ["sh", "-c", "sleep 120"]
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
]

[First, the initContainer creates and execute the associated command and then create the container. And, initContainer will be terminated automatically]
[if run the "kubectl get pods" command it will shows only the container count of the pod, without initContainers]
