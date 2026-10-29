---
title: "Crocodile - HackTheBox"
date: 2026-10-29 17:00:00 +0200
categories: [Write-up, Starting Point, HackTheBox]
tags: [linux, easy, web, ftp]
pin: false
image:
  path: /assets/img/logos/fm-crocodile.png
---

[Crocodile](https://app.hackthebox.com/machines/Crocodile){:target="_blank"}

## Task 1
### What Nmap scanning switch employs the use of default scripts during a scan?

`-sC` means script default, this will allow the usage of scripts and it will show aditional information on the scans

## Task 2
### What service version is found to be running on port 21?

```shell
sudo nmap -p- -sS -sV --min-rate 5000 -T3 <IP>
```

After doing a quick scan we can see thanks to the switch -sV the version of the open port 23 which is `vsftpd 3.0.3`

## Task 3
### What FTP code is returned to us for the "Anonymous FTP login allowed" message?

```shell
ftp <IP>
```
After we enter as anonymous it will throw us the code `230` which means everything's OK

## Task 4
### After connecting to the FTP server using the ftp client, what username do we provide when prompted to log in anonymously?

`anonymous` is the classic standard if ftp has no configuration

## Task 5
### After connecting to the FTP server anonymously, what command can we use to download the files we find on the FTP server?

`get` is the command to transfer files outside the ftp client

## Task 6
### What is one of the higher-privilege sounding usernames in 'allowed.userlist' that we download from the FTP server?

its clearly `admin` the username tells us everything we want to know

## Task 7
### What version of Apache HTTP Server is running on the target host?

`Apache httpd 2.4.41` we have this info from our previous scan

## Task 8
### What switch can we use with Gobuster to specify we are looking for specific filetypes?

`-x` which stands for extension so its like telling gobuster we are looking for this specific extension or filetype

## Task 9
### Which PHP file can we identify with directory brute force that will provide the opportunity to authenticate to the web service?

![Image](assets/img/writeups/p17.png)

Here we can see the `login.php` this is interesting because before we had credentials, so after a little brute-force with the `admin` user and the `rKXM59ESxesUFHAd` password we are logged in

## Submit Single Flag
### Submit the flag located in the webpage.

![Image](assets/img/writeups/p18.png)

