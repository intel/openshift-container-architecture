# Installation

1. requires forked [Lenovo-cnos repo](https://github.com/lenovo/ansible-cnos.git). Included as a submodule.    
```$ git submodule init```    
```$ git submodule update```
2. make sure, that you don't have ssh-agent used in this session, or login will fail. 
```$ unset SSH_AUTH_SOCK```
3. Install `python-paramiko` in version *2.1.1* or newer.
4. Execute with appriopriate python path.    
```$ env  PYTHONPATH=`pwd`/ansible-cnos/library/ ansible-playbook configure-networking.yaml```
