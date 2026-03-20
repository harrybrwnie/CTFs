# SQL Map

# Info

- Author: Phan Dang Canh Huan
- Finish: 08/12/2025
- GitHub: harrybrwnie

# Overview

The SQLMap: The Basics room on TryHackMe is part of the Cyber Security 101 learning path, designed for beginners to learn about SQL injection and how to use SQLMap, an open-source tool for automating the detection and exploitation of SQL injection vulnerabilities in web applications.

# Learning Objectives

- Understand SQL injection vulnerabilities and how they allow attackers to manipulate database queries
- Learn to use SQLMap to automate SQL Injection testing, including enumerating databases, tables and data
- Apply SQLMap to practical scenarios to extract information from vulnerable web applications
- Gain insight into securing web applications against SQL Injection

# Question 1

![image.png](img/image.png)

Access to the URL and observe that is the website about the “CHATAI” and has a form to login.

![image.png](img/image%201.png)

By Inspect the website and sent a test form we can see that the GET Method

![image.png](img/image%202.png)

Using the SQL map and that URL to get the answer

- ai
- information_schema
- mysql
- performance_schema
- phpmyadmin
- test

```python
http://10.201.52.63/ai/inclues/user_login?email=test&password=test
```

![image.png](img/image%203.png)

![image.png](img/image%204.png)

The result show that there are 6 databases

![image.png](img/image%205.png)

# Question 2

![image.png](img/image%206.png)

By using the command below, we get the information about the ai database

![image.png](img/image%207.png)

![image.png](img/image%208.png)

The result show that there is 1 table which named “user”

![image.png](img/image%209.png)

# Question 3

![image.png](img/image%2010.png)

Using the command below to observe the content in user table

![image.png](img/image%2011.png)

![image.png](img/image%2012.png)

The result show that there is 1 instance has some attributes as

- id = 1
- email = test@chatai.com
- created = 2023-02-21 09:05:46
- password = 12345678

![image.png](img/image%2013.png)