---
title: "DNS"
date: "2024-06-05"
author: ["Luiz Felipe"]
categories: 
- network
weight: # 1 means pin the article, sort articles according to this number
slug: ""
draft: false # draft or not
comments: false
showToc: true # show contents
TocOpen: false # open contents automantically
hidemeta: false # hide information (author, create date, etc.)
disableShare: false	# do not show share button
showbreadcrumbs: true # show current path
---



### What is DNS?
The DNS (Domain Name System) converts human-readable domain names into machine-readable IP addresses.


All devices on the internet use unique numerical addresses assigned to each one to locate and communicate with each other. These numbers are known as IP addresses. An IP address can be something like 192.168.100.1 (IPv4), consisting of four sets of numbers between 0 and 255 separated by periods, or it can be a more complex and recent alphanumeric version like 2001:0db8:85a3:0000:0000:8a2e:0370:7334 (IPv6).


When we browse the internet using a web browser, we don't need to enter a long and complicated number; just a domain is enough to find what we want.

### DNS Service
The DNS is a fundamental component of the internet's infrastructure, globally distributed, that essentially functions like a phone book, managing the mapping between domain names and their respective IP addresses. DNS servers convert domain name requests into IP addresses, controlling which server the end user will connect to when entering a domain name in browser. These requests made by the client to a DNS server are called **queries**.

### Types of DNS Service

#### Recursive DNS
When a client makes a query, the recursive DNS server acts as an intermediary to obtain the DNS information and respond to the request. If the requested DNS reference is stored in the recursive server's cache, it will respond to the query directly. Otherwise, it will forward the query to one or more authoritative DNS servers until it gets all the information needed to respond to the client.

#### Authoritative DNS
The authoritative DNS has the final authority over the domain and is responsible for providing responses to recursive DNS servers with IP address information of specific domain names. They are also used by administrators to manage public DNS names.

### How DNS works
Four DNS servers are involved in loading internet content. These servers operate in a distributed and hierarchical manner:

1. DNS Recursor:
It is the initial contact point of your device with DNS servers. It is designed to receive requests from client machines through applications like web browsers. The recursor is responsible for making additional requests to the rest of the DNS infrastructure to fulfill the client's request. It is often provided by your Internet Service Provider (ISP) or a third-party service like Google Public DNS.

2. Root Server:
At the top of the hierarchy, root servers perform the first step in resolving a domain name into an IP address. They direct DNS queries to the appropriate Top-Level Domain servers (TLD).

3. Top-Level Domain (TLD) Server:
These servers hold information about the last part of the URL (.com, .net, .org, .gov). They respond to DNS queries with the address of the corresponding authoritative DNS server.

4. Authoritative DNS Server:
Responsible for storing DNS records, authoritative DNS servers know the address of the specific domain name requested and do not need to query or redirect to other servers to respond to requests with the IP address.


### DNS Service Workflow

![DNS-scheme-en](https://raw.githubusercontent.com/lfelipeee/hugo-site/main/static/images/dns-en.png)

1. The end user uses a web browser to request resources from www.example.com.

2. The device cannot translate this domain name to an IP address, so it makes a query to the DNS recursor.

3. The DNS Recursor, in turn, does not have the information cached, so it queries a Root Server.

4. The Root Server directs the DNS Recursor to the Top-Level Domain (TLD) server responsible for '.com' domains.

5. The DNS Recursor queries the indicated TLD Server.

6. The TLD Server directs the DNS Recursor to the Authoritative Server that holds the desired IP address.

7. The DNS Recursor queries the indicated Authoritative Server.

8. The Authoritative Server responds with the IP address for the requested domain name.

9. The DNS recursor forwards the IP address to the end user's machine.

10. The web browser requests the resources found at the provided IP address via the HTTP protocol.

11. The web server sends the requested web page content to the end user's web browser.