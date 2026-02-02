#  Ansible Azure  Infrastructure  Automation

This  repository  showcases  production-grade infrastructure  automation  using  Ansible, with  a  focus  on Azure,  security,  and  repeatable application  deployment.  It  is structured  to  demonstrate  engineering maturity:  clear  environments,  reusable roles,  testing  with  Molecule, and  CI  via  GitHub Actions.

##  Key capabilities

-  Provision Azure  virtual  machines  and networking  using  Ansible  collections.
-  Configure  Linux  hosts with  a  `common`  baseline (packages,  users,  MOTD,  time sync).
-  Apply  opinionated `security_hardening`  (SSH,  firewall,  basic CIS-style  tweaks).
-  Deploy a  `webserver`  role  (NGINX) with  templated  content  and environment-specific  configuration.
-  Support multiple  environments  (`dev`,  `prod`) via  inventories  and  group vars.
-  Enforce  quality with  `ansible-lint`  and  Molecule tests  in  CI.

##  Tech  stack

-  Ansible
-  Azure Ansible  Collection  (`azure.azcollection`)
- Molecule  +  Ansible  for role  testing
-  GitHub Actions  for  CI

##  Getting  started

###  1.  Install  dependencies

```bash
pip  install ansible  ansible-lint  molecule  molecule-plugins[docker]
ansible-galaxy  collection  install  -r requirements.yml
