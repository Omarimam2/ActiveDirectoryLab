<h1>Active Directry - Mass User Creation Lab </h1>

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
