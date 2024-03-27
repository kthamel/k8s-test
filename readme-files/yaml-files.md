# Top level properties of kubernetes yaml file#
# apiVersion
[Version of the kubernetes API going to use for create the object]
[For pod its - v1]
[For service its - v1]
[For replicaSet its - apps/v1]
[For deployment its - apps/v1]

# kind
[Type of object that trying to create]
[Pod]
[Service]
[Deployment]
[ReplicaSet]

# metadata
[Data ablout the object, like names and labels]
[name - string value]
[lables - dictionary]

# spec
[Specification of the objects, alos its dictionary]
 