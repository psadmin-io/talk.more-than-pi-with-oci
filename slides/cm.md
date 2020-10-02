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

* My opinion, as of CM 11
* Why bad? TODO
* DB limitations? TODO
* Question even Dev\Test

---

# Considerations

* List a few things here that are concerns with CM
* Maybe good too?

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

* Can't use it actually! TODO
* Control domain attributes and config in templates\env overrides.
* CM will generate needed yaml from that.

---
class: middle, center, gray

# Demo

???

Show CM STUFF

* TODO