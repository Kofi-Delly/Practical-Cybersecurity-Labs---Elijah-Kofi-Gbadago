# Practical-Cybersecurity-Labs---Elijah-Kofi-Gbadago
This repository documents practical cybersecurity labs focused on network reconnaissance and packet manipulation. The objective was to master Cybersecurity tools.


# Nmap & Scapy Practical Lab

## Overview
This repository documents practical cybersecurity labs focused on network reconnaissance and packet manipulation. The objective was to master Nmap for host discovery and service enumeration, and Scapy for custom packet crafting and sniffing.

## Prerequisites
* **Kali Linux** (Virtual Machine)
* **Nmap** installed
* **Python** with **Scapy** library installed
* Root/Sudo privileges

## Part 1: Nmap (Network Mapper)
**Objective:** Perform host discovery, OS fingerprinting, and service detection on the target network `10.6.6.0/24`.

### 1. Ping Scan (Host Discovery)
Scans the subnet to identify live hosts without scanning ports.
Command
```
─(kali㉿Kali)-[~]
└─$ nmap -sn 10.6.6.0/24
```
![Screenshot of host discovery output](screenshots/host_of_discovery_output.png)

2. OS Fingerprinting
Attempts to identify the Operating System of the target 10.6.6.23 based on TCP/IP stack behavior.
Command
```
─(kali㉿Kali)-[~]
└─$ sudo nmap -O 10.6.6.23
```
![Screenshot of OS detection results](screenshots/Screenshot_of_OS_detection_results.png)

3. Aggressive Scan on Specific Port
Runs service version detection (-sV), OS detection, script scanning (-sC), and traceroute (--traceroute) on port 21 (FTP) with timing template 4 (faster).
COMMAND
```
─(kali㉿Kali)-[~]
└─$ nmap -p 21 -sV -A -T4 10.6.6.23
```
![Screenshot of aggressive scan on port 21](screenshots/Screenshot_of_aggressive_scan_on_port_21.png)

4. Aggressive Scan on SMB Ports
Targeting specific NetBIOS/SMB ports (139, 445) to enumerate file sharing services.
Command
```
─(kali㉿Kali)-[~]
└─$ nmap -A -p 139,445 10.6.6.23
```
![Screenshot of SMB port scan](screenshots/Screenshot_of_SMB_port_scan.png)

6. SMB Enumeration Script
Uses the Nmap Scripting Engine (NSE) to specifically list available shares on the target.
Command
```
─(kali㉿Kali)-[~]
└─$ nmap --script smb-enum-shares.nse -p 445 10.6.6.23
```
![Screenshot of script output](screenshots/Screenshot_of_script_output.png)

7. SMB Client Connection
Connects to the print$ share on the target without a password (-N) to test access.
Command
```
─(kali㉿Kali)-[~]
└─$ smbclient //10.6.6.23/print$ -N
```
# Type 'exit' to close the shell
![Screenshot of smbclient connection](screenshots/Screenshot_of_smbclient_connection.png)

8. Network Configuration Checks
Verifying local IP configuration and routing table.
Commands
```
─(kali㉿Kali)-[~]
└─$ ifconfig
─(kali㉿Kali)-[~]
└─$ ip route
─(kali㉿Kali)-[~]
└─$ cat /etc/resolv.conf
```
![Screenshot of network config commands](screenshots/Screenshot_of_network_config_commands.png)

10. Packet Capture with TCPDump
Captures traffic on interface eth0, writing the full packet (-s 0) to a file named ladies.pcap.
Command
```
─(kali㉿Kali)-[~]
└─$ sudo tcpdump -i eth0 -s 0 -w ladies.pcap
```
# Press ctrl + c to stop packet capture
```
─(kali㉿Kali)-[~]
└─$ ls ladies.pcap
```
![Screenshot of tcpdump running and file listing](screenshots/Screenshot_of_tcpdump_running_and_file_listing.png)

10. Wireshark Analysis
Opening the captured packet file for graphical analysis.
Command
```
─(kali㉿Kali)-[~]
└─$ wireshark
```
![Screenshot of Wireshark opening the pcap file](screenshots/Screenshot_of_Wireshark_opening_the_pcap_file.png)

## Part 2: Scapy (Packet Manipulation)
Objective: Use Scapy's interactive shell to sniff network traffic and analyze packets programmatically.
1. Launching Scapy
Starting the interactive Scapy environment with root privileges.
Command
```
─(kali㉿Kali)-[~]
└─$ sudo su
(root㉿Kali)-[/home/kali]
└─# scapy
```
![Screenshot of Scapy startup](screenshots/Screenshot_of_Scapy_startup.png)

3. Basic Sniffing
Step A: Start sniffing in Scapy.
Command
>>> sniff()
Step B: Open a NEW terminal window and ping Google to generate traffic.
Command
```
─(kali㉿Kali)-[~]
└─$ ping google.com
```
# Press Ctrl+C in this terminal to stop pinging
Step C: Stop sniffing in the Scapy window (Ctrl+C) and view summary.
Command
```
>>> paro = _
>>> paro.summary()
```
![Screenshot of paro.summary() output](screenshots/Screenshot_of_paro.summary()_output.png)

3. Interface Specific Sniffing
Sniffing specifically on the br-internal interface while generating local traffic.
Command
```
>>> sniff(iface="br-internal")
(In a separate window/browser: Ping 10.6.6.1 or browse to 10.6.6.23)
```
Command
```
>>> paro2 = _
>>> paro2.summary()
```
![Screenshot of paro2 summary](screenshots/Screenshot_of_paro2_summary.png)

4. Filtered Sniffing (ICMP)
Capturing exactly 5 packets (count=5) that match the ICMP protocol (Ping).
Command
```
>>> sniff(iface="br-internal", filter="icmp", count=5)
(In a separate window: Ping 10.6.6.23)
```
Commad
```
>>> paro3 = _
>>> paro3.summary()
```
![Screenshot of paro3 summary showing 5 ICMP packets](screenshots/Screenshot_of_paro3_summary_showing_5_ICMP_packets.png)

5. Packet Inspection
Inspecting the details of the 4th packet (index 3) captured in the previous step.
Command
```
>>> paro3[3]
```
![Screenshot of specific packet details](screenshots/Screenshot_of_specific_packet_details.png)
