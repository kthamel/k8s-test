# Persistent Volume Claims
[Using this, can make available the volume to the cluster]
[Administrator creates the PVs and developper creates the PVC]
[If the PVC is matching with the PV, can bind it]
[But have to fullfile the requirement]
[
    Sufficent capacity
    Access modes
    Volume modes
    Storage class
]

[If the are multiple matchings, have to use the labels and selectors]
[Because there is a one to one relationship between PV and PVC]
[Simple PVC as below]
[
    apiVersion: v1
    kind: PersistentVolumeClaim
    metadata:
    name: pvc-dev
    spec:
    accessModes:
        - ReadWriteMany
    volumeMode: Filesystem
    resources:
        requests:
        storage: 50Mi
]

[Once the PVC was created, can fetch it using the below command]
[kubectl get pvc]
[There have to check the status]
[Bound or Pending]
[
    Bound:      Specification of the PVC is matching with the PV
    Pending:    Not enough capacity is available on PV
]

[There is a retain policy for PV]
[
    Retain:     PV will not be deleted, after executing the "kubectl delete pvc pvc-01" command, Until administrator delete it.
    Delete:     Delete the PV after executing the "kubectl delete pvc pvc-01" command.
    Recycle:    Recycle option will clean the volume and will be available to the other claims.
]

