# Scheduler profiles
[When multiple pod creation requests came to the cluster, all pods are not creates at one, It will create according to the priority classes]
[Until sorting the priority class, requests are in the "scheduling queue"]
[There we have to create the priority classes as below]
[

    apiVersion: scheduling.k8s.io/v1
    kind: PriorityClass
    metadata:
    name: system-workers-critical
    value: 2000001000

]

[Scheduling queue: Queue the pod creation requests]
[Filtering: Priority order will be filtering according to the value]
[Scoring: Choose which node is most suitable to place the new newly creation pod]
[Binding: Bound the pod into the node according to the highest score]

