chmod +x scan/scanit.py
#!/usr/bin/env python3
./scan/scanit.py --target config/targets.txt
#!/bin/bash
echo "[*] Installing SCANIT dependencies..."
sudo apt update
sudo apt install -y nmap python3 wkhtmltopdf
echo "[+] Setup complete. You can now run scanIT using scan/scanit.py"
## 🔧 Quick Start (Kali Linux)

```bash
git clone https://github.com/Acherm4n/SCANIT-PCI-ASV-SCANNER.git
cd SCANIT-PCI-ASV-SCANNER
bash setup.sh
python3 scan/scanit.py --target config/targets.txt

---

### 4. ✅ Optional: Add a `.desktop` launcher (GUI shortcut)

Create `scanit.desktop`:
```ini
[Desktop Entry]
Name=SCANIT PCI Scanner
Exec=python3 /home/kali/SCANIT-PCI-ASV-SCANNER/scan/scanit.py --target /home/kali/SCANIT-PCI-ASV-SCANNER/config/targets.txt
Icon=utilities-terminal
Type=Application
Terminal=true
~/.local/share/applications/
git add .
git commit -m "Ready for Kali Linux deployment"
git push origin main
# 🔍 SCANIT – PCI DSS 4.0 ASV Scanner  
**Author:** John Dominick Limpag  
**Platform:** Kali Linux  
**Version:** 1.0.0  
**License:** MIT

---

## 🛡️ Overview

**SCANIT** is a lightweight PCI DSS 4.0 audit automation tool built for Kali Linux. It uses **Nmap** to perform internal scans aligned with PCI DSS requirements and generates clean, readable **HTML reports** — with optional PDF export — for compliance documentation.

---

## 🔧 Quick Start (Kali Linux)

```bash
git clone https://github.com/Acherm4n/SCANIT-PCI-ASV-SCANNER.git
cd SCANIT-PCI-ASV-SCANNER
bash setup.sh
python3 scan/scanit.py --target config/targets.txt
┌──(kali㉿scanit)-[~/SCANIT-PCI-ASV-SCANNER]
└─$ python3 scan/scanit.py --help

SCANIT – PCI DSS 4.0 Audit Tool by John Dominick Limpag

Usage:
  scanit.py --target <target_file> [--output <html_file>] [--log <log_file>] [--pdf <pdf_file>]

Options:
  --target     Path to target list file (required)
  --output     Path to output HTML report [default: reports/report.html]
  --log        Path to log file (optional)
  --pdf        Path to export PDF report (optional)
  --help       Show this help message and exit
🧪 Example Commands
🔹 Run a scan with default output
bash
python3 scan/scanit.py --target config/targets.txt
🔹 Run a scan with custom output path
bash
python3 scan/scanit.py --target config/targets.txt --output reports/custom.html
🔹 Log the scan
bash
python3 scan/scanit.py --target config/targets.txt --log logs/scan.log
🔹 Export to PDF
bash
python3 scan/scanit.py --target config/targets.txt --pdf reports/report.pdf
📁 Directory Structure
Code
SCANIT-PCI-ASV-SCANNER/
├── setup.sh
├── banner.sh
├── scan/
│   └── scanit.py
├── config/
│   └── targets.txt
├── reports/
│   └── (auto-generated files)
├── logs/
│   └── (optional log files)
├── README.md
🛡️ PCI DSS 4.0 Coverage
11.3.1.2 – Internal vulnerability scans

6.2.3 – Service discovery and patch validation

12.3.3 – Inventory of exposed services

10.4.1.1 – Audit log review (via optional logging)

📄 License
This project is licensed under the MIT License.
