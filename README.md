<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

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

<p>Use Remote Desktop to login to each virtual machine. Once logged into Domain Controller 1 (DC-1) go to the Start menu and locate and click the Sever Manager.</p>
<p>Once inside of Server Manager , you need to add Active Directory Services.Start by clicking> Add Roles and features. </p>

<img width="1250" alt="Screenshot 2024-12-05 at 2 25 43 PM" src="https://github.com/user-attachments/assets/1ec9cb3c-f790-480c-85fe-b01be4afbcea">
