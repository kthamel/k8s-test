# Multiple schedulers
[In kubernetes, can create own scheduler programs and run along with kube-scheduler]
[When creating specific pods, have to define use the newly created own scheduler, other than the default scheduler]

[custom-scheduler.yaml file configuration as below]
[
    apiVersion: kubescheduler.config.k8s.io/v1
    kind: KubeSchedulerConfiguration
    profile:
    - schedulerName: custom-scheduler
]

[Also, able to create the scheduler as a pod]

[If there are multiple master nodes, can enable the leaderElect as true]

[

apiVersion: kubescheduler.config.k8s.io/v1
kind: KubeSchedulerConfiguration
profile:
- schedulerName: custom-scheduler
leaderElection:
  leaderElect: true
  resourceNamespace: kube-system
  resourceName: lock-object-custom-scheduler

]

[When creating the custom scheduler as pod have to put the scheduler.conf into the correct path]
