---
---
|                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Name                                                                                                                                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Command                                                                                                                                                             | Explain                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Gobuster                                                                                                                                     | take a list of potential page or directory names and try accessing a website with each of them                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | gobuster -u http://fakebank.thm -w wordlist.txt dir                                                                                                                 | \-u is used to state the website we're scanning, -w takes a list of words to iterate through to find hidden pages.                                                                                                                                                                                                                                                                                                                                           |
| Search operators                                                                                                                             | **"exact phrase":** Double quotes indicate that you are looking for pages with the exact word or phrase. For example, one might search for "passive reconnaissance" to get pages with this exact phrase.<br>**site::** This operator lets you specify the domain name to which you want to limit your search. For example, we can search for success stories on TryHackMe using site:tryhackme.com success stories.<br>**\-:** The minus sign allows you to omit search results that contain a particular word or phrase. For example, you might be interested in learning about the pyramids, but you don’t want to view tourism websites; one approach is to search for pyramids -tourism or -tourism pyramids.<br>**filetype::** This search operator is indispensable for finding files instead of web pages. Some of the file types you can search for using Google are Portable Document Format (PDF), Microsoft Word Document (DOC), Microsoft Excel Spreadsheet (XLS), and Microsoft PowerPoint Presentation (PPT). For example, to find cyber security presentations, try searching for **filetype:ppt cyber security.** |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Shodan                                                                                                                                       | It allows you to search for specific types and versions of servers, networking equipment, industrial control systems, and IoT devices.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [Censys](https://search.censys.io/) ([Search use cases](https://support.censys.io/hc/en-us/articles/20720064229140-Censys-Search-Use-Cases)) | Censys, on the other hand, focuses on Internet-connected hosts, websites, certificates, and other Internet assets.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [VirusTotal](https://www.virustotal.com/)                                                                                                    | is an online website that provides a virus-scanning service for files using multiple antivirus engines. It allows users to upload files or provide URLs to scan them against numerous antivirus engines and website scanners in a single operation. They can even input file hashes to check the results of previously uploaded files.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [Have I Been Pwned](https://haveibeenpwned.com/) (HIBP)                                                                                      | it tells you if an email address has appeared in a leaked data breach.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [CVE Program](https://www.cve.org/)                                                                                                          | search for existing CVEs                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [Exploit Database](https://www.exploit-db.com/)                                                                                              | lists exploit codes from various authors; some of these exploit codes are tested and marked as verified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Google Directives                                                                                                                            | Google provides “directives” that are easy to use and help us get<br>the most out of every search. These directives are keywords that enable us to<br>more accurately extract information from the Google Index.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 1. site:domain term(s) to search<br>2. allintitle:index of<br>3. inurl:admin<br>4. cache:[syngress.com](https://syngress.com)<br>5. filetype:pdf<br>6. filetype:pdf |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| The Harvester                                                                                                                                | This tool allows us to quickly and accurately catalog both e-mail addresses and subdomains that are directly related to our target.The Harvester can be used to search Google, Bing, and PGP servers for e-mails,hosts, and subdomains. It can also search LinkedIn for user names.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | theharvester<br>Ex:<br>./theharvester.py -d syngress.com -l 10 eb google                                                                                            | \-d used to specify the target domain.<br>\-l used to limit the number of result.                                                                                                                                                                                                                                                                                                                                                                            |
| [Whois](http://www.whois.net)                                                                                                                | The Whois service allows us to access specific information about our target including the IP addresses or host names of the company’s Domain Name Systems (DNS) servers and contact information which usually contains an address and a phone number.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | whois <domain>                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [NetCraft](http://news.netcraft.com)                                                                                                         | Netcraft will return any websites it is aware of that contain your search words.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Host                                                                                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | host target\_hostname (also in reverse)                                                                                                                             | \-a (verbose)                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| nslookup                                                                                                                                     | nslookup is a tool that can be used to query DNS servers and potentially obtain records about the various hosts of which it is aware                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | nslookup <hostname>                                                                                                                                                 | use it in interactive mode combined with host tool                                                                                                                                                                                                                                                                                                                                                                                                           |
| dig                                                                                                                                          | extracting info from DNS. dig makes it very simple to attempt a zone transfer. Recall that a zone transfer is used to pull multiple records from a DNS server.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | dig @target\_ip                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Fierce                                                                                                                                       | Fierce is an easy to use, powerful Perl script that can provide you with dozens of additional targets.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | fierce -dns <domain>                                                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Metagoofil                                                                                                                                   | MetaGooFil is a metadata extraction tool<br>After navigating to the MetaGooFil directory, it is a good idea to create a “files” folder. The purpose of this folder is to hold all the target files that will be downloaded                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                                                                                                                                                                     | The “-d” switch is used to specify the target domain to be<br>searched. The “-t” switch is used to specify which type or types of files you want<br>MetaGooFil to attempt to locate and download.<br>The “-n” switch is used to specify how many files of each type you would like to download for examination. our command “eo files” will save each of the discovered documents into this folder. Lastly we use the “ef” switch to specify an output file. |
| [ThreatAgent Drone](https://www.threatagent.com)                                                                                             | ThreatAgent takes OSINT gathering to the next level by using a number of different sites, tools, and technologies to create an entire dossier for you about your target. The only thing you need is the organization name (Syngress) and a domain name such as syngress.com                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

## Useful Links

* [Web Enumeration](https://tryhackme.com/r/room/webenumerationv2) - Learn the methodology of enumerating websites by using tools such as Gobuster, Nikto and WPScan
* [Become a Hacker](https://tryhackme.com/r/room/becomeahackeroa) - Learn how TryHackMe can help you become a hacker.
* [Introduction to SIEM](https://tryhackme.com/r/room/introtosiem) - An Introduction to Security Information and Event Management
* [Security Operations](https://tryhackme.com/r/room/securityoperations) - Learn about the Security Operations Center (SOC): its responsibilities, services, and data sources
* [DFIR : An Introduction](https://tryhackme.com/r/room/introductoryroomdfirmodule) - Introductory room for the DFIR module
* [Intro to Malware Analysis](https://tryhackme.com/r/room/intromalwareanalysis) - What to do when you run into a suspected malware

## Windows Fundamental

The file system used in modern versions of Windows is the **New Technology File System** or simply [NTFS](https://docs.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview).
Before NTFS, there was **FAT16/FAT32** (File Allocation Table) and **HPFS** (High Performance File System). 

NTFS is known as a journaling file system. In case of a failure, the file system can automatically repair the folders/files on disk using information stored in a log file. This function is not possible with FAT.   
NTFS addresses many of the limitations of the previous file systems; such as: 

* Supports files larger than 4GB
* Set specific permissions on folders and files
* Folder and file compression
* Encryption ([Encryption File System](https://docs.microsoft.com/en-us/windows/win32/fileio/file-encryption) or **EFS**)

On NTFS volumes, you can set permissions that grant or deny access to files and folders.

The permissions are:

* **Full control**
* **Modify**
* **Read & Execute**
* **List folder contents**
* **Read**
* **Write**

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.png]]

The System Configuration utility (MSConfig) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues
The **Computer Management** (`compmgmt`) utility has three primary sections: **System Tools**, **Storage**, and **Services and Applications**.
**System Tools**

Let's start with **Task Scheduler**. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.

A task can run an application, a script, etc., and tasks can be configured to run at any point. A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule, for example, every five mins.

To create a basic task, click on `Create Basic Task` under **Actions** (right pane)

Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. This information is often used to diagnose problems and investigate actions executed on the system. 
Event Viewer has three panes.

1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above)
2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
3. The pane on the right is the actions pane.

There are five types of events that can be logged. Below is a table from [docs.microsoft.com](https://docs.microsoft.com/en-us/windows/win32/eventlog/event-types) providing a brief description for each.
![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.1.png]]
The standard logs are visible under **Windows Logs**. Below is a table from [docs.microsoft.com](https://docs.microsoft.com/en-us/windows/win32/eventlog/eventlog-key) providing a brief description for each.
![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.2.png]]
Windows Update is a service provided by Microsoft to provide security updates, feature enhancements, and patches for the Windows operating system and other Microsoft products, such as Microsoft Defender. 

Updates are typically released on the 2nd Tuesday of each month. This day is called **Patch Tuesday**. That doesn't necessarily mean that a critical update/patch has to wait for the next Patch Tuesday to be released. If the update is urgent, then Microsoft will push the update via the Windows Update service to the Windows devices.

**Tip**: Another way to access Windows Update is from the Run dialog box, or CMD, by running the command `control /name Microsoft.WindowsUpdate`.

## Active Directory

The main idea behind a domain is to centralise the administration of common components of a Windows computer network in a single repository called **Active Directory (AD)**. The server that runs the Active Directory services is known as a **Domain Controller (DC)**.

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.3.png]]
The main advantages of having a configured Windows domain are:

* **Centralised identity management:** All users across the network can be configured from Active Directory with minimum effort.
* **Managing security policies:** You can configure security policies directly from Active Directory and apply them to users and computers across the network as needed.

﻿The core of any Windows Domain is the **Active Directory Domain Service (AD DS)**. This service acts as a catalogue that holds the information of all of the "objects" that exist on your network. Amongst the many objects supported by AD, we have users, groups, machines, printers, shares and many others. Let's look at some of them:

**_Users_**

Users are one of the most common object types in Active Directory. Users are one of the objects known as **security principals**, meaning that they can be authenticated by the domain and can be assigned privileges over **resources** like files or printers. You could say that a security principal is an object that can act upon resources in the network.

Users can be used to represent two types of entities:

* **People:** users will generally represent persons in your organisation that need to access the network, like employees.
* **Services:** you can also define users to be used by services like IIS or MSSQL. Every single service requires a user to run, but service users are different from regular users as they will only have the privileges needed to run their specific service.

**_Machines_**

Machines are another type of object within Active Directory; for every computer that joins the Active Directory domain, a machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

The machine accounts themselves are local administrators on the assigned computer, they are generally not supposed to be accessed by anyone except the computer itself, but as with any other account, if you have the password, you can use it to log in.

**Note:** Machine Account passwords are automatically rotated out and are generally comprised of 120 random characters.

Identifying machine accounts is relatively easy. They follow a specific naming scheme. The machine account name is the computer's name followed by a dollar sign. For example, a machine named `DC01` will have a machine account called `DC01---
---
.

**_Security Groups_**

If you are familiar with Windows, you probably know that you can define user groups to assign access rights to files or other resources to entire groups instead of single users. This allows for better manageability as you can add users to an existing group, and they will automatically inherit all of the group's privileges. Security groups are also considered security principals and, therefore, can have privileges over resources on the network.

Groups can have both users and machines as members. If needed, groups can include other groups as well.

Several groups are created by default in a domain that can be used to grant specific privileges to users. As an example, here are some of the most important groups in a domain:

|     |     |
| --- | --- |
| **Security Group** | **Description** |
| Domain Admins | Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs. |
| Server Operators | Users in this group can administer Domain Controllers. They cannot change any administrative group memberships. |
| Backup Operators | Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers. |
| Account Operators | Users in this group can create or modify other accounts in the domain. |
| Domain Users | Includes all existing user accounts in the domain. |
| Domain Computers | Includes all existing computers in the domain. |
| Domain Controllers | Includes all existing DCs on the domain. |

To configure users, groups or machines in Active Directory, we need to log in to the Domain Controller and run "Active Directory Users and Computers" from the start menu. These objects are organised in **Organizational Units (OUs)** which are container objects that allow you to classify users and machines. OUs are mainly used to define sets of users with similar policing requirements.
It is very typical to see the OUs mimic the business' structure, as it allows for efficiently deploying baseline policies that apply to entire departments. Remember that while this would be the expected model most of the time, you can define OUs arbitrarily.
Windows creates automatically containers in Active Directory and those are:

* **Builtin:** Contains default groups available to any Windows host.
* **Computers:** Any machine joining the network will be put here by default. You can move them if needed.
* **Domain Controllers:** Default OU that contains the DCs in your network.
* **Users:** Default users and groups that apply to a domain-wide context.
* **Managed Service Accounts:** Holds accounts used by services in your Windows domain.

You are probably wondering why we have both groups and OUs. While both are used to classify users and computers, their purposes are entirely different:

* **OUs** are handy for **applying policies** to users and computers, which include specific configurations that pertain to sets of users depending on their particular role in the enterprise. Remember, a user can only be a member of a single OU at a time, as it wouldn't make sense to try to apply two different sets of policies to a single user.
* **Security Groups**, on the other hand, are used to **grant permissions over resources**. For example, you will use groups if you want to allow some users to access a shared folder or network printer. A user can be a part of many groups, which is needed to grant access to multiple resources.\\

### Delegation

One of the nice things you can do in AD is to give specific users some control over some OUs. This process is known as **delegation** and allows you to grant users specific privileges to perform advanced tasks on OUs without needing a Domain Administrator to step in.

One of the most common use cases for this is granting `IT support` the privileges to reset other low-privilege users' passwords. According to our organisational chart, Phillip is in charge of IT support, so we'd probably want to delegate the control of resetting passwords over the Sales, Marketing and Management OUs to him.

### Managing Computers in AD

While there is no golden rule on how to organise your machines, an excellent starting point is segregating devices according to their use. In general, you'd expect to see devices divided into at least the three following categories:

**1\. Workstations**
Workstations are one of the most common devices within an Active Directory domain. Each user in the domain will likely be logging into a workstation. This is the device they will use to do their work or normal browsing activities. These devices should never have a privileged user signed into them.

**2\. Servers**
Servers are the second most common device within an Active Directory domain. Servers are generally used to provide services to users or other servers.

**3\. Domain Controllers**
Domain Controllers are the third most common device within an Active Directory domain. Domain Controllers allow you to manage the Active Directory Domain. These devices are often deemed the most sensitive devices within the network as they contain hashed passwords for all user accounts within the environment.

### Group Policies

Windows manages such policies through **Group Policy Objects (GPO)**. GPOs are simply a collection of settings that can be applied to OUs. GPOs can contain policies aimed at either users or computers, allowing you to set a baseline on specific machines and identities.

To configure GPOs, you can use the **Group Policy Management** tool, available from the start menu.
The first thing you will see when opening it is your complete OU hierarchy, as defined before. To configure Group Policies, you first create a GPO under **Group Policy Objects** and then link it to the OU where you want the policies to apply. As an example, you can see there are some already existing GPOs in your machine:

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.4.png]]
you can also apply **Security Filtering** to GPOs so that they are only applied to specific users/computers under an OU. By default, they will apply to the **Authenticated Users** group, which includes all users/PCs.
The **Settings** tab includes the actual contents of the GPO and lets us know what specific configurations it applies. As stated before, each GPO has configurations that apply to computers only and configurations that apply to users only. In this case, the `Default Domain Policy` only contains Computer Configurations.

### GPO distribution

GPOs are distributed to the network via a network share called `SYSVOL`, which is stored in the DC. All users in a domain should typically have access to this share over the network to sync their GPOs periodically. The SYSVOL share points by default to the `C:\Windows\SYSVOL\sysvol\` directory on each of the DCs in our network.

Once a change has been made to any GPOs, it might take up to 2 hours for computers to catch up. If you want to force any particular computer to sync its GPOs immediately, you can always run the following command on the desired computer:

```
PS C:\> gpupdate /force
```

### 

## Authentication Methods

When using Windows domains, all credentials are stored in the Domain Controllers. Whenever a user tries to authenticate to a service using domain credentials, the service will need to ask the Domain Controller to verify if they are correct. Two protocols can be used for network authentication in windows domains:

* **Kerberos:** Used by any recent version of Windows. This is the default protocol in any recent domain.
* **NetNTLM:** Legacy authentication protocol kept for compatibility purposes.

### Kerberos Authentication

When Kerberos is used for authentication, the following process happens:

1. The user sends their username and a timestamp encrypted using a key derived from their password to the **Key Distribution Center (KDC)**, a service usually installed on the Domain Controller in charge of creating Kerberos tickets on the network.
	
	The KDC will create and send back a **Ticket Granting Ticket (TGT)**, which will allow the user to request additional tickets to access specific services. The need for a ticket to get more tickets may sound a bit weird, but it allows users to request service tickets without passing their credentials every time they want to connect to a service. Along with the TGT, a **Session Key** is given to the user, which they will need to generate the following requests.
	
	Notice the TGT is encrypted using the **krbtgt** account's password hash, and therefore the user can't access its contents. It is essential to know that the encrypted TGT includes a copy of the Session Key as part of its contents, and the KDC has no need to store the Session Key as it can recover a copy by decrypting the TGT if needed.
	

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.5.png]]

1. When a user wants to connect to a service on the network like a share, website or database, they will use their TGT to ask the KDC for a **Ticket Granting Service (TGS)**. TGS are tickets that allow connection only to the specific service they were created for. To request a TGS, the user will send their username and a timestamp encrypted using the Session Key, along with the TGT and a **Service Principal Name (SPN),** which indicates the service and server name we intend to access.
	
	As a result, the KDC will send us a TGS along with a **Service Session Key**, which we will need to authenticate to the service we want to access. The TGS is encrypted using a key derived from the **Service Owner Hash**. The Service Owner is the user or machine account that the service runs under. The TGS contains a copy of the Service Session Key on its encrypted contents so that the Service Owner can access it by decrypting the TGS.
	

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.6.png]]

1. The TGS can then be sent to the desired service to authenticate and establish a connection. The service will use its configured account's password hash to decrypt the TGS and validate the Service Session Key.

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.7.png]]

### NetNTLM Authentication

NetNTLM works using a challenge-response mechanism. The entire process is as follows:

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.8.png]]

1. The client sends an authentication request to the server they want to access.
2. The server generates a random number and sends it as a challenge to the client.
3. The client combines their NTLM password hash with the challenge (and other known data) to generate a response to the challenge and sends it back to the server for verification.
4. The server forwards the challenge and the response to the Domain Controller for verification.
5. The domain controller uses the challenge to recalculate the response and compares it to the original response sent by the client. If they both match, the client is authenticated; otherwise, access is denied. The authentication result is sent back to the server.
6. The server forwards the authentication result to the client.

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.8.png]]

1. The client sends an authentication request to the server they want to access.
2. The server generates a random number and sends it as a challenge to the client.
3. The client combines their NTLM password hash with the challenge (and other known data) to generate a response to the challenge and sends it back to the server for verification.
4. The server forwards the challenge and the response to the Domain Controller for verification.
5. The domain controller uses the challenge to recalculate the response and compares it to the original response sent by the client. If they both match, the client is authenticated; otherwise, access is denied. The authentication result is sent back to the server.
6. The server forwards the authentication result to the client.

Note that the user's password (or hash) is never transmitted through the network for security.Note that the user's password (or hash) is never transmitted through the network for security.

**Note:** The described process applies when using a domain account. If a local account is used, the server can verify the response to the challenge itself without requiring interaction with the domain controller since it has the password hash stored locally on its SAM.
**Note:** The described process applies when using a domain account. If a local account is used, the server can verify the response to the challenge itself without requiring interaction with the domain controller since it has the password hash stored locally on its SAM.

### Trees

### Trees

Active Directory supports integrating multiple domains so that you can partition your network into units that can be managed independently. If you have two domains that share the same namespace (ctive Directory supports integrating multiple domains so that you can partition your network into units that can be managed independently. If you have two domains that share the same namespace (`thm.localthm.local`
This partitioned structure gives us better control over who can access what in the domain. The IT people from the UK will have their own DC that manages the UK resources only. For example, a UK user would not be able to manage US users. In that way, the Domain Administrators of each branch will have complete control over their respective DCs, but not other branches' DCs. Policies can also be configured independently for each domain in the tree.
This partitioned structure gives us better control over who can access what in the domain. The IT people from the UK will have their own DC that manages the UK resources only. For example, a UK user would not be able to manage US users. In that way, the Domain Administrators of each branch will have complete control over their respective DCs, but not other branches' DCs. Policies can also be configured independently for each domain in the tree.
A new security group needs to be introduced when talking about trees and forests. TheA new security group needs to be introduced when talking about trees and forests. The **Enterprise AdminsEnterprise Admins** group will grant a user administrative privileges over all of an enterprise's domains. Each domain would still have its Domain Admins with administrator privileges over their single domains and the Enterprise Admins who can control everything in the enterprise group will grant a user administrative privileges over all of an enterprise's domains. Each domain would still have its Domain Admins with administrator privileges over their single domains and the Enterprise Admins who can control everything in the enterprise.

### Forests

The domains you manage can also be configured in different namespaces. Suppose your company continues growing and eventually acquires another company called `MHT Inc.` When both companies merge, you will probably have different domain trees for each company, each managed by its own IT department. The union of several trees with different namespaces into the same network is known as a **forest**.
![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.9.png]]

### Trust Relationships

### Forests

The domains you manage can also be configured in different namespaces. Suppose your company continues growing and eventually acquires another company called `MHT Inc.` When both companies merge, you will probably have different domain trees for each company, each managed by its own IT department. The union of several trees with different namespaces into the same network is known as a **forest**.
![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.9.png]]

### Trust Relationships

Having multiple domains organised in trees and forest allows you to have a nice compartmentalised network in terms of management and resources. But at a certain point, a user at Having multiple domains organised in trees and forest allows you to have a nice compartmentalised network in terms of management and resources. But at a certain point, a user at THM UK might need to access a shared file in one of MHT ASIA servers. For this to happen, domains arranged in trees and forests are joined together by THM UK might need to access a shared file in one of MHT ASIA servers. For this to happen, domains arranged in trees and forests are joined together by **trust relationships**.**trust relationships**.

In simple terms, having a trust relationship between domains allows you to authorise a user from domain In simple terms, having a trust relationship between domains allows you to authorise a user from domain `THM UK` to access resources from domain `THM UK` to access resources from domain `MHT EUMHT EU`..

The simplest trust relationship that can be established is a simplest trust relationship that can be established is a **one-way trust relationship**. In a one-way trust, if `Domain AAA` trusts `Domain BBB`, this means that a user on BBB can be authorised to access resources on AAA:**one-way trust relationship**. In a one-way trust, if `Domain AAA` trusts `Domain BBB`, this means that a user on BBB can be authorised to access resources on AAA:

![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.10.png]]![[Evernote/My Notes/_resources/Cyber_Security_101_-_TryHackMe.resources/image.10.png]]
The direction of the one-way trust relationship is contrary to that of the access direction.The direction of the one-way trust relationship is contrary to that of the access direction.

**Two-way trust relationshipsTwo-way trust relationships** can also be made to allow both domains to mutually authorise users from the other. By default, joining several domains under a tree or a forest will form a two-way trust relationship. can also be made to allow both domains to mutually authorise users from the other. By default, joining several domains under a tree or a forest will form a two-way trust relationship.

It is important to note that having a trust relationship between domains doesn't automatically grant access to all resources on other domains. Once a trust relationship is established, you have the chance to authorise users across different domains, but it's up to you what is actually authorised or not.It is important to note that having a trust relationship between domains doesn't automatically grant access to all resources on other domains. Once a trust relationship is established, you have the chance to authorise users across different domains, but it's up to you what is actually authorised or not.

# Command Line

# Command Line

## Windows Command Line

Before issuing commands, we should note that we can only issue the commands within the Windows Path. You can issue the command set to check your path from the command line.

## Windows Command Line

Before issuing commands, we should note that we can only issue the commands within the Windows Path. You can issue the command set to check your path from the command line.
Let’s use the **ver** command to determine the operating system (OS) version.Let’s use the **ver** command to determine the operating system (OS) version.
Let’s discover more in-depth information about the system. We can run the `systeminfo` command to list various information about the system such as OS information, system details, processor and memory. The terminal below shows a snippet of the displayed output.
Let’s discover more in-depth information about the system. We can run the `systeminfo` command to list various information about the system such as OS information, system details, processor and memory. The terminal below shows a snippet of the displayed output.
First, you can pipe it throughFirst, you can pipe it through `mormore` if the output is too long. Then, you can view it page after page by pressing the space bar button. To demonstrate this, try running `driverquery` and compare it with running `driverquery | more`. In the latter, you can display the output page by page and you can exit it using `CTRL + C`. if the output is too long. Then, you can view it page after page by pressing the space bar button. To demonstrate this, try running `driverquery` and compare it with running `driverquery | more`. In the latter, you can display the output page by page and you can exit it using `CTRL + C`.

* `help` - Provides help information for a specific command
* `cls` - Clears the Command Prompt screen.
* `help` - Provides help information for a specific command
* `cls` - Clears the Command Prompt screen.

### Network Troubleshooting

### Network Troubleshooting

One common troubleshooting task is checking if the server can access a particular server on the Internet. The command syntax isOne common troubleshooting task is checking if the server can access a particular server on the Internet. The command syntax is `ping target_nameping target_name`. Inspired by ping-pong, we send a specific ICMP packet and listen for a response. If a response is received, we know that we can reach the target and that the target can reach us.. Inspired by ping-pong, we send a specific ICMP packet and listen for a response. If a response is received, we know that we can reach the target and that the target can reach us.
Another valuable tool for troubleshooting is `tracert`, which stands for _trace route_. The command `tracert target_name` traces the network route traversed to reach the target. Without getting into more details, it expects the routers on the path to notify us if they drop a packet because its time-to-live (TTL) has reached zero.Another valuable tool for troubleshooting is `tracert`, which stands for _trace route_. The command `tracert target_name` traces the network route traversed to reach the target. Without getting into more details, it expects the routers on the path to notify us if they drop a packet because its time-to-live (TTL) has reached zero.
One networking command worth knowing is `nslookup`. It looks up a host or domain and returns its IP address. The syntax `nslookup` [example.com](https://example.com) will look up [example.com](https://example.com) using the default name server
One networking command worth knowing is `nslookup`. It looks up a host or domain and returns its IP address. The syntax `nslookup` [example.com](https://example.com) will look up [example.com](https://example.com) using the default name server

The final networking command we will cover in this room is`netstat`. This command displays current network connections and listening ports. A basic`netstat`command with no arguments will show you established connectionsThe final networking command we will cover in this room is`netstat`. This command displays current network connections and listening ports. A basic`netstat`command with no arguments will show you established connections
If you are curious about the other options, you can run `netstat -h`, where `-h` displays the help page. We opted for the following options:
If you are curious about the other options, you can run `netstat -h`, where `-h` displays the help page. We opted for the following options:

* `-a` displays all established connections and listening ports
* `-b` shows the program associated with each listening port and established connection
* `-o` reveals the process ID (PID) associated with the connection
* `-n` uses a numerical form for addresses and port numbers
* `-a` displays all established connections and listening ports
* `-b` shows the program associated with each listening port and established connection
* `-o` reveals the process ID (PID) associated with the connection
* `-n` uses a numerical form for addresses and port numbers

We combine these four options and execute theWe combine these four options and execute the `netstat -abonnetstat -abon` command.  command.

### Working Directories

### Working Directories

You can ususe `cdcd` without parameters to display the current drive and directory. It is the equivalent of asking the system, without parameters to display the current drive and directory. It is the equivalent of asking the system, _where am I?where am I?_

You can view the child directories usingcan view the child directories using `dirdir`..

Note that you can use the following options withNote that you can use the following options with `dirdir`::

* `dir /a` - Displays hidden and system files as well.
* `dir /s` - Displays files in the current directory and all subdirectories.
* `dir /a` - Displays hidden and system files as well.
* `dir /s` - Displays files in the current directory and all subdirectories.

You can type You can type `treeree` to visually represent the child directories and subdirectories. to visually represent the child directories and subdirectories.

You are working with the command line. You are curious about the contents of a particular text file. You can easily view text files with the command `type`. This command will dump the contents of the text file on the screen; this is convenient for files that fit within your terminal window. You might want to consider `more` for longer text files.

We can list the running processes using `tasklist`.

Some filtering is helpful because the output is expected to be very long. You can check all available filters by displaying the help page using `tasklist /?`. Let’s say that we want to search for tasks related to `sshd.exe`, we can do that with the command `tasklist /FI "imagename eq sshd.exe"`. Note that `/FI` is used to set the filter _image name equals_ `sshd.exe`.
With the process ID (PID) known, we can terminate any task using `taskkill /PID target_pid`.

* `chkdsk`: checks the file system and disk volumes for errors and bad sectors.
* `driverquery`: displays a list of installed device drivers.
* `sfc /scannow`: scans system files for corruption and repairs them if possible.

It is important to remember all the commands covered in the previous tasks; moreover, it is equally important to know that `/?` can be used with most commands to display a help page.

You are working with the command line. You are curious about the contents of a particular text file. You can easily view text files with the command `type`. This command will dump the contents of the text file on the screen; this is convenient for files that fit within your terminal window. You might want to consider `more` for longer text files.

We can list the running processes using `tasklist`.

Some filtering is helpful because the output is expected to be very long. You can check all available filters by displaying the help page using `tasklist /?`. Let’s say that we want to search for tasks related to `sshd.exe`, we can do that with the command `tasklist /FI "imagename eq sshd.exe"`. Note that `/FI` is used to set the filter _image name equals_ `sshd.exe`.
With the process ID (PID) known, we can terminate any task using `taskkill /PID target_pid`.

* `chkdsk`: checks the file system and disk volumes for errors and bad sectors.
* `driverquery`: displays a list of installed device drivers.
* `sfc /scannow`: scans system files for corruption and repairs them if possible.

It is important to remember all the commands covered in the previous tasks; moreover, it is equally important to know that `/?` can be used with most commands to display a help page.
