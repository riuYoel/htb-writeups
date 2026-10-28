---
title: "Appointment - HackTheBox"
date: 2026-10-28 17:00:00 +0200
categories: [Write-up, Starting Point, HackTheBox]
tags: [linux, easy, sql, web, gobuster]
pin: false
image:
  path: /assets/img/logos/fm-appointment.png
---

[Appointment](https://app.hackthebox.com/machines/Appointment){:target="_blank"}

## Task 1
### What does the acronym SQL stand for?

It means `Structured Query Language`, structured means that the information is inside DBs in a organizated way in tables. Query because we can ask for that information

## Task 2
### What is one of the most common type of SQL vulnerabilities?

The most common type of SQL vulnerability is `SQL injection`

## Task 4 (Here i noticed theres not Task 3)
### What is the 2021 OWASP Top 10 classification for this vulnerability?

If we search the OWASP Top 10 of 2021 we can see its `A03:2021-Injection`

## Task 5
### What does Nmap report as the service and version that are running on port 80 of the target?

```shell
sudo nmap -sV -p80- <IP>
```

With this basic scan we can see the version thanks to the sV swhich

## Task 6
### What is the standard port used for the HTTPS protocol?

`443` meanwhile the port 80 is for HTTP

## Task 7
### What is a folder called in web-application terminology?

Its called `directory` for example when we do fuzzing

## Task 8
### What is the HTTP response code that is returned for Not Found errors?

`404` since always (4xx and 3xx) are related to errors

## Task 9
### Gobuster is one tool used to brute force directories on a webserver. What switch do we use with Gobuster to specify we're looking to discover directories, and not subdomains?

`dir` which stands for directories

## Task 10
### What single character can be used to comment out the rest of a line in MySQL?

`#` same as in a lot of programming languages

## Task 11
### If user input is not handled carefully, it could be interpreted as a comment. Use a comment to login as admin without knowing the password. What is the first word on the webpage returned?

Here we have to go onto the page and on the username we have to do `admin'#` and the rest will be taken as a comment, inside the page we will login and there will be the `Congratulations`! text and the flag

## Submit Single Flag
### Submit the flag located in the webpage after bypassing the login.

![Image](/assets/img/writeups/p15.png)
