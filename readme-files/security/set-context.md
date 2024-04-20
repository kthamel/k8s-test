# Fetch the current using kubernetes context file
[kubectl config current-context]
[From below command, can set new context]
[kubectl config current-context --kubeconfig new-config-file]

# Use new context file
[kubectl config --kubeconfig=/root/new-kube-config use-context new-context ]
[After switching to the new context, ]