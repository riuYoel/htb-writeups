---
title: "Preignition - HackTheBox Write-up"
date: 2026-10-27 13:00:00 +0200
categories: [Write-up, Starting Point, HackTheBox]
tags: [linux, easy, dir, gobuster, VIP+]
pin: false
image:
  path: /assets/img/logos/fm-preignition.png
---

[Preignition](https://app.hackthebox.com/machines/Preignition){:target="_blank"}

## Task 1
### Directory Brute-forcing is a technique used to check a lot of paths on a web server to find hidden pages. Which is another name for this? (i) Local File Inclusion, (ii) dir busting, (iii) hash cracking.

`dir busting` its basically a brute-force of directorys, you try a lot in a short amount of time using tools like Gobuster or ffuf

## Task 2
### What switch do we use for nmap's scan to specify that we want to perform version detection?

The switch `-sV`(Version Detection) gives us the versions included in the scans

## Task 3
### What does Nmap report is the service identified as running on port 80/tcp?

```shell
nmap <IP>
```
Running a basic scan we can see the service in this case `http`

## Task 4
### What server name and version of service is running on port 80/tcp?

```shell
nmap -p80- -sV <IP>
```
![Image](/assets/img/writeups/p9.png)

Using the sV we learned before we can see the version of the service `nginx 1.14.2`

## Task 5
### What switch do we use to specify to Gobuster we want to perform dir busting specifically?

`dir` is the main switch to perform dir busting

## Task 6
### When using gobuster to dir bust, what switch do we add to make sure it finds PHP pages?

`-x php` by using -x we tell gobuster to use the php extension

## Task 7 
### What page is found during our dir busting activities?

```
gobuster dir -u http://<IP> -w /usr/share/seclists/Discovery/Web-Content/common.txt -x php
```
![Image](/assets/img/writeups/p10.png)

Using this command we can see that gobuster finds us the `admin.php` page

## Task 8
### What is the HTTP status code reported by Gobuster for the discovered page?

As we saw clearly before its the status `200` which means there was no issues 

## Submit Single Flag
### Submit the flag located in the webpage.

Here we just have to enter the page `http://10.129.77.204/admin.php`

and use `admin` on user and password

![Image](/assets/img/writeups/p11.png)

