# Hydra

# Info

- Author: Huan Phan Canh Dang
- Finish: 08/11/2025
- GitHub: harrybrwnie

# Overview

The Hydra room is a beginner-friendly, hands-on lab focused on using Hydra, a fast and flexible password-cracking tool, to perform brute-force attacks on network services. It is a part of the compTIA Pentest+ learning path, making it ideal for those starting in penetration testing. The room teaches you how to use Hydra to crack credentials for services like HTTP forms and SSH, emphasizing ethnical hacking in controlled environment. It is rated as easy and typically takes 2-4 hours to complete, depending on your familiarity with Linux and brute-forcing concepts.

# Learning Objectives

Learn to use Hydra to brute-force credentials for a web login form and an SSH service, capturing flags to demonstrate success. The room provides practical experience with password guessing at scale, a key skill for identifying weak credentials (aligned with OWASP’s A07:2021 - Identification and Authentication Failures).

# Question 1

Go to the website and observe that there is a form /login. Then try to use Hydra to brute force the password using the rockyou.txt as wordlist

![image.png](img/image.png)

![image.png](img/image%201.png)

Wait for a little bit and get the molly password is sunshine. Then login with the username as molly and password is sunshine and then we be able to get into the website and get the flag

![image.png](img/image%202.png)

![image.png](img/image%203.png)

![image.png](img/image%204.png)

![image.png](img/image%205.png)

## Question 2

![image.png](img/image%206.png)

Trying to use Hydra to brute force the password (SSH Protocol)

Wait for a little bit and get the password is butterfly

![image.png](img/image%207.png)

Login to ssh as molly and password is butterfly and get the password

![image.png](img/image%208.png)

![image.png](img/image%209.png)

![image.png](img/image%2010.png)