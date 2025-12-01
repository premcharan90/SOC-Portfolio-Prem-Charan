# Network Traffic Analysis Report
**Project:** Project-4_Network-Traffic-Analysis  
**Investigator: Prem Charan 
**PCAP File:** portscan.pcap  
**Date: 1-12-2025

---

## 1. Summary

Analysis of the provided PCAP revealed clear evidence of a **TCP SYN port scan** performed by an external host (**202.153.48.66**) targeting a private network host (**10.100.18.12**).  
The attacker probed multiple well-known ports including **80, 445, 21, 23, and 22**, indicating reconnaissance activity aimed at identifying exposed services or vulnerabilities.

This activity is consistent with automated scanning tools such as **Nmap**, commonly used by attackers before launching exploitation attempts.

---

## 2. Key Findings

- **Attacker IP:** 202.153.48.66  
- **Victim IP:** 10.100.18.12  
- **Scan Type:** TCP SYN Scan  
- **Ports Targeted:**  
  - 22  → SSH  
  - 23  → Telnet  
  - 21  → FTP  
  - 80  → HTTP  
  - 445 → SMB  

- **Attack Characteristics:**
  - High volume of SYN packets  
  - No corresponding ACK packets from victim  
  - Short inter-packet interval (fast scan)  
  - Pattern matches typical Nmap SYN scan fingerprint  

---

## 3. Indicators of Compromise (IOCs)

| Type | Value |
|------|--------|
| Attacker IP | 202.153.48.66 |
| Victim IP | 10.100.18.12 |
| Ports Scanned | 22, 23, 21, 80, 445 |
| Scan Type | TCP SYN Scan |
| Packet Signature | `tcp.flags.syn == 1 && tcp.flags.ack == 0` |
| Tools Suspected | Nmap / masscan |

---

## 4. Attack Narrative

The attacker at IP **202.153.48.66** initiated a sequence of TCP SYN packets toward the victim **10.100.18.12** across several commonly targeted service ports such as **SSH (22), Telnet (23), FTP (21), HTTP (80), and SMB (445)**.  
The SYN packets did **not** result in successful handshakes, suggesting the attacker’s goal was to check which ports respond (open), rather than establish full connections.

This behavior strongly indicates a **reconnaissance phase**, typically conducted using tools like Nmap:

- Rapid-fire SYN probes  
- Minimal follow-up traffic  
- Sequential port targeting  

This reconnaissance helps attackers identify potential entry points for future exploitation.

---

## 5. Evidence (Screenshots to Include)

You should capture the following in your GitHub:

1. **Wireshark SYN Filter Output**
   tcp.flags.syn == 1 && tcp.flags.ack == 0 && ip.src == 202.153.48.66

2. **Statistics → Conversations → TCP Window**
- Shows attacker scanning multiple ports on victim

3. **Packet Detail Screenshot**
- Expand `Internet Protocol` + `Transmission Control Protocol`
- Show source: 202.153.48.66  
  destination: 10.100.18.12  
  destination port: 80

4. **Packet Graph (optional)**
- `Statistics → Flow Graph → TCP`  
- Shows isolated SYN packets

---

## 6. MITRE ATT&CK Mapping

| Technique | Description |
|-----------|-------------|
| **T1046** | Network Service Scanning |
| **T1595** | Active Scanning |
| **T1592** | Gather Victim Host Information |

---

## 7. Recommendations

### **Immediate Actions**
- Block attacker IP `202.153.48.66` at perimeter firewall  
- Add IDS rule to detect future SYN scan patterns  
- Review firewall configuration on victim host (10.100.18.12)

### **Hardening Measures**
- Disable unused services on victim (FTP, Telnet)  
- Restrict SSH access to internal subnets only  
- Enable host-based firewall logging  
- Ensure SMB (445) is not exposed externally  

### **Long-Term Improvements**
- Implement network intrusion detection (Suricata/Snort)  
- Enable rate-limiting / connection throttling  
- Regular vulnerability scanning to detect exposed services  
- Add scanning detection rules in SIEM
