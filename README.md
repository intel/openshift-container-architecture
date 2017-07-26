# Red Hat OpenShift®  Container Platform Reference Architecture for Lenovo® Rack Servers

## Instructions
*Please, refer to Reference Architecture document for actual instructions*

### Clone the repository
```git clone https://github.com/intel/openshift-container-architecture.git```

#### Optional: if switch provisioning is planned, submodule has to be initiated

```git submodule init```

```git submodule update```

### Creating inventory
Inventory file has to be filled manually.
Refer to *hosts.example* for possible variables. 

```cp hosts.example /etc/ansible/hosts```

```vim /etc/ansible/hosts```


### Preparing the nodes for OpenShift Container Platform

```ansible-playbook src/prerequisites/nodes_setup.yaml -k```

### Setting up multimaster HA
switch user to *openshift*
```su - openshift```

```ansible-playbook src/keepalived-multimaster/keepalived.yaml```

### Deploying DRDB for NFS storage (Docker Images)

```ansible-playbook src/drbd/drbd.yml```

### Deploying OpenShift cluster
```ansible-playbook /usr/share/ansible/openshift-ansible/playbooks/byo/config.yml```

### etcd scaling and other optional features
Description can be find inside the _src_ directory

## Authors:
Łukasz Łuczaj (lukasz.luczaj@intel.com) - GitHub: lluczaj

Łukasz Sztachański (lukasz.sztachanski@intel.com) - GitHub: lsztachanski
