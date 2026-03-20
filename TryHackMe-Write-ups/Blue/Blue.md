# Blue

# Info

- Author: Huan Phan Canh Dang
- Finish: 08/08/2025
- GitHub: harrybrwnie

# Overview

In the Blue room, you’ll deploy and hack a Windows machine by leveraging common misconfigurations. This isn’t boot-to-root challenge but a beginner-focused, guided exercises idea for reinforcing foundational penetration testing skills

## Learning Objectives

- Reconnaissance: & Enumeration: Identify open ports, services and versions using Nmap and manual exploration
- Vulnerability Exploitation: Utilize the EternalBlue (MS17-010) SMB vulnerability using Metasploit
- Post-Exploitation: Gain a shell, upgrade it to a Meterpreter session, migrate to stable processes, escalate privileges, and extract sensitive data (password hashed, flags)

This room covers the essentials stages of Window pentesting:

- Scanning & Enumeration
- Exploitation via Metasploit
- Privilege Escalation & Credential Dumping
- Pursuing In-Game Flags

# Recon

![image.png](img/image.png)

## Question 1

![image.png](img/image%201.png)

![image.png](img/image%202.png)

## Question 2

![image.png](img/image%203.png)

The nmap result above show that there are 3 ports under 1000 that are running

- 135/tcp
- 139/tcp
- 445/tcp

So the answer is 3

![image.png](img/image%204.png)

## Question 3

![image.png](img/image%205.png)

![image.png](img/image%206.png)

The nmap result also show that there is a vulnerable machine MS17-010

![image.png](img/image%207.png)

# Gain Access

## Question 1

![image.png](img/image%208.png)

We can use the Metasploit Framework by using the msfconsole command

## Question 2

![image.png](img/image%209.png)

We can use the search command in Metasploit to find out what exploit module want to ultilize

![image.png](img/image%2010.png)

There are 2 available modules but due to the vulnerable machine we found on question 1.  The nmap has mentioned about the SMB Server so that it is likely that we will use the exploit/windows/smb/ms17_010_eternalblue.

![image.png](img/image%2011.png)

## Question 3

![image.png](img/image%2012.png)

![image.png](img/image%2013.png)

According to the show options command, we need to set up the RHOSTS parameter (stand for Remote Hosts). The target’s IP is 10.201.69.192 so we use the set command to set it up

![image.png](img/image%2014.png)

![image.png](img/image%2015.png)

## Question 4

![image.png](img/image%2016.png)

![image.png](img/image%2017.png)

## Question 5

![image.png](img/image%2018.png)

![image.png](img/image%2019.png)

After run that module, we get access to the shell.

# Escalate

## Question 1

![image.png](img/image%2020.png)

We use the background command to background our current session and “upgrade” it to the meterpreter by using the sessions -u command

![image.png](img/image%2021.png)

![image.png](img/image%2022.png)

## Question 2

![image.png](img/image%2023.png)

Change to the post/multi/manage/shell_to_meterpreter module and show options

![image.png](img/image%2024.png)

We can see the session parameter is required and we already the session that are running (we had background it before). So that we assign that value for the SESSION parameter

![image.png](img/image%2025.png)

![image.png](img/image%2026.png)

## Question 3

![image.png](img/image%2027.png)

## Question 4

![image.png](img/image%2028.png)

## Question 5

![image.png](img/image%2029.png)

## Question 6

![image.png](img/image%2030.png)

![image.png](img/image%2031.png)

## Question 7

![image.png](img/image%2032.png)

![image.png](img/image%2033.png)

## Question 8

![image.png](img/image%2034.png)

![image.png](img/image%2035.png)

Because in the Metasploit:Meterpreter room, I had migrate to the lsass.exe process and success so in this room I also choose this process and migrate to it

# Cracking

## Question 1

![image.png](img/image%2036.png)

After migrate to the lsass.exe, we use the hashdump command and observe that “Jon” is the user

![image.png](img/image%2037.png)

![image.png](img/image%2038.png)

## Question 2

![image.png](img/image%2039.png)

Use the online tool such as [crackstation.net](http://crackstation.net) to crack the hash password of Jon

![image.png](img/image%2040.png)

We can see the actual password and answer this question.

![image.png](img/image%2041.png)

# Find flag!

## Question 1

![image.png](img/image%2042.png)

![image.png](img/image%2043.png)

Use the pwd command and see that we are at C:\Windows\system32, cd .. twice to get to the C:\ and type the ls to show all directory and files and get the flag1.txt. The only mission now is cat this file

![image.png](img/image%2044.png)

![image.png](img/image%2045.png)

![image.png](img/image%2046.png)

## Question 2

![image.png](img/image%2047.png)

I had asked ChatGPT where password are stored within Windows and get the path is C:\\Windows\System32\config. So I cd to that and ls and see the flag

![image.png](img/image%2048.png)

![image.png](img/image%2049.png)

![image.png](img/image%2050.png)

![image.png](img/image%2051.png)

## Question 3

![image.png](img/image%2052.png)

![image.png](img/image%2053.png)

Simplify the process by using the search command, I can see the both 2 previous flags has the name of rules (flag1.txt, flag2.txt for example). So that in this question I only search for the flag3.txt and find out where it is and cat it out to get the answer.

![image.png](img/image%2054.png)

![image.png](img/image%2055.png)