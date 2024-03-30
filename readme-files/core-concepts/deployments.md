# Deployemts are required to run application in production level
[Just pods are not siutable for prod, its suits for dev]

# Seamless upgrade, as performing rolling update. 
[Deployments can change the version rolling-update strategy, other than the all at once]
[With this strategy no more outage]
[With all at once method, there is service outage]
[In case of upgrade failure, able to roll-back into the previously working version smoothly]

# Each services are deployed into containers inside the pods
[Sets of pods will be managed by replicaset or replication-controllers]

# Required the deployment definetion file containing the below;
apiVersion: apps/v1
kind: Deployment
metadata:
spec:

# Create the deployment using the definition file or single command if possible
[kubectl create deployment nginx-test --image=nginx --replicas=2]
[kubectl create deployment nginx-test --image=nginx --replicas=2 --namespace=develop --dry-run=client -o yaml > deployment.yaml] || <-- Create the defenition file.
[kubectl create -f test-deployment.yaml]
[kubectl edit deployment test-deployment] || <-- Can make the changes to the deployment without the definetion file.
