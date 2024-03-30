# Rolloing updates and Rollbacks
[When the exixting deployment moving to the new version, called rollout]
[From the below command, can get the status of the rollout deployment]
[kubectl rollout status deployment/deployment-nginx] || <-- Can get the rollout status of a deployment
[kubectl rollout history deployment/deployment-nginx] || <-- Can get the rollout history and the revision of a deployment

# Deployment strategy
[
    Recreate - All at once || There will be a downtime for deployment.
    Rolling update - Half of pods will be deployed to the new version at once. Once that half was completed it will do the same for the remaining pods
]
[If the deployment strategy not mentioned, it will processed as "Rolling update" deployment]
[Rolling update - The default deployment strategy]
[Once modified the yaml file of the deployment can do the rolling update using the below command]
[kubectl apply -f deployment-nginx.yaml]
[If the only change of the deployment, is image chage can do it from single command. But changes are not replicated to the originated yaml file]
[ie: kubectl set image deployment/deployment-nginx nginx=nginx:stable-alpine3.17-perl]
[If want to rollback the deployment into the previous version, can do it from below command]
[kubectl rollout undo deployment deployment-nginx]

# Application Commands and Arguments
[Containers are only required, when there is a process to execute.]
[Otherwise container/pod will be exited]
[ie: kubectl run ubuntu-pod --image=ubuntu:latest] || <-- This pod will be exited without running. Because there's no specific job to execute
[ie: kubectl run ubuntu-pod --image=ubuntu:latest --command sleep 300] || If the same command pass with "--command" argument this will execute the command, and then it will be exited.
[In advance, we can define which command to be run when creating the docker image using Dockerfile]

[When creating the Dockerfile, can define the command from below 2 formats]
[
    CMD sleep 300 || <-- Bash format
    CMD ["sleep", "300"] || <-- JSON Array format
]

# Entrypoint of Dockerfile
[Other than defining the CMD in Dockerfile, we can use "ENTRYPOINT"]
[ie: We can create a Dockerfile as below]
[
    FROM: ubuntu:latest
    ENTRYPOINT ["sleep"]
]

[When execute the "kubectl run ubuntu-pod --image=ubuntu-sleep-image" we can pass the sleep time as argivement]
[ie: kubectl run ubuntu-pod --image=ubuntu-sleep-image 300] || <-- Here, "sleep 300" will be execute.
[Entrypoint is the command that execute, when creating the pod, when pass 300 it will execute as "sleep 300"]
[If forget to pass this value as argument, pod creation will be failed]
[To avoid that, can use default value. If pass the argument value, it will replace the default value]
[
    FROM: ubuntu:latest
    ENTRYPOINT: ["sleep"]
    CMD ["60"]
]

# Environment variables
[Inside the pod definition yaml files, environment variables define as an array]
[ie:
    containers:
    -   name: ubuntu-container
        image: ubuntu:latest
        env:
            -   name: APP_NAME
                project: PROJECT
]

[When creating the pods from CLI, can pass the values for the environment variables as follows]
[kubectl run ubuntu-dev --image=ubuntu:latest -e APP_NAME=utest PROJECT=dev]