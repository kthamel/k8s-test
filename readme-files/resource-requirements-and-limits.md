# Resource requirements and limits
[When the maximum amount of pods were scheduled inside the nodes and no more capacity to create new pod, it will throw below error]
[Insufficent CPU/Memory]
[Required minimum CPU and Memory called: Resource request]

spec:
  containers:
  - image: nginx
    name: nginx-pod
    resources:
      requests:
        memory: "200Mi"
        cpu: 10

[kubectl run nginx-pod --image=nginx --dry-run=client -o yaml > resource-requirements-and-limits.yaml] || When the definetion file generated like this. 
[There is a "resources: {}" will generate automatically]
[1 count of CPU is equls to 1 vCPU in Aws]

[Also, able to define the limits]

spec:
  containers:
  - image: nginx
    name: nginx-pod
    resources:
      requests:
        memory: "200Mi"
        cpu: 1
      limits:
        memory: "300Mi"
        cpu: 2

[If the pod trying to exceed the CPU limit, it will throttle, and not going to exceed  the limitation of CPU]
[If the pod trying to exceed the memory limit, pod will be terminated with the OOM kill. Out of Memory error]

[By default pods doesn't have the CPU or Memory limitation. So, pods can sonsume the CPU and Memory as much as they can]
[When creating the pods, best approach is "Defining the requests and not defining the limits" Other 3 request and limit combinations are not much suitable]
