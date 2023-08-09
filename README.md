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

<img width="728" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/0634eed9-30af-4c83-8231-0965ddc250c4">

---

#### Let's rename the PC 

#### Right click on the menu and click "system" and press "rename this PC" and restart the VM 

<img width="728" alt="Screenshot 2023-08-07 at 11 30 36 PM" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/9266a995-6e73-454e-a8af-eff0e11e1793">

---

## Installing Active Directory Domain Services (ADDS) and creating a domain

---

#### We're installing the software for Active Directory Domain Services

<img width="809" alt="Screenshot 2023-08-07 at 11 47 39 PM" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/1197af47-92dc-40ea-98d7-ca63a42769ac">

#### Now we need to create the domain 

#### Click on the yellow triangle and click "Promote this server to a domain controller" 

<img width="809" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/fd085d38-112d-4c21-9997-1c6746b504c9">

---

#### Let's create our own dedicated domain admin account 
#### Click on Start > Admin Tools > Active Directory users and computers 
#### Right click on mydomain.com > New > Organizational Unit and name it _ADMIN

<img width="809" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/b3502b3b-63df-4a47-9854-39cdf19a3755">






























