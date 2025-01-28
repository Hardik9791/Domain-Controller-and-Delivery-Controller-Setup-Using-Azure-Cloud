# Domain-Controller-and-Delivery-Controller-Setup-Using-Azure-Cloud 

### Overview:
This lab involved setting up a Domain Controller (DC) and a Delivery Controller (DDC) using Windows Server 2022 virtual machines on Azure Cloud. The goal was to configure and test Active Directory Domain Services (ADDS), DNS, and DHCP while ensuring secure communication between the two machines. This project demonstrates my ability to deploy and manage enterprise-level infrastructure in a cloud environment.
 
### Lab Objectives:
1.	Deploy and configure a Domain Controller to manage a custom domain (Dc.com).
2.	Set up a Delivery Controller to join the custom domain and authenticate domain users.
3.	Configure and test key services: Active Directory, DHCP, and DNS.
4.	Validate successful communication between the DC and DDC virtual machines.
 
### Lab Screenshots 👉🏻 : [Link](https://github.com/Hardik9791/Domain-Controller-and-Delivery-Controller-Setup-Using-Azure-Cloud/blob/main/Screenshots.pdf)

### Step 1: Setting Up the Domain Controller (DC)
**1.	Provisioning the VM:**
-	Deployed a Windows Server 2022 Datacenter VM in Azure.
- Assigned the VM a static private IP address (10.0.0.4).
- Placed the VM in a new virtual network (DC-vnet) to facilitate communication with other machines.
- Accessed the VM using RDP by entering username and password created during deployment of VM.
  
**2.	Installing Roles:**
- Configured the server with Active Directory Domain Services (ADDS), DNS Server, and DHCP Server roles.
-	Promoted the server to a Domain Controller and created the domain Dc.com.
  
**3.	Configuring DHCP:**
-	Set up a DHCP scope to assign IPs in the range 10.0.0.20 - 10.0.0.30.
-	Activated the DHCP configuration and verified IP address assignment.


### Step 2: Setting Up the Delivery Controller (DDC)

**1.	Provisioning the VM:**
-	Deployed a second Windows Server 2022 Datacenter VM in Azure.
-	Assigned the VM a static private IP address (10.0.0.5).
-	Placed it in the same DC-vnet and subnet as the DC for seamless communication.
  
**2.	Joining the Domain:**
-	Changed the DNS settings on the DDC to point to the DC’s private IP.
-	Joined the Dc.com domain using domain administrator credentials.

### Step 3: Configuring Organizational Units (OUs) and Users

**1.	Creating OUs:**
-	Created three Organizational Units (OUs) in Active Directory: HR, Workstations, and Admin Users.
  
**2.	Adding Users:**
-	Created the following domain users:
	 - Hardik Rathod (privileges similar to Administrator with no password expiration).
   - Citrix Admin (copied from Administrator, placed in the Admin Users OU, and modified to restrict certain profile permissions).
     
**3.	Testing User Authentication:**
-	Successfully logged into the DDC VM using domain credentials for Hardik Rathod and Citrix Admin.

**4.	Testing DNS:**
-	Configured DNS settings to resolve queries within the Dc.com domain.
-	Tested DNS functionality to ensure proper domain name resolution.

 
### Challenges and Solutions:
**1.	Challenge:** Connectivity Between DC and DDC VMs
-	**Issue:** The DDC VM initially could not communicate with the DC due to incorrect DNS settings.
-	**Solution:** Updated the DNS server address on the DDC to point to the DC’s private IP. This resolved the issue and enabled the domain join process.
  
**2.	Challenge:** DHCP Scope Configuration
-	**Issue:** DHCP failed to assign IP addresses to the DDC during initial tests.
-	**Solution:** Verified and corrected the DHCP scope configuration, ensuring the scope was activated and the address range was not overlapping with other network configurations.
  
**3.	Challenge:** Lost RDP Connectivity to DDC VM
-	**Issue:** The DDC VM lost RDP connectivity after the network adapter was disabled.
-	**Solution:** Stopped the VM in the Azure portal and detached the existing Network Interface. Created a new Network Interface, assigning a new public and private IP address, and attached it to the DDC VM. Restarted the VM, successfully restoring RDP connectivity.
 
### Key Learnings:
-	Hands-on experience with configuring Active Directory, DNS, and DHCP in a cloud environment.
-	Troubleshooting network connectivity issues in Azure, including Network Interface reconfigurations.
-	Importance of precise configuration for successful domain join and user authentication.
-	Practical understanding of managing enterprise infrastructure components in a scalable cloud environment.
 
### Impact Statement: This lab project demonstrates my ability to:
-	Set up and manage enterprise-grade infrastructure in Azure Cloud.
-	Configure and troubleshoot key Windows Server services like ADDS, DNS, and DHCP.
-	Ensure secure and seamless communication between virtual machines.
-	Support IT operations by creating scalable and secure domain environments.

