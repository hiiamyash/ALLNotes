
he file system used in modern versions of Windows is the **New Technology File System** or simply [NTFS](https://docs.microsoft.com/en-us/windows-server/storage/file-server/ntfs-overview).

Before NTFS, there was **FAT16/FAT32** (File Allocation Table) and **HPFS** (High Performance File System).

Alternate Data Streams (ADS) is a file attribute specific to Windows NTFS (New Technology File System).

what is ADS?
what are data steams in ads



<h3>The Windows\System32 Folders</h3>
the system  environment variable for the Windows directory is `%windir%`.
The System32 folder holds the important files that are critical for the operating system.

<h3>User Accounts, Profiles, and Permissions</h3>

User accounts can be one of two types on a typical local Windows system: **Administrator** & **Standard User**.

The location for each user profile folder will fall under is C:\Users.

Each group has permissions set to it, and users are assigned/added to groups by the Administrator. When a user is assigned to a group, the user inherits the permissions of that group. A user can be assigned to multiple groups.

<h3>**User Account Control** (UAC)</h3>
How does UAC work? When a user with an account type of administrator logs into a system, the current session doesn't run with elevated permissions. When an operation requiring higher-level privileges needs to execute, the user will be prompted to confirm if they permit the operation to run

![[../../../attchments/Pasted image 20241204140413.png]]


<h1>Windows Fundamental 2</h1>

<h3>introduction</h3>

<h4>Change UAC Settings</h4>
![[Pasted image 20241204143121.png]]

<h3>Computer Management</h3>
We're continuing with Tools that are available through the System Configuration panel.  

The **Computer Management** (`compmgmt`) utility has three primary sections: System Tools, Storage, and Services and Applications.

**System Tools**(it's like an cronjob)

Let's start with **Task Scheduler**. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.

**Event Viewer**.

Event Viewer allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system

![[../../../attchments/Pasted image 20241204143931.png]]
![[../../../attchments/Pasted image 20241204144035.png]]

regisrty se logs


**Shared Folders** is where you will see a complete list of shares and folders shared that others can connect to. 

![](https://assets.tryhackme.com/additional/win-fun2/shared-folders.png)

in **Performance**, you'll see a utility called **Performance Monitor** (`perfmon`).

Perfmon is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote.

**Device Manager** allows us to view and configure the hardware, such as disabling any hardware attached to the computer.

![](https://assets.tryhackme.com/additional/win-fun2/device-mgr.png)

**Services and Applications**

![](https://assets.tryhackme.com/additional/win-fun2/services-apps.png)  

Recall from the previous task; a service is a special type of application that runs in the background. Here you can do more than enable and disable a service, such as view the Properties for the service.


<h3>System information</h3>

We're continuing with Tools that are available through the System Configuration panel.  

What is the **System Information** (`msinfo32`) tool


_windows includes a tool called Microsoft System Information (Msinfo32.exe).  This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues_

The  information in **System Summary** is divided into three sections:

- **Hardware Resources**
- **Components**
- **Software Environment**

In the **Software Environmen**t section, you can see information about software baked into the operating system and software you have installed. Other details are visible in this section as well, such as the **Environment Variables** and **Network Connections**. 

![](https://assets.tryhackme.com/additional/win-fun2/software-env.png)

Click on `Environment Variables` to see the assigned values for the virtual machine.

![](https://assets.tryhackme.com/additional/win-fun2/env-variables.png)





<h3>Resource Monitor</h3>


We're continuing with Tools that are available through the System Configuration panel.  

What is **Resource Monitor** (`resmon`)?


_Resource Monitor displays per-process and aggregate CPU, memory, disk, and network usage information, in addition to providing details about which processes are using individual file handles and modules._

Resmon has four sections:

- **CPU**
- **Disk**
- **Network**
- **Memory**

![](https://assets.tryhackme.com/additional/win-fun2/resmon1.png)


<h3>Command Prompt</h3>
commands, such as `hostname` and `whoami`.

The command **hostname** will output the computer name.

![](https://assets.tryhackme.com/additional/win-fun2/hostname.png)  

The command **whoami** will output the name of the logged-in user.

![](https://assets.tryhackme.com/additional/win-fun2/whoami.png)

A command used often is `ipconfig`. This command will show the network address settings for the computer.

![](https://assets.tryhackme.com/additional/win-fun2/ipconfig.png)

A  command to retrieve the help manual for a command is `/?`.

the help manual for **ipconfig**, you can use the following command: `ipconfig /?`


next command is `netstat`. Per the help manual, this command will display protocol statistics and current TCP/IP network connections. 

![](https://assets.tryhackme.com/additional/win-fun2/netstat.png)  

In the above image, the line within the red box shows us an example syntax for the command. 

The structure tells us the **netstat** command can be run alone or with parameters, such as `-a`,  `-b`,  `-e`, etc.



<h3>Registry Editor</h3>

We're continuing with Tools that are available through the System Configuration panel.  

The **Windows Registry** (per Microsoft) is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices.


<h1>Windows fundaments 3</h1>

<h3>Windows update</h3>
Another way to access Windows Update is from the Run dialog box, or CMD, by running the command `control /name Microsoft.WindowsUpdat`

<h3>Windows Security</h3>

In case you missed it, **Windows Security** is also available in **Settings**. 

![](https://assets.tryhackme.com/additional/win-fun3/windows-security.png)  

In the above image, focus your attention on **Protection areas**.

- **Virus & threat protection**
- **Firewall & network protection**
- **App & browser control**
- **Device security**

<h3>Firewall & network protection</h3>

Per Microsoft, "_Windows Firewall offers three firewall profiles: domain, private and public"._

- **Domain** - _The domain profile applies to networks where the host system can authenticate to a domain controller._ 
- **Private** - _The private profile is a user-assigned profile and is used to designate private or home networks._
- **Public** - _The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations._

Command to open the Windows Defender Firewall is 
```WF.msc```


<h3>Volume Shadow Copy Service</h3>

Per [Microsoft](https://docs.microsoft.com/en-us/windows-server/storage/file-server/volume-shadow-copy-service), the Volume Shadow Copy Service (VSS) coordinates the required actions to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up. 

Volume Shadow Copies are stored on the System Volume Information folder on each drive that has protection enabled.  

If VSS is enabled (**System Protection** turned on), you can perform the following tasks from within **advanced system settings**. 

- **Create a restore point**
- **Perform system restore**
- **Configure restore settings**
- **Delete restore points**

From a security perspective, malware writers know of this Windows feature and write code in their malware to look for these files and delete them. Doing so makes it impossible to recover from a ransomware attack unless you have an offline/off-site backup.


