# Replica Set and Replication Controller
[Doing the samething, but recommended is replicaSet]
[Having minor differences, main one is "selector"]

# Replication controller
[Can spin up new pod, if existing pod got failed]
[Ensuring specific pods are running in the cluster at all time]
[Can span accross multiple nodes]
[kubectl get replicationcontrollers] <-- Can get the created replicationControllers

# Replica set
[Defining the selector]
[Its expecting the lables same that we used to the pods]
[Using these lables to ensure, always fulfil the required pod count]
[kubectl get replicasets.apps] <-- Can get the created replicaSets

# Update the number of replicas
[kubectl replace -f replicaset.yaml] || <-- Definition file and the replicaset having the equal number of replicas
[kubectl scale --replicas=6 -f replicaset.yaml] || <-- Only the replicaset having the desired number of pods and definition file contains old value
[kubectl scale --replicas=5 replicaset test-replicaset] || <-- Only the replicaset having the desired number of pods and definition file contains old value