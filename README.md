# Stage and Configuration of a Nutanix Cluster with Ansible

This Git repository contains the Ansible script to stage and configure a Nutanix cluster. The goal is to run the code once and automate the manual steps.

## Prerequisites

Development and testing were done within Ubuntu WSL 20.04.6 LTS on a local notebook. Followed this guide to install the environment correctly: [Installing Ansible on Ubuntu WSL](https://www.thomaspreischl.de/ansible-wsl-windows/). Test if the Ubuntu WSL can ping the Nutanix Cluster or any element in the IP Range. If you are working with Ansible for the first time, review this guide to get familiar with Ansible: [Getting Started with the Nutanix Ansible Module](https://www.nutanix.dev/2022/08/05/getting-started-with-the-nutanix-ansible-module/). The following modules need to be installed on the host where the Ansible script is running from:
- `gradvies.nutanix`
- `nutanix.ncp`

## Staging
the following steps are automated in ansible:
- add nodes
- define IP range of Host, CVM and IPMI
- define IP for Host, CVM and IPMI
- cluster formation
  
To stage the cluster, modify only the JSON file in `group_vars/dev/vars-staging.json` with the correct values. To run the automated cluster staging, you need to enter following command:

```bash
ansible-playbook image_nodes_manual.yml
```

## Cluster configuration

the following steps are automated in ansible:
- add cluster IP
- add data service IP
- add DNS
- add NTP
- delete default storage container
- add storage container with the name ctr01
- update storage pool name to sp01
- add VLANs
- add SMTP
- add alert configuration 
- configure HA

To add customer values, modify only the JSON file `group_vars/dev/config.json` with the values from the Config Sheet. To run the the automated cluster configuration, you need to enter the following command in the folder tasks:
 
```bash
ansible-playbook cluster-config.yml

```
## IPMI Configuration
the following steps are automated in ansible:
- change IPMI IP address
  
To modify the IPMI configuration, modify only the JSON file in  `group_vars/dev/vars-staging.json` with the values from the config sheet. To run the automated IPMI configuration, you need to enter the following command in the folder tasks:

```bash
ansible-playbook ipmi-config.yml
```

## Helpful sources
- official Github Repo from Nutanix Ansible: https://github.com/nutanix/nutanix.ansible/tree/main
- First try with Ansible on Nutanix: https://www.nutanix.dev/2022/08/05/getting-started-with-the-nutanix-ansible-module/
- Gitrepo from AD-Code with some automated Ansible Scripts: https://github.com/AD-Code/Automation/tree/master/ansible/nutanix_cluster_baseline
