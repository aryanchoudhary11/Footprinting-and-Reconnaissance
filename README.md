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

## 👥 Footprinting through Social Networking Sites

Social media is one of the **richest sources of information** for hackers. Employees often **overshare** details about their company, technologies, or even internal systems without realizing attackers can use it.

### 1. People Search on Social Networking Sites

Attackers look up **employees, partners, or executives** on platforms like Facebook, Twitter, Instagram, LinkedIn, etc.

- Info gained:
  - Full name, job role, email ID pattern
  - Location, work culture, office pictures
  - Friends/colleagues (who can be social engineered)

👉 Example: Searching ```site:linkedin.com "Company ABC"``` on Google shows all employees working at ABC.

### 2. Gathering Information from LinkedIn

- LinkedIn is a goldmine for hackers because employees post:

  - Current role and responsibilities
  - Technologies they work with (“5 years of AWS, Docker, Kubernetes”)
  - Job switches (helps track who has insider knowledge)

👉 **Case Example:**
A sysadmin writes *“managing Fortinet firewalls and Splunk SIEM”*.
➡️ Now an attacker knows the company uses Fortinet + Splunk.

### 3. Harvesting Email Lists

- Attackers gather employee emails to use in **phishing or brute force attacks.**
- Common ways:
    - Guessing format: (```firstname.lastname@company.com```)
    - Scraping from LinkedIn, GitHub, or public documents.
    - Using tools like **theHarvester** or **Hunter.io**.

👉 **Example:** If one email is ```john.doe@abc.com```, then others likely follow the same pattern.

### 4. Harvesting Email Lists with AI

AI can:
- Predict email patterns (e.g., first.last, first_initial+last).
- Cross-verify emails with data leaks.
- Generate phishing targets list quickly.

👉 **Example:** AI scrapes 100 LinkedIn profiles from abc.com, detects the email format, and auto-builds a valid email list for spear phishing.

### 5. Analyzing Target Social Media Presence

Hackers analyze:

