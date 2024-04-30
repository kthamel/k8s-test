# Volumes
[In kubernetes pods using the "volumes" to store data as docker containers]
[If the pod getting terminated, data will be persist into the volume]
[Simply can use the directories inside the cluster as volume]
[Other than that, can use the different type of volues]
[ie: persistent volumes, EBS volumes, EFS volumes, iSCSI]

[
spec:
  containers:
  - command:
    - sleep
    - "300"
    image: ubuntu:latest
    name: pod-volume
    resources: {}
    volumeMounts:
    - mountPath: /kdata || <<-- Pod will be mounted to this path
      name: pod-volume  || <<-- Name of the volume, as below
  volumes:
  - name: pod-volume    || <<-- Given name to the volume
    hostPath:
      path: /kubernetes || <<-- Host instance, directory path
      type: Directory
]

[When the pod is deleted, data will be remaining inside the "/kubernetes" directory inside the "host machine"]
[This option is suitable if is a "single node" kubernetes cluster]
[Having multiple nodes, its not a good option]
[Solution for it was, NFS, CEPH, GlusterGS, AWS, Azure, GCP]
[If using the AWS EBS volume, have to mention the below details under the volume]
