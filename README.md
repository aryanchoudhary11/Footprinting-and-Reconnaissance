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

---

## 🌐 Footprinting through Search Engines

Search engines (Google, Bing, DuckDuckGo, etc.) are powerful tools for **hackers and ethical hackers** to gather information. They index **publicly available data**, but often reveal sensitive or misconfigured data unintentionally exposed.

### 1. Footprinting Using Advanced Google Hacking Techniques

Google allows special search operators (called Google Dorks) to refine searches.
Hackers use these operators to find hidden files, misconfigurations, or sensitive information.

Common Google Dorks:

  - ```site:example.com``` → Shows indexed pages only from example.com.
  - ```filetype:pdf confidential``` → Finds confidential PDFs.
  - ```intitle:"index of"``` → Finds exposed directories.
  - ```inurl:admin``` → Finds login/admin panels.

👉 **Real-World Example:** Searching filetype:xls site:abc.com may reveal spreadsheets with employee data.

### 2. What Can a Hacker Do with Google Hacking?

- Using Google Hacking, attackers can:

  - Find login pages (inurl:login)
  - Discover config files (filetype:cfg)
  - Identify error messages revealing server info
  - Locate database dumps (filetype:sql)
  - Access exposed cameras (inurl:/view.shtml)

👉 **Case Study:** A hacker once found NASA login portals using inurl:wp-login.php site:nasa.gov.

### 3. Footprinting Using Advanced Google Hacking Techniques with AI

- AI can automate Google Dorking by:
  - Generating custom dork queries based on target domain.
  - Filtering useful results vs noise.
  - Summarizing sensitive findings.

👉 **Example:** Instead of manually typing 50 queries, an AI-powered script can run site:abc.com filetype:pdf, site:abc.com intitle:"index of", etc., and return a list of sensitive URLs.

### 4. Google Hacking Database (GHDB)

- GHDB is a repository of pre-built Google Dorks maintained by security researchers.
- Website: https://www.exploit-db.com/google-hacking-database
- Categories include:
  - Files with passwords
  - Vulnerable servers
  - Sensitive directories
  - Error messages

👉 **Example:**
From GHDB, you can find a dork like:
intitle:"Index of /" password → which shows password files in public folders.

### 5. VPN Footprinting through Google Hacking Database

- Attackers can also identify VPN login portals exposed online.
- Common Dorks:

  - inurl:/remote/login (Fortinet VPN)
  - intitle:"GlobalProtect Portal" (Palo Alto VPN)
  - inurl:logon.html (Citrix VPN)

👉 **Example:** Using GHDB, a hacker may find a misconfigured Cisco VPN portal that reveals version details.

### 6. VPN Footprinting through Google Hacking Database with AI

- AI can enhance VPN footprinting by:

  - Automatically identifying if the VPN version is outdated.
  - Matching it with known CVEs (Common Vulnerabilities & Exposures).
  - Generating possible exploitation paths.

👉 **Example:** AI detects a Fortinet VPN login page and checks if it matches a known vulnerability (like CVE-2018-13379, a famous Fortinet SSL VPN bug).

### 7. Footprinting through SHODAN Search Engine

Shodan.io
 = “Google for Hackers.”

- Unlike Google (which indexes websites), Shodan indexes devices connected to the internet.
- You can find:

  - Exposed webcams
  - IoT devices (smart homes, routers, printers)
  - VPNs, firewalls, databases
  - Servers with specific ports/services

👉 **Example:** Searching Shodan for port:3389 shows exposed RDP servers (Remote Desktop).

### 8. Other Techniques for Footprinting through Search Engines

- Apart from Google & Shodan:

  - **Bing Dorking** – Similar operators to Google.
  - **DuckDuckGo Search** – Sometimes shows data Google misses.
  - **Censys.io** – Another tool like Shodan for device scanning.
  - **ZoomEye** – Chinese equivalent of Shodan.

👉 **Example:** Searching on Censys may reveal SSL certificates of a target company, helping enumerate subdomains.

---

## 🌍 Footprinting through Internet Research Services

