<p align="center">
<img src="https://i.imgur.com/gJkqIbs.png" alt="Network File Share Logo"/>
</p>

<h1>Configuring Network File Shares and Permissions within Azure</h1>
This tutorial outlines the implementation of file sharing and permission settings within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create some sample file shares with various permissions
- Attempt to access file shares as a normal user
- Create an “ACCOUNTANTS” Security Group, assign permissions, and test access

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/LNuie2T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This is a continuation of the Active Directory project. Open Active Directory Users and Computers on DC-1 and pick a user to log into Client-1 with. Remember the passwords created for the users were "Password1".
</p>
<br />

<p>
<img src="https://i.imgur.com/YBRVpg8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into Client-1 with the random user.
</p>
<br />

<p>
<img src="https://i.imgur.com/Scnj4wU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On DC-1 go to Start and File Explorer. We will create 4 files.
</p>
<br />

<p>
<img src="https://i.imgur.com/0RNVFkF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to This PC, C Drive and create the 4 highlighted folders.
</p>
<br />

<p>
<img src="https://i.imgur.com/27lWTwW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Oon the read-access folder, right click and click on properties.
</p>
<br />

<p>
<img src="https://i.imgur.com/au4MPTA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on Sharing tab then Share and add domain users and make sure it's read only and click Share.
</p>
<br />

<p>
<img src="https://i.imgur.com/78XlFVj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Do the same for the write-access folder but give it Read/Write access.
</p>
<br />

<p>
<img src="https://i.imgur.com/CvLhRBf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the no-access folder, add domain admins and give read/write permissions.
</p>
<br />

<p>
<img src="https://i.imgur.com/esO61HM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to Client-1 and open File Explorer and type in \\dc-1 and hit enter to find the shared DC-1 file.
</p>
<br />

<p>
<img src="https://i.imgur.com/2l7xbrk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Try to open no-access and notice you cannot.
</p>
<br />

<p>
<img src="https://i.imgur.com/LPdWLPK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open the read-access folder and try to make a new folder inside.
</p>
<br />

<p>
<img src="https://i.imgur.com/UA4h2XX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
An error message should appear.
</p>
<br />

<p>
<img src="https://i.imgur.com/Nw7Fis7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The write-access folder should allow you to create a folder inside.
</p>
<br />

<p>
<img src="https://i.imgur.com/FrouDPl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to DC-1 and in the read-access only folder, right click to create a text file and write something in it.
</p>
<br />

<p>
<img src="https://i.imgur.com/Zfo0C30.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to Client-1 and go to the read-access folder and try to make a folder. Then try to read the text document.
</p>
<br />

<p>
<img src="https://i.imgur.com/Zd495Mt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The folder shouldn't be able to be created but the text file should be able to open.
</p>
<br />

<p>
<img src="https://i.imgur.com/eA5TMEX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to Active Directory Users and Computers and create a new Organizational Unit called _SECURITY_GROUPS.
</p>
<br />

<p>
<img src="https://i.imgur.com/FYwMFws.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a new group inside _SECURITY_GROUPS.
</p>
<br />

<p>
<img src="https://i.imgur.com/LvfEp2d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a new group called ACCOUNTANTS.
</p>
<br />

<p>
<img src="https://i.imgur.com/6fubmmy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to the accounting folder created earlier and go to properties then sharing and add ACCOUNTANTS with Read/Write access and Share.
</p>
<br />

<p>
<img src="https://i.imgur.com/iD9Sach.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to Client-1 and go to \\dc-1 folder. The accounting folder should be visible.
</p>
<br />

<p>
<img src="https://i.imgur.com/l8Oi78t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The user on Client-1 still has no access.
</p>
<br />

<p>
<img src="https://i.imgur.com/gRxxsd8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to DC-1 and Active Directory. Right click ACCOUNTANTS security group, go to Properties.
</p>
<br />

<p>
<img src="https://i.imgur.com/E6lOqcJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Under Members tab click add and add the user you're logged into Client-1 with. Make sure to check the name, press Ok and then Apply.
</p>
<br />

<p>
<img src="https://i.imgur.com/07l9LFx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Access to accounting folder still isn't allowed. You must log out and log back in as the user. 
</p>
<br />

<p>
<img src="https://i.imgur.com/LsvRHws.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Logoff and log back in.
</p>
<br />

<p>
<img src="https://i.imgur.com/jcolmoJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The accounting folder can now be accessed.
</p>
<br />
