# Active-Directory-Infrastructure-Preparation

<h2>Discription </h2>

In this project we will lay the ground work or infrastructure foundation which will allow us to use Active Directory.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022 Azure Edition

<h2>Project Steps</h2>
 
1. Create Resource Group

Create -> Select Resource Group -> enter Name -> select region -> review and Create

3. Create Virtual Network (VNet)

Create -> Put in Resource Group (previously created) -> Enter Vnet Name -> Select Region (same as Resource Group) -> Review and Create

5. Create first Virtual Machine (Vm) Domain Controooller

Create -> Put in Resource Group (previously created) -> Enter (Vm) Name "Domain Controller" -> Select Region (same as before) -> Select Image: Windows Server 2022 "Azure Edition" -> *Note* Size: Standard, 2vcpus, 8 gib memory -> Username/Password -> Check "License" -> Next to Disk -> Next to Networking -> Select VNet (previously created) -> Review and Create -> Create

7. Create Second Virtual Machine (Vm) Client-1

Create -> Put in Resource Group (previously created) -> Enter (Vm) Name "Client-1" -> Select Region (same as before) -> Select Image: Windows 10 Pro Version 22H2 -> *Note* Size: Standard, 2vcpus, 8 gib memory -> Username/Password -> Check "License" -> Next to Disk -> Next to Networking-> Select VNet (previously created) -> Review and Create -> Create

9. Modify Dc-1 Ip settings

Go to Vm in Azure -> Dc-1 -> Networking -> Network settings -> Virtual Nic Card -> "ipconfig" -> Choose Static -> Save
  
11. Login to Dc-1
  
Go to Vm in Azure -> Dc-1 -> Public Ip address -> Remote Desktop -> Enter Username/Password
  
12. Modify Dc-1 Firewall
  
Rt click Start -> Run -> Type "wf.msc" -> Enter -> Windows Defender Firewall Properties -> Public Profile tab -> Firewall State Switch to "Off" -> Private Profile tab -> Firewall State Switch to "Off" -> Domain Profile tab -> Firewall State Switch to "Off" -> Apply -> Ok

13. Modify Client-1 Ip settings (Change to Dc-1 private Ip address)

Go to Vm in Azure -> Dc-1 -> Copy Private Ip address -> Go to Vm in Azure -> Client-1 -> Networking -> Network settings -> Virtual Nic Card -> DNS Server -> Select Custom -> Paste/Enter Dc-1 Privet Ip Address -> Save
  
15. Reset Client-1

Go to Vm in Azure -> Client-1 -> Restart

17. Login to client-1

Go to Vm in Azure -> Client-1 -> Public Ip address -> Remote Desktop -> Enter Username/Password
   
19. Ping Dc-1 from client-1

Client-1 -> Search bar -> Type "Powereshell" -> Run -> Type "ping paste/enter Dc-1 public Ip address" -> Enter
   
If the ping succeds there will be a reply and timeout. If the ping didn't go through them a reply and "Destination host Unreactable" is displayed. This means that the Domain Controller's Windows Firewall is still running.

12. Check client-1 Ip Address Changed

Client-1 -> Powereshell -> Type "ipconfig /all" -> Enter

The data results will disply Dc-1's Private Ip address for Client-1's Private Ip address.

Congratulations on successfully setting up the infrastructure for the cnotinuing labs to deploy and use Active Directory.
  
   
   

   
