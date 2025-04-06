# Web Application Penetration Test (WebVAPT) Automation Script

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Build Status](https://github.com/CYBMOD/CYBMOD/actions/workflows/main.yml/badge.svg)
![Security](https://img.shields.io/badge/security-tested-green)

This script automates a Web Application Penetration Test (WebVAPT) using popular security tools to identify potential vulnerabilities in a target web application.

---

## 📌 Overview

The script performs the following key tasks:

1. **Nmap Scan** – Service enumeration and vulnerability analysis.
2. **Nikto Scan** – Web server vulnerability scan.
3. **OWASP ZAP Scan** – Active scanning for OWASP Top 10 issues.
4. **SQLMap Scan** – Detects and attempts to exploit SQL injection vulnerabilities.

---

## 🚀 Getting Started

### 🔧 Prerequisites

Ensure the following tools are installed:

- **Nmap** – Network scanner  
  `sudo apt-get install nmap`

- **Nikto** – Web server vulnerability scanner  
  `sudo apt-get install nikto`

- **OWASP ZAP CLI** – Web app scanner  
  `pip install zapcli` *(or install via ZAP Desktop and CLI wrapper)*

- **SQLMap** – SQL injection testing tool  
  `sudo apt-get install sqlmap`

---

### 💾 Installation

```bash
# Clone the repository
git clone https://github.com/CYBMOD/CYBMOD.git

# Navigate to the script directory
cd CYBMOD

# Grant execute permissions
chmod +x final.sh
```

---

## ⚙️ Usage

Run the script and follow the prompt to enter a target URL or IP:

```bash
./final.sh
```

**Example:**

```bash
./final.sh
Enter the target (URL or IP address): http://example.com
Do you want to perform this test? (yes/no): yes
```

---

## 🔐 Authorization Disclaimer

> This script is intended for authorized security assessments **only**.  
> **Do not** run it against any system without explicit permission.  
> Unauthorized testing is **illegal** and **unethical**.

---

## 🛠️ How It Works

1. **Input Validation** – Ensures valid URL or IP is entered.
2. **User Confirmation** – Asks for consent before running scans.
3. **Domain Extraction** – Derives domain from the input if URL.
4. **Directory Setup** – Creates a results directory using a timestamp.
5. **Scan Execution** – Performs:
    - 📡 **Nmap Scan**
    - 🔎 **Nikto Scan** (if URL)
    - 🛡️ **OWASP ZAP Scan** (if URL)
    - 💥 **SQLMap Scan** (if URL)

---

## 📁 Output Structure

Results are stored in a directory named:

```
vapt_results_YYYY-MM-DD_HH:MM:SS/
```

With the following files:

```
├── nmap_scan.txt
├── nikto_scan.txt
├── owasp_zap_scan.txt
├── sqlmap_scan/
│   └── results.txt
└── vapt_log.txt
```

---

## ⚖️ Legal Disclaimer

This script is provided for **educational** and **authorized testing** purposes only.  
You **must** obtain proper permission before testing any system.

> Use responsibly. Stay ethical. Hack the right way. 🛡️
