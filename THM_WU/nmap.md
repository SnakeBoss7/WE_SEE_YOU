### TRYHACKME Nmap Room --- Beginner Write-up
Platform:Tryhackme\
Room:https://tryhackme.com/room/furthernmap <br>
level:Beginner\
Topic: Nmap Cli , NSE scripts ,firewall Evasion\
Date : 2 Aug 2025\

## what i learnt 
1. SCAN TYPES
2. HOW TO BE STEALTHY
3. ICMP RESPONSE
### Task-by-Task Breakdown

## Task 1 -
Deploy the machine

## Task 2 -
Introduction to ports\
Available Ports to system - 65535

## Task 3 -
Switches in nmap (nmap -h)
listed some basic swithces such as ->
- scans -> -sS,-sU,-O
- performance switch - -T (1-5), -v )(verbosity) , -vv (even mroe )
-port specific swithces - -p <-port->(range or value), -p- for all

## Task 4 -
- Basics
TCP Connect Scans (-sT)(3 way handshake)
SYN "Half-open" Scans (-sS)
UDP Scans (-sU)

- Additional
TCP Null Scans (-sN)
TCP FIN Scans (-sF)
TCP Xmas Scans (-sX)

## Task 5 - TCP scan
TCP scan uses full 3 way handshake
-sT
involves :
- SYN
- SYN-ACK
- ACK

-- least stealthy !!

## Task 6 - SYN scan
-sS
involves :
- SYN
- SYN-ACK
- RST

-- more stealthy than -sT

## Task 7 - UDP scan
-sU
involves :
- SYN

--Less reliable , slow, but more stealthy than -ST

!!IMP : 
- only sends packet to UDP ports
- no response means open|filtered (rarely gets response)
- response with ICMP means closed or blocked

### ICMP Types (Important ones)

Type &nbsp;&nbsp;&nbsp;&nbsp; Code &nbsp;&nbsp;&nbsp;&nbsp; Meaning  
3 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0–15 &nbsp;&nbsp;&nbsp;&nbsp; Destination Unreachable (subcodes: host, port, etc.) (either blocked or filtered by firewall)  
5 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1,2 &nbsp;&nbsp;&nbsp;&nbsp; Redirect (change route)  
11 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0/1 &nbsp;&nbsp;&nbsp;&nbsp; Time Exceeded (TTL expired)  
13/14 &nbsp;&nbsp;&nbsp;&nbsp; - &nbsp;&nbsp;&nbsp;&nbsp; Timestamp Request/Reply  

## Task 8 (Xmas,FIN,NULL)

- NULL (-sN) -> send no flags sent, and empty packets, expects RST as response for closed port 
- FIN (-sF) -> it sends FIN packets , expects RST as response for closed port 
- Xmas (-sX) -> sends FIN,PSH,URG , expects RST as response for closed port 

NOTE: used for unix not supported for windoes ,as windows always returns RST

# Task 9 (ICMP Network Scanning)

its like ping testing for the host and other devices on the network , checking if they are up and skips port scanning

-sn

its like `ping <IP_address>` for multiple devices  
