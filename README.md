# Web Application Penetration Test (WebVAPT) Automation Script

This script automates a Web Application Penetration Test (WebVAPT) by running multiple security tools to identify potential vulnerabilities in a target web application.

## Overview

The script performs the following tasks:

- **Nmap Scan**: Basic service enumeration and version detection.
- **Nikto Scan**: Scans the target for common web vulnerabilities.
- **OWASP ZAP Scan**: Active vulnerability scanning using ZAP CLI.
- **SQLMap Scan**: Identifies SQL injection vulnerabilities.

## Getting Started

### Prerequisites

Ensure the following tools are installed and properly configured on your system:

- **Nmap**: Network scanner for service enumeration  
  ```bash
  sudo apt-get install nmap
Nikto: Web server vulnerability scanner

bash
Copy
Edit
sudo apt-get install nikto
OWASP ZAP CLI: Automated scanner for web applications

bash
Copy
Edit
pip install zapcli
SQLMap: SQL injection detection and exploitation tool

bash
Copy
Edit
sudo apt-get install sqlmap
Installation
Clone this repository:

bash
Copy
Edit
git clone https://github.com/yourusername/yourrepository.git
Navigate to the project directory:

bash
Copy
Edit
cd WebVAPT
Grant execute permissions to the script:

bash
Copy
Edit
chmod +x vapt.sh
Usage
Run the script and follow the prompts to enter the target URL or IP:

bash
Copy
Edit
./vapt.sh
Example:
bash
Copy
Edit
./vapt.sh
(Then enter the target when prompted.)

Authorization Disclaimer
This script is intended for authorized security testing only. Do not run this script against systems without explicit authorization. Unauthorized testing is illegal and unethical.

How It Works
User Input Validation: Ensures the target is a valid URL or IP.

User Confirmation: The script asks for confirmation before initiating the test.

Domain Extraction: Extracts the domain name from the target URL.

Directory Setup: Results are stored in a timestamped vapt_results_YYYY-MM-DD_HH:MM:SS directory.

Scan Execution: The following scans are performed:

📡 Nmap Scan: Service detection and vulnerability analysis.

🔎 Nikto Scan: Identifies security vulnerabilities in the target’s web server (only if a URL is provided).

🛡️ OWASP ZAP Scan: Conducts an active scan to detect OWASP Top 10 vulnerabilities (only if a URL is provided).

💥 SQLMap Scan: Attempts to identify and exploit SQL injection vulnerabilities (only if a URL is provided).

Output
All scan results are saved in the dynamically created results directory:

plaintext
Copy
Edit
vapt_results_YYYY-MM-DD_HH:MM:SS/
├── nmap_scan.txt
├── nikto_scan.txt
├── owasp_zap_scan.txt
└── sqlmap_scan/
    └── results.txt
The scan log is available in:

plaintext
Copy
Edit
vapt_results_YYYY-MM-DD_HH:MM:SS/vapt_log.txt
Legal Disclaimer
This script is for educational purposes only. Performing unauthorized penetration tests without consent is illegal and unethical. Always obtain proper authorization before conducting any security tests.

csharp
Copy
Edit
