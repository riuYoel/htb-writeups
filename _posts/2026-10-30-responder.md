---
title: "Responder - HackTheBox"
date: 2026-10-30 10:00:00 +0200
categories: [Write-up, Starting Point, HackTheBox]
tags: [windows, easy, web, http, responder, php]
pin: false
image:
  path: /assets/img/logos/fm-responder.png
---

[Responder](https://app.hackthebox.com/machines/Responder){:target="_blank"}

## Task 1
### When visiting the web service using the IP address, what is the domain that we are being redirected to?

![Image](/assets/img/writeups/p19.png)

For this one i used 

```shell
curl -I http://<IP>
```

which redirected me to `unika.htb`

## Task 2
### Which scripting language is being used on the server to generate webpages?

since we asked also for the headers in our previous command we can see its `php`

## Task 3
### What is the name of the URL parameter which is used to load different language versions of the webpage?

For this one we have to solve the name of the host in order to enter the page we can do the following steps

```shell
sudo nano /etc/hosts
```

![Image](/assets/img/writeups/p20.png)

Here we can add it and then go to the domain again and we will see that the page now loads 

![Image](/assets/img/writeups/p21.png)

Once we change the page language we can see the answer is `page`

## Task 4 
### Which of the following values for the page parameter would be an example of exploiting a Local File Include (LFI) vulnerability: "french.html", "//10.10.14.6/somefile", "../../../../../../../../windows/system32/drivers/etc/hosts", "mimikatz.exe"

`../../../../../../../../windows/system32/drivers/etc/hosts` LFI (Local File Inclusion) its when an web app gets the value of a parameter and adds it to the code to show an file in local server without validating the entrance, using Directory Traversal we can go up in directories in this case going down quickly to find sensitive files

## Task 5
### Which of the following values for the page parameter would be an example of exploiting a Remote File Include (RFI) vulnerability: "french.html", "//10.10.14.6/somefile", "./../../../../../../../windows/system32/drivers/etc/hosts", "mimikatz.exe"


`//10.10.14.6/somefile` its different from LFI bc it allows to load files or codes located in a external or remote server

## Task 6
### What does NTLM stand for?

`New Technology Lan Manager` developed for Microsoft they are protocols used to authenticate users and computers on Windows Networks

## Task 7 
### Which flag do we use in the Responder utility to specify the network interface?

`-I` or its longer version --interface

## Task 8
### There are several tools that take a NetNTLMv2 challenge/response and try millions of passwords to see if any of them generate the same response. One such tool is often referred to as john, but the full name is what?.

`John The Ripper` its one of the most popular tools of cracking in Cybersecurity

## Task 9
### What is the password for the administrator user?

`badminton` after getting the hash, we can use john the ripper to discover the password

```shell
 john --wordlist=<YourDirectory>/rockyou.txt hash.txt
```

## Task 10
### We'll use a Windows service (i.e. running on the box) to remotely access the Responder machine using the password we recovered. What port TCP does it listen on?

In our previous scan we can see its the port `5985`

## Task 11
### On which user's desktop is the flag located?

After connecting using

```shell
evil-winrm -i <IP> -u Administrator -p badminton
```

After exploring a bit if we use 
```shell
dir C:\users
type C:\Users\mike\Desktop\flag.txt
```

we can see its `mike`

## Submit Single Flag
### Submit the flag located on the mike user's desktop.

![Image](/assets/img/writeups/p22.png)
