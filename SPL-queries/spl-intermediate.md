# ⚡ Intermediate SPL Cheat Sheet

A quick reference for intermediate **Search Processing Language (SPL)** commands commonly used by SOC analysts, threat hunters, and detection engineers.

---

## 📝 eval

Create or modify fields.

```spl
index=* EventCode=4625
| eval severity="High"
| table _time Account_Name severity
```

**Use Case:** Assign severity levels or calculate new values.

---

## 🔄 dedup

Remove duplicate events or field values.

```spl
index=*
| dedup src_ip
| table src_ip
```

**Use Case:** Display unique IP addresses or users.

---

## 🎯 rex

Extract values from raw logs using regular expressions.

```spl
index=*
| rex field=_raw "(?<ip>\d+\.\d+\.\d+\.\d+)"
| table ip
```

**Use Case:** Extract IP addresses, usernames, email addresses, or custom fields.

---

## 🔗 transaction

Group related events into a single transaction.

```spl
index=* (EventCode=4624 OR EventCode=4625)
| transaction Account_Name maxspan=15m
```

**Use Case:** Investigate failed logins followed by successful authentication.

---

## 📚 lookup

Enrich events using external lookup tables.

```spl
index=*
| lookup malicious_ips.csv ip AS src_ip OUTPUT threat_level
```

**Use Case:** Compare logs against threat intelligence feeds.

---

## 📊 stats

Aggregate and summarize data.

```spl
index=*
| stats count by Account_Name
```

**Use Case:** Count events, identify top users, or summarize activity.

---

## 📈 sort

Sort search results.

```spl
index=*
| stats count by src_ip
| sort -count
```

**Use Case:** Display the highest or lowest values first.

---

## 🔍 where

Filter results based on conditions.

```spl
index=*
| stats count by src_ip
| where count > 10
```

**Use Case:** Detect suspicious activity above a defined threshold.

---

# 🚨 Investigation Examples

## Brute Force Detection

```spl
index=* EventCode=4625
| bucket _time span=5m
| stats count by src_ip _time
| where count >= 10
```

**Purpose:** Detect repeated failed logins from a single IP address.

---

## Lateral Movement Detection

```spl
index=* EventCode=4624 Logon_Type=3
| stats dc(host) as systems by Account_Name
| where systems >= 3
```

**Purpose:** Identify accounts authenticating across multiple systems.

---

# 📋 Command Summary

| Command | Description |
|---------|-------------|
| `eval` | Create or modify fields |
| `dedup` | Remove duplicate events |
| `rex` | Extract fields using regular expressions |
| `transaction` | Group related events |
| `lookup` | Enrich data from lookup tables |
| `stats` | Aggregate and summarize data |
| `sort` | Order search results |
| `where` | Filter results based on conditions |

---

# 💼 Skills Demonstrated

- Intermediate SPL
- Log Enrichment
- Field Extraction
- Detection Engineering
- Threat Hunting
- Security Investigations
- IOC Matching
- SOC Analyst Workflows