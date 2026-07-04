# 🚀 Splunk Enterprise Installation on Windows 11

> A step-by-step guide to installing **Splunk Enterprise 10.4.0** on **Windows 11** for SOC analysts, detection engineers, and cybersecurity enthusiasts.
---

## 📋 Project Information

| Item | Details |
|------|---------|
| **Author** | Paul Doniyal |
| **Platform** | Windows 11 (64-bit) |
| **Splunk Version** | Splunk Enterprise 10.4.0 |
| **Installation Time** | 10–15 Minutes |
| **Status** | ✅ Successfully Installed |

---

# 📌 Overview

Splunk Enterprise Free allows users to ingest **500 MB of data per day** without purchasing a license.

It includes full **Search Processing Language (SPL)** functionality, making it perfect for:

- 🛡 SOC Analyst Practice
- 🔍 Threat Hunting
- 📊 Log Analysis
- ⚙ Detection Engineering
- 🚨 SIEM Training
- 🧪 Home Lab Projects

> **Note**
>
> The Free license includes all core SPL features required for learning and practicing Splunk.

---

# ✅ Prerequisites

Before starting, ensure you have:

| Requirement | Recommended |
|-------------|------------|
| Operating System | Windows 11 (64-bit) |
| RAM | 8 GB Minimum (16 GB Recommended) |
| Disk Space | 10 GB Free |
| Internet Connection | Required |
| Administrator Rights | Required |

---

# 📥 Download Splunk Enterprise

1. Visit the official Splunk download page.

   https://www.splunk.com/en_us/download/splunk-enterprise.html

2. Create a free Splunk account.

3. Select:

   - Windows

4. Download:

   - **Splunk Enterprise (.msi)**

**Download Size**

Approximately **450 MB**

---

# 🛠 Installation Steps

## Step 1 — Launch the Installer

- Double-click the downloaded `.msi` installer.
- Accept the User Account Control (UAC) prompt.
- The Splunk Setup Wizard opens.

---

## Step 2 — Accept the License

- Accept the License Agreement.
- Select:

  - **Splunk Enterprise Free License**

- Click **Next**.

---

## Step 3 — Configure Administrator Credentials

Create your administrator account.

| Setting | Example |
|---------|---------|
| Username | admin |
| Password | Strong Password |

> **Important**
>
> Save your administrator password securely. Password recovery is difficult without reinstalling Splunk.

---

## Step 4 — Select Installation Directory

Default installation path:

```text
C:\Program Files\Splunk
```

Recommended:

- Keep the default installation path.

Click **Install**.

---

## Step 5 — Complete Installation

Installation takes approximately **10–15 minutes**.

When finished:

- ✔ Launch browser with Splunk Enterprise

Click **Finish**.

---

# 🌐 Access Splunk Web

Open your browser and navigate to:

```text
http://localhost:8000
```

If the browser doesn't open automatically:

1. Open any browser.
2. Enter:

```text
http://localhost:8000
```

---

# 🔐 First Login

Log in using the credentials created during installation.

| Field | Value |
|--------|-------|
| Username | admin |
| Password | Your Password |

After login, the Splunk Home Dashboard will load successfully.

---

# ✅ Verify Installation

| Check | Verification | Expected Result |
|---------|-------------|----------------|
| Splunk Web | Open localhost:8000 | Dashboard Loads |
| Login | Admin Account | Successful |
| Search | Run `index=*` | Events Displayed |
| Splunk Service | Check SplunkD | Running |

---

# ⚙ Managing Splunk Services

## Using Command Prompt

Open **Command Prompt** as Administrator.

Navigate to:

```powershell
cd "C:\Program Files\Splunk\bin"
```

### Start Splunk

```powershell
splunk start
```

### Stop Splunk

```powershell
splunk stop
```

### Restart Splunk

```powershell
splunk restart
```

---

## Using Windows Services

1. Press **Windows + R**

2. Type:

```text
services.msc
```

3. Locate:

```
SplunkD
```

4. Right-click the service.

5. Select:

- Start
- Stop
- Restart

---

# 🔗 Useful Splunk URLs

| URL | Purpose |
|------|---------|
| http://localhost:8000 | Splunk Home |
| http://localhost:8000/en-US/app/search | Search & Reporting |
| http://localhost:8000/en-US/manager/search/data/inputs | Data Inputs |
| http://localhost:8000/en-US/app/search/dashboards | Dashboards |

---

# 📂 Splunk Directory Structure

```text
C:\Program Files\Splunk\
│
├── bin\
│   ├── splunk.exe
│   └── CLI Tools
│
├── etc\
│   ├── apps\
│   └── system\
│
├── var\
│   └── log\
│       └── splunk\
│
└── share\
```

---

# 📚 Core Splunk Concepts

| Concept | Description |
|----------|-------------|
| Index | Stores searchable event data |
| Sourcetype | Defines the format of ingested logs |
| Host | Device generating the events |
| SplunkD | Background service that powers Splunk |
| Splunk Web | Browser interface for administration |
| Search & Reporting | Primary workspace for SPL searches |

---

# 🔍 Basic SPL Queries

## View All Indexed Events

```spl
index=*
```

---

## Count Events by Sourcetype

```spl
index=* | stats count by sourcetype
```

---

## View Internal Splunk Logs

```spl
index=_internal | stats count by sourcetype
```

---

# 🛠 Troubleshooting

| Problem | Solution |
|----------|----------|
| Splunk Web not loading | Verify SplunkD service is running |
| Cannot log in | Check username and password |
| Port 8000 unavailable | Ensure another application isn't using the port |
| No search results | Verify data has been indexed |

---

# 🎯 Key Takeaways

- ✅ Installed Splunk Enterprise on Windows 11
- ✅ Accessed the Splunk Web interface
- ✅ Verified the SplunkD background service
- ✅ Executed basic SPL searches
- ✅ Learned the Splunk directory structure
- ✅ Prepared the environment for log analysis and threat hunting

---

# 💼 Skills Practiced

- Splunk Enterprise Installation
- Windows Administration
- Splunk Service Management
- Search Processing Language (SPL)
- Log Analysis
- SIEM Fundamentals
- SOC Analyst Lab Setup
- Detection Engineering Basics

---

## ⭐ Support

If you found this guide helpful, consider giving this repository a **⭐ Star**.

It helps others discover the project and supports future cybersecurity lab content.

---


This project is for **educational and learning purposes**.