## Integrated Active Directory Enviornment in VirtualBox 
---
### Introduction 
---
For this project, Oracle VirtualBox was utilized to create an integrated enviornment that consisted of a Windows Server 2019 Virtual Machine (VM) serving as the Domain Controller (DC) with Active Directory (AD) service. A custom PowerShell script was deployed to populate approximately 1,000 users. Windows 10 Pro VM was integrated into AD to create a centralized management system for user accounts, computers, and other network resources. 

<img width="1066" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/c5aa082c-1bc8-4199-9c21-b9c73401ff64">

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

#### Now that we have our new folder, we will create a new user 

#### Right click _ADMIN > New > User

<img width="425" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/ff39a745-f8cf-4756-b883-8143400b6a6d">

#### We have created our first user and now we will make it a domain admin 

#### Right click the user > Properties > Member of > Add > type Domain Admin > Apply > Sign out

---

## Installing RAS (Remote Access Server) and NAT (Network Address Translation) on our domain controller 

---

### When we create our Windows 10 client it's going to allow this client to be on a private virtual network, but still be able to access the internet through the domain controller. 

#### Go back to the domain controller and click "Add roles and features" > next > remote access > routing > next > Install

#### Go to tools > routing and remote access > DC (local) and click "Configure and enable..."

<img width="547" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/0712e468-7a16-458e-a2dc-e58795eb5d16">

#### Once you get to configuration click "NAT" it will give us 2 options and click on the one we named "internet" and it should now be configured

<img width="547" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/a082b4b8-38f3-4100-b310-33858bb23357">


---

## Setting up a DHCP server on our domain controller 

---

### DHCP allows our windows 10 clients to get an IP address automatically which will let them get on the internet and browse the internet although they're on this private internal network. 
---

#### Go to the domain controller and click on "add roles," go to the server roles tab and click "DHCP Server" > "add features" > next > Install

#### Go to tools > DHCP > right click IPv4 > new scope > next 

<img width="1066" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/df28b531-697a-44f5-abc4-25d5866d3387">

#### For the name we will put the IP range (172.16.0.100-200)
---

#### For IP address range insert this 

<img width="1066" alt="image" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/84d4a947-5d9d-4bb3-9fd8-7f1ff4fecbcb">

---





















