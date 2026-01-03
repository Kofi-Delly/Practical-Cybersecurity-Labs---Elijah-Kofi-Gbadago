# Practical-Cybersecurity-Labs
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

## Part 2: Scapy (Packet Manipulation)
Objective: Use Scapy's interactive shell to sniff network traffic and analyze packets programmatically.

[Link to documentation](https://github.com/Kofi-Delly/Practical-Cybersecurity-Labs/tree/main/NMAP_and_Scapy_Lab)




## Lab: Website Cloning and SMB Vulnerability Scanning

This repository documents how I used:

1. `setoolkit` in my **Website Cloning Lab**
2. `enu4linux` and `smbclient` in my **SMB Vulnerability Scanning Lab**

My objective for these activities is to practice **ethical hacking techniques** in a controlled environment for **learning and security testing purposes only**.


##  Ethical & Legal Disclaimer

All activities documented here were performed:

- In a **controlled lab environment**
- Against **intentionally virtual systems I own and have explicit permission to test**
- Strictly for **educational and training** purposes.

 **Do not** use these techniques on networks or systems without explicit authorization. Unauthorized access or testing is illegal and unethical.


##  Repository Structure

- `README.md` – The documentation
- `screenshots/` – Screenshots of key steps and results.

## Part 1: Website Cloning Lab (SET Toolkit)

###  Objective

Use **Social-Engineer Toolkit (SET)** to clone a target website and capture login credentials, demonstrating:

- Proper use of `setoolkit`
- Understanding how credential harvesting via cloning works
- Awareness of the **ethical context** (for education/testing only)

###  Tools & Environment

- **Kali Linux** (attacker machine)
- **SET (Social-Engineer Toolkit)**
- **DVWA** (`http://dvwa.vm`) as the target web application – intentionally vulnerable virtual web app.
- Browser and text editor (e.g. `firefox`, `pluma`)


### 1.1 High-Level Concept

The idea of this lab is to:

1. Use SET to **clone a legitimate login page**.
2. Host the cloned page on the attacker machine (e.g. `10.6.6.1`).
3. Trick a user into visiting this cloned page.
4. When the user submits their credentials, SET **captures** them and then **redirects** the user back to the original site to avoid suspicion.

Once again, this is only acceptable in a **lab** or with **explicit permission**.


# Link to the lab documentation:
[Lab_setoolkit(web_cloning)_and_enum4linux & smbclient](https://github.com/Kofi-Delly/Practical-Cybersecurity-Labs/tree/main/Lab_setoolkit(web_cloning)_and_enum4linux%20%26%20smbclient)


# Vulnerability Scanning Lab: Nikto

## 1. Objective
The purpose of this lab was to utilize **Nikto**, an Open Source (GPL) web server scanner, to execute extensive testing against web servers for multiple items.

## 2. Tools Used
* **Kali Linux Ethical Hacker VM** (Virtual Environment)
* **Nikto v2.5.0**
* **Invicti/CVE Databases** (For vulnerability research)
* **Nano Text Editor** (Used to list targeted IPs)

# Link to the lab documentation:
[Vulnerability Scanning Lab with Nikto](https://github.com/Kofi-Delly/Practical-Cybersecurity-Labs/tree/main/Vulnerability%20Scanning%20Lab%20with%20Nikto)



# Web Application Vulnerability Scanning with OWASP ZAP

## 1. Objective
The main goal of this lab was to conduct a Dynamic Application Security Testing (DAST) scan against a vulnerable target (Damn Vulnerable Web Application - DVWA) to identify security flaws. I utilized **OWASP ZAP (Zed Attack Proxy)** to perform an automated scan of the **DVWA (Damn Vulnerable Web Application)** to find issues such as Remote Code Execution (RCE) and Information Disclosure.

## 2. Tools & Environment
* **Scanner:** OWASP ZAP v2.13.0
* **Target:** DVWA (Damn Vulnerable Web Application) running on `172.17.0.2`
* **Platform:** Kali Linux

# Link to the lab documentation:
[Web Application Vulnerability Scanning with OWASP ZAP](https://github.com/Kofi-Delly/Practical-Cybersecurity-Labs/tree/main/Web_Application_Vulnerability_Scanning_with_OWASP_ZAP)
