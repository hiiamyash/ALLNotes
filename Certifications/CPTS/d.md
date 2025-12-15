
![](../../attchments/Pasted%20image%2020251213162646.png)

The concept is based on four categories that occur for each vulnerability. First, we have a `Source` that performs the specific request to a `Process` where the vulnerability gets triggered. Each process has a specific set of `Privileges` with which it is executed. Each process has a task with a specific goal or `Destination` to either compute new data or forward it. However, the individual and unique specifications under these categories may differ from service to service.

Every task and piece of information follows a specific pattern, a cycle, which we have deliberately made linear. This is because the `Destination` does not always serve as a `Source` and is therefore not treated as a source of a new task.

For any task to come into existence at all, it needs an idea, information (`Source`), a planned process for it (`Processes`), and a specific goal (`Destination`) to be achieved. Therefore, the category of `Privileges` is necessary to control information processing appropriately.


#### Initiation of the Attack

|**Step**|**Log4j**|**Concept of Attacks - Category**|
|---|---|---|
|`1.`|The attacker manipulates the user agent with a JNDI lookup command.|`Source`|
|`2.`|The process misinterprets the assigned user agent, leading to the execution of the command.|`Process`|
|`3.`|The JNDI lookup command is executed with administrator privileges due to logging permissions.|`Privileges`|
|`4.`|This JNDI lookup command points to the server created and prepared by the attacker, which contains a malicious Java class containing commands designed by the attacker.|`Destination`|

This is when the cycle starts all over again, but this time to gain remote access to the target system.

#### Trigger Remote Code Execution

|**Step**|**Log4j**|**Concept of Attacks - Category**|
|---|---|---|
|`5.`|After the malicious Java class is retrieved from the attacker's server, it is used as a source for further actions in the following process.|`Source`|
|`6.`|Next, the malicious code of the Java class is read in, which in many cases has led to remote access to the system.|`Process`|
|`7.`|The malicious code is executed with administrator privileges due to logging permissions.|`Privileges`|
|`8.`|The code leads back over the network to the attacker with the functions that allow the attacker to control the system remotely.|



