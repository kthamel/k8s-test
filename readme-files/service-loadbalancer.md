# LoadBalancer service
[When using the NodePort service, we can access the serices externaly]
[But, have to using the IP address and port is not comfortable]
[For an example http://172.16.49.2:30008 this is not good, but it's working]
[This is for the one hosted service, If lots of services are hosted, ip:port combination is not good solution]

# Nginx proxy, HA proxy 
[From hosting the separate proxy instance and then forward the traffic to the relevant IP:NodePort]
[For an example, http://k8s-dev.pt --> http://172.16.49.2:30008]
[For an example, http://k8s-test.pt --> http://172.16.49.2:30009]

# On cloud platforms
[In AWS can use ALB or NLB to route the traffic to the specific paths]
[Same thing can do on any Public cloud platform as well]
[These LoadBalancers are also know as Native LoadBalancers]
[To use this, have to create the service in Kubernetes as "LoadBalancer" service type]
