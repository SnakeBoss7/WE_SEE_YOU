### TRYHACKME Nmap Room --- Beginner Write-up
Platform:Tryhackme
Room:https://tryhackme.com/room/furthernmap
level:Beginner
Topic: Nmap Cli , NSE scripts ,firewall Evasion
Date : 2 Aug 2025

## what i learnt 
1. SCAN TYPES
2. HOW TO BE STEALTHY
3. ICMP RESPONSE
### Task-by-Task Breakdown

## Task 1 -
Deploy the machine

## Task 2 -
Introduction to ports
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

ICMP Types (Important ones):
Type	Code	   Meaning
3	      0-15	   Destination Unreachable (subcodes: host, port, etc.) (either blocked or filtered by firewall)
5	      1,2	   Redirect (change route)
11	      0/1	   Time Exceeded (TTL expired)
13/14	   -	   Timestamp Request/Reply