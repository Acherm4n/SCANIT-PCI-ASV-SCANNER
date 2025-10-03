# PCI DSS Nmap Scanner
# Author:ACHERM4N
# by john dominick limpag
# Description: A simple tool to automate some PCI DSS compliance scans using Nmap.
# Disclaimer: This tool is for educational and auditing purposes only. It is not a substitute
# for a full PCI DSS audit by a qualified professional. Achieving compliance requires more
# than just running scans.

# Colors for output
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
BLUE='\033[0;34m'
NC='\033[0m' # No Color

# Function to display the main menu
show_menu() {
    echo -e "${GREEN}"
    echo "   _________                      __  __      "
    echo "  /   _____/ ____ _____  ______ _/  |_|__| ____"
    echo "  \_____  \ /    \\__  \ \____ \\   __\  |/ __ \\"
    echo "  /        \   |  \/ __ \|  |_> >|  | |  \  ___/"
    echo " /_______  /___|  (____  /   __/ |__| |__|\___  >"
    echo "         \/     \/     \/|__|               \/"
    echo -e "${NC}"
    echo -e "${BLUE}=====================================================${NC}"
    echo -e "${YELLOW}         PCI DSS Nmap Compliance Scanner             ${NC}"
    echo -e "${BLUE}=====================================================${NC}"
    echo "1. Discover Live Hosts (Requirement 1.1.2)"
    echo "2. Full Port Scan on a Single Host (Reqs 1.1.2, 2.2.4)"
    echo "3. Scan for Weak SSL/TLS Ciphers (Reqs 2.3, 4.1)"
    echo "4. Basic Vulnerability Scan (Req 11.2.1)"
    echo "5. Firewall & IDS/IPS Evasion Test (Req 1.2.1, 1.3.4)"
    echo "6. Exit"
    echo -e "${BLUE}=====================================================${NC}"
}

# Function to get target IP or range
get_target() {
    read -p "Enter target IP address or range (e.g., 192.168.1.1 or 192.168.1.0/24): " TARGET
    if [ -z "$TARGET" ]; then
        echo -e "${YELLOW}Target cannot be empty.${NC}"
        get_target
    fi
}

# Function for Host Discovery
discover_hosts() {
    get_target
    echo -e "${GREEN}Starting host discovery on ${TARGET}...${NC}"
    OUTPUT_FILE="host_discovery_$(date +%Y%m%d_%H%M%S).txt"
    nmap -sn -oN "$OUTPUT_FILE" "$TARGET"
    echo -e "${GREEN}Host discovery complete. Results saved to ${OUTPUT_FILE}${NC}"
}

# Function for Full Port Scan
full_port_scan() {
    get_target
    echo -e "${GREEN}Starting full port scan on ${TARGET}... (This may take a while)${NC}"
    OUTPUT_FILE="full_port_scan_${TARGET}_$(date +%Y%m%d_%H%M%S).txt"
    nmap -p- -sV -O -oN "$OUTPUT_FILE" "$TARGET"
    echo -e "${GREEN}Full port scan complete. Results saved to ${OUTPUT_FILE}${NC}"
}

# Function to scan for weak SSL/TLS ciphers
ssl_scan() {
    get_target
    echo -e "${GREEN}Scanning for weak SSL/TLS ciphers on ${TARGET}...${NC}"
    OUTPUT_FILE="ssl_scan_${TARGET}_$(date +%Y%m%d_%H%M%S).txt"
    nmap --script ssl-enum-ciphers -p 443 -oN "$OUTPUT_FILE" "$TARGET"
    echo -e "${GREEN}SSL/TLS scan complete. Results saved to ${OUTPUT_FILE}${NC}"
}

# Function for basic vulnerability scan
vuln_scan() {
    get_target
    echo -e "${GREEN}Starting basic vulnerability scan on ${TARGET}...${NC}"
    OUTPUT_FILE="vuln_scan_${TARGET}_$(date +%Y%m%d_%H%M%S).txt"
    nmap --script vuln -sV -oN "$OUTPUT_FILE" "$TARGET"
    echo -e "${GREEN}Vulnerability scan complete. Results saved to ${OUTPUT_FILE}${NC}"
}

# Function for Firewall & IDS/IPS Evasion Test
firewall_test() {
    get_target
    echo -e "${GREEN}Starting Firewall/IDS Evasion test on ${TARGET}...${NC}"
    echo -e "${YELLOW}Note: These scans can be aggressive and might trigger alerts.${NC}"
    OUTPUT_FILE="firewall_test_${TARGET}_$(date +%Y%m%d_%H%M%S).txt"
    # Using a fragmented packet scan
    nmap -f -sV --scan-delay 1s -oN "$OUTPUT_FILE" "$TARGET"
    echo -e "${GREEN}Firewall/IDS test complete. Results saved to ${OUTPUT_FILE}${NC}"
}

# Main loop
while true; do
    show_menu
    read -p "Select an option [1-6]: " choice
    case $choice in
        1)
            discover_hosts
            ;;
        2)
            full_port_scan
            ;;
        3)
            ssl_scan
            ;;
        4)
            vuln_scan
            ;;
        5)
            firewall_test
            ;;
        6)
            echo "Exiting."
            break
            ;;
        *)
            echo -e "${YELLOW}Invalid option. Please try again.${NC}"
            ;;
    esac
    echo ""
done





