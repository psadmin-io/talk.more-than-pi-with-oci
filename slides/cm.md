class: center, middle, blue

# Cloud Manager

???

Assuming most have heard of this.

---
class: center, middle, black

![:img Cloud is Easy!, 100%](images/cloudeasy.gif)

???

As of image 11, not always! Depends on use case

---
class: middle, apples

.float[.pad-top[![:img fruit picker](images/fruit.jpg)]]

</br>
* ~~AUTO SCALE/PATCH~~
* ~~ADV HA/DR~~
* ~~SANDBOX, PTF~~
* ~~PROD~~
* ~~STAGE, DR~~
* *DEV, TEST*
* **PUM, DEMO, POC**

???

* As of CM 11, I feel its use is pretty limited
* Question even Dev\Test

---

# Considerations

Good
* Subscribe to DPK Downloads
* Self Service Operations
* Automated Upgrades/Patching
* Good "Management" Node

"Not Great"

* Creates all resources per Environment
* Inflexible 
* Refreshes actions limited
* Password Management

???

* Good
    * Install Phire on same box? Other things?
* Bad
    * Can't do "shared" resources
        * Leads to sprawl
        * Instances
        * Load Balancer
        * DB systems
        * ExaCS, but each DB needs its own home
* Not as flexible
* Refresh needs needs to fit in "custom scripts"

---
class: center, middle, white

# Environments

---
class: middle

.float-right[![:img Topology, 50%](images/repo.png)]
--
* Auto download DPK
    * PI
    * PRP
    * PeopleTools
--
* Subscribe to what you want
--
* Uses MOS credentials from CM settings

---
class: middle

.float-right[![:img Topology, 50%](images/top.png)]
--
* Infrastructure layout
--
* Nodes = Instances
--
* Attributes 
    * Type
    * OS
    * Shape
    * Disk 

---
class: middle

.float-right[![:img Topology, 50%](images/temp.png)]
--
* Topology
--
* PSFT Attributes
--
* OCI Attributes
--
* Security

---
class: middle

.float-right[![:img Topology, 50%](images/env.png)]
--
* Create from Template
--
* Override as needed

---
class: center, middle, white

# Custom Provisioning

---

# Pre\Post Custom Script

| Type          | Where?            |
|:------------- |:----------------- |
| ------------- | ------------------|
| Python        | Full Tier         |
|               | Middle Tier       |
|               | Database Tier     |
|               | PeopleSoft Client |
|               | ELK Stack         |
|               | DBaaS             |

---

# Pre\Post Custom Script
| Type          | Where?            |
|:------------- |:------------------|
| ------------- | ------------------|
| Shell         | Full Tier         |
|               | Middle Tier       |
|               | Database Tier     |
|               | ELK Stack         |
|               | DBaaS             |
| ------------- | ------------------|
| Batch         | PeopleSoft Client |

---

# CM Variables in Scripts

Custom scripts can use CM provisioning environment variables.

```python
# python
os.environ['PSFT_ACCESS_ID'] = "xyz" 
```
```bash
# bash
$PSFT_ACCESS_ID=xyz 
```
```batch
# batch
%PSFT_ACCESS_ID% = xyz
```

???

There is a long list in PeopleBooks

---
class: middle, center

![:img Topology](images/where.jpg)

???

* Can't use it actually! 
* Used to be there in OCI-C versions, < Image 8
* Now control domain attributes and config in templates\env overrides.
* CM will generate needed yaml from that.
* Still not enough? Leverage pre and post provision scripts some how

---
class: middle, center, gray

# Demo

???

* My Settings
* CM Settings
* Repository
* Topology
    * Show delivered PUM
    * Create new one (DB and Mid)
* Template
    * Add New
        * IH Linux
        * "Reconnect Topology"
        * Edit Custom Attributes
        * Validate Network
        * Security (DEV:PACL_*)
            * Cloud Administrator (PACL_CAD)
            * Cloud PeopleSoft Administrator (PACL_PAD)
            * Self-Service User (PACL_SSC)
* Environment
    * Show FSS option
    * Set Passwords
    * "Create"
    * Show previous ENV build