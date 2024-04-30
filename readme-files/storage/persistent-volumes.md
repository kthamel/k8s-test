# Persistent volumes - PV
[Persistent volumes having the differetn manifest files of configurations]
[Just volumes not like that, it defining inside the pod definition YAML files]
[Persistent volume is a cluster wide pool of "Storage Volumes"]

# Persistent volume claims - PVC
[This is using for select the specific storage from the pool]

# Access modes
[There are 3 access modes, can use when creating the PV]
[
    ReadWriteOnce
    ReadWriteMany
    ReadOnlyMany
]

[Simple PV definition file as below]
[
    apiVersion: v1
    kind: PersistentVolume
    metadata:
    name: pv-dev
    spec:
    accessModes:
        - ReadWriteMany
    capacity:
        storage: 100Mi
    hostPath:
        path: /kubernetes
]

[Can list the created PVs from below command]
[kubectl get pv]
