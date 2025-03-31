#!/bin/bash

# Asking the user to enter the target (URL or IP)
read -p "Enter the target (URL or IP address): " TARGET

# Validating URL or IP
if [[ "$TARGET" =~ ^https?://[a-zA-Z0-9.-]+$ || "$TARGET" =~ ^[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+$ ]]; then
    echo "Valid target: $TARGET"
else
    echo "Invalid input. Please enter a valid URL (http://example.com) or IP address (e.g., 192.168.1.1)."
    exit 1
fi

# Display a disclaimer message
echo "********************************************************************"
echo "      WARNING: You are about to initiate a Web Application          "
echo "    Penetration Test (WebVAPT) on $TARGET                           "
echo "********************************************************************"

# Asking  user for confirmation
read -p "Do you want to perform this test? (yes/no): " response

# Convert the response to lowercase
response=$(echo "$response" | tr '[:upper:]' '[:lower:]')

# Check users response
if [[ "$response" != "yes" ]]; then
    echo "Permission denied or authorization not confirmed. Aborting the test."
    exit 1
fi

echo "Authorization confirmed. Proceeding with the WebVAPT..."

# Extracting the  domain name from URL entered
if [[ "$TARGET" =~ ^https?:// ]]; then
    DOMAIN=$(echo "$TARGET" | sed -E 's#https?://([^/]+).*#\1#')
else
    DOMAIN=$TARGET
fi

# Define variables for scanning
OUTPUT_DIR="vapt_results_$(date +%F_%T)"
mkdir -p "$OUTPUT_DIR"
LOGFILE="$OUTPUT_DIR/vapt_log.txt"

echo "Starting VAPT for $TARGET"
echo "VAPT Scan Report - $(date)" > "$LOGFILE"

# 1. Nmap Scan (Basic Enumeration)
echo "Starting Nmap Scan on $DOMAIN..."
nmap -sV -A -oN "$OUTPUT_DIR/nmap_scan.txt" "$DOMAIN"
echo "[+] Nmap scan completed." >> "$LOGFILE"

# 2. Nikto Scan (Web Server Vulnerability Scan)
if [[ "$TARGET" =~ ^https?:// ]]; then
    echo "Starting Nikto Scan..."
    nikto -h "$TARGET" -Tuning 4 -timeout 10 -maxrequests 200 -output "$OUTPUT_DIR/nikto_scan.txt"
    echo "[+] Optimized Nikto scan completed." >> "$LOGFILE"
else
    echo "Skipping Nikto Scan. Not applicable for IP-only targets."
fi

# 3. OWASP ZAP Scan (Active Scan)
if [[ "$TARGET" =~ ^https?:// ]]; then
    echo "Starting OWASP ZAP Scan..."
    zap-cli quick-scan --self-contained -o "$OUTPUT_DIR/owasp_zap_scan.txt" "$TARGET"
    echo "[+] OWASP ZAP scan completed." >> "$LOGFILE"
else
    echo "Skipping OWASP ZAP Scan. Not applicable for IP-only targets."
fi

# 4. SQLmap Scan (SQL Injection Test)
if [[ "$TARGET" =~ ^https?:// ]]; then
    echo "Starting SQLMap Scan..."
    sqlmap -u "$TARGET" --batch --risk=3 --level=5 --dbs --output-dir="$OUTPUT_DIR/sqlmap_scan"
    echo "[+] SQLMap scan completed." >> "$LOGFILE"
else
    echo "Skipping SQLMap Scan. Not applicable for IP-only targets."
fi

echo "VAPT Scan Completed. You can view results in $OUTPUT_DIR"

