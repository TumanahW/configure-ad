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
<h2>Step 1 </h2>
<p>To set up Active Directory, start by creating two virtual machines (VMs) in Azure. One VM will be a domain controller running Windows Server, named DC-1, and the other will be a client running Windows 10 Pro, named Client-1. Make sure both machines are on the same virtual network (VNet) to ensure they can communicate.

After setting up the VMs and confirming network connectivity, log in to DC-1 to begin configuring Active Directory.</p>
