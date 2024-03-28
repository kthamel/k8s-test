# Taints and Tolerations
Taints --> on Nodes
Tolerations --> on Pods
[Mainly taints and tolerations are use for which pods can schedule in the nodes.]
[By default pods are spreading equally in the nodes]

# Taints
[If we want to schedule the specific pods to the node, we have to "taint" the node]
[Taint is just like a label]
[ie: Taint the node-01 as database, non of the pods can scheduled in this node. Thats true]
[But database pods can scheduled in other nodes as well.]
[That means no way to swchedule pods on this node]
[command ie: kubectl taint node node-01 app=nginx-test:NoSchedule --dry-run=client]

# Tolerations
[Once the toleration was added to the database pods, it can scheduled on the tainted node (node-01)]
[Now database pods are scheduling on node-01 and other nodes too]

# Types of taints
[NoSchedule: Pods not going to schedule in the node]
[PreferNoSchedule: System will try to avoid scheduling pods on the node]
[NoExecute: New pods will not schedule on the node, and existing pods will be evicted from the node]