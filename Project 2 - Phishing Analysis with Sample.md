# Project 2 – Phishing Analysis Challenge (Sample 1)

On Day 2 of the phishing analysis challenge, we moved beyond the theory and got hands-on with a real-world scenario. Our instructor, [Rajneesh G.](https://www.linkedin.com/in/rajneeshgupta01/) provided a sample suspicious email for us to investigate. It wasn’t known if it was phishing or a legitimate message.  

The email appeared to come from a credit card company and claimed that the recipient had **92,990 reward points** that were about to expire. Naturally, this type of message could catch a user’s attention and push them to act quickly, whether by trying to redeem the points or clicking on a provided link. That “too good to miss” urgency is exactly what makes this kind of email suspicious.  

From the provided scenario, this was sent to an employee and submitted to the security team. As a SOC analyst, this is where I step in. My task was to take this email and begin analyzing the message to determine whether it was a phishing attempt or a genuine communication.  

This exercise really highlighted how phishing investigations often start with very little information. The challenge for me was to apply the process I learned on Day 1: check the headers, analyze the sender’s domain, review the content, and investigate any links before making a determination.  

## **Lab Task: Analyze the Suspicious Email**

### Scenario:  
You received an email from **BANCO DO BRADESCO LIVELO** claiming that your card has **92,990 points expiring today**, sent from `banco.bradesco@atendimento.com.br`. 

Investigate and answer the following:

### 🔍 **Questions:**

**What is the full email address of the sender?**  

- The email came from banco.bradesco@atendimento.com.br. This stood out because the domain didn’t seem to align with a trusted source.

<img width="980" height="255" alt="image" src="https://github.com/user-attachments/assets/ba77b329-a6eb-4990-90b9-d1f2157a1508" />

**What domain is used to send this email?**

- The domain is the same as from the email address from the first question, atendimento.com.br.

<img width="627" height="47" alt="image" src="https://github.com/user-attachments/assets/e6037d44-a3e1-4cb6-a416-2b3f766ffd8f" />

**What is the sender’s IP address from the header?**  

- I will look at the first IP address from the Hops section. The answer is 137.184.34.4

<img width="1523" height="420" alt="image" src="https://github.com/user-attachments/assets/c3d8b097-684f-405b-b41f-93ddaa51dcda" />


**Is the sender IP blacklisted?** (Check using AbuseIPDB or VirusTotal – Answer Yes/No)  

- The answer is uncertain after searching the IP address in VirusTotal and AbuseIPDB. VirusTotal returned 1 of 95 reported malicious and AbuseIPDB 0% confidence rating as being abusive, however, it has beeen reported 10 times for abusive activities.

<img width="1362" height="453" alt="image" src="https://github.com/user-attachments/assets/f8163af3-bebb-4972-a459-207ece717e60" />
<img width="690" height="698" alt="image" src="https://github.com/user-attachments/assets/047065f8-ce1b-424e-b3e2-0edd27844395" />

**What is the result of SPF authentication?** (Pass / Fail / Neutral)  

- Sender Policy Framework (SPF) is an email authentication method designed to reduce spam and spoofing. Its primary purpose is to verify that the mail exchange server’s IP address is authorized to send messages on behalf of a given domain. When SPF validation fails, the email typically does not reach the inbox and is instead delivered to the junk or spam folder. In corporate environments, these emails are often quarantined automatically to prevent users from accidentally interacting with potentially harmful content.
  
- The SPF result came back as a temperror, which means the receiving server couldn’t complete the DNS lookup to verify if the sending IP 137.184.34.4 was authorized. The DKIM check shows “none,” meaning the message wasn’t signed by the domain, making it easier to spoof. Finally, Microsoft’s Composite Authentication (compauth) gave a hard fail, meaning the combination of SPF, DKIM, and DMARC didn’t align and the sender could not be authenticated. Taken together, these results strongly suggest the email is suspicious and likely spoofed.

<img width="1535" height="66" alt="image" src="https://github.com/user-attachments/assets/96f8c6de-d10b-4cc4-bbef-7ca7c7c099bc" />
<img width="792" height="491" alt="image" src="https://github.com/user-attachments/assets/19006286-01cc-4644-afd5-275f51baf426" />

**What is one suspicious URL or link found in the email body?**

<img width="996" height="186" alt="image" src="https://github.com/user-attachments/assets/8f94d4e9-8b7c-4e59-87cf-048dfb480ee3" />

## By the end of the lab, I had practiced:  
- Extracting sender details, domains, and IPs from headers  
- Checking IP and domain reputation using VirusTotal and AbuseIPDB  
- Verifying SPF authentication and recognizing failures as warning signs  
- Identifying suspicious URLs from email bodies and testing their reputations  

Day 2 helped me build confidence in taking apart a phishing email from multiple angles. It felt less about guessing and more about applying a **structured, repeatable process**. Most importantly, I learned that phishing detection isn’t just about spotting obvious red flags — it’s about connecting technical details (headers, IPs, SPF, URLs) with investigative reasoning to decide whether an email is safe or malicious.  
