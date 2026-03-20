# OWASP Top 10 - 2021

# Info

- Author: Huan Phan Canh Dang
- Finished: 08/10/2025
- GitHub: harrybrwnie

# Overview

This room is an intermediate-level-hands-on lab focused on the Open Web Application Security Project (OWASP) Top 10 Vulnerabilities from the 2021 edition. OWASP is a global nonprofit organization that provides free resources to improve software security, and their Top 10 list represents a consensus on the most critical risks in web applications, based on data from thousands of applications and security experts

## Learning Objectives

- Understand the root causes of common web vulnerabilities and their impact on applications.
- Learn exploitation techniques using tools like Burp Suite, SQLMap, or manual methods.
- Gain insights into prevention strategies, such as secure coding practices and configuration hardening.
- Relate these risks to real-world breaches (e.g., data leaks from injection flaws or access control issues).

# Broken Access Control (IDOR Challenge)

## Question 1

![image.png](img/image.png)

Change the URL to 10.201.124.180/note.php?node-id=0 to get the flag.

![image.png](img/image%201.png)

![image.png](img/image%202.png)

# Cryptographic Failures Challenge

## Question 1

![image.png](img/image%203.png)

Open the source and check for a note, we can see the command told us that the answer is /assets

![image.png](img/image%204.png)

![image.png](img/image%205.png)

## Question 2

![image.png](img/image%206.png)

Access to /assets/ to see code inside and we can see webapp.db (likely the database)

![image.png](img/image%207.png)

![image.png](img/image%208.png)

## Question 3

![image.png](img/image%209.png)

Use our machine to get the webapp.db and has the permission to access and query

![image.png](img/image%2010.png)

Use some basic SQL knowledges to get a better understanding on the database and get the answer

![image.png](img/image%2011.png)

![image.png](img/image%2012.png)

## Question 4

![image.png](img/image%2013.png)

By using some online tool such as [crackstation.net](http://crackstation.net), copy the hash into it and get the plain password.

![image.png](img/image%2014.png)

![image.png](img/image%2015.png)

## Question 5

![image.png](img/image%2016.png)

Since we got the username and password, login as admin and get our flag

![image.png](img/image%2017.png)

![image.png](img/image%2018.png)

# Injection Challenge

## Question 1

![image.png](img/image%2019.png)

Use the ls command to get the information

![image.png](img/image%2020.png)

![image.png](img/image%2021.png)

## Question 2

![image.png](img/image%2022.png)

To define what user is this app running as, just use the command whoami

![image.png](img/image%2023.png)

![image.png](img/image%2024.png)

## Question 3

![image.png](img/image%2025.png)

Using command cat /etc/passwd to get the shell

![image.png](img/image%2026.png)

![image.png](img/image%2027.png)

## Question 4

![image.png](img/image%2028.png)

![image.png](img/image%2029.png)

Due to the hint, use the command cat /etc/alpine-release and get the answer

![image.png](img/image%2030.png)

![image.png](img/image%2031.png)

# Insecure Design Challenge

![image.png](img/image%2032.png)

Use the forgot password and guess the answer “What’s Joseph favourite color?”. Due to the limited amount of color, our mission is brute force all the answer. I found that the answer is green and got the permission to reset Joseph’s password.

![image.png](img/image%2033.png)

After had changed the password, loged in as Joseph and get the flag

![image.png](img/image%2034.png)

![image.png](img/image%2035.png)

![image.png](img/image%2036.png)

# Security Misconfiguration Challenge

![image.png](img/image%2037.png)

## Question 1

![image.png](img/image%2038.png)

Use the ls -l to get the answer

![image.png](img/image%2039.png)

## Question 2

![image.png](img/image%2040.png)

Use the cat [app.py](http://app.py) to get the answer

![image.png](img/image%2041.png)

![image.png](img/image%2042.png)

# Vulnerable and Outdated Components Challenge

## Question 1

![image.png](img/image%2043.png)

![image.png](img/image%2044.png)

Accessed to the URL and see that this is the web about “Online CSE bookstore”. By google that phrase we got the exploit

[https://www.exploit-db.com/exploits/47887](https://www.exploit-db.com/exploits/47887)

Get the script, change permission for executive and we get the RCE in our shell. Then cat the flag

![image.png](img/image%2045.png)

![image.png](img/image%2046.png)

![image.png](img/image%2047.png)

# Identification and Authentication Failures Challenge

## Question 1

![image.png](img/image%2048.png)

Accessed to the web and register with the username “ darren” (there is a blank on first character), Due to the vulnerability, we get access to “darren” account (no blank on first character) and get the flag

![image.png](img/image%2049.png)

![image.png](img/image%2050.png)

![image.png](img/image%2051.png)

![image.png](img/image%2052.png)

## Question 2

![image.png](img/image%2053.png)

Use same method as question 1 and get the flag

![image.png](img/image%2054.png)

![image.png](img/image%2055.png)

# Data Integrity Failures Challenge

## Question 1

![image.png](img/image%2056.png)

The web provides the information that username is guest and password is guest too.

![image.png](img/image%2057.png)

![image.png](img/image%2058.png)

## Question 2

![image.png](img/image%2059.png)

Right click onto the website and click on the Inspect tab. Go into the Application then Cookies sub-tab we can observer the name is “jwt-session”

![image.png](img/image%2060.png)

![image.png](img/image%2061.png)

## Question 3

![image.png](img/image%2062.png)

Use burpsuite to intercept request and use some online tools to decode and modify jwt such as [https://fusionauth.io/dev-tools/jwt-decoder](https://fusionauth.io/dev-tools/jwt-decoder). Then we modify the request by Burpsuite. Change the alg to none and username is admin. Get the jwt-token after being modified and sent to server to get access with admin permission

![image.png](img/image%2063.png)

![image.png](img/image%2064.png)

![image.png](img/image%2065.png)

![image.png](img/image%2066.png)

![image.png](img/image%2067.png)

![image.png](img/image%2068.png)

# Security Logging and Monitoring Failures Challenge

## Question 1

![image.png](img/image%2069.png)

In this challenge, we have provided the log.txt to investigate. Due to the log we can see an IP for attacker

![image.png](img/image%2070.png)

![image.png](img/image%2071.png)

## Question 2

![image.png](img/image%2072.png)

Cause several times trying to access the server, kind of attack is likely “brute force”

![image.png](img/image%2073.png)

# Server-Side Request Forgery Challenge

## Question 1

![image.png](img/image%2074.png)

After explore the website, we can easily get the answer

![image.png](img/image%2075.png)

![image.png](img/image%2076.png)

## Question 2

![image.png](img/image%2077.png)

Use the Download Resume on the Web and use Burpsute to catch the request and we observed the server

![image.png](img/image%2078.png)

![image.png](img/image%2079.png)

## Question 3

![image.png](img/image%2080.png)

Use our machine as as server and looking for any connection on port 444 by the command nc

Then use Burpsuite to modified the request to our server. Forward the request and get the flag

![image.png](img/image%2081.png)

![image.png](img/image%2082.png)

![image.png](img/image%2083.png)