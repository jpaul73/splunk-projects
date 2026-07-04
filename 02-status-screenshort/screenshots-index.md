# 📸 Dashboard Screenshots Index

This document explains each dashboard screenshot included in this project, including what it displays, the SPL query used to generate it, and why it is valuable for security monitoring and analysis.

---

# 📋 Screenshots Overview

| Screenshot | Description | SPL Query |
|------------|-------------|-----------|
| dashboard-overview.png | Complete HTTP Monitoring Dashboard | Multiple dashboard panels |
| top-source-ips.png | Source IPs generating the highest number of requests | `index=main | stats count by clientip | sort -count` |
| top-destination-ips.png | Destination IPs receiving the highest number of requests | `index=main | stats count by dest_ip | sort -count` |
| top-status-codes.png | Distribution of HTTP response status codes | `index=main | stats count by status` |
| top-requested-urls.png | Most frequently requested URLs | `index=main | stats count by uri_path | sort -count` |
| top-404-errors.png | URLs generating the most 404 (Not Found) responses | `index=main status=404 | stats count by uri_path | sort -count` |
| request-trend.png | HTTP request volume over time | `index=main | timechart count` |

---

# 📊 Screenshot Details

---

## status-1.png

### Description

This screenshot displays the complete HTTP Monitoring Dashboard built in Splunk Enterprise.

The dashboard combines multiple visualizations to provide a high-level overview of web traffic, client activity, server responses, and request trends.

### Dashboard Panels

- Top Source IPs
- Top Destination IPs
- HTTP Status Codes
- Top Requested URLs
- HTTP Request Timeline
- Top 404 Errors

### Why It Matters

This dashboard enables analysts to quickly identify:

- High-volume clients
- Frequently accessed resources
- Error trends
- Suspicious request activity
- Overall web traffic behavior

---

## status-1.png

### Description

Displays the IP addresses generating the highest number of HTTP requests.

### SPL Query

```spl
index=main
| stats count by clientip
| sort -count
```

### Why It Matters

Helps identify:

- Heavy users
- Web crawlers
- Scanners
- Potential attackers

---

## status2.png

### Description

Shows which destination IP addresses receive the most requests.

### SPL Query

```spl
index=main
| stats count by dest_ip
| sort -count
```

### Why It Matters

Useful for:

- Monitoring server traffic
- Identifying heavily accessed servers
- Detecting unusual communication patterns

---

## status2.png

### Description

Displays the distribution of HTTP response codes.

### SPL Query

```spl
index=main
| stats count by status
```

### Why It Matters

Allows analysts to monitor:

- Successful requests (200)
- Redirects (301,302)
- Client errors (404)
- Server errors (500)

---

## status2.png

### Description

Lists the most frequently requested web resources.

### SPL Query

```spl
index=main
| stats count by uri_path
| sort -count
```

### Why It Matters

Useful for identifying:

- Popular resources
- Web application hotspots
- Frequently accessed endpoints

---

## top-404-errors.png

### Description

Shows URLs that generated the highest number of HTTP 404 responses.

### SPL Query

```spl
index=main status=404
| stats count by uri_path
| sort -count
```

### Why It Matters

A high number of 404 responses may indicate:

- Directory enumeration
- Broken links
- Automated scanners
- Reconnaissance activity

---

## spl.png

### Description

Visualizes the number of HTTP requests over time.

### SPL Query

```spl
index=main
| timechart count
```

### Why It Matters

Helps analysts detect:

- Traffic spikes
- Unusual activity
- Peak usage periods
- Potential denial-of-service events

---

# 📂 Related Files

| File | Purpose |
|------|---------|
| `dashboards/http-dashboard.xml` | Exported Splunk dashboard |
| `queries/http-searches.md` | HTTP monitoring SPL queries |
| `reports/dashboard-analysis.md` | Dashboard analysis report |
| `docs/setup-guide.md` | Splunk installation and configuration |

---

# 🎯 Learning Objectives

This dashboard demonstrates practical experience with:

- Splunk Dashboard Development
- Search Processing Language (SPL)
- HTTP Log Analysis
- Security Monitoring
- Web Traffic Visualization
- Detection Engineering
- SOC Analyst Workflows

---

**Author:** Paul Doniyal  
**Project:** Splunk HTTP Monitoring Lab