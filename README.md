# Footprinting-and-Reconnaissance

## 🔎 Footprinting Concepts

### 1. Reconnaissance (What it Means)

- **Reconnaissance** = Information gathering phase of hacking (legal or illegal).
- Before attacking, a hacker (or ethical hacker) collects as much data as possible about the target:

  - People (employees, emails, social media)
  - Technology (IP addresses, domains, servers, operating systems)
  - Security (firewalls, VPN, IDS/IPS, etc.)

**👉 Real-world analogy:**
Imagine you want to rob a bank (black-hat) or test security of a bank (ethical hacker).

- First, you observe: number of guards, cameras, entry/exit points.
- You don’t attack yet, you’re just gathering intel.

This is what Reconnaissance is in hacking.

### 2. Types of Footprinting/Reconnaissance

There are two main categories:

🔹 **Passive Footprinting**

    Collecting information without directly interacting with the target system.

- **Example:** Google search, LinkedIn employee details, Whois lookup, social media analysis.
- Safer because the target won’t know you’re investigating.

👉 Example: You Google site:example.com confidential and find exposed documents.

🔹 Active Footprinting

    Directly interacting with the target system to get information.

- **Example:** Port scanning (Nmap), pinging servers, banner grabbing.
- More risky because it may trigger IDS/IPS alerts.

👉 Example: Running nmap -sV example.com to see what services are running.

### 3. Information Obtained in Footprinting

During footprinting, you may gather:

  - **Network information:** IP addresses, subnets, domains.
  - **System information:** OS version, server software (Apache, IIS, Nginx).
  - **Employee information:** emails, phone numbers, social engineering targets.
  - **Security posture:** firewalls, VPN, IDS/IPS, cloud usage.
  - **Physical information:** office location, Wi-Fi SSIDs.

👉 **Real-world Example:** Suppose you’re hired to test security of abc.com.

  - Whois lookup gives you registrant name and DNS servers.
  - Google search reveals Excel files with employee emails.
  - Nmap shows port 3306 (MySQL) is open.
  - Now you know: employees + technology stack + possible entry points.

### 4. Objectives of Footprinting

Why footprinting is done?

  - **Understand Target** – Know the business, infrastructure, and attack surface.
  - **Identify Vulnerabilities** – Example: Outdated Apache version.
  - **Find Weak Links** – Example: An employee email that can be phished.
  - **Prepare for Exploitation** – Create attack strategies.

👉 **Example:** If you find that a company uses WordPress 4.7, you can later check for vulnerabilities in that version.

### 5. Footprinting Threats

Why is footprinting dangerous if done by attackers?

  - **Information leakage:** Sensitive data exposed online.
  - **Social engineering attacks:** Attackers may impersonate employees.
  - **Phishing attacks:** Emails harvested can be used for phishing.
  - **System compromise:** Publicly known vulnerabilities exploited.
  - **Physical threats:** Office address can lead to physical attacks.

👉 **Example:** A hacker finds employee details on LinkedIn and sends a phishing email pretending to be HR.

### 6. Footprinting Methodology

The step-by-step process ethical hackers follow:

1. **Define the target:**
   - Example: example.com
2. **Information Gathering (Passive)**
   - Whois lookup, DNS records, Google dorks, job postings.
3. **Network Enumeration (Active)**
   - Ping sweep, traceroute, Nmap scanning.
4. **Identify Technologies**
   - Find OS, web server, database, CMS, cloud provider.
5. **Gather Employee/Organizational Info**
   - Emails, phone numbers, social media accounts.
6. **Analyze and Document**
   - Create a footprinting report to plan next steps.

👉 **Example Flow:**
- Target: abc.com
- Whois → Find IP range 192.168.61.0/24.
- Google dorks → Found an Excel file with usernames.
- Nmap → Discovered SSH and MySQL open.
- Social media → Found sysadmin email.
