# USE CASE

This ansible script enables you to automate the staging process of a nutanix cluster

## PREREQUISITES 

The following modules need to be installed on the host which the ansible script is running from:
- gradvies.nutanix
- nutanix.ncp

## How to use 

To run this script type:
ansible-playbook *PATH/TO/script name*.yml

    you can type -v for verbose levels
    it goes up to -vvvvv which is the maximum verbose level

In the vars.json file you will need to adjust the IP's according to your configuration


