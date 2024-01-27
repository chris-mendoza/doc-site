## Configure Network Adapter

### Ubuntu

Show all Network Interfaces:
`ip a`

Identify all network interfaces:
`lshw -class network`

Modify `/etc/netplan`

`sudo netplan apply`

Create Docker Network:

`docker network create -o "com.docker.network.bridge.host_binding_ipv4"="192.168.0.188" --subnet=192.168.0.188/32 --gateway=192.168.0.1 waffles-network`

`minikube start --network=waffles-kube --driver=docker --service-cluster-ip-range='192.168.0.188/24'`
