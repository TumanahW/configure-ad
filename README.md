<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

1. Set Up an Azure Account and Create a Virtual Network
2. Deploy a Virtual Machine for the Domain Controller
3. Install Active Directory Domain Services (ADDS)
4. Configure DNS and Active Directory Settings

<h2>Deployment and Configuration Steps</h2>
<h3>Step 1- Create two virtual machines within Azure </h3>
<p>To set up Active Directory, start by creating two virtual machines (VMs) in Azure. One VM will be a domain controller running Windows Server, named DC-1, and the other will be a client running Windows 10 Pro, named Client-1. Make sure both machines are on the same virtual network (VNet) to ensure they can communicate.

After setting up the VMs and confirming network connectivity, log in to DC-1 to begin configuring Active Directory.</p>
<img width="1415" alt="Screenshot 2024-12-05 at 1 43 28 PM" src="https://github.com/user-attachments/assets/5d79e196-7dcf-4ca4-9614-a8b3d6d6db15">
 </br>
<p>Use Remote Desktop to login to each virtual machine. Once logged into Domain Controller 1 (DC-1) go to the Start menu and locate and click the Sever Manager.</p>
<p>Once inside of Server Manager , you need to add Active Directory Services.Start by clicking> Add Roles and features. </p>

<img width="1250" alt="Screenshot 2024-12-05 at 2 25 43 PM" src="https://github.com/user-attachments/assets/1ec9cb3c-f790-480c-85fe-b01be4afbcea">

</br>
<p>Follow the prompts and click "Next" until you reach Server Selection.Make sure that DC-1 is the virtual machine that is selected. On the side bar, you should have "Server Roles" selected and on the main screen you need to check the box that says " Active Directory Domain Services".
</p>

![Screenshot 2024-12-05 at 4 26 43 PM](https://github.com/user-attachments/assets/3d4900f3-10e1-45f3-9332-81baa40126a0)

<p>For the confirmation tab check the box that says Restart the destination sever automatically if required" and then click install. This will install Active Directory Domain services on to  server manager.On the left side bar you should see AD DS added as an option.</p>

![Screenshot 2024-12-05 at 4 31 24 PM](https://github.com/user-attachments/assets/5e664885-65ea-411d-8c6b-f71eb48524d4)

<p> Next, we will the promote  the server as Domain Controller and Set a new forest as "mydomain.com". Do this by going to the server manager  and click on the flagged icon in the upper right region of the screen. Then click on the link that say promote this server to a domain controller.</p>

![Screenshot 2024-12-05 at 4 48 58 PM](https://github.com/user-attachments/assets/3a608736-d2f6-4aaa-a30f-e4050c8b8734)

![Screenshot 2024-12-05 at 4 50 43 PM](https://github.com/user-attachments/assets/fb45fe9b-94c0-464d-a83b-23b1192b55d4)

<p> Click next to move forward  and in the Directory services restore mode passoword field  create a password. For any other fields that populate eave them as is and uncheck  "DNS Delegation". Complete the configuration and the system will automatically sign you out as Active Directory completes installation.</p>

![Screenshot 2024-12-05 at 4 56 51 PM](https://github.com/user-attachments/assets/a4cee472-1a23-4890-8ed7-3b4d8c98ad1b)
</br>
<p>Next, we’ll attempt to log in to the Client-1 machine. If you use your regular credentials, the login will fail because no domain has been specified, as we just configured DC-1 as the domain controller. To successfully log in, you must include the domain in the format: mydomain.com\username, followed by the corresponding password.</p>
<p>Once inside of  Client-1 machine, go to start and then Active Directory Users and Computers.</p>

![Screenshot 2024-12-05 at 5 46 01 PM](https://github.com/user-attachments/assets/f11627c6-31d7-4eee-b1f7-0f3cf503589c)

<p>On the DC-1 machine, the next step is to create a domain administrator user within the domain. This user will have the authority to manage all users and resources in the domain, making it a critical task. To begin, go to <b> Start > Windows Administrative Tools > Active Directory Users and Computers.</b> Once there, right-click on <b>mydomain.com </b> , select<b> New, and then choose Organizational Unit (OU)</b> and name it _EMPLOYEES.</p>

![Screenshot 2024-12-05 at 5 50 43 PM](https://github.com/user-attachments/assets/b153ac8c-e00a-4f2a-a871-3acb4c8ccd80)

![Screenshot 2024-12-05 at 9 50 26 PM](https://github.com/user-attachments/assets/594cc37a-1a3d-4522-b5c7-b1b7a630d6c3)

</br>
<p> Create a second OU and name it _ADMIN. We will next create an admin user. Do this by right clicking _ADMINS > NEW > USER. Name the Admin user "Jane Doe" </p>
<p>Next, We need to make Jane Doe  a Domain Admin. To give her priviliages, we <b> click on _ADMINS (OU) and then right click on Jane Doe > Properties > Member OF </b> then  type <b>Domain Admins </b> in the field  and click on Check Names.</p>

![Screenshot 2024-12-05 at 10 54 17 PM](https://github.com/user-attachments/assets/d90f0f3c-ea3e-4d2e-8d7d-3fe66b2e32ed)

<p> Next, we will  change Client- 1's DNS Servers  so that they can point to the private IP Address of Domain Controller One (DC-1). To complete this  go to the Microsoft Azure Portal > Virtual Machines > Client-1> Network Settings > DNS Servers.</p>

![Screenshot 2024-12-05 at 11 10 50 PM](https://github.com/user-attachments/assets/03d2fc4c-a937-4ffb-9ecb-63e766378ab0)

<p> Now we will go back to Client 1 Virtual Machine  settings  and right click the start menu> system > rename this PC ( ADVANCED) on the right side> computer name tab > input my domain.com . </p>

![Screenshot 2024-12-05 at 11 14 45 PM](https://github.com/user-attachments/assets/9256774e-1a81-4cad-9448-868787bb2ed5)

![Screenshot 2024-12-05 at 11 19 57 PM](https://github.com/user-attachments/assets/bc8774b4-f6dc-43c8-9545-79371e8881aa)
<p> Your computer will restart  and then next login to the Domain Controller and verify  that client-1 shows up in AD UC.</p>

![Screenshot 2024-12-05 at 11 22 36 PM](https://github.com/user-attachments/assets/be67f3ee-00e5-44e7-91fe-b712a8da38c1)

