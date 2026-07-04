# 🔍 Threat Hunting SPL Cheat Sheet

A collection of commonly used **Search Processing Language (SPL)** queries for identifying suspicious activity in Splunk. These examples demonstrate practical techniques used during threat hunting and security investigations.

---

## 🎯 Failed Login Activity

Detect accounts with multiple failed authentication attempts.

```spl
index=* EventCode=4625
| stats count by Account_Name
| sort -count
```

**Use Case:** Detect brute-force or password spraying attacks.

---

## 🔑 Failed Login Followed by Success

Identify accounts that experience multiple failed logins before a successful authentication.

```spl
index=* (EventCode=4624 OR EventCode=4625)
| transaction Account_Name maxspan=15m
```

**Use Case:** Investigate potential credential compromise.

---

## 🌐 Top Source IP Addresses

Display the most active source IP addresses.

```spl
index=*
| top src_ip limit=20
```

**Use Case:** Detect scanners, automated tools, or high-volume clients.

---

## ⚙️ Process Creation Activity

Monitor newly created processes.

```spl
index=* EventCode=4688
| stats count by New_Process_Name
| sort -count
```

**Use Case:** Identify unusual or suspicious process execution.

---

## 💻 PowerShell Activity

Search for PowerShell execution events.

```spl
index=* powershell
```

**Use Case:** Detect administrative activity or malicious PowerShell usage.

---

## 📈 Authentication Trend

Visualize authentication events over time.

```spl
index=* EventCode=4624
| timechart count
```

**Use Case:** Identify spikes in login activity or unusual authentication patterns.

---

# 📌 Common Windows Event IDs

| Event ID | Description |
|----------|-------------|
| **4624** | Successful Logon |
| **4625** | Failed Logon |
| **4688** | Process Creation |
| **4720** | User Account Created |
| **4728** | User Added to Security Group |

---

# 🛡️ Threat Hunting Workflow

1. Define a hunting hypothesis.
2. Search relevant log sources.
3. Identify anomalies.
4. Validate findings.
5. Document evidence.
6. Escalate if required.

---

# 💼 Skills Demonstrated

- Threat Hunting
- Search Processing Language (SPL)
- Log Analysis
- Detection Engineering
- Windows Security Monitoring
- Incident Investigation