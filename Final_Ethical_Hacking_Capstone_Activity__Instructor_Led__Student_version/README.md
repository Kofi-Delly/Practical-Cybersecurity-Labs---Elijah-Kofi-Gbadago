# Ethical Hacking Capstone Activity: Vulnerability Assessment & Remediation

## Overview
This repository documents my hands-on **Ethical Hacking Capstone Activity**, performed in a controlled lab environment using **Kali Linux** and **DVWA** (Damn Vulnerable Web App). 

The project focuses on identifying vulnerabilities, exploiting them to retrieve "flags" (simulating sensitive data), and proposing industry-standard remediation strategies.

## Tools Used
* **OS:** Kali Linux
* **Network Scanning:** Nmap, NetBIOS
* **Web Recon:** Dirb, Browser Manipulation
* **Exploitation:** SQL Injection (Manual), SMBClient
* **Password Cracking:** John the Ripper, Hashcat
* **Analysis:** Wireshark (Packet Capture Analysis)

---

## Challenge Breakdown

### Challenge 1: SQL Injection (SQLi)
* **Objective:** Retrieve specific user credentials from the database to find a flag file.
* **Methodology:** Used `UNION SELECT` statements to identify the database structure, extract the `users` table, and dump password hashes.
* **Cracking:** Cracked the retrieved MD5 hash using **John the Ripper** and **Hashcat**.
* **Recommended Remediation:** Implement **Parameterized Queries (Prepared Statements)** and strict input validation/sanitization.

### Challenge 2: Web Server Vulnerabilities & Reconnaissance
* **Objective:** Investigate web directories to locate hidden files.
* **Methodology:** Utilized **dirb** to enumerate directories, discovering a "Directory Indexing" vulnerability that exposed sensitive files such as`/config`, and `/docs`.
* **Finding:** Located the `db_form.html` file containing the second flag.
* **Recommended Remediation:** Disable **Directory Browsing** in the web server configuration (Apache/Nginx) and use placeholder index files.

### Challenge 3: SMB Exploitation
* **Objective:** Exploit open Samba shares to access restricted files.
* **Methodology:** Scanned the network (ports 139/445) and identified a host running SMB. Used `smbclient` with a **Null Session** (anonymous login) to list shares and download the ` sxij42.txt ` file.
* **Recommended Remediation:** Disable **Null Sessions** and anonymous access; enforce **SMB Signing** and Encryption.

### Challenge 4: Network Traffic Analysis
* **Objective:** Analyze captured traffic (`SA.pcap`) to find the location of a hidden file.
* **Methodology:** Used **Wireshark** to filter for `http` traffic. Identified plaintext GET requests pointing to a sensitive file (`user_accounts.xml`) containing the final flag.
* **Recommended Remediation:** Implement **TLS/SSL (HTTPS)** to encrypt data in transit and replace FTP with **SFTP/SSH**.


## Security Best Practices Learned
This capstone reinforced the importance of:
1.  **Defense in Depth:** Layering security (WAFs, permissions, encryption).
2.  **Encryption:** Ensuring no sensitive data (like passwords or file contents) travels in plaintext.
3.  **Configuration Management:** Disabling default features like Directory Indexing and Guest accounts.

### You can find the documentation here:
[Final Ethical Hacking Capstone Activity Instructor-Led Student versio](Final_Ethical_Hacking_Capstone_Activity__Instructor_Led__Student_version.pdf)

*Disclaimer: This project was conducted in a controlled, isolated lab environment for educational purposes.*
