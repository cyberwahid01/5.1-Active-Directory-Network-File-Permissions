<p align="center">
<img src="https://i.imgur.com/9JmwJSF.png" alt="osTicket logo"/>
</p>

<h1>Active Directory: Network File Permissions 🪟</h1>
In this lab we run through the process of creating folders within a Domain Controller and configuring different levels of access for different users within our domain. We will use the same Active Directory Server and Client Machine environments that we used in the last lab.

(Link Back to Main Project Contents Page is at the Bottom of this Repo)
<h2>Environments and Technologies Used</h2>

- Lenovo Ideapad 5 Pro 16gb AMD Ryzen 7
- Microsoft Azure Resource Group
- Microsoft Azure Windows 10 Pro version 22H2 - x64 Gen2 Virtual Machine
- Microsoft Azure Windows Server 22 Datacenter: Azure Edition - x64 Gen2 Virtual Machine

<h2>Operating Systems Used </h2>

- Local Windows 11 Home Version 21H2</b>
- Windows 10 Pro Version 22H2 Virtual Machine
- Windows Server 22 Datacenter: Azure Edition - x64 Gen2 Virtual Machine
  
<h2>List of Prerequisites</h2>

- Microsoft Azure Subscription
- Microsoft Azure Subscription Credit 

<h2>Installation, Setup, Resource Setup, Executing Functions</h2>
1. Initially we will log into our client machine as our test user for whom we will be configuring permissions and access. We are logged into our Domain Controller as an Admin user and it is here we will create the initial folders for which will configure these settings
</p>
<br />

<p>
<img src="https://i.imgur.com/UacmGY4.png" alt="1"/>
</p>
<p>
2. Within the C: Drive of our Domain Controller machine, we create the following folders which we will then assign permissions to. The folders have been labeled with the permissions that will be granted to them.
</p>
<br />

<p>
<img src="https://i.imgur.com/QILw8jO.png" alt="2"/>
</p>
<p>
3. For the READ folder we will grant Read access to all Domain Users. We do this by right-clicking the folder and accessing the Advanced Sharing settings. From here we find the Domain Users property that includes all users in the domain, add them to the list and give them the Read permission level.
</p>
<br />

<p>
<img src="https://i.imgur.com/qAZhyms.png" alt="3"/>
</p>
<p>
4. For the READ-WRITE folder we will follow the same process as above and grant Read/Write access to all Domain Users. We do this by right-clicking the folder and accessing the Advanced Sharing settings. From here we find the Domain Users property that includes all users in the domain, add them to the list and give them the Read/Write permission level.
</p>
<br />

<p>
<img src="https://i.imgur.com/0n6GKCj.png" alt="4"/>
</p>
<p>
5. For the NO-ACCESS folder, we want to only grant Read/Write access to Domain Admins. We will follow the same process as above and instead of choosing the Domain Users group we instead add the Domain Admins group to the list and give them Read/Write access. 
</p>
<br />

<p>
<img src="https://i.imgur.com/e0PuN70.png" alt="5"/>
</p>
<p>
6. Here we go through the process of now accessing these folders on our Client machine. Since the Client machine is on the Domain Controller network, we can go to the Network section in the Client Machine. Within the Network we can see both the Domain Controller and the Client machine. If we click on the Domain Controller machine (VNet-AD) we see our created folders.
</p>
<br />

<img src="https://i.imgur.com/pkVvojs.png" alt="6"/>
</p>
<p>
7. Since we are logged into our Client machine as a Domain User that is not an admin, we can see here that we can access the READ folder and see what is inside, but when we try to create a folder inside it we are denied access since we cannot Write in the folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/Bvhvfim.png" alt="7"/>
</p>
<p>
8. Here we can see that as a Domain User, not only are we able to access the READ-WRITE folder but we can also Write inside it and create files.
</p>
<br />

<p>
<img src="https://i.imgur.com/00AvUzZ.png" alt="8"/>
</p>
<p>
9. Here we can see that if we try to access the NO-ACCESS folder there is a Network Error as only Domain Admins can access the folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/EDxJCtY.png" alt="9"/>
</p>
<p>
10. Now we will create a Security Group Organisational Unit and name it _ACCOUNTANTS. This will be done within our Domain Controller Active Directory.
</p>
<br />

<img src="https://i.imgur.com/bovmblS.png" alt="10"/>
</p>
<p>
11. Now we can configure the ACCOUNTING folder that we created within the C: Drive of our Domain Controller Network. Here we want to configure special access to only users who belong in the _ACCOUNTANTS Security Group. People in this Organisational Unit have been given Read/Write access.
</p>
<br />

<p>
<img src="https://i.imgur.com/us2wqJk.png" alt="11"/>
</p>
<p>
12. Back in our Client machine we are still logged in as our test Domain User. If we try to access the ACCOUNTING folder with this user we are unable to since the Domain User is not part of the _ACCOUNTING Security Group. 
</p>
<br />

<p>
<img src="https://i.imgur.com/VXZVUVW.png" alt="12"/>
</p>
<p>
13. In order for us to grant access to our test user we need to add them _ACCOUNTANTS Security Group.
</p>
<br />

<p>
<img src="https://i.imgur.com/7sKD0on.png" alt="13"/>
</p>
<p>
14. We can now see that the our test user is a Member of the _ACCOUNTANTS Security Group.
</p>
<br />

<p>
<img src="https://i.imgur.com/SeLjAuZ.png" alt="14"/>
</p>
<p>
15. After adding our Domain user to the _ACCOUNTANTS group we can see they are able to access and write inside the ACCOUNTING folder.
</p>
<br />

<p>
<img src="https://i.imgur.com/0qhM7Fd.png" alt="15"/>
</p>
<p>
LINK BACK TO THE MAIN PROJECT CONTENTS PAGE - https://github.com/cyberwahid01/Azure-Compute-and-Networking
