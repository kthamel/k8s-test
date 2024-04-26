# Secirity Context
[Can set the security context in kubernetes on pod level and container level]
[If the context added to the pod level, it will override the container level security context]

[For an example, there can define the securityContext as below]
[
spec:
  containers:
  - image: docker.io/kthamel/kdev
    name: pod-ubuntu
    securityContext:
      runAsUser: 1000
      capabilities:
        add: ["MAC_ADMIN"]
]
