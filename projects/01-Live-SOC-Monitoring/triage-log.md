# SOC Alert Triage Log

## Alert #1 
**Date:** September 7 2026
**Alert Title:** SOC325 - Unauthorized Cloud Region Access Attempt Detected
**Severity:** Low
**Source IP:**  134.209.145.73 (External/DigitalOcean)
**Target:** 52.15.206.21 (AWS_Services Endpoint)

**Hypothesis:** External attacker attempting a brute-force/credential stuffing attack.

**Evidence:**
- Searched the source IP (134.209.145.73) in Log Management. Found over 50 requests to /accounts/login. All attempts returned a 403 status code and the action was blocked.
- Investigated the destination IP (52.15.206.21) within Endpoint Security. Verified zero succesful connections were stablished by the attacker.
- Looked up the source IP on VirusTotal. It has been flagged for phishing and malicious activity.

**Classification:**  True Positive 

**Action Taken:** No Endpoint containment was required as the firewall successfully blocked all login attempts. Password for targeted user (test@letsdefend.io) was changed. 

**Time to Triage:** 10 minutes.

## Alert #2
**Date** September 7 2026
**Alert Title:** SOC143 - Password Stealer Detected
**Severity:** Medium
**Source IP:** 180.76.101.229 (bill@microsoft.com)
**Target:** ellie@letsdefend.io

**Hypothesis:** External threat actor is spoofing a Microsoft email address to deliver a malicious file designed to steal employee credentials.

**Evidence:**
- The email address of the sender claims to be bill@microsft.com. The SMTP IP (180.76.101.229) belongs to Baidu Netcom Science and Technology Co. located in Beijing, China, confirming the sender address is spoofed.
- The email contains no subject and no text, only a .zip attachment. Upon closer inspection of the file using VirusTotal, the file was flagged by multiple vendors as malware phishing.
- The email bypassed the spam filters and reached the users inbox. Reviewed Log Management and Endpoint logs to check for outbound connections to any of the IP addresses associated with the malicious file. Zero connections were found, confirming the user did not open the attachment.

**Classification:** True Positive (Phishing attempt)

**Action Taken:** Deleted the malicious email from the users inbox to prevent future interactions. Blocked the senders IP address and updated the spam filter rules.

**Time to Triage:** 20 minutes.