- Posting habits (when employees are active).
- Company events (conferences, new launches).
- Pictures/videos (sometimes show ID cards, desktops, whiteboards with passwords).
- Hashtags (#LifeAtABC, #TeamABC → reveals projects/office info).

👉 **Example:** An employee posts a picture of their workstation on Instagram → monitor shows internal dashboard URL.

### 6. Tools for Footprinting through Social Networking Sites

- **theHarvester** – Email/username gathering.
- **Maltego** – OSINT framework with social media integration.
- **Social-Searcher** – Monitors mentions across social media.
- **Creepy** – Finds geolocation info from Twitter/Flickr.
- **Sherlock** – Finds usernames across multiple platforms.

👉 **Example:** Using Sherlock, you find that a sysadmin’s username techguy21 is reused on GitHub → where he posted company code.

### 7. Footprinting through Social Networking Sites with AI

AI-powered footprinting helps by:
- Automating profile crawling.
- Extracting emails, job roles, and technologies from LinkedIn at scale.
- Detecting **patterns of behavior** (e.g., when employees log in or post).
- Analyzing images for hidden data (like EXIF metadata → location info).

👉 Example: AI scans employee selfies → metadata reveals GPS coordinates of the office → attacker now knows exact building location.

--- 

## 🌍 Whois Footprinting

Whois is one of the oldest and most useful methods for footprinting. It provides domain registration details stored in public records when someone buys a domain. Attackers (and ethical hackers) use it to find who owns a website, their contact details, and server information.

### 1. Whois Lookup

What it is:

- Whois lookup shows **domain registration info** from registrars like GoDaddy, Namecheap, etc.
- Data can include:

    - Registrant’s name/organization
    - Email address & phone number
    - Domain creation & expiry date
    - Nameservers (DNS servers)
    - Registrar details
 
**How hackers use it:**
- If the registrant uses **personal email**, attackers may try phishing.
- If the expiry date is near, attackers may try domain hijacking (re-registering it if it lapses).
- Nameservers reveal hosting provider (AWS, Cloudflare, etc.).

**Tools for Whois lookup:**
- Online tools: whois.domaintools.com, whois.com
- CLI:

  ```
  whois example.com
  ```

👉 **Example:**

- Looking up abc.com might reveal:
- Registrant: ABC Technologies Pvt Ltd
- Email: admin@abc.com
- Nameservers: ns1.aws.amazon.com, ns2.aws.amazon.com

➡️ Now you know the company uses AWS hosting.

### 2. Finding IP Geolocation Information

After Whois, hackers map **where the IP address is located physically.**

**What it reveals:**

- Country, city, ISP (Internet Service Provider).
- Hosting provider (AWS, Azure, Google Cloud, etc.).
- Sometimes even **exact data center region.**

**Why it matters:**

- Helps attackers know whether a site is hosted **on-premises or cloud.**
- Useful for **social engineering** (e.g., pretending to be local ISP support).
- Helps choose **attack timing** (timezone differences).

**Tools for IP Geolocation:**

- iplocation.net
- ipinfo.io
- Shodan.io (also provides geolocation + open ports).
- CLI (Linux):

  ```
  curl ipinfo.io/8.8.8.8
  ```
👉 **Example:** If IP 192.168.61.129 resolves to Bangalore, India → ISP: Reliance Jio, attackers know where the server is hosted.

---

## 🌐 DNS Footprinting

DNS (Domain Name System) is like the internet’s directory – it maps **domain names** (example.com) to **IP addresses**.
Footprinting DNS gives attackers technical insights into a company’s network.

### 1. Extracting DNS Information

Attackers gather DNS records to understand a target’s infrastructure.

**Important DNS Records:**

- **A Record** → Maps a domain to an IPv4 address.
  - ```abc.com → 203.0.113.10```

- **AAAA Record** → Maps to IPv6 address.
- **MX Record** → Mail server info.
  - If ```mail.abc.com``` points to Google → company uses Gmail/Google Workspace.

- **NS Record** → Nameservers (who handles DNS).
- **TXT Record** → Can reveal SPF/DKIM for email, sometimes API keys or misconfigurations.
- **CNAME Record** → Alias for subdomains.

**Tools to extract DNS info:**

- nslookup (Windows/Linux)
  ```
  nslookup abc.com
  ```

- dig (Linux/macOS)
  ```
  dig abc.com ANY
  ```

- Online: ```dnsdumpster.com```, ```MXToolBox```.

👉 Example:
Running dig abc.com MX might show →
```
mail.abc.com priority 10
```
➡️ Now attacker knows company’s mail server.

### 2. DNS Lookup with AI

AI can **automate DNS lookups** by:

- Querying multiple record types in one go.
- Identifying patterns (like naming conventions for subdomains).
- Correlating DNS info with known vulnerabilities.

👉 Example: AI checks ```vpn.abc.com``` → detects it points to ```Cisco ASA VPN``` → matches with a CVE like **CVE-2020-3452.**

Instead of manually testing every subdomain, AI automates scanning + vulnerability mapping.

### 3. Reverse DNS Lookup

**Forward DNS** → Domain → IP
**Reverse DNS** → IP → Domain

- Reverse DNS finds **all domains hosted on a specific IP.**
- Useful when one server hosts multiple websites (shared hosting).
- Can reveal **hidden/test domains** not publicly known.

**Tools:**
- Command line:
  ```
  nslookup 203.0.113.10
  ```

- Online: viewdns.info/reverseip

👉 **Example:**
IP ```203.0.113.10``` may resolve to:

- abc.com
- test.abc.com
- dev.abc.com

➡️ Now attacker knows additional subdomains like ```dev.abc.com``` which might be less secure.

---

## 🌐 Network and Email Footprinting

This step focuses on mapping **how data flows across the internet** (network-level reconnaissance) and learning how to extract information from **email communications.**

### 1. 🔎 Locate the Network Range

When targeting an organization, the attacker first needs to know **which IP range** (block of IP addresses) belongs to the target.

- Every organization has IP ranges assigned by Regional Internet Registries (RIRs) like ARIN, RIPE, APNIC.
- Using tools like ```whois```, attackers can find the **NetRange**.

**Example:**
```
whois microsoft.com
```
Might show:
```
NetRange:   13.64.0.0 - 13.107.255.255
OrgName:    Microsoft Corporation
```

👉 This means Microsoft owns 13.64.0.0 → 13.107.255.255.
An attacker now knows all live hosts will lie in this range.

**✅ Real-world use**: Security teams monitor their entire IP range for vulnerabilities, not just their main domain.

### 2. 🌍 Traceroute

Traceroute maps the path packets take from your computer to the target server.

- Shows **routers (hops) in between**.
- Reveals the **network infrastructure** (ISPs, routers, firewalls).
- Helps identify **where the target’s network begins**.

**Example:**
```
traceroute google.com    # Linux / Mac
tracert google.com       # Windows
```

You might see output like:

```
1  192.168.1.1 (home router)
2  isp.local.net
3  72.14.219.1 (Google edge router)
...
```

👉 From this, you know where the **internal Google network starts**.

### 3. 🤖 Traceroute with AI

Attackers (and defenders) can use AI models to analyze traceroute outputs and identify:

- Which hops belong to ISPs vs the target
- Possible VPNs, proxies, or CDN usage (like Cloudflare)
- Detect geographical routes → AI can map hops on a world map.

✅ **Example:** AI sees ```ae1.paris.gblx.net``` and automatically says “Hop passes through Paris, Global Crossing ISP”.

### 4. 📊 Traceroute Analysis

Key insights attackers/security analysts get:

- Where firewalls filter packets (e.g., sudden timeout at hop 6).
- Which ISPs partner with the target company.
- Latency points (helps in DoS attack planning).
- Detect load balancers/CDNs if multiple routes appear.

### 5. ⚙️ Traceroute Tools

- **Built-in**: ```tracert``` (Windows), ```traceroute``` (Linux/Mac).
- **VisualRoute** → GUI + Geo-mapping.
- **Path Analyzer Pro** → Advanced traceroute with reporting.
- **tracetcp** → Traceroute over TCP (can bypass ICMP block).

### 6. 📧 Tracking Email Communications

Email headers leak tons of information.
Attackers can trace:

- The **originating IP** of the sender.
- The **mail servers** used.
- Possible **geolocation**.

### 7. 📜 Collecting Information from Email Header

Let’s say you received this header:

```
Received: from mail.example.com (mail.example.com [203.0.113.25])
  by smtp.gmail.com with ESMTPS id x12si87332qtk.23.2025.08.31
```

- **203.0.113.25** = Mail server IP.
- Running ```whois 203.0.113.25``` shows the organization hosting it.
- Sometimes, the **sender’s real IP** leaks (if no anonymization).

**✅ Defenders:** Configure mail servers to remove sensitive info.

### 8. 🛠️ Email Tracking Tools

- **MXToolBox (mxtoolbox.com)** → Analyze mail headers, MX records.
- **PoliteMail / Yesware** → Track if mail is opened (legit marketing tools, abused by attackers).
- **Infoga** → OSINT tool for email footprinting.
- **Email Header Analyzer (Google Apps)** → Decodes headers into readable info.

---

## 🎭 Footprinting through Social Engineering

Social Engineering is the **art of manipulating people** into giving up confidential information rather than breaking systems technically.
It’s one of the **most effective footprinting techniques** because humans are the weakest security link.

### 1. Collecting Information through Social Engineering on Social Networking Sites

- Attackers exploit trust and oversharing on platforms like Facebook, Instagram, LinkedIn, or Twitter (X).
- People often reveal:

  - Birthdays, phone numbers, and emails
  - Workplace and job role details
  - Travel plans and geolocation tags
  - Family connections and personal interests

📌 Techniques:

- **Fake Profiles (Impersonation)**: Attacker creates a fake persona to connect with employees.
- **Phishing via Social Media:** Sending malicious links through DMs.
- **Information Harvesting:** Collecting info from public profiles, group memberships, or likes.

⚡ **Example:** An attacker connects with an employee on LinkedIn, poses as a recruiter, and extracts internal project details by casual chatting.

### 2. Collecting Information Using Eavesdropping, Shoulder Surfing, Dumpster Diving, and Impersonation

**🔍 Eavesdropping**

- Secretly listening to conversations in public (cafes, airports, offices).
- Attackers may **overhear credentials, project names, or phone calls**.

**👀 Shoulder Surfing**

- Looking over someone’s shoulder to **steal sensitive info**.
- **Example:** Watching someone type an ATM PIN, office password, or email login.

**🗑 Dumpster Diving**

- Searching through trash bins to retrieve **confidential papers, notes, invoices, or USB drives**.
- **Example:** An attacker finds discarded documents with network details.

**🎭 Impersonation**

- Pretending to be a **trusted individual** (IT staff, delivery person, or manager).
- **Example:** An attacker impersonates tech support, asks for Wi-Fi credentials under the pretense of fixing internet issues.

--- 

## 🤖 Footprinting Tasks using Advanced Tools and AI

Traditionally, footprinting relied on manual methods or limited automation.
But now, **AI + OSINT** (Open Source Intelligence) makes reconnaissance **faster, smarter, and harder to detect.**

### 1. AI-Powered OSINT Tools

AI-based OSINT tools can **analyze, correlate, and summarize massive amounts of public data** quickly.

**Popular AI-Powered Tools**

- **Maltego with AI plugins** → Visual link analysis of people, companies, domains. AI can automatically highlight suspicious connections.
- **SpiderFoot HX** → Automated OSINT scanner with AI to analyze results.
- **Recon-ng with AI Modules** → Automates domain, WHOIS, IP lookups with AI correlation.
- **Shodan AI Integrations** → AI analyzes IoT devices exposure trends.
- **ChatGPT / LLMs** → Can generate Google dorks, analyze traceroute output, summarize whois data, or correlate multiple OSINT sources.

**⚡ Example:**
Instead of manually checking 100 LinkedIn profiles, AI scrapes them, extracts job titles, and summarizes “Company X uses AWS, is hiring DevOps engineers, and recently shifted to Kubernetes.”

### 2. Create and Run Custom Python Script to Automate Footprinting Tasks with AI

You can build a Python script that:

- Collects OSINT (via APIs like Shodan, Whois, Google Dorks).
- Sends results to an AI model.
- AI summarizes & highlights the most **useful reconnaissance data.**

---

