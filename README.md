# active-directory-homelab
Step-by-step documentation of a Windows Server 2019 Active Directory homelab built using VirtualBox.

# Overview
This homelab demonstrates how to:

Install and configure Windows Server 2019

Promote a server to a Domain Controller (DC)

Set up Active Directory Domain Services (AD DS)

Create and manage users, groups, and OUs

Join a Windows client machine to the domain

Practice basic domain administration tasks

# Server Setup

1. Use Virtual Box and to create a New VM with two network adapters and selecting Windows 2019 as the OS, ensuring that you mount the required ISO file found here: https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019

2. Ensure you select the desktop experience when installing the server

<img width="638" height="479" alt="Screenshot 2026-02-21 155431" src="https://github.com/user-attachments/assets/798ebb3d-daec-4e3f-897a-f54f55b9ad87" />


3. Create Admin Password and login


<img width="802" height="473" alt="Screenshot 2026-02-21 162532" src="https://github.com/user-attachments/assets/6b6b3870-ae6b-43f8-a338-89fe373b451a" />

4. You can install guest editions CD image to make it more compatabile with a VM and improve resolution (optional). Run amd64 and reboot

<img width="774" height="582" alt="Screenshot 2026-02-21 175533" src="https://github.com/user-attachments/assets/f0c718e3-54d0-4d84-86fe-2655fe1eff8e" />

5. Go To settings > Network & Internet > Ethernet > Change adapter options. Name the network adapters according to their IP. 

<img width="1119" height="213" alt="Screenshot 2026-02-21 182248" src="https://github.com/user-attachments/assets/6d65d082-b32f-42aa-a510-615d8860ec77" />

6. For internal network go to properties and change ipv4 address and subnet mask to the following leaving default gateway empty since the domain controller will act as the default gateway. Preferred DNS is loopback address

<img width="398" height="453" alt="Screenshot 2026-02-21 182757" src="https://github.com/user-attachments/assets/744fc828-5ab0-4b99-90b1-01e51c13cf3c" />


7. Go to Settings > System > About. Rename the system to something suitable and restart

<img width="677" height="293" alt="Screenshot 2026-02-21 181438" src="https://github.com/user-attachments/assets/be6d04c2-d196-4f02-940b-0e49381907f4" />

# Creating a Domain

Open server manager - click add roles or fetaures. ensure AD DS is slected and install
<img width="782" height="553" alt="Screenshot 2026-02-21 184314" src="https://github.com/user-attachments/assets/bd6a9eb4-7e1a-4fc3-b181-058df3d56944" />

Click on icon to promote domain
<img width="1719" height="903" alt="Screenshot 2026-02-24 164323" src="https://github.com/user-attachments/assets/a5046522-ed99-4474-a137-f90b61387cc9" />

Click add new forest, name domain and proceed
<img width="753" height="559" alt="Screenshot 2026-02-24 164451" src="https://github.com/user-attachments/assets/e257192c-8a2f-49a1-a3eb-6b5055fe4608" />

Give domain A recovery PW. cONTINUE THROUGH WIZARD CLICKING NEXT AND INSTALL.

<img width="751" height="554" alt="Screenshot 2026-02-24 165038" src="https://github.com/user-attachments/assets/64349462-bf82-4716-994c-c2d87b19c58f" />

Server will restart and you will see a new admin account to sign in as

Open windows Active Directory Users and COmputers, right click on domain and add a new organisational unit and name it Admins 
<img width="751" height="521" alt="image" src="https://github.com/user-attachments/assets/61f944c3-78c0-4081-8dc1-e69c01a8fc78" />

On the admins unit right click abd new user and create your first admin

<img width="435" height="370" alt="image" src="https://github.com/user-attachments/assets/a54df87c-2481-46db-86c6-cdc7c6dc1d40" />

<img width="434" height="372" alt="image" src="https://github.com/user-attachments/assets/c54f2f4f-b460-41c3-8ef1-fa6ef70eda9a" />

Right click on the new user profile in the admin folder > click properties > member of > add a domian admin account and apply

<img width="412" height="537" alt="image" src="https://github.com/user-attachments/assets/59ec8b5a-cea7-42d3-bebb-297358e1e544" />

You should now be able to successfuly login as your new admin account

<img width="1710" height="861" alt="image" src="https://github.com/user-attachments/assets/8f1bd26a-5e17-41ad-bd0d-e0c5e8570507" />Password1

# Remote access Server & Network Address Translation setup
Will alllow windows client to connect to server via private virtual network


