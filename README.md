# Splunk HTTP Log Analysis Dashboard

A hands-on Splunk project focused on analyzing HTTP server logs through an interactive dashboard. The project demonstrates how raw web server logs can be transformed into actionable insights using Splunk Search Processing Language (SPL) and data visualizations.

---

## Project Overview

This dashboard provides visibility into HTTP traffic by identifying high-volume source IPs, monitoring destination IP activity, analyzing HTTP response codes, and highlighting common client errors such as **400 (Bad Request)** and **404 (Not Found)** responses.

The goal of this project is to practice:

- HTTP log analysis
- Splunk Search Processing Language (SPL)
- Dashboard development
- Security monitoring
- Data visualization

---

## Dashboard Preview

> Replace these images with your own screenshots.

### Dashboard Overview

![Dashboard](dashboard.png)

---

## Dashboard Features

### Top Source IPs by Request Volume
- Identify clients generating the highest number of HTTP requests.
- Detect unusually active hosts.

---

### Top Destination IPs
- Monitor the destination servers receiving the highest traffic.
- Identify heavily accessed services.

---

### Most Requested HTTP 404 Resources
- Discover resources frequently requested but not found.
- Identify broken links or reconnaissance activity.

---

### Top Bad Request (HTTP 400) Source IPs
- Detect malformed requests.
- Identify potentially suspicious or misconfigured clients.

---

### HTTP Response Distribution
- Analyze the overall distribution of HTTP response codes.
- Understand server response behavior.

---

## Technologies Used

| Technology | Purpose |
|------------|---------|
| Splunk Enterprise | Log Management |
| SPL | Query Language |
| HTTP Server Logs | Dataset |
| Dashboard Studio / Classic Dashboard | Visualization |

---

## Sample SPL Queries

### Top Source IPs

```spl
index=http_logs
| top src_ip
```

### Top Destination IPs

```spl
index=http_logs
| top dest_ip
```

### HTTP Response Distribution

```spl
index=http_logs
| top res
```

### Top HTTP 404 Requests

```spl
index=http_logs res=404
| top uri
```

### Top Bad Requests

```spl
index=http_logs res=400
| top src_ip
```

---

## Skills Demonstrated

- Log Analysis
- Splunk Dashboard Development
- Search Processing Language (SPL)
- HTTP Traffic Monitoring
- SIEM Fundamentals
- Network Traffic Analysis
- Security Monitoring
- Data Visualization

---

## Repository Structure

```
splunk-http-log-analysis/
│
├── README.md
├── images/
│   ├── dashboard-overview.png
│   ├── top-source-ips.png
│   ├── top-destination-ips.png
│   ├── response-distribution.png
│   ├── http-404-analysis.png
│   └── bad-request-analysis.png
│
├── queries/
│   ├── top_source_ips.spl
│   ├── top_destination_ips.spl
│   ├── response_distribution.spl
│   ├── http_404_analysis.spl
│   └── bad_request_analysis.spl
│
└── docs/
    └── dashboard-report.pdf
```

---

## Future Improvements

- Dashboard filters
- Time range selector
- Geo-IP visualization
- User-Agent analysis
- HTTP method analysis
- Response time monitoring
- Alert creation
- Threat hunting dashboards

---

## Learning Outcomes

This project helped strengthen my understanding of:

- Splunk Search Processing Language (SPL)
- Dashboard creation
- HTTP server log analysis
- Web traffic monitoring
- Data visualization
- Security event analysis

---

## Connect With Me

If you have suggestions or feedback, feel free to connect with me on LinkedIn or open an issue in this repository.

---

⭐ If you found this project helpful, consider giving it a star.
