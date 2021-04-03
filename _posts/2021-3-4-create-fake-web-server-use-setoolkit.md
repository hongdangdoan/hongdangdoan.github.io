---
layout: post
title: Man In The Middle Attack - DNS Spoofing Part 1   
subtitle: Part 1: Create Fake Web Server Include Malicious Code
categories: Hacking-Lab
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [hacking, dnsspoof, redirect dns, dns spoofing, mitmd ]
---


## 1. Social Engineering Tool Kit (SET): 

SET is an open source, free Python cybersecurity tool used by security researchers, penetration testers, blue and purple teams from around the world.  
Instead of targeting apps, SET uses humans as the main target of its attack techniques.  
Social engineering attack options such as Spear-Phishing Attacks, Website Attacks, Infection Media Generator, Mass Mailing, Arduino-Based Attack,  
QRCode Attacks, Powershell Attack Vectors, and much more.  

**Web Attack**: This module combines different options for attacking your victim to compromise the remote victim. It includes attack techniques such as  
Java Applet Attack and Metasploit Browser Exploit to deliver malicious payloads. Also handy is the Credential Harvester method, which lets you clone   
a website and harvest the information from user and password fields, as well as the TabNabbing, HTA Attack, Web-Jacking and Multi-Attack techniques,   
all with the same goal of tricking end users into revealing their credentials.  

**Phishing Attacks:** This option allows you to choose from several phishing attack options to help you decide how to approach your victim. You can craft  
email messages with malicious payloads attached, and send them to a small or large number of recipients.  

## 2. Installation:  

```
git clone https://github.com/trustedsec/social-engineer-toolkit/ set/
cd set
pip install -r requirements.txt  
```  

## 3. Use SET To Create Fake Web Server:  

In the web attack module of SET, it includes the function of creating a fake web server by cloning from the website source code of the real server.   
Source code saved at */var/www/html/* if you use apache server for default. To do that, please see more at [here](https://www.youtube.com/watch?v=l_vpr0TS5_E)  
After we have the source code of the website, we need to add some exploit code. After that, you should start you web server and wait for a connection from anyone.  
```
service apache2 start 
```  

## 4. Protection From Attack:  

Usually DNS spoofing attacks are carried out inside the LAN, so make sure the network devices are secure.  
Uses intrusion detection systems.  
Use DNSSEC instead of DNS.  
For network users:  
* Do not access strange links.  
* Use anti-virus software.  

### Watch the instructional video at [here](https://www.youtube.com/watch?v=LM_wO-42qS0)

