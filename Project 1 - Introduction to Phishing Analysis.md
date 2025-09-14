# Project 1 – Introduction to Phishing Analysis

## Overview  

Today was the first day of a Phishing Analysis Challenge from [Hax Security](https://learn.haxsecurity.com/), and it provided an understanding of what phishing is and how to break down and investigate it from a **SOC analyst’s perspective**.  

The hands-on part of the lab was investigating a suspicious PayPal-themed domain (`secure-paypai.com`) and run it through **VirusTotal**. It was simple since most of the class was theoritical in explaining phishing, the different types of attacks, and process of analyzing a potential phishing email.

## Phishing analysis repeatable process:  
- Collecting and exporting the email sample in `.eml`/`.msg` format  
- Reviewing email headers for sender and routing details  
- Checking the body for tone, urgency, and suspicious content  
- Hovering over URLs to reveal hidden redirections  
- Scanning files and links in tools like VirusTotal and CyberChef

## Types of Phishing Attacks  
- **Email Phishing** – Email campaigns that pretend to come from well-known companies or services to trick users.  
- **Spear Phishing** – Customized phishing attempts directed at a particular individual, team, or department.  
- **Whaling** – A phishing attack that targets high-level executives such as CEOs or CFOs.  
- **Smishing** – Fraudulent messages sent over SMS that include harmful links or requests.  
- **Vishing** – Phone calls where attackers impersonate IT staff, helpdesk agents, or other trusted roles to gather information.  
- **Clone Phishing** – An authentic email is copied, but the original link or file is swapped with a malicious version.  
- **Business Email Compromise (BEC)** – Criminals pose as senior leadership to pressure employees in finance or HR into sending funds or sensitive records.  

## Common Phishing Techniques
- **Display name spoofing** – impersonating a legitimate sender.  
- **Lookalike domains** – e.g., `paypai.com` vs `paypal.com`.  
- **URL redirection** – shortened or disguised links.  
- **Malicious attachments** – disguised executables or Office files with macros.  
- **Business Email Compromise (BEC)** – impersonating executives to request fraudulent fund transfers.

## Indicators of Suspicious Attachments
- Executables disguised as documents (`Invoice.pdf.exe`)  
- Encrypted ZIP files with hidden malware  
- Macro-enabled Office files (`.docm`, `.xlsm`)  
- Obfuscated scripts (Base64/hex encoded payloads)

## Common Tools Used in Phishing Analysis  
- **[Email Header Analyzer](https://mha.azurewebsites.net/)** – Helps break down sender details and trace the real source of an email.  
- **[VirusTotal](https://www.virustotal.com/)** – Checks links and file attachments against multiple antivirus engines to identify threats.  
- **[Sandbox Analysis](https://www.browserling.com/) / [Any.Run](https://app.any.run/)** – Cloud-based sandboxes that let you safely observe how files and URLs behave when executed.  
- **[OLETools](https://github.com/DidierStevens/DidierStevensSuite/blob/master/oledump.py)** – A toolkit for inspecting Office documents to uncover hidden or malicious macros.  
- **[CyberChef](https://gchq.github.io/CyberChef/)** – A versatile utility for decoding, encoding, and transforming obfuscated data such as Base64 or hex.  
- **[Base64 Decoder](https://gchq.github.io/CyberChef/)** – Converts Base64-encoded text back into its original readable or executable form.  
- **[Whois/IP Lookup](https://whois.domaintools.com/)** – Provides information about a domain’s registration or an IP address’s ownership and reputation.  

## What I Learned   
- Tools like **VirusTotal, Hybrid Analysis, AnyRun, CyberChef, and OLETools** are invaluable for cutting through obfuscation and identifying Indicators of Compromise (IOCs).  
- **Business Email Compromise (BEC)** is one of the most dangerous phishing types because it leverages trust and authority in organizations.  
- Awareness of **suspicious attachments** (e.g., macro-enabled Office files, disguised executables, encrypted zips) is critical for spotting early red flags.  
- Even small businesses without advanced email security tools can greatly benefit from **user awareness training**.  

## Closing Thoughts  
Day 1 gave me a view into how structured and investigative phishing analysis really is. I walked away with more confidence in examining email headers, checking domains, and using online tools to validate suspicious activity.  
