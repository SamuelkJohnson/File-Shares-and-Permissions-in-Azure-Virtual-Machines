<p align="center">
<img src="https://imgur.com/jgPG99G.png" alt="Traffic Examination"/>
</p>

<h1>File Shares and Permissions in Azure Virtual Machines</h1>
In this tutorial, we will practice setting up different file permissions and access (on a domain) to different users within different groups. This is all done within Active Directory on our CLient Virtual Machine in Azure. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory
- File Permissions
- Security Groups

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022

<h2>High-Level Steps</h2>

- Step 1: Login to both VMs
- Step 2: Create 4 Shared Folders & Set Permissions
- Step 3: Test Permissions
- Step 4: Create Security Group & Grant Additional Permissions
- Step 5: Test Security Group Members' Access

<h2>Actions and Observations</h2>

<p>
<img src="https://imgur.com/OBFtOuo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 1: Remote Desktop into both VMs that were used in the previous lab (DC-1 & Client-1). These are the subject VMs that will be used again for this lab with DC-1 being the Domain Controller once again. 
</p>
</p>
<p>
Step 2: Create four folders on DC-1's C: drive all with different access permissions: 
  - "read-access" - permission: read, 
  <p>
  - "write-access" - permission read/write", 
      <p>
  - "no-access" - permission none
          <p>
  - "accounting" - permission read/write.
</p>
<br />
<p>
<img src="https://imgur.com/2ptRUDM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Step 3: Log into a random employee account on Client-1 to test the newly added permissions/access created in step #2. 
  <p>
  - Type "\\dc-1" into file explorer to show all shared folders created on the domain in step #2.
    <p>
  - click any of the created shared folders and try to perfrom an action that does not align with the permissions used for said folder. 
      <p>
  - You should not be allowed to open the folder titled "no-access" or write in the folder titled "read-access", etc.
</p>
<br />
<img src="https://imgur.com/2ptRUDM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 4: Create an "Organizational Unit" (OU) in Active Directory on DC-1 titled "Security Group"
  <p>
- Create a new group within the OU titled "Accountants"
  <p>
    <br />
<img src="https://imgur.com/j5HJenP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p> 
- Add 2 random users to the "Accountant" security group (this will give the users access to the shared accountant folder created earlier)
  <p>
  - 1st User: babi.com/bixoli.xihep
</p>
<br />
<img src="https://imgur.com/HR6fATO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
  <p>
  - 2nd User: babi.com/duva.miduk
      <p>
<img src="https://imgur.com/OSsh2Fg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  - Share accounting folder with Accountants Security Group
  <p>
    <img src="https://imgur.com/NdsZnns.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
    <p>
   - Remote desktop Client-1 using one of the accountants security group members (1st user OR 2nd user) 
      <p>
      <img src="https://imgur.com/v5lbuDz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
        <p>
          - as you can see, the user is having access to the accounting folder.
          <p>
            <p>
   - Remote desktop Client-1 with a user who is not part of the accountants group
      <p>
        <p>
          - The user should not be able to access the accounting folder as shown below:
          </p>
         <p>
      <img src="https://imgur.com/5PsmWOV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>  
        <p>       
<br />
This concludes this tutorial on file permissions. Please note the criteria for creating security groups can be based on departments or office branches etc as a way of implementing the PoLp. 
