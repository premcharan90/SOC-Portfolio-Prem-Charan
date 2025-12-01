# Project 4: Network Traffic Analysis  
**SOC Portfolio – Port Scan Detection using Wireshark**

---

## 📌 Overview
This project demonstrates my ability as a SOC Analyst to analyze raw network traffic, detect malicious behavior, extract indicators of compromise (IOCs), and document the incident.

In this project, I investigated a PCAP file containing **TCP SYN port scanning activity**, a common form of reconnaissance used by attackers before launching exploitation attempts.

---

## 🎯 Objectives
- Analyze a PCAP file using Wireshark  
- Identify attacker and victim hosts  
- Detect scanning patterns  
- Extract actionable IOCs  
- Build an attack narrative  
- Map activity to MITRE ATT&CK  
- Document findings in a SOC-style report  

---

## 🧰 Tools Used
- **Wireshark** – Deep packet inspection  
- **tshark** – Command-line packet analysis  
- **VirusTotal / AbuseIPDB** – IP reputation checking  
- **Markdown** – Report documentation  

---

## 🕵️ Highlights From the Investigation

### 🔹 Attacker IP
**202.153.48.66**

### 🔹 Victim IP  
**10.100.18.12**

### 🔹 Ports Scanned  
**22 (SSH), 23 (Telnet), 21 (FTP), 80 (HTTP), 445 (SMB)**

### 🔹 Scan Type  
**TCP SYN Scan** (half-open scan, typical of Nmap)

### 🔹 MITRE ATT&CK Techniques  
| ID | Name |
|----|------|
| **T1046** | Network Service Scanning |
| **T1595** | Active Scanning |

---

## 📎 IOCs Extracted
| Type | Value |
|------|--------|
| Attacker IP | 202.153.48.66 |
| Victim IP | 10.100.18.12 |
| Ports Targeted | 22, 23, 21, 80, 445 |
| Scan Type | SYN Scan |
| Packet Signature | `tcp.flags.syn == 1 && tcp.flags.ack == 0` |

---

## 📘 Deliverables
This project includes the following files:

- **REPORT.md** – Full SOC-style investigation report  
- **screenshots/** – Evidence from Wireshark  
  - SYN packet filter  
  - TCP conversations  
  - Packet details  
- **README.md** (this file)

---

## 📝 Summary
This project demonstrates my capability to:

- Perform packet-level analysis  
- Detect reconnaissance activity  
- Understand attacker behavior  
- Extract technical IOCs  
- Present findings in a clean, SOC-ready report  

This is a core skill required for SOC Level 1 and Level 2 analysts.

---

**Author:** Prem Charan
**Role:** SOC Analyst  

  

