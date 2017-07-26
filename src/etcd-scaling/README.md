**Roles for etcd scaling and management.**

**scale.yml** - scale etcd cluster basing on new_etcd hosts in OpenShift inventory file


```[OSEv3:children]

[...]

new_etcd
[new_etcd]

etcd-4 openshift_ip=100.64.80.15 openshift_hostname=etcd-4.openshift.com containerized=True

etcd-5 openshift_ip=100.64.80.16 openshift_hostname=etcd-5.openshift.com containerized=True
```
```
$ ansible-playbook scale.yml
```

This script assumes that environment has already a functional etcd cluster with at least 3 members.

