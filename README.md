<h1>Active Directory - Mass User Creation Lab </h1>

<h2>Description</h2>
In this lab we will be utilzing a PowerShell script to create 10000 users in Active Directory. We will assume that the server and client have already been initialized  and ready to use. For this specific setup, I will be using Oracle Virtualbox to run the Virtual Machines and to set up our Domain Controller. We will also install server 2019 on this Virtual Machine and install Active Directory to create our domain. I will then be using another Virtual Machine and installing Windows 10. We will ensure that the Windows 10 VM is able to connect to the domain and has the ability login to any random user we have created. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle Virtual Machine</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Windows Server 2019</b>

<h2>Lab walk-through:</h2>

<p align="center">
Go into Server Manager and add roles and features: <br/>
<img src="https://i.imgur.com/Jgfo1hQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Select Active Directory Domain Services and conintue to the next steps with the default options: <br/>
<img src="https://i.imgur.com/P0HXPZg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once completed, we will go on to the post deployment configurations by selecting "promote this server to a domain controller" : <br/>
<img src="https://i.imgur.com/dtJ7vHh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Select Add a new forest and create your domain name which in this case will be mydomain.com : <br/>
<img src="https://i.imgur.com/YadzV3S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Go into "Active Directory Users and Computers" and create an Organization Unit to put the ADMIN account  inside of : <br/>
<img src="https://i.imgur.com/rLTvfKx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Inside the ADMIN folder we will create a new user with any credentials you would like : <br/>
<img src="https://i.imgur.com/2nFnfzL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Right click on the newly created account and go into properties to give the account "Domain Admins" : <br/>
<img src="https://i.imgur.com/GjRS7bR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Now we can sign out of the account and see that we are able to log in to our newly created Domain Admin Account : <br/>
<img src="https://i.imgur.com/DvqqufJ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next we will install RAS/NAT on Domain Controller by Adding Roles and Features and selecting Remote Access as well as Routing : <br/>
<img src="https://i.imgur.com/J8QeaSc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Selectg Tools and go to Routing and Remote Access : <br/>
<img src="https://i.imgur.com/FNnJ4hJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Right click on DOMAINCONTROLLER and select Configure and Enable Routing and Remote Access : <br/>
<img src="https://i.imgur.com/TeP8b8f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Network address Translation NAT and finish setup: <br/>
<img src="https://i.imgur.com/eCDT6bo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We will now setup a DCHP server on domain controller by Adding Roles and selecting DHCP Server and installing  : <br/>
<img src="https://i.imgur.com/G4UqGUe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Go into the DHCP settings and right click on IPv4 and create New Scope. We can name the scope the same as the IP Range: <br/>
<img src="https://i.imgur.com/oiLX9k4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br /> 
Here we can input the Start and End IP Address with a mask of 24: <br/>
<img src="https://i.imgur.com/TLLfivD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the Domain Controllers IP address and click ADD: <br/>
<img src="https://i.imgur.com/Catv7vR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Right click the DHCP server and select Authorize and then Refresh: <br/>
<img src="https://i.imgur.com/Cr0DRL8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />  
Save AD_PS-master zip to server desktop: <br/>
<img src="https://imgur.com/7pixq7h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open PowerSell ISE as administrator and open 1_CREATE_USERS file:  <br/>
<img src="https://imgur.com/z1te4JC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In order for program to run, we must run the Set-ExecutionPolicy Unrestricted and click "Yes to All": <br/>
<img src="https://imgur.com/u3t1sZ8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to approtiate directory where file was saved:  <br/>
<img src="https://imgur.com/R3BwlJx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run the script and select "Run Once":  <br/>
<img src="https://imgur.com/LWgTTDt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The PowerShell command will comeplete and you will be able to open Active Directory Users and Computers to check:  <br/>
<img src="https://imgur.com/RjOfDyX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We can then login to our connected Windows VM as any randomly selected user from the list (Default Password: Password1):  <br/>
<img src="https://imgur.com/ilgymlI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Here we can confirm that we are logged in as "acoke" in "mydomain" which is the domain we crated:  <br/>
<img src="https://imgur.com/9EwlaJ9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
