# 🖥️ Integrated Active Directory Environment in VirtualBox

## 🔎 Introduction

In this project, Oracle VirtualBox was used to create an integrated environment consisting of:

- A **Windows Server 2019** VM acting as a **Domain Controller** with Active Directory (AD) services.
- A **Windows 10 Pro** VM joined to the domain.
- A custom **PowerShell script** was deployed to generate ~1,000 users in AD.

This lab demonstrates centralized management of user accounts, computers, and network resources.

<img width="1066" alt="AD Overview" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/c5aa082c-1bc8-4199-9c21-b9c73401ff64">

---

## 🔧 Prerequisites

- [Download Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads) – where we’ll run the VMs  
- [Download Windows 10 ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)  
- [Download Windows Server 2019 ISO](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019)  

---

## ⚙️ Windows Server 2019 Setup

### Configure Network Adapters (NAT + Internal)

Two adapters are used:
- NAT for internet access  
- Internal for communication with client VM  

<img width="728" alt="NICs" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/0634eed9-30af-4c83-8231-0965ddc250c4">

### Assign Static IP

Go to:
`Network Connections > Properties > IPv4 > Use the following IP address`

<img width="462" alt="IP Setup" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/3d411bd4-0ee1-424a-a28a-27e38011d429">

### Rename the Server

Go to:
`Start > System > Rename this PC` and reboot

<img width="728" alt="Rename PC" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/9266a995-6e73-454e-a8af-eff0e11e1793">

---

## 🏢 Install Active Directory Domain Services (ADDS)

1. Add the ADDS role from Server Manager  
2. Click yellow triangle → `Promote this server to a domain controller`  
3. Create new forest (e.g., `mydomain.com`)  

<img width="809" alt="Install AD" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/1197af47-92dc-40ea-98d7-ca63a42769ac">
<img width="809" alt="Promote Server" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/fd085d38-112d-4c21-9997-1c6746b504c9">

---

## 👩‍💼 Create Domain Admin Account

1. Go to `Start > Administrative Tools > Active Directory Users and Computers`  
2. Create Organizational Unit: `_ADMIN`  
3. Inside `_ADMIN`, create new user  
4. Add user to **Domain Admins** group

<img width="809" alt="Create OU" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/b3502b3b-63df-4a47-9854-39cdf19a3755">
<img width="425" alt="Create User" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/ff39a745-f8cf-4756-b883-8143400b6a6d">

---

## 🌐 Configure RAS (Remote Access Server) + NAT

To allow internet access for internal clients:

1. Add Remote Access + Routing roles  
2. Open `Routing and Remote Access` > Configure > Choose `NAT`  
3. Select external NIC (named “Internet”)

<img width="547" alt="RAS NAT" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/0712e468-7a16-458e-a2dc-e58795eb5d16">
<img width="547" alt="NAT Setup" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/a082b4b8-38f3-4100-b310-33858bb23357">

---

## 📡 Setup DHCP Server on Domain Controller

1. Add DHCP Server role  
2. Go to `Tools > DHCP`  
3. Right-click IPv4 > New Scope  
4. Scope Name: `172.16.0.100 – 172.16.0.200`

<img width="1066" alt="DHCP 1" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/df28b531-697a-44f5-abc4-25d5866d3387">
<img width="1066" alt="DHCP 2" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/84d4a947-5d9d-4bb3-9fd8-7f1ff4fecbcb">
<img width="1066" alt="DHCP Gateway" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/fcce7b79-80c0-48fe-97bb-61c0dcbc775e">

---

## ⚡ Automate User Creation with PowerShell

1. Open `PowerShell ISE as Administrator`  
2. Run custom script to auto-generate users

<img width="691" alt="ISE" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/5a2a3f3a-bd29-41f5-8378-eedc1a0aff30">
<img width="640" alt="Script Execution" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/a8cf2183-f846-462a-ae1a-5e082c7b47b5">
<img width="640" alt="Users Created" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/fb600808-7e33-42e1-9816-c416ca7961e5">

---

## 🧑‍💻 Set Up Client VM + Join Domain

1. Create **Windows 10** VM  
2. Set **internal network adapter** to match domain controller  
3. Boot and run `ipconfig` to verify DHCP lease  
4. Rename PC > Join domain

<img width="425" alt="Client NIC" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/66674a9e-cf16-4f27-83c9-18d7bfa5f19b">
<img width="520" alt="Ping Test" src="https://github.com/VanessaMancia/Azure-Active-Directory-/assets/112146207/a0aa9a41-11d1-4ee6-8f05-8b5b63dbbc0a">

---

## ✅ Summary

You have successfully created a fully functional Active Directory environment in **VirtualBox** including:

- A Windows Server 2019 Domain Controller  
- DHCP and NAT for internal client routing  
- Bulk user creation using PowerShell  
- Windows 10 client VM joined to the domain

This simulates a real-world small office AD infrastructure — perfect for labs, red/blue team practice, or portfolio building!

---

👩‍💻 **Created by:** Vanessa Mancia  
📅 **Date:** July 2025  
🔗 [LinkedIn](https://www.linkedin.com/in/vanessamancia)
