# Cybmod2 - Web Application Penetration Testing Script

Cybmod2 is a Bash script designed to automate basic Web Application Vulnerability and Penetration Testing (WebVAPT) tasks. It performs reconnaissance and vulnerability scanning on a target (URL or IP address) using popular tools like Nmap, Nikto, OWASP ZAP, and SQLmap. This script is intended for educational purposes and authorized security testing only.

> **Disclaimer**: Use this tool responsibly and only on systems you have explicit permission to test. Unauthorized scanning or testing may violate laws and regulations.

---

## Features
- Validates user-provided targets (URL or IP address).
- Performs basic enumeration with Nmap.
- Scans for web server vulnerabilities using Nikto (for URLs).
- Conducts active web application scanning with OWASP ZAP (for URLs).
- Tests for SQL injection vulnerabilities using SQLmap (for URLs).
- Organizes results in a timestamped output directory.

---

## Prerequisites
Before running `Cybmod2.sh`, ensure the following tools are installed on your system:
- **Nmap**: For network enumeration and service detection.
  - Install: `sudo apt install nmap` (Debian/Ubuntu) or `sudo yum install nmap` (CentOS/RHEL)
- **Nikto**: For web server vulnerability scanning.
  - Install: `sudo apt install nikto` or download from [Nikto GitHub](https://github.com/sullo/nikto)
- **OWASP ZAP**: For active web application scanning.
  - Install: `pip install zap-cli` (requires Python) or download from [OWASP ZAP](https://www.zaproxy.org/)
- **SQLmap**: For SQL injection testing.
  - Install: `sudo apt install sqlmap` or download from [SQLmap GitHub](https://github.com/sqlmapproject/sqlmap)

Additionally, ensure you have:
- Bash shell (pre-installed on most Linux distributions).
- Write permissions in the directory where the script is executed.

---

## Installation
1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/yourusername/cybmod2.git
   ```
2. Navigate to the repository directory:
   ```bash
   cd cybmod2
   ```
3. Make the script executable:
   ```bash
   chmod +x Cybmod2.sh
   ```

---

## Usage
Run the script and follow the prompts:
```bash
./Cybmod2.sh
```

1. **Enter the target**: Provide a valid URL (e.g., `http://example.com`) or IP address (e.g., `192.168.1.1`).
2. **Confirm the test**: Type `yes` to authorize the scan or `no` to abort.
3. **View results**: Once completed, results are saved in a directory named `vapt_results_[date_time]`.

### Example
```bash
$ ./Cybmod2.sh
Enter the target (URL or IP address): http://example.com
********************************************************************
      WARNING: You are about to initiate a Web Application          
    Penetration Test (WebVAPT) on http://example.com            
********************************************************************
Do you want to perform this test? (yes/no): yes
Authorization confirmed. Proceeding with the WebVAPT...
Starting VAPT for http://example.com
[...]
VAPT Scan Completed. You can view results in vapt_results_2025-04-06_12:00:00
```

---

## Output
The script creates a directory with the following structure:
```
vapt_results_[date_time]/
├── vapt_log.txt          # Summary log of scan progress
├── nmap_scan.txt         # Nmap scan results
├── nikto_scan.txt        # Nikto scan results (for URLs)
├── owasp_zap_scan.txt    # OWASP ZAP scan results (for URLs)
└── sqlmap_scan/          # SQLmap scan results (for URLs)
```

---

## Limitations
- Nikto, OWASP ZAP, and SQLmap scans are skipped for IP-only targets (non-URL inputs).
- Requires pre-installed tools; the script does not handle tool installation.
- Basic validation; advanced URL parameters may require manual testing.

---

## Contributing
Feel free to submit issues or pull requests to improve this script. Contributions are welcome!

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Contact
For questions or feedback, reach out via GitHub Issues or [your-email@example.com].

---

Replace `yourusername` in the installation command with your actual GitHub username, and update the contact section with your preferred contact info. Save this as `README.md` in your repository! Let me know if you need any tweaks.
