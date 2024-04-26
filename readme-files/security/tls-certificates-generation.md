# Client side certificates

# Generate certificates using OPENSSL
[From executing the below command, can generate the "ca.key" file]
[openssl genrsa -out ca.key 2048]

[Then generate the "ca.csr" file using the above "ca.key" file] || <<-- CSR: Certificate Signing Request
[openssl req -new -key ca.key -subj "/CN=KUBERNETES-CA" -out ca.csr]

[Then signing the generated certificate using the "x509" and generate the self signed certificate]
[openssl x509 -req -in ca.csr -signkey ca.key -out ca.crt]

# Generate certificates for Admin user
[Can using the same way to generate the certificates to the Admin user as well]
[
    openssl genrsa -out ca-admin.key 2048
    openssl req -new -key ca-admin.key -subj "/CN=KUBERNETES-ADMIN/O=system:masters" -out ca-admin.csr || <<-- With adding the "/O=system:masters" relevent group can identify as admin user.
    openssl x509 -req -in ca-admin.csr -signkey ca-admin.key -out ca-admin.crt
]

# Server side certificates
[Can follow the above method to generate the certificates for ETCD]
[
    openssl genrsa -out ca-etcd.key 2048
    openssl req -new -key ca-etcd.key -subj "/CN=KUBERNETES-ETCD/O=system:masters" -out ca-etcd.csr 
    openssl x509 -req -in ca-etcd.csr -signkey ca-etcd.key -out ca-etcd.crt
]
