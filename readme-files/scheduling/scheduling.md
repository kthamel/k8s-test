# Manual scheduling pods
[Can use "nodeName" attribute to schedule the pod in specific node.]

[
    spec:
      nodeName: manual-sch-node
      containers:
      - name: nginx-test
        image: nginx
]

[If the "nodeName" is wrong, pod will be move to the "Pending" state.]
[nodeName can be set only at the creating time of the pod.]
