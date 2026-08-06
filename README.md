<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1 align="center">Azure Active Directory Lab - Deploy and Configure AD</h1>

<p>The objective of this lab is to deploy and configure Active Directory (AD) in a virtual Azure environment. This includes setting up a Domain Controller (DC), joining a client computer to the domain, creating and managing user accounts, and configuring Remote Desktop access for administrative and standard users.</p>

<h2>Deployment and Configuration Steps</h2>
<ol>
  <li>Configure Azure resources by creating a Domain Controller and a client virtual machine.</li>
  <li>Establish and verify network connectivity between the client machine and Domain Controller.</li>
  <li>Install and configure Active Directory Domain Services (AD DS) on the Domain Controller.</li>
  <li>Create administrative and standard user accounts in Active Directory.</li>
  <li>Join the client virtual machine to the domain.</li>
  <li>Use Group Policy to grant Remote Desktop access to non-administrative users in the _CLIENTS and _EMPLOYEES Organizational Units (OUs).</li>
  <li>Use a PowerShell ISE script to create additional user accounts and verify that they can successfully access the domain environment.</li>
</ol>

<h2>Environments and Technologies </h2>
<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Remote Desktop/Windows App</li>
  <li>Windows Server 2022 (Domain Controller)</li>
  <li>Windows 10 (Client)</li>
</ul>

<h2>Operating Systems</h2>
<ul>
  <li>Windows Server 2022</li>
  <li>Windows 10 </li>
</ul>


<h2>Setup Resources in Azure</h2>
<ul>
  <li>Create a Windows Server 2022 virtual machine named DC-1 to serve as the Domain Controller.</li>
  <li>Record the Resource Group and Virtual Network (VNet) associated with DC-1.</li>
  <li>Configure DC-1’s network interface card (NIC) to use a static private IP address for consistent network connectivity.</li>
  <li>Create a Windows 10 virtual machine named Client-1 within the same Resource Group and VNet as DC-1.</li>
  <li>Confirm that DC-1 and Client-1 are connected to the same VNet using Azure’s Network Watcher Topology tool.</li>
</ul>
