# Task 1 — Local Network Port Scan

## Overview
This repository contains the results of a local network port scan performed as part of the Cyber Security Internship Task 1. The objective was to discover open ports on devices within my local network and assess basic security exposure.

## Environment
- OS: Kali Linux
- Tools: Nmap, Wireshark/tshark (optional)
- Scan time: <PUT DATE/TIME HERE>
- Network Range Scanned: 10.68.55.0/24

## Commands Used
1. Determine local IP:
```bash
ip -4 -o addr show scope global

sudo nmap -sS -sV -O 10.68.55.0/24 -oN scan_results.txt -oX scan_results.xml

xsltproc scan_results.xml -o scan_results.html

timeout 30s tshark -i eth0 -w ~/nmap_capture.pcap

| IP Address    | Open Ports | Services         | Risk / Notes                              |
|---------------|------------|-----------------|------------------------------------------|
| 10.68.55.221  | 53         | dnsmasq 2.51    | DNS service open on phone; minimal risk for internal network, but avoid exposing externally |
| 10.68.55.248  | 22         | OpenSSH 10.0p2  | SSH open on Linux host; ensure strong passwords or key-based authentication |

