# <h1>Active Directory Home Lab</h1>

<h2>Description</h2>
Project consists of a simple PowerShell script that allows the user to mass create users in an Active Directory home lab environment using Oracle Virtual Box. Configuring and running this lab helps develop a solid foundation for how active directory and windows networking work together.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle Virtual Box</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Server 2019</b> 

<h2>Program walk-through:</h2>

<p align="center">
Project Blueprint:  <br/>
<img src="https://i.imgur.com/vmuNAiR.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Created Virtual Machines:  <br/>
-One VM was configured as a Domain Controller to manage permissions and access, while another VM acted as a client to receive and test those permissions 
 
<img width="80%" height="80%" alt="MainDomain" src="https://github.com/user-attachments/assets/9d1e17bd-cbbb-4ac4-ba4c-b7f5adc4a8f1" />

 
 <img width="80%" height="80%" alt="Client" src="https://github.com/user-attachments/assets/275ee541-91cc-4a6f-b621-f7fdc58b0390" />
<br />

<br />
<br />
Install Active Directory Domain Services: It lets the VM manage users, computers, and permissions on a network. <br/>
<img width="80%" height="80%" alt="Active Directory" src="https://github.com/user-attachments/assets/8a4e42d3-c083-4e22-be23-d08236c66cb6" />

<br />
<br />
Configure Domain Controller: It turns a server into the “brain” of the network that controls logins, access, and security. <br/>
- To establish admin access
<img src="https://i.imgur.com/2hLveDw.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Create an Organizational Unit to house our personally created admin account:  <br/>
- Create New User > Name user > "Properties" > "Member of" > Add to "Domain Admins"
<img src="https://i.imgur.com/SSbLS2t.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Configuring Remote Access and installing NAT on the internet interface allows your server to connect internal machines to the internet and manage that traffic.:  <br/>
<img src="https://i.imgur.com/QGblLb6.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Set up DHCP Server on the Domain Controller:  <br/>
- Allows Windows 10 Clients to get an IP address that will let them browse the internet even though they are on the private internal network. <br/>
- Add scope range to ensure that clients are assigned IP addresses within the specified range.
<img src="https://i.imgur.com/mxLBY10.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Using a Domain Controller as a DNS server allows your network to find and connect to devices and services using names instead of IP addresses—and is required for Active Directory to work properly.  <br/>
<img width="80%" height="80%" alt="DNS" src="https://github.com/user-attachments/assets/e9e79bcd-cefb-496c-93e3-fb453ecc2787" />

<br />
<br />
Text file with several randomly generated names:  <br/>
- A user will be created for each one of the names on this list. <br/>
<img width="80%" height="80%" alt="Text Of Names" src="https://github.com/user-attachments/assets/02b8bf26-7c64-4f59-811f-d8bd7fa84dc7" />

<br />
<br />
Enable execution of all scripts:  <br/>
<img src="https://i.imgur.com/0nnAutm.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Run the CREATE_USERS Powershell script to create client users:  <br/>
- Users will all use the same generic password "Password1". <br/>
- "Get-Content" used to bring all names into an array. <br/>
- "$password" takes generic password and creates a password object for it. <br/>
- "New-ADOrganizationalUnit" creates a new organizational unit named "Users". <br/>
- "Foreach" loop runs for each individual user in the text file and creates a username using the first initial of the user's first name and their entire last name. <br/>
- "New-AdUser" creates a new user in Active Directory and assigns them the generic "Password1" and some credentials. <br/>
<img width="80%" height="80%" alt="new ad user" src="https://github.com/user-attachments/assets/995312fe-7e98-497b-8cdc-ade79e9664d1" />

<br />
<img src="https://i.imgur.com/qxK5VMq.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Observe users being created:  <br/>
<img src="https://i.imgur.com/1UMP6E6.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Ensure the client machine can ping to the internet:  <br/>
<img width="1025" height="772" alt="Pingback" src="https://github.com/user-attachments/assets/3b483327-1f5f-49ef-acb1-d7d641c96ffc" />

<br />
<br />
Observe that the client machine is joined with the domain:  <br/>
<img src="https://i.imgur.com/gq8xJpr.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Use any one of the several logins that were created to access the Windows 10 machine:  <br/>
<img width="1028" height="765" alt="OtherUser" src="https://github.com/user-attachments/assets/1d708180-c578-40cf-9a50-d826fcb94869" />

<br />


</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
