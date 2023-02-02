# DISCONTINUATION OF PROJECT

This project will no longer be maintained by Intel.

Intel has ceased development and contributions including, but not limited to, maintenance, bug fixes, new releases, or updates, to this project.

Intel no longer accepts patches to this project.

If you have an ongoing need to use this project, are interested in independently developing it, or would like to maintain patches for the open source software community, please create your own fork of this project. 

# Deploying Red Hat OpenShift® Container Platform 3.6 with Container-Native Storage

## Instructions
Please, refer to [Reference Architecture document](https://builders.intel.com/docs/cloudbuilders/deploying-red-hat-openshift-container-platform-3-6-with-container-native-storage.pdf)
 for actual instructions.

### Clone the repository
`git clone git@github.com:intel/openshift-container-architecture.git`

### Creating inventory
Inventory file has to be filled manually.
Refer to *hosts.example* for possible variables.

`cp hosts.example /etc/ansible/hosts;
vim /etc/ansible/hosts`

### Switch Configuration (optional)
Update inventory group *[arista]* and run:

`ansible-playbook src/eos-configuration/configure_eos.yaml`

### Provisioning system setup

`ansible-playbook ipxe-deployer/ipxe.yml`

`env IPMI_PASSWORD=password /tftp/reboot.sh -b pxe -r -f /tftp/ipmi.list.txt`

### Preparing the nodes for OpenShift Container Platform

`ansible-playbook src/prerequisites/nodes_setup.yaml -k`

### Setting up multimaster HA
switch user to *openshift*:

`su - openshift`

run:

`ansible-playbook src/keepalived-multimaster/keepalived.yaml`

### Deploying OpenShift cluster
As user *openshift* run:

`ansible-playbook /usr/share/ansible/openshift-ansible/playbooks/byo/config.yml`
