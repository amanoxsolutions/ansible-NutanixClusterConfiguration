### Stage and Configuration of a Nutanix Cluster with Ansible

This git repo containts the ansible script to stage and configure a cluster with Ansible. The target of this is, to run the code once and to automatize the manuel steps.

## Prerequisites

The developement and testing was done within the Ubuntu WSL 20.04.6 LTS on the local notebook. I used this guide to install the environnement correctly: https://www.thomaspreischl.de/ansible-wsl-windows/. Test if the Ubuntu WSL can ping the Nutanix Cluster or something in the environnement in the IP Range. If you are working first time with ansible, go through this guide to get in touch a bit with ansible: https://www.nutanix.dev/2022/08/05/getting-started-with-the-nutanix-ansible-module/. The following modules need to be installed on the host which the ansible script is running from:
 - gradvies.nutanix
 - nutanix.ncp

## Staging

To stage the cluster with, you nee to fill up the json file in group_vars/dev/vars-template.json with the correct data. Then you will be able to start the YAML file tasks/image_nodes_manual.yml with the following command:

`ansible-playbook image_nodes_manual.yml`

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

To add the values of the customer, you have to ==modify only the JSON file templates/config.json== with the values from the Config Sheet.

## Helpful sources
- official Github Repo from Nutanix Ansible: https://github.com/nutanix/nutanix.ansible/tree/main
- First try with Ansible on Nutanix: https://www.nutanix.dev/2022/08/05/getting-started-with-the-nutanix-ansible-module/
- Gitrepo from AD-Code with some automated Ansible Scripts: https://github.com/AD-Code/Automation/tree/master/ansible/nutanix_cluster_baseline