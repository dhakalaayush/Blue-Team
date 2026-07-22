# Boss of the SOC (BOTSv1) - Threat Hunting Investigation with Splunk

## Project Overview
This repository contains a comprehensive Blue Team threat hunting investigation utilizing **Splunk Enterprise** to analyze the Boss of the Splunk version 1 (BOTSv1) dataset. The project includes investigation on a multi-stage cyberattack against Wayne Enterprises' infrastructure, where the attacker was responsible for defacement of a Joomla-based web server.

# Tool used
- Splunk Enterprise

## Telemtry
- Windows Event Logs
- Sysmon
- IIS Web Server Logs
- Network Streams
- Fortinet Firewall Logs
- Suricata IDS Alerts

# Investigation Methodology
The threat hunting was structured according to cyber kill chain, i.e. the attacker progression.
1.  **Reconnaissance:** Identifying automated vulnerability scanning (Acunetix) targeting the web infrastructure.
2.  **Delivery:** Tracking a high-volume brute-force attack originating from a secondary IP address against the Joomla administrator portal.
3.  **Exploitation:** Analyzing malicious post-authentication enumeration using the `com_extplorer` Joomla component.
4.  **Installation:** Verifying the upload and execution of a malicious payload (`3791.exe`) leveraging Sysmon Event ID 1 (Process Creation) and file hash analysis.
5.  **Action on Objectives:** Confirming the final defacement of the web server (`poisonivy-is-coming-for-you-batman.jpeg`).

## Key Findings
1.	The attacker (40.80.148.42) used free edition of Acunetix Web Vulnerability Scanner to scan vulnerabilities in the website iamreallynotbatman.com (192.168.250.70). The website was also using the CMS Joomla.
2.	The attacker tried to brute-force using the IP address 23.22.63.114.
3.	The attacker uses the server with the domain name prankglassinebracket.jumpingcrab.com to upload malware or deface the website.
4.	The attacker defaced the website by posting the image poisonivy-is-coming-for-you-batman.jpeg.
