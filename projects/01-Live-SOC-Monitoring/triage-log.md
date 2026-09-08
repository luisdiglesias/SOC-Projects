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
**Time to Triage:** 30 minutes.

## Alert #2
**Date** September 7 2026
**Alert Title:** SOC143 - Password Stealer Detected
**Severity:** Medium
**Source IP:** 
**Target:**

**Hypothesis:**

**Evidence:**
- 

**Classification:**
**Action Taken:**
**Time to Triage:**
