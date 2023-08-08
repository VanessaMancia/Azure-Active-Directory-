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

#### Two network adapters were used to seperate traffic between external (NAT) and internal (VMWare Network)

<img width="702" alt="Screenshot 2023-08-07 at 10 03 38 PM" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/e4bad594-d73f-4ca4-b7d9-600b4cdf270e">
























