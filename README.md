# Vulnerability Managment on Windows 10 VM using Nessus
<h2>Table of Contents</h2>

<h2>Features</h2>

- Using and configuring Nessus Essentials on Linux Mint
- Scanning a Windows 10 virtual machine for potential vulnerabilities
- Remidiating any found critical vulnerabilites on the VM

<h2>Prerequisites</h2>

- Internet Connection
- Nessus Version 10.8.3
- VMWare Workstation
- Windows 10 Home ISO Image

<h2>Setting up the Windows 10 VM for a Credential Scan</h2>

Note: the Windows Defender Firewall is turned off on the VM for this project due to the Linux Mint system and the Windows VM not being on the same domain. This allows Nessus to scan for vulnrabilities without needing to join them both to the same domian.
- To setup the VM for a Nessus credential scan, I first went to Services using the search function on the taskbar, and then set Remote Registry to automatic.

