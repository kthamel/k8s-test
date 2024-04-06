# Save the configurations.
[Simply configurations can export into the YAML files as declaratice approach]
[It's not a propper solution at all]
[If required, only resource configurations can export into the YAML file using the below command]
[kubectl get all -A -o yaml > resource-configurations.yaml]

# Velero
[Using this tool, can take the backups of the cluster using the kubernetes-api]

# Backup ETCD
[All the configuration data about the cluster is containing inside the ETCD database]
[Before executing the backup command, have to identify the "ca.cert" "server.crt" and "server.key" locations.]
[Can find these file locations using the "kubectl get pods --namespace=kube-systemet etcd "]
[Can take the "Snapshots" of this database can restore if necessary]
[Can do it using the CLI]

[
    ETCDCTL_API=3 etcdctl --endpoints=https://[127.0.0.1]:2379 \
    --cacert=/etc/kubernetes/pki/etcd/ca.crt \
    --cert=/etc/kubernetes/pki/etcd/server.crt \
    --key=/etc/kubernetes/pki/etcd/server.key \
    snapshot save /opt/snapshot-pre-boot.db      || <-- Take the snapshot

    ETCDCTL_API=3 etcdctl snapshot status 2024-04-06-snapshot.db    || <-- Check the status of the snapshot
]

# Restore tha backup
[Before restoring the ETCD backup, have to stop the kube-apiserver service]
[Then restore the snapshot using the CLI]

[   
    ETCDCTL_API=3 etcdctl snapshot restore 2024-04-06-snapshot.db --data-dir /var/lib/etcd-backup-2024-04-06
]

[Then edit the etcd.service file and add the below line]
[- --data-dir=/var/lib/etcd-backup-2024-04-06]
[Also, have to update the "volumeMounts" of the same file adding the above path]

[After that, have to restart the daemons and restart the etcd service as well]
[systemctl daemon-reload]
