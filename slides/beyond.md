class: center, middle, blue

# Beyond Cloud Manager

---

# Cloud Manager's Toolbox

* DPK Repository
* Terraform
* Python

---

# DPK Repository

```
/cm_psft_dpks/dpk
├── linux
│   ├── CS
│   │   └── 18
│   │       ├── CS-920-UPD-018-LNX_1of11.zip
│   │       └── ...
│   ├── FSCM
│   │   ├── 36
│   │   └── 37
│   └── tools
│       ├── 857
│       │   ├── 15
│       │   │   ├── PEOPLETOOLS-LNX-8.57.15_1of4.zip
│       │   │   └── ...
│       │   ├── ...
│       │   └── custom
│       └── 858
│           └── ...
└── windows
    └── ...
```

???

* Uses File Storage Service
* NFS mounts to /cm_dpk_files as read-only
* Uses these DPK when provisioning 
* You can use it too!

---

# Terraform

* OpenSource from HashiCorp
* Enables you to safely and predictably create, change, and improve infrastructure. 
* Codifies APIs into declarative configuration files

???

Uses this to build all the OCI Resources 

---

# Python

* Extensive Cloud Manager python library
* Leverages OCI SDK for Python
* Bootstrapping DPK
* Provisioning and Configuration tasks

???

* We can use python, too
* Leverage OCI SDK
* Maybe leverage the CM library in future?

---

# ioco
## psadmin.io Cloud Operations Utility

A python utility for common tasks related to administering PeopleSoft in the Cloud

[github.com/psadmin-io/ioco](https://github.com/psadmin-io/ioco)

```bash
$ # Examples
$ ioco oci block --make-file-system --mount
$ ioco dpk deploy --dpk-type=IH
```

---
class: middle, center, gray

# Demo

???

* Cloud Console
    * Show CM build status?
    * Show Cloud Shell
* Terraform
    * `terraform apply --var-file=demo.tfvars -auto-approve > /tmp/tf.log &`
    * `ll *.tf`
    * Show `example.tf`
    * Show `demo.tfvars` 
    * Only do this if we need to kill time
        * `cd ps-instance`
        * `ll`
        * `view instance.tf`
    * `ssh opc@123`
    * Show instance in console
    * connect to new instance
    * `tail /var/log/cloud.init`    
    * `tail /u01/app/ioco/logs/ioco.log` 
* DPK Repository
    * `df -Th`
    * `cd /cm_dpk_files`
    * `tree -L 3 dpk/linux`
* Python
    * `cd cloud`
    * `cd /u01/app/ioco`
    * `cat conf.json`
    * `tail -F /u01/app/ioco/logs/psft-dpk-setup.log`
* Cleanup
    * `terraform destroy --var-file=demo.tfvars`
