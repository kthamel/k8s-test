# Docker image security
[Simply, images are pull from Docker Hub] || <<-- It's https://hub.docker.com/
[
    apiVersion: v1
    kind: Pod
    metadata:
    creationTimestamp: null
    labels:
        run: pod-ubuntu
    name: pod-ubuntu
    spec:
    containers:
    - command:
        - sleep
        - "300"
        image: ubuntu:latest
        name: pod-ubuntu
        resources: {}
]

[According to the above, pod definetion YAML file it's using the docker image called "ubuntu:latest"]
[That's exactly means like below]
[
    library/ubuntu:latest || <<-- If we haven't speciffy the repository name, by default it will choose "docker hub library"
]

[This library name is could be company_name or user_id]
[If the images from docker hub, can define the immage id as follows]
[image: docker.io/library/ubuntu:latest]

[If the images are pulled from "Private image registry" there we have to specify the "credentials" to login to the "docker hub private image repository"]
[Can do this using the "ImagePullSecrets" associating to the Pod definition files]

[
    apiVersion: v1
    kind: Pod
    metadata:
    name: private-reg
    spec:
    containers:
    - name: private-reg-container
        image: docker.io/kthamel/ubuntu:latest || <<-- From private image registry
    imagePullSecrets:
    - name: regcred
]

[This pull secret should be contain the below]
[
    --docker-server= docker.io
    --docker-username= kthamel
    --docker-password= password
    --docker-email=docker_email@gmail.com
]

[Using the below command, can create the image pull secret]
[kubectl create secret docker-registry regcred --docker-server=docker.io --docker-username=kthamel --docker-password=password --docker-email=docker_email@gmail.com]

[From below command can fetch the created secret]
[kubectl get secret]

[Then define it inside the pod definition file]
[
    spec:
    containers:
    - command:
        - sleep
        - "300"
        image: docker.io/kthamel/ubuntu-sleep
        name: pod-ubuntu
        resources: {}
    imagePullSecrets:
        - name: regcred
]