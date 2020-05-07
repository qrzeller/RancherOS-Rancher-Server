# RancherOS-Rancher-Server
Some tips to install rancher OS and server
## Infos
 - run this [script](./runDockerTools.sh) to have a tools in RancherOS instead of changing to a big bash with the command ROS and persistant images. Alternatively you can use the well known busybox.
 - The ros config-cloud is in ´/var/lib/rancher/conf´, we provide an [example](./example/cloud-config.yml). You can boot directly with that in some cloud provider or in proxmox or other vms managment system. 
 - - We recommand you change your docker data system to you external drive. This make backup and migaration easier and provide way to increase disk memory. See section `write_files`
 - - And don't forget to mount the disk
 - - If you do on baremetal you want probably to add ip configuration. As it does not mount in same order all the times, you probably more safe with ids.

## Encountred problems
 - If you need to reinstall the agents etcd. You need to clean a lot of host path. [This file help you.](./scripts/clean.sh)
 - You need to precise the agents local and public ip if you are in a NAT. Some cloud provider are in NATs Azure, Infomaniak, etc...
 - For Ingress to work a full public ip is recommanded.
 - If you enable Github authentication you may loose the admin local login.
