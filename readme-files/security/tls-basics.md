# Symmetric Encryption
[Use the same key to encrypt and de-crypt the data.]
[That means sender has to share the key to reciver to decrypt the data.]
[Sender ***Encryption key*** --->>> Recipient]
[This method is not much secure]

# Asymmetric Encryption
[There, using public lock and private key. That means encrypting the data using the one file //lock// and decrypting the data using the different file //key//]

# Asymmetric Encryption - SSH
[from the below command, can generate the key-pair]
[
    ssh-keygen -f ssh_key
]

[It will generate below two files]
[
    ssh_key         <<-- Private key
    ssh_key.pub     <<-- Public key
]

[Then copy the public key into the target server/host]
[If read the below file of the server end, can list the authorized keys ***Public key***]
[cat ~/.ssh/authorized_keys]

[Now, user can SSH to the server using the private key]
[ssh -i ssh_key k8s_user@k8s_cluster.local]

[Also, using the below commands can generate the keys. Its using with to secure HTTP communication]
[
    openssl genrsa -out new_key.key 1024
    openssl rsa -in new_key.key -pubout > new_key.pem
]

