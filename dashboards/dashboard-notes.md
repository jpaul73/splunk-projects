# 📊 Dashboard Notes

This document explains the dashboards created in this Splunk lab, including their purpose, SPL queries, and how they support web traffic monitoring and security analysis.

---

# 📋 Dashboard Overview

| Screenshot | Description | SPL Query |
|------------|-------------|-----------|
| dashboard-overview.png | Complete HTTP Monitoring Dashboard | Multiple dashboard panels |
| top-source-ips.png | Top client IP addresses generating requests | `index=main \| stats count by clientip \| sort -count` |
| top-destination-ips.png | Destination IPs receiving the most traffic | `index=main \| stats count by dest_ip \| sort -count` |
| top-status-codes.png | Distribution of HTTP response status codes | `index=main \| stats count by status` |
| top-requested-urls.png | Most frequently requested URLs | `index=main \| stats count by uri_path \| sort -count` |
| top-404-errors.png | URLs returning HTTP 404 responses | `index=main status=404 \| stats count by uri_path \| sort -count` |
| request-trend.png | HTTP request volume over time | `index=main \| timechart count` |

---

# 📈 Dashboard Descriptions

## dashboard-overview.png

### Description

Displays the complete HTTP Monitoring Dashboard created in Splunk Enterprise.

### Dashboard Panels

- Top Source IPs
- Top Destination IPs
- HTTP Status Codes
- Top Requested URLs
- Top 404 Errors
- HTTP Request Timeline

### Why It Matters

Provides a centralized view of web server activity, making it easier to identify abnormal traffic patterns and monitor application health.

---

## top-source-ips.png

### Description

Shows the client IP addresses generating the highest number of HTTP requests.

### SPL Query

```spl
index=main
| stats count by clientip
| sort -count
```

### Why It Matters

Useful for identifying:

- High-volume users
- Automated scanners
- Web crawlers
- Potential attackers

---

## top-destination-ips.png

### Description

Displays destination IP addresses receiving the most traffic.

### SPL Query

```spl
index=main
| stats count by dest_ip
| sort -count
```

### Why It Matters

Helps monitor backend servers and identify heavily accessed systems.

---

## dashboard
.png

### Description

Visualizes the distribution of HTTP response codes.

### SPL Query

```spl
index=main
| stats count by status
```

### Why It Matters

Quickly highlights:

- Successful responses (200)
- Redirects (301/302)
- Client errors (404)
- Server errors (500)

---

## top-requested-urls.png

### Description

Lists the most frequently requested web resources.

### SPL Query

```spl
index=main
| stats count by uri_path
| sort -count
```

### Why It Matters

Identifies the most accessed pages and application endpoints.

---

## top-404-errors.png

### Description

Displays URLs generating the highest number of HTTP 404 responses.

### SPL Query

```spl
index=main status=404
| stats count by uri_path
| sort -count
```

### Why It Matters

A large number of 404 responses may indicate:

- Directory enumeration
- Broken links
- Vulnerability scanning
- Reconnaissance attempts

---

## request-trend.png

### Description

Shows the volume of HTTP requests over time.

### SPL Query

```spl
index=main
| timechart count
```

### Why It Matters

Helps analysts identify:

- Traffic spikes
- Peak usage periods
- Unusual request patterns
- Potential denial-of-service activity

---

# 🔄 Dashboard Workflow

```text
HTTP Logs
      │
      ▼
Data Ingestion
      │
      ▼
Splunk Index
      │
      ▼
SPL Queries
      │
      ▼
Dashboard Panels
      │
      ▼
Traffic Monitoring
      │
      ▼
Security Analysis
```

---

# 📂 Related Files

- `queries/basic-spl-cheatsheet.md`
- `queries/intermediate-spl-cheatsheet.md`
- `queries/dashboard-queries.md`
- `reports/dashboard-analysis.md`
- `docs/setup-guide.md`

---

# 💼 Skills Demonstrated

- Dashboard Development
- Search Processing Language (SPL)
- HTTP Log Analysis
- Security Monitoring
- Data Visualization
- SOC Analyst Workflows
- Detection Engineering Fundamentals