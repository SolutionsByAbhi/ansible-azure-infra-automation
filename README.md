
 #  **Azure  Infrastructure Automation  with  Ansible**   
 ###  *Production‑grade  automation engineered  for  cloud-scale  environments*

 This  repository  demonstrates a  complete,  enterprise-ready  automation framework  built  with  **Ansible**, designed  specifically  for  **Azure infrastructure  provisioning**,  **secure  configuration management**,  and  **repeatable  application deployment**.    
 
The  project  is  intentionally structured  to  reflect  the engineering  standards  expected  at Microsoft:  modular  design,  strong security  posture,  CI-driven  quality gates,  and  clear  separation of  concerns.
 
 ---

 ##  🌐  **Project Overview**
 
 Modern  cloud environments  demand  automation  that is:
 
 -  **Idempotent**   
 -  **Secure by  default**    
-  **Environment-aware**    
-  **Tested  and  validated**   
 -  **Extensible for  scale**
 
 This repository  delivers  exactly  that. It  provisions  Azure  compute and  networking  resources,  applies hardened  baseline  configurations,  and deploys  a  fully  managed NGINX-based  web  tier  — all  through  reusable,  well‑documented Ansible  roles.
 
 The repo  is  built  to showcase:
 
 -  Infrastructure-as-Code discipline    
 - Azure-native  automation  patterns   
 -  DevOps  best practices    
 - CI-driven  validation    
-  Clean,  maintainable  Ansible architecture    
 
---
 
 ##  🚀 **Key  Features**
 
 ### **🔧  Azure  Infrastructure  Provisioning**
-  Automated  creation  of:
    -  Resource Groups    
    -  Virtual  Networks   
    -  Subnets    
    -  Public IPs    
    -  Virtual  Machines   
 -  Uses the  official  `azure.azcollection`  for reliability  and  future  compatibility.

 ###  **🛡️  Security-First Configuration**
 -  SSH  hardening (no  root  login,  no password  auth)    
-  UFW  firewall  configuration   
 -  Baseline OS  hardening  aligned  with common  CIS  patterns   
 
 ###  **📦 Application  Deployment**
 -  NGINX installation  and  configuration   
 -  Environment-specific  templated web  content    
-  Automated  service  management and  reload  handlers   
 
 ###  **📁 Multi-Environment  Support**
 -  Separate inventories  for  `dev`  and `prod`    
 - Scoped  `group_vars`  and  `host_vars`   
 -  Environment-aware templates  and  defaults   
 
 ###  **🧪 Automated  Testing  with  Molecule**
-  Docker-based  Molecule  scenario   
 -  Converge +  verify  steps   
 -  Ensures  roles remain  idempotent  and  functional   
 
 ### **🔍  CI/CD  with  GitHub Actions**
 -  Linting  via `ansible-lint`    
 - Molecule  test  execution   
 -  Fast  feedback for  every  PR  and commit    
 
---
 
 ##  🏗️ **Repository  Structure**
 
 ```text
ansible-azure-infra-automation/
 ├──  playbooks/                 #  Entry-point  playbooks
 ├── roles/                         #  Modular, reusable  roles
 ├──  inventories/              # dev/prod  environment  definitions
 ├── molecule/                    # Automated  role  testing
 ├── .github/workflows/    #  CI pipeline
 ├──  ansible.cfg                # Project-wide  Ansible  config
 └── requirements.yml       #  Collections  and  dependencies
```
 
 Each  directory is  intentionally  structured  to reflect  real-world  automation  patterns used  in  enterprise  cloud environments.
 
 ---
 
##  📘  **How  It Works**
 
 ###  **1. Provision  Azure  Infrastructure**
 
```bash
 ansible-playbook  -i  inventories/dev/hosts.ini playbooks/azure_provision.yml
 ```
 
 This creates  the  full  Azure stack:  VNet,  subnet,  NICs, and  VMs.
 
 ### **2.  Apply  Baseline  + Security  Hardening**
 
 ```bash
ansible-playbook  -i  inventories/dev/hosts.ini  playbooks/site.yml
```
 
 This  ensures every  VM  meets  your baseline  security  and  configuration standards.
 
 ###  **3. Deploy  the  Web  Tier**

 ```bash
 ansible-playbook  -i inventories/dev/hosts.ini  playbooks/web.yml
 ```
 
This  installs  NGINX,  deploys templated  content,  and  configures the  service.
 
 ---

 ##  🧩  **Design Principles**
 
 ###  **✔️ Modularity**
 Roles  are  self-contained and  reusable  across  environments and  projects.
 
 ### **✔️  Idempotency**
 Every  task is  written  to  avoid unnecessary  changes.
 
 ### **✔️  Security**
 Defaults  follow secure  patterns:
 -  No password  SSH    
-  Firewall  enabled   
 -  Minimal  packages installed    
 
###  **✔️  Observability**
 Clear logging,  structured  output,  and CI  validation.
 
 ### **✔️  Scalability**
 Azure  provisioning supports  VM  count  scaling and  naming  conventions.
 
---
 
 ##  🧪 **Testing  &  Quality**
 
###  **Molecule  Testing**
 Every role  is  validated  using Molecule  with  Docker-based  ephemeral instances.
 
 ```bash
 molecule test
 ```
 
 ### **GitHub  Actions  CI**
 The pipeline  enforces:
 -  Syntax validation    
 - Linting    
 - Molecule  tests    

 This  ensures  every commit  maintains  production  readiness.

 ---
 
 ## 🔧  **Prerequisites**
 
 - Python  3.9+    
-  Ansible    
-  Azure  CLI  or Service  Principal  credentials   
 -  SSH  key pair    
 - Docker  (for  Molecule  tests)

 Install  dependencies:
 
```bash
 pip  install  ansible ansible-lint  molecule  molecule-plugins[docker]
 ansible-galaxy collection  install  -r  requirements.yml
```
 
 ---
 
##  🔐  **Azure  Authentication**

 Export  your  Azure service  principal  credentials:
 
```bash
 export  AZURE_SUBSCRIPTION_ID="..."
 export AZURE_CLIENT_ID="..."
 export  AZURE_SECRET="..."
 export AZURE_TENANT="..."
 ```

