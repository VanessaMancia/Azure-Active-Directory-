## Integrated Active Directory Enviornment in VirtualBox 
---
### Introduction 
---
For this project, Oracle VirtualBox was utilized to create an integrated enviornment that consisted of a Windows Server 2019 Virtual Machine (VM) serving as the Domain Controller (DC) with Active Directory (AD) service. A custom PowerShell script was deployed to populate approximately 1,000 fake users. Windows 10 Pro VM was integrated into AD to create a centralized management system for user accounts, computers, and other network resources. 
---

### Download [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads)
#### This is where we will run our VMs 

---

### Download [Windows 10](https://www.microsoft.com/en-us/software-download/windows10ISO) and [erver 2019](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)

#### This is what we will use to install the 2 operating systems on two seperate virtual machines
---

## Windows Server 2019 Setup
---

#### Two network adapters were used to seperate traffic between external (NAT) and internal (VirtualBox Network)


<img width="702" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/86acdaa0-41d3-4aeb-8ca9-b5007d97d276">

---

#### Now that we are in our Server 2019 we're going to change some settings

<img width="696" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/5a53fc02-2c76-4ff8-a0d3-49ae23cac166">














