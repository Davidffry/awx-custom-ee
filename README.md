# Awx-custom-ee

This repositoy list some links to facilitate the AWX integration, and it is the simplier template to generate an Awx-custom-ee.

***Please note that : This information below are valid to the date of the commit***

Recently, for some project I need this items to this file `requirements.txt`:
```
pyvmomi
pywinrm
netaddr
...
```
the other, `requirements.yml`, represent the "necessary" collection to install :
```
---
collections:
    - ansible.netcommon
    - community.general
    - community.vmware
    - community.windows
```

and finaly : 
```
# file : execution-environment.yml
---
version: 1
dependencies:
  galaxy: requirements.yml
  python: requirements.txt
  # system: bindep.txt

additional_build_steps:
  prepend: |
    RUN pip3 install --upgrade pip setuptools
  append:
    - RUN ls -la /etc
```

```
$ansible-build --build-arg EE_BASE_IMAGE=<Basic Image> --container-runtime docker 
```

The links :

[Ansible Automation Controller User Guide](https://docs.ansible.com/automation-controller/latest/html/userguide/index.html)  
- [Ansible Log Management](https://docs.ansible.com/automation-controller/latest/html/administration/logging.html)  
- [Ansible Awx Best Practices](https://docs.ansible.com/automation-controller/latest/html/userguide/best_practices.html)
- [Ansible Execution Environment](https://docs.ansible.com/automation-controller/latest/html/userguide/execution_environments.html)  
- [Ansible Execution Environment Setup](https://docs.ansible.com/automation-controller/latest/html/userguide/ee_reference.html)  
- --> [Ansible-builder](https://www.ansible.com/blog/introduction-to-ansible-builder)*
- --> [Ansible builder env example](https://www.linkedin.com/pulse/ansible-execution-environments-phil-griffiths/)
- And so on ...