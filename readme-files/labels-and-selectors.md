# Labels and Selectors
[Using it for resources grouping together]
[Label is a property attached to each item]
[Selectors are the filters of the items]
[ie: Add env-java label to java based pods, when filtering the java based pods use the "env-java" filter]
[Deploying the pods, under the metadata section can define the required labels]
[ie:
metadata:
    name: java-based-pod
    labels:
        env: env-java
        platform: linux
] || <-- This the label for above example.

[kubectl get pods --selector "env=env-java"] || <-- From this command we can filter the required pods using the labels.

[Also, we can add labels to the containers, services, replicaSets as well]

# Annotations
[Additionally we can add annotations, for integration purposes, under the metadata.]