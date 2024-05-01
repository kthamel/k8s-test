# Storage classes
[There are two storage provisioning methods]
[
    static provisioning
    dynamic provisioning
]
[When using the "local storage" as a volume, there have to use the "static provisioning"]
[When using the "cloud storage" like EBS, there have to use the "dynamic provisioning"]
[That means, when using it, it will create the required size of PVC on cloud platform and attch to the pod]
[This process called dynamic provisioning]
[To do that, there have to define the storage class matching with cloud platform]
[When using the storage classes, not require to provision the "pv" Because, it will created automatically]
[To do that, have to define the "storageClassName" inside the "PVC" definition file]

[Simple storage class definition file like below]
[
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: ebs-sc
provisioner: ebs.csi.aws.com
volumeBindingMode: WaitForFirstConsumer
parameters:
  csi.storage.k8s.io/fstype: xfs
  type: gp2
  iopsPerGB: "5"
  encrypted: "true"
allowedTopologies:
- matchLabelExpressions:
  - key: topology.ebs.csi.aws.com/zone
    values:
    - us-east-1a
]

[And, there have to create a new PVC matching with the storageClass]
[Under the pod definition file, there have to define with "pvc" to be use]
[When the pod getting created, required volume will be created automatically]
