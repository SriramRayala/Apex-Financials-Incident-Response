# Apex-Financials-Incident-Response
Part 1: Spear-phishing &amp; ransomware attack report (INC250306)  Part 2: Web server compromise with c99shell backdoor (INC250422)

# 🛡️ Apex Financials – Incident Response Report (Part 1 & Part 2)

This repository documents two separate but high-impact cybersecurity incidents that occurred at Apex Financials. These incidents were investigated using industry-standard tools (Splunk, Wireshark, IDS, firewall analysis) and mapped to MITRE ATT&CK tactics.

---

## 📁 Repository Structure

| File Name | Description |
|-----------|-------------|
| `INC250306_5689_Group1_Report_Part1.pdf` | Part 1: Full technical report on a spear-phishing attack leading to ShadowCrypt ransomware |
| `Project_Part1_Resource_INC250306_5689.pdf` | Part 1: Task description, scope, and objectives from faculty |
| `INC40122_5689_Group_1_Report_Part2.pdf` | Part 2: Full analysis of a web server compromise involving web shells and data exfiltration |
| `Project_Part2_Resource.pdf` | Part 2: Network diagram, asset roles, and context |
| `Project_Part2_Resource_INC250422.pptx` | Part 2: Source logs and attack hints (PowerPoint format) |
| `Project_Part2_Resource_readme.txt` | Part 2: XOR decoding clue or assignment identifier |
| `Project_Presentation_Report2.pdf` | Part 2: Final presentation with visual summary and key takeaways |

---

## 🔍 Part 1: ShadowCrypt Ransomware Attack (INC250306)

- Initial Vector: Spear-phishing email with malicious PDF
- Target: WORKSTATION-01 (`apexfinancial\analyst1`)
- Execution Technique: Malicious macro (MITRE T1204.002)
- Credential Compromise: Brute force, pass-the-hash attack (T1110, T1550.002)
- Lateral Movement: WMI, PsExec
- Final Payload: ShadowCrypt ransomware on `192.168.1.200`
- Persistence: Scheduled tasks created for long-term access (T1053.005)
- IOCs:
  - Malicious PDF: `Q1 Performance Review.pdf`
  - C2 IP: `185.143.223.47`
  - Registry & Scheduled Task modifications
- Business Impact: Operational disruption, IP theft risk, loss of financial records

---

## 🔎 Part 2: Web Server Compromise & Data Exfiltration (INC250422)

- Initial Entry: Brute-force login to `/login.php`
- Exploitation:
  - SQL Injection
  - File upload of `c99shell.php` and `eval-stdin.php`
- Command Execution: `cmd=ls`, `cmd=whoami` via PHP shell
- Data Exfiltration:
  - Over 50GB of sensitive data exfiltrated to `167.172.3.114`
  - Included `db_config.php`, `backup.tar.gz`, and `.csv/.xls` files
- Logs Analyzed:
  - `access.log`
  - `IDS_logs.txt`
  - `FW_logs.txt`
- Mapped MITRE Techniques:
  - T1110 – Brute Force
  - T1505.003 – Web Shell
  - T1059.003 – PHP Execution
  - T1041 – Exfiltration over HTTP

---

## 🛠️ Tools & Techniques Used

- Splunk: Log query correlation and timeline reconstruction
- Firewall and IDS logs: Confirmed exploitation and data movement
- YARA / ClamAV / Sysmon / Wazuh: Detection and containment (simulated)
- Security Onion: Perimeter telemetry
- PowerShell & Linux CLI: Forensic preservation, system hardening

---

## 📑 Lessons Learned

- Spear-phishing must be countered with advanced email filtering and training
- Input validation, WAF, and PHP hardening are critical for web apps
- MFA and endpoint telemetry must be enforced for all privileged systems
- Forensic readiness (image capture, log hashing) is essential for incident response

---

## 👨‍💻 Authors

Sriram R, Leela Pavan, Shalem Raju, SriVarsha A, Junaid M, Phanindhar Reddy K  
Master’s in Cybersecurity & Digital Forensics  
University at Albany, SUNY — Spring 2025

---

## 📄 License

This project is licensed under the  
**Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0)

📌 You may view and share this work with proper credit, but you may not modify it or use it commercially.

🔗 [View License Terms](https://creativecommons.org/licenses/by-nc-nd/4.0/)
