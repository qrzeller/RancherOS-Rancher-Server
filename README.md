# RancherOS-Rancher-Server
Some tips to install rancher OS and server
## Infos
 - run this [script](./runDockerTools.sh) to have a tools in RancherOS instead of changing to a big bash with the command ROS and persistant images.
 - The ros config-cloud is in ´/var/lib/rancher/conf´, we provide an [example](./example/cloud-config.yml). You can boot directly with that in some cloud provider or in proxmox or other vms managment system. 
 - - We recommand you change your docker data system to you external drive. This make backup and migaration easier and provide way to increase disk memory. See section `write_files`
 - - And don't forget to mount the disk
 - - If you do on baremetal you want probably to add ip configuration.
 - - 
```
network:
    interfaces:
      eth0:
        address: 192.168.1.99/24
        gateway: 192.168.1.1
        mtu: 1500
        dhcp: false
      "mac=52:54:00:00:cf:85":
        address: 51.158.29.88/32
        broadcast: 51.158.29.88
        gateway: 195.154.214.129
        mtu: 1500
        dhcp: false
```

## Encountred problems
 - If you need to reinstall the agents etcd. You need to clean a lot of host path. [This file help you.](./scripts/clean.sh)
 - You need to precise the agents local and public ip if you are in a NAT. Some cloud provider are in NATs Azure, Infomaniak, ...
 - For Ingress to work a full public ip is recommanded.
 - If you enable Github authentication you may loose the admin local login.