Internet research services are publicly available online resources that attackers or ethical hackers use to gather deeper information about a target beyond search engines. This is part of OSINT (Open Source Intelligence).

### 1. Finding a Company’s Top-Level Domains (TLDs) and Sub-domains

- **TLDs** = extensions like .com, .org, .net, .in.
- Companies often own multiple TLDs (e.g., google.com, google.in, google.org).
- **Subdomains** = subdivisions of the main domain (e.g., mail.google.com, dev.google.com).

How hackers find them:

- Tools: sublist3r, Amass, crt.sh, dnsdumpster.com.
- Passive way: Check SSL certificates → they often list subdomains.

👉 **Example:** A company has portal.abc.com for internal logins, which might be overlooked by admins but indexed online.

### 2. Finding TLDs and Sub-domains with AI

AI can:

- Automate subdomain enumeration with multiple tools (Sublist3r + Amass + crt.sh).
- Cross-check which subdomains are live.
- Match them with vulnerabilities in CVE databases.

👉 **Example**: AI finds vpn.abc.net and correlates it with an outdated version → potential entry point.

### 3. Extracting Website Information from Archive.org

- Archive.org (Wayback Machine) stores historical snapshots of websites.

- Hackers use it to find:

  - Old pages containing sensitive info.
  - Deprecated APIs/endpoints.
  - Exposed employee details (before they were removed).

👉 **Example:** abc.com may have hidden admin pages today, but in 2016 snapshots you find /admin/login.php.

### 4. Footprinting through People Search Services

- Websites like Pipl, Spokeo, PeekYou, BeenVerified provide personal data.
- Attackers can collect: phone numbers, emails, social media profiles, addresses.
- Used for social engineering attacks (phishing, impersonation).

👉 Example: Searching for an employee’s name reveals LinkedIn + GitHub → attacker learns about technologies the company uses.

### 5. Footprinting through Job Sites

- Job postings often leak internal details:
  - Technologies used (e.g., “looking for AWS & Kubernetes admin”).
  - Security tools (“must have Splunk experience”).
  - Infrastructure scale.

👉 **Example:** If abc.com posts a job for “Oracle DBA with SQL*Plus experience,” an attacker knows Oracle DB is in use.

### 6. Dark Web Footprinting

The **Dark Web** is used by attackers to buy/sell data.
- Hackers search for leaked credentials, company documents, or data dumps.
- Tools: Tor Browser, marketplaces, breach databases.

👉 **Example:** An attacker finds abc.com employee emails + passwords leaked from a previous breach.

### 7. Searching the Dark Web with Advanced Search Parameters

- Dark Web search engines (e.g., Ahmia, Onion Search Engine) allow specific queries.
- Example parameters:
    - ```company.com password```
    - ```company.com confidential```

👉 **Case:** A security researcher found banking credentials of employees from a past leak indexed on a hidden forum.

### 8. Determining the Operating System

Footprinting can also reveal a company’s OS:
  - Job postings (“Linux Admin required”).
  - Shodan scan showing Windows RDP ports open.
  - Banner grabbing from services.

👉 **Example:** If Nmap shows ```Microsoft-IIS/10.0```, attacker knows the server is **Windows Server 2016+.**

### 9. Competitive Intelligence Gathering

This means gathering business-related intelligence for hacking or analysis.

- **When Did the Company Begin? How Did it Develop?**
  → From Crunchbase, Wikipedia, company blogs.

- **What Are the Company's Plans?**
  → From press releases, news articles, job postings.

- **What Do Experts Say?**
  → From forums, tech blogs, analyst reports.

👉 **Example:** If a company announces it is “migrating to AWS Cloud,” attackers may target misconfigured S3 buckets.

## 10. Other Techniques for Footprinting through Internet Research Services

- Social bookmarking sites (Reddit, Quora, GitHub).
- Pastebin leaks (searching ```site:pastebin.com company.com```).
- SSL certificate transparency logs (crt.sh).
- Tech blogs where employees write about their work.

👉 **Example:** A developer posts a code snippet on GitHub that contains API keys.

---

