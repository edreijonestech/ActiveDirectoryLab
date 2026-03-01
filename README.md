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
-One for Domain Controller and one for client
<img src="https://i.imgur.com/cqb74j7.png height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<img src=https://i.imgur.com/71CDXMu.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Install Active Directory Domain Services:  <br/>
<img src="https://i.imgur.com/tiHwSI5.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Configure Domain Controller:  <br/>
- To establish admin access
<img src="https://i.imgur.com/2hLveDw.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Create an Organizational Unit to house our personally created admin account:  <br/>
- Create New User > Name user > "Properties" > "Member of" > Add to "Domain Admins"
<img src="https://i.imgur.com/SSbLS2t.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Configure Remote Access and install NAT on internet interface:  <br/>
<img src="https://i.imgur.com/QGblLb6.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Set up DHCP Server on the Domain Controller:  <br/>
- Allows Windows 10 Clients to get an IP address that will let them browse the internet even though they are on the private internal network. <br/>
- Add scope range to ensure that clients are assigned IP addresses within the specified range.
<img src="https://i.imgur.com/ZknBGwj.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Use Domain Controller as DNS Server:  <br/>
<img src="https://i.imgur.com/cC0JxHe.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Text file with several randomly generated names:  <br/>
- A user will be created for each one of the names on this list. <br/>
<img src="https://i.imgur.com/p903z3U.png" height="80%" width="80%" alt="Active Directory Steps"/>
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
<img src="https://i.imgur.com/8KrHwfh.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<img src="https://i.imgur.com/qxK5VMq.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Observe users being created:  <br/>
<img src="https://i.imgur.com/1UMP6E6.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Ensure the client machine can ping to the internet:  <br/>
<img src="https://i.imgur.com/ToOfcNE.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Observe that the client machine is joined with the domain:  <br/>
<img src="https://i.imgur.com/gq8xJpr.png" height="80%" width="80%" alt="Active Directory Steps"/>
<br />
<br />
Use any one of the several logins that were created to access the Windows 10 machine:  <br/>
<img src="https://i.imgur.com/RgWw34r.png" height="80%" width="80%" alt="Active Directory Steps"/>
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
