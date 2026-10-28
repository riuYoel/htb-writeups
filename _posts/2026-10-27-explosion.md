---
title: "Explosion - HackTheBox"
date: 2026-10-27 12:00:00 +0200
categories: [Write-up, Starting Point, HackTheBox]
tags: [windows, easy, remote, VIP+]
pin: false
image:
  path: /assets/img/logos/fm-explosion.png
---

[Explosion](https://app.hackthebox.com/machines/Explosion){:target="_blank"}

## Task 1
### What does the 3-letter acronym RDP stand for?

RPD stands for `Remote Desktop Protocol` this protocol was developed by microsoft it allows a user to connect to another computer using the wifi and a GUI 

## Task 2
### What is a 3-letter acronym that refers to interaction with the host through a command line interface?

`CLI` (Command Line Interface) its a system that allows the user to interact with a program using lines of text

## Task 3
### What about graphical user interface interactions?

`GUI` while CLI is the text, GUI is the interface that we can see instead of writting

## Task 4
### What is the name of an old remote access tool that came without encryption by default and listens on TCP port 23?

`telnet` (Teletype Network) its an old protocol that allows the user to comunicate with another computer remotely using CLI

## Task 5
### What is the name of the service running on port 3389 TCP?

```shell
nmap <IP>
```

doing a quick and basic scan we can see the answer of this besides the port `ms-wbt-server`

## Task 6
### What is the switch used to specify the target host's IP address when using xfreerdp?

`/v:` to indicate the value /u: or /p: would be the user and password for example

## Task 7
### What username successfully returns a desktop projection to us with a blank password?

```shell
xfreerdp3 /v:<IP> /u:Administrator
```

Using `Administrator` which is the default if its not configured will allow us to enter without password

## Submit Single Flag
### Submit the flag located on the administrator's desktop.

![Image](/assets/img/writeups/p8.png)
