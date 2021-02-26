---
layout: post
title: Install And Config DHCP On CentOS Minimal
#subtitle: Excerpt from Soulshaping by Jeff Brown
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [books, test]
---
## 1.Install:
``` bash
yum install dhcpd
```
Check if dhcpd was installed in system:
```
dhcpd --version 
```
Allow dhcpd start with system startup
```
systemctl enable dhcpd
```
Directory structure of dhcpd:  
* **/etc/dhcp/dhcpd.conf**: The file config of dhcpd.  
* **/var/lib/dhcpd/dhcpd.lease**: The file contains information about dynamic IPs being granted via DHCP.  
* **/var/log/message**: The default log file of 4 way DHCP.  
## 2.Config DHCP Service:  
First, you can copy the existing sample configuration file to use for configuring the DHCP service.  
```
cp -f /usr/share/doc/dhcp-*/dhcpd.conf.example /etc/dhcp/dhcpd.conf
```
```
vi /etc/dhcp/dhcpd.conf
```
Configuration file content simple:
```
default-lease-time 600;
max-lease-time 7200;
lease-file-name "/var/lib/dhcpd/dhcpd.leases";
authoritative;
log-facility local7;
 
subnet 192.168.1.0 netmask 255.255.255.0 {
        range 192.168.1.100 192.168.1.200;
        default-lease-time 3600;
        max-lease-time 7200;
        option subnet-mask 255.255.255.0;
        option routers 192.168.1.1;
        option broadcast-address 192.168.1.255;
        option domain-name-servers 8.8.8.8;
}
```
## 3.Start DHCP and set rule firewall
```
systemctl start dhcpd
```
show status of dhcpd:  
```
systemctl status dhcpd
```
Open port 67 UDP:
```
iptables -A INPUT -p udp -m state --state NEW --dport 67 -j ACCEPT
```
If you use another firewall service you should research the way to open port 67 UDP in your system.  
Check if there is a DHCPd service that has been listened to socket port 67 udp.  
```
netstat -ulnp | grep 67
```
