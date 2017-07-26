**Ansible playbook for DRBD deployment automation**
ansible-playbook drbd.yaml

DRBD installs on nodes added to [nfs] section in ansible inventory file

If Your **VG/private interface** differs from the ones in reference architecture then change proper parameters in:

_defaults/main.yml_ 

_vars/main.yml_
