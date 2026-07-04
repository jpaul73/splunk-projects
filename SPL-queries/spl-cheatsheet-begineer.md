# 📘 Basic SPL Cheat Sheet

A quick reference to essential **Search Processing Language (SPL)** commands used in Splunk for log analysis, threat hunting, and SOC investigations.

---

## 🔍 View All Events

Display all indexed events.

```spl
index=*
```

**Use Case:** Verify data ingestion and explore available logs.

---

## 🔐 Failed Logins

Search for failed authentication events.

```spl
index=* EventCode=4625
```

**Use Case:** Detect brute-force or password spraying attempts.

---

## ✅ Successful Logins

Search for successful authentication events.

```spl
index=* EventCode=4624
```

**Use Case:** Monitor user login activity.

---

## 📊 Count Total Events

Count the total number of indexed events.

```spl
index=*
| stats count
```

**Use Case:** Measure overall event volume.

---

## 👤 Failed Logins by User

Identify accounts with the highest number of failed logins.

```spl
index=* EventCode=4625
| stats count by Account_Name
| sort -count
```

**Use Case:** Detect targeted user accounts.

---

## 📋 Display Selected Fields

Create a clean investigation table.

```spl
index=* EventCode=4625
| table _time Account_Name host src_ip
```

**Use Case:** Simplify event review during investigations.

---

## 🌐 Top Source IP Addresses

Display the most active source IPs.

```spl
index=*
| top src_ip
```

**Use Case:** Identify scanners, attackers, or high-volume clients.

---

## ⚙️ Rare Processes

Find uncommon process executions.

```spl
index=*
| rare process_name
```

**Use Case:** Detect suspicious or unusual processes.

---

## 📈 Authentication Timeline

Visualize authentication activity over time.

```spl
index=* EventCode=4625
| timechart count
```

**Use Case:** Identify spikes in failed login attempts.

---

## 📑 Top Event Codes

Display the most common Windows Event IDs.

```spl
index=*
| top EventCode
```

**Use Case:** Understand the distribution of Windows security events.

---

# 📚 Common SPL Commands

| Command | Purpose |
|---------|---------|
| `search` | Filter events matching specific criteria |
| `stats` | Aggregate and summarize data |
| `table` | Display selected fields |
| `top` | Show the most common values |
| `rare` | Show the least common values |
| `timechart` | Visualize trends over time |

---

# 🪟 Common Windows Event IDs

| Event ID | Description |
|----------|-------------|
| **4624** | Successful Logon |
| **4625** | Failed Logon |
| **4688** | Process Creation |

---

# 💼 Skills Demonstrated

- Search Processing Language (SPL)
- Log Analysis
- Authentication Monitoring
- Threat Hunting
- Security Investigations
- SOC Analyst Fundamentals