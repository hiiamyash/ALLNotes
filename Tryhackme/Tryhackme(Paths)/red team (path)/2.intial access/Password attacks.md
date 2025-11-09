Weak Passwords  
Professionals collect and generate weak password lists over time and often combine them into one large wordlist. Lists are generated based on their experience and what they see in pentesting engagements. These lists may also contain leaked passwords that have been published publically. Here are some of the common weak passwords lists :

- [https://wiki.skullsecurity.org/index.php?title=Passwords](https://wiki.skullsecurity.org/index.php?title=Passwords)[](https://wiki.skullsecurity.org/index.php?title=Passwords) - This includes the most well-known collections of passwords.
- [SecLists](https://github.com/danielmiessler/SecLists/tree/master/Passwords) - A huge collection of all kinds of lists, not only for password cracking.

### Leaked Passwords

Sensitive data such as passwords or hashes may be publicly disclosed or sold as a result of a breach. These public or privately available leaks are often referred to as 'dumps'. Depending on the contents of the dump, an attacker may need to extract the passwords out of the data. In some cases, the dump may only contain hashes of the passwords and require cracking in order to gain the plain-text passwords. The following are some of the common password lists that have weak and leaked passwords, including webhost, elitehacker,hak5, Hotmail, PhpBB companies' leaks:  

- [SecLists/Passwords/Leaked-Databases](https://github.com/danielmiessler/SecLists/tree/master/Passwords/Leaked-Databases)

### Customized Wordlists

Tools such as Cewl can be used to effectively crawl a website and extract strings or keywords. Cewl is a powerful tool to generate a wordlist specific to a given company or target. Consider the following example below:

```
user@thm$ cewl -w list.txt -d 5 -m 5 http://thm.labs
```

-w will write the contents to a file. In this case, list.txt.

-m 5 gathers strings (words) that are 5 characters or more

-d 5 is the depth level of web crawling/spidering (default 2)

http://thm.labs is the URL that will be used

As a result, we should now have a decently sized wordlist based on relevant words for the specific enterprise, like names, locations, and a lot of their business lingo. Similarly, the wordlist that was created could be used to fuzz for usernames. 

Apply what we discuss using cewl against https://clinic.thmredteam.com/ to parse all words and generate a wordlist with a minimum length of 8. Note that we will be using this wordlist later on with another task!


### Username Wordlists

there is a tool username_generator that could help create a list with most of the possible combinations if we have a first name and last name.

```
user@thm$ git clone https://github.com/therodri2/username_generator.git
```

```
user@thm$ python3 username_generator.py -h usage: username_generator.py [-h] -w wordlist [-u]  Python script to generate user lists for bruteforcing!  optional arguments:   -h, --help            show this help message and exit   -w wordlist, --wordlist wordlist                         Specify path to the wordlist   -u, --uppercase       Also produce uppercase permutations. Disabled by default
```

### CUPP - Common User Passwords Profiler

CUPP is an automatic and interactive tool written in Python for creating custom wordlists. For instance, if you know some details about a specific target, such as their birthdate, pet name, company name, etc., this could be a helpful tool to generate passwords based on this known information. CUPP will take the information supplied and generate a custom wordlist based on what's provided. There's also support for a 1337/leet mode, which substitutes the letters a, i,e, t, o, s, g, z  with numbers. For example, replace a  with 4  or i with 1. For more information about the tool, please visit the GitHub repo [here](https://github.com/Mebus/cupp).

To run CUPP, we need python 3 installed. Then clone the GitHub repo to your local machine using git as follows:

```
user@thm$  git clone https://github.com/Mebus/cupp.git
```

```
user@thm$  python3 cupp.py -i
```

