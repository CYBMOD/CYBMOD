# Web Application Penetration Test (WebVAPT) Automation Script

This script automates a Web Application Penetration Test (WebVAPT) by running multiple security tools to identify potential vulnerabilities in a target web application.

## Overview
The script performs the following tasks:
1. **Nmap Scan** - Basic service enumeration and version detection.
2. **Nikto Scan** - Scans the target for common web vulnerabilities.
3. **OWASP ZAP Scan** - Active vulnerability scanning using ZAP CLI.
4. **SQLMap Scan** - Identifies SQL injection vulnerabilities.

## Getting Started

### Prerequisites
Ensure the following tools are installed and properly configured on your system:

#### **Nmap: Network scanner for service enumeration**
```bash
sudo apt-get install nmap
```

#### **Nikto: Web server vulnerability scanner**
```bash
sudo apt-get install nikto
```

#### **OWASP ZAP CLI: Automated scanner for web applications**
```bash
pip install zapcli
```

#### **SQLMap: SQL injection detection and exploitation tool**
```bash
sudo apt-get install sqlmap
```

### Installation
1. Clone this repository:
```bash
git clone https://github.com/CYBMOD/CYBMOD.git
```
2. Navigate to the project directory:
```bash
cd WebVAPT
```
3. Grant execute permissions to the script:
```bash
chmod +x vapt.sh
```

## Usage
Run the script and follow the prompts to enter the target URL or IP:
```bash
./vapt.sh
```

Example:
```bash
./vapt.sh
```
(Then enter the target when prompted.)

## Authorization Disclaimer
This script is intended for authorized security testing only. Do not run this script against systems without explicit authorization. Unauthorized testing is illegal and unethical.

## How It Works
1. **User Input Validation**: Ensures the target is a valid URL or IP.
2. **User Confirmation**: The script asks for confirmation before initiating the test.
3. **Domain Extraction**: Extracts the domain name from the target URL.
4. **Directory Setup**: Results are stored in a timestamped `vapt_results_YYYY-MM-DD_HH:MM:SS` directory.
5. **Scan Execution**: The following scans are performed:
   - **📡 Nmap Scan**: Service detection and vulnerability analysis.
   - **🔎 Nikto Scan**: Identifies security vulnerabilities in the target’s web server (only if a URL is provided).
   - **🛡️ OWASP ZAP Scan**: Conducts an active scan to detect OWASP Top 10 vulnerabilities (only if a URL is provided).
   - **💥 SQLMap Scan**: Attempts to identify and exploit SQL injection vulnerabilities (only if a URL is provided).

## Output
All scan results are saved in the dynamically created results directory:
```
vapt_results_YYYY-MM-DD_HH:MM:SS/
├── nmap_scan.txt
├── nikto_scan.txt
├── owasp_zap_scan.txt
└── sqlmap_scan/
    └── results.txt
```

The scan log is available in:
```bash
vapt_results_YYYY-MM-DD_HH:MM:SS/vapt_log.txt
```

## Legal Disclaimer
This script is for educational purposes only. Performing unauthorized penetration tests without consent is illegal and unethical. Always obtain proper authorization before conducting any security tests.

