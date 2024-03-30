# Selecting nodes to schedule pods
[Some pods required specific nodes to schedules. ie: high memory/cpu nodes]
[These pods required to scheduled on specific nodes]
[Can do this from two methods]

# Node Selectors and Node Affinity
[Using nodeSelector can select which node to be scheduled]
[Defining it under the metadata section of the pod defenition file]

metadata:
  nodeSelector:
    size: Large 

[On above example, size: Large is the label of the node, that pod going to be scheduled]
[That means, before scheduling have to labeling the nodes]
[kubectl label nodes node-01 capacity=Large --dry-run=client ]

[With node affinity we can use advanced expressions. Like "or" "and"]
[Its impossible to do with nodeSelectors]
[Under the spec of the pod, affinity configurations are adding]

metadata: 
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: kubernetes.io/arch
            operator: In
            values:
            - arm64
      preferredDuringSchedulingIgnoredDuringExecution:
      - weight: 1
        preference:
          matchExpressions:
          - key: kubernetes.io/os
            operator: In
            values:
            - linux

