# API Groups 
[From calling the version API of kubernetes master node can fetch information about it]
[curl https://cluster.k8s.local:6443/version]

[Also, there are different APIs for different purposes]
[
    /metrics    : Monitor the health
    /healthz    : Monitor the health
    /api        : Core functionalities
    /apis       : Named groups, new features
    /logs       : Log management
    /version    : Check version
]

[Can autheticate to the APIs by passing the certificates]

# kubectl proxy
[From execuing the below command can start proxy service on locally and provide the APIs]
[kubectl proxy &]

[Then, from the curl the localhost with port 8001, can list the API information]
[curl http://127.0.0.1:8001 -k]
[It will use the current context configurations to authenticate with cluster]
