---
layout: post
title: How To Use Nmap
categories: Hacking-Lab
#subtitle: Excerpt from Soulshaping by Jeff Brown
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [nmap, hacking]
---
Before attempting to attack a particular system it is essential to first understand the network model of the target system.  
This is intended to identify the system's critical servers and vulnerable services. There are many tool to do this, but you can  
use nmap.  
## 1. Determine The Active Hosts:  
First you should netmask of the target system.    
```
ifconfig  
```  
![](/assets/img/How-To-Use-Nmap/ifconfig.png)  
You can see the nestmask of target system is *192.168.1.0/24*  
Use  
```
nmap -PR 192.168.1.0/24
```  
-PR send packet ping ARP  

![](/assets/img/How-To-Use-Nmap/nmap-PR.png) 

But option PR will scan port of target so it spend many time.  
Use option -sn(no port scan) to shorten scan time.  

![](/assets/img/How-To-Use-Nmap/nmap-PR-sn.png)  
## 2.Get Server Information When Knowing Ip:  

get version OS  
```
nmap -O 192.168.111.8
```   
![](/assets/img/How-To-Use-Nmap/nmap-O.png)  

You can see some services are running and their port.
Get version of service is running in system target   
```
nmap -sV -p 21 192.168.111.8
```  

![](/assets/img/How-To-Use-Nmap/nmap-sV-p.png)  
