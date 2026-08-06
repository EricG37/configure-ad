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


<h2>Ensure Connection between Client and Domain Controller</h2>
<ul>
  <li>Connect to Client-1 using Remote Desktop, then run a continuous ping to DC-1’s private IP address using: (<code>ping -t &lt;ip_address&gt;</code>).</li>
  <li>Connect to DC-1 and enable the ICMPv4 Echo Request rule in Windows Defender Firewall to allow incoming ping requests.</li>
  <li>Return to Client-1 and verify that the ping receives successful replies, confirming network connectivity between the client machine and Domain Controller.</li>
</ul>

<h2>Install Active Directory</h2>
<ul>
  <li>Connect to DC-1 and install the Active Directory Domain Services (AD DS) server role.</li>
  <li>Promote DC-1 to a Domain Controller by creating a new forest and specifying a domain name, such as mydomain.com.</li>
  <li>After the promotion is complete, restart DC-1 and sign in using the domain administrator account: mydomain.com\labuser</li>
</ul>

<h2>Create Admin User and Organizational Units (OUs) in Active Directory</h2>
<ul>
  <li>Open Active Directory Users and Computers (ADUC) and create three Organizational Units (OUs).</li>
   <li>Create the first OU named _EMPLOYEES to store standard employee accounts.</li>
   <li>Create the second OU named _ADMINS to organize administrative user accounts.</li>
   <li>Create the third OU named _CLIENTS to contain client computers.</li>
  <li>Create a new user named Jane Doe with the username jane_admin, then add the account to the Domain Admins security group.</li>
  <li>Sign out of DC-1, then sign back in using the new domain administrator account: mydomain.com\jane_admin</li>
</ul>

<h2>Join Client-1 to the Domain</h2>
<ul>
  <li>In the Azure portal, update Client-1’s DNS settings so its DNS server points to DC-1’s private IP address.</li>
  <li>Restart Client-1 from the Azure portal to apply the updated network settings.</li>
  <li>Connect to Client-1 using the local administrator account, labuser, and join the computer to the mydomain.com domain.</li>
  <li>After successfully joining the domain, restart Client-1 and confirm that it appears in Active Directory Users and Computers (ADUC) under the Computers container.</li>
  <li>Optionally, move Client-1 into the previously created _CLIENTS Organizational Unit to keep domain computers properly organized.</li>
</ul>

<h2>Configure Remote Desktop via Group Policy for Non-Administrative Users</h2>
<ul>
  <li>Create and link a new Group Policy Object (GPO) to the _CLIENTS and _EMPLOYEES Organizational Units and Configure the GPO to allow domain users to connect through Remote Desktop.</li>
  <li>Using Group Policy centralizes the management of Remote Desktop permissions for the computers and users in these OUs, eliminating the need to configure each client individually.</li>
  <li>Apply the updated policy immediately by running the following command on each client machine, or wait for the next automatic Group Policy refresh: gpupdate /force</li>
</ul>

<h2>Create more user accounts with a Powershell ISE script and verify access.</h2>
<ul>
  <li>Sign in to DC-1 using the jane_admin account, then launch PowerShell ISE with administrator privileges..</li>
  <li>Run a PowerShell script to automatically create multiple user accounts in Active Directory.</li>
  <li>After the script finishes, open Active Directory Users and Computers (ADUC) and confirm that the new accounts were created in the correct Organizational Unit.</li>
  <li>Sign in to Client-1 with one of the newly created domain accounts to verify that the account was created successfully and has the appropriate access.</li>
</ul>

<h2>Conclusion</h2>
<p>In this lab, we built an Active Directory environment in Azure using a Domain Controller and a client VM. We created a domain, organized users and computers into OUs, added user accounts, joined the client to the domain, and configured Remote Desktop access through Group Policy. We also used PowerShell to create additional users and verified that they could successfully sign in.</p>

